<style>
pre {
    min-height: 34px;
}
:global(.hljs) {
    padding: .5rem;
}
</style>

{#if highlighted}
<div class="relative">
    <BrowserFrame><pre class="pa0 ma0 lh-copy" style="max-height: {maxHeight}; overflow-y: scroll;" bind:this={codeEle}></pre></BrowserFrame>
</div>
{:else}
<div class="ba b--black-10 bg-washed-blue pa0 ma0">
    <Loader><pre><code>{@html code}</code></pre></Loader>
</div>
{/if}

<script>
import { afterUpdate, onMount } from 'svelte';

import highlight from './helpers/highlight';
import BrowserFrame from './BrowserFrame.svelte';
import Loader from './Loader.svelte';

let highlighted = '';
let copied = false;
let codeEle;

// Public props
let code = '';
let lang = 'html';
let maxHeight = '';

$: {
    highlighted = highlight(
        // Replace the fake tags with the real one
        // If I use <link> or <script> tag inside sample code, Sapper tries to load them
        code.replace(/link-tag/g, 'link')
            .replace(/script-tag/g, 'script')
            .replace(/fix-html-id/g, 'id'),
        lang
    );
    if (codeEle) {
        codeEle.innerHTML = highlighted;
    }
}

const copy = () => {
    const selection = window.getSelection();
    const range = document.createRange();
    range.selectNodeContents(codeEle);
    selection.removeAllRanges();
    selection.addRange(range);
    document.execCommand('copy');

    copied = true;

    selection.removeAllRanges();
};

export {
    code,
    lang,
    maxHeight,
};
</script>
