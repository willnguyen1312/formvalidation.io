<svelte:head>
	<title>FormValidation • v0.5.1</title>
</svelte:head>

<ChangelogLayout>
    <h1 class="f3 f2-m f1-l tc">Version 0.5.1</h1>
    <h2 class="f4 fw4 tc">Released 22 August 2014</h2>

    <section class="mv5">
        <Heading>New features</Heading>
        <ul class="pa0 ma0 ml3 lh-copy">
            <li>Add <a href="/guide/validators/meid" class="blue dim link">meid validator</a></li>
            <li>Add <a href="/guide/validators/imo" class="blue dim link">imo validator</a></li>
            <li>Add French <a href="/guide/validators/phone" class="blue dim link">phone number</a> validator</li>
            <li>Add Spanish <a href="/guide/validators/phone" class="blue dim link">phone number</a> validator</li>
            <li>Add Iceland <a href="/guide/validators/vat" class="blue dim link">VAT</a> number validator</li>
            <li>Add Pakistan <a href="/guide/validators/phone" class="blue dim link">phone number</a> validator</li>
            <li>Add event name options to avoid window.onerror being invoked by jQuery</li>
            <li>Add South African <a href="/guide/validators/vat" class="blue dim link">VAT</a> number validator</li>
            <li>Add Brazilian <a href="/guide/validators/phone" class="blue dim link">phone number</a> and <a href="/guide/validators/zip-code" class="blue dim link">postal code</a> validator</li>
            <li>Add <a href="/guide/validators/zip-code/">zipCode</a> and <a href="/guide/validators/phone" class="blue dim link">phone number</a> validators for Morocco</li>
            <li>Add Brazilian <a href="/guide/validators/vat" class="blue dim link">VAT</a> number validator</li>
        </ul>
    </section>

    <section class="mv5">
        <Heading>Improvements</Heading>
        <ul class="pa0 ma0 ml3 lh-copy">
            <li>Allowing sites without TLD to pass URI validation</li>
            <li>Change the CSS/JS path in <code>demo/remote.html</code> and <code>demo/message.html</code></li>
            <li>Fix the <code>demo/date.html</code> and <code>demo/tab.html</code> examples</li>
            <li>Add content-type header for <code>demo/remote.php</code></li>
            <li>Add <code>headers</code> option to the <a href="/guide/validators/remote" class="blue dim link">remote</a> validator</li>
            <li>Fix the feedback icon position for Bootstrap 3.2</li>
            <li>Force the format option to be <code>YYYY-MM-DD</code> when using <code>&lt;input type="date" /&gt;</code></li>
            <li>Ignore type checking if the file type is empty</li>
        </ul>
    </section>

    <section class="mv5">
        <Heading>Bug fixes</Heading>
        <ul class="pa0 ma0 ml3 lh-copy">
            <li>The HTML 5 <code>&lt;input type="number" /&gt;</code> input allows to input non-digits characters</li>
            <li>Fix the issue when using <a href="/guide/validators/different" class="blue dim link">different</a> validator to compare with not existing field</li>
            <li>Cannot validate against both ipv4 and ipv6 at the same time</li>
            <li>Don't use min, max attributes (greaterThan, lessThan validators) for <code>&lt;input type="date" /&gt;</code></li>
            <li>The <code>submitButtons</code> option doesn't work correctly</li>
            <li>The <a href="/guide/validators/zip-code" class="blue dim link">zipCode</a> validator throw an exception when passing not supported country code</li>
            <li>Fix the <a href="/guide/validators/date" class="blue dim link">date</a> validator issue where one of date/month/year or hours/minutes/seconds is prefixed by zero</li>
            <li>The <a href="/guide/validators/remote" class="blue dim link">remote</a> validator can't set the type option via HTML attribute</li>
            <li>The <a href="/guide/validators/between" class="blue dim link">between</a>, <a href="/guide/validators/greater-than/">greaterThan</a>, <a href="/guide/validators/less-than" class="blue dim link">lessThan</a> validators accept param which isn't number</li>
        </ul>
    </section>
</ChangelogLayout>

<script>
import ChangelogLayout from '../../../components/ChangelogLayout.svelte';
import Heading from '../../../components/Heading.svelte';
</script>