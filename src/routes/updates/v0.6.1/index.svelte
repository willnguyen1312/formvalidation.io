<svelte:head>
	<title>FormValidation • v0.6.1</title>
</svelte:head>

<ChangelogLayout>
    <h1 class="f3 f2-m f1-l tc">Version 0.6.1</h1>
    <h2 class="f4 fw4 tc">Released 24 February 2015</h2>

    <section class="mv5">
        <Heading>New features</Heading>
        <ul class="pa0 ma0 ml3 lh-copy">
            <li>Add <code>dataType</code>, <code>crossDomain</code>, <code>validKey</code> options for <a href="/guide/validators/remote" class="blue dim link">remote</a> validator.</li>
            <li>It's possible to use remote validator to connect to external validator API, such as MailGun.</li>
            <li>In addition to Bootstrap, Foundation, Pure, Semantic, UIKit, v0.6.1 provides the ability of supporting custom framework</li>
            <li>Add <code>declarative</code> option to support big form</li>
            <li>Add Netherlands <a href="/guide/validators/phone" class="blue dim link">phone</a> validator</li>
            <li>Add Bulgarian <a href="/guide/validators/zip-code" class="blue dim link">zip code</a> validator</li>
            <li>Add Bulgarian <a href="/guide/validators/phone" class="blue dim link">phone number</a> validator</li>
            <li>Add Polish <a href="/guide/validators/zip-code/">zip code</a> and <a href="/guide/validators/id" class="blue dim link">id</a> validators</li>
        </ul>
    </section>

    <section class="mv5">
        <Heading>Improvements</Heading>
        <ul class="pa0 ma0 ml3 lh-copy">
            <li>The <a href="/guide/validators/remote" class="blue dim link">remote</a> validator fails if Ajax request fails</li>
            <li>Update Netherlands <a href="/guide/validators/phone" class="blue dim link">phone number</a> validator</li>
            <li>Add plugin instance to the 3rd parameter of transformer callback</li>
            <li>Add Grunt task that runs the jasmine test suites</li>
        </ul>
    </section>

    <section class="mv5">
        <Heading>Bug fixes</Heading>
        <p class="lh-copy">This version fixed the <code>isValid()</code> method which should return <code>null</code> when there is not validated or being validated field.
            It also solves the issues where the submit button is disabled even when the form is valid.</p>

        <ul class="pa0 ma0 ml3 lh-copy">
            <li>remote validator and <code>isValid()</code> combined do not work</li>
            <li>Submit button is disabled</li>
            <li>Submit button being disabled</li>
            <li>Can only submit form after changing a value</li>
            <li>Remote validation trigger <code>err.form.fv</code></li>
            <li>Submit incorrectly enabled even though form has errors</li>
            <li>Show the <code>validating</code> icon when the field is being validated</li>
            <li>Reset checkbox when calling <code>resetForm()</code> method</li>
            <li>Fix Slovakia <a href="/guide/validators/phone" class="blue dim link">phone number</a> validator</li>
            <li>Fix the issue where custom validator doesn't provide default message</li>
            <li>Don't continue if there is no validators attached to fields</li>
            <li><code>transformer</code> option doesn't work with <a href="/guide/validators/not-empty" class="blue dim link">notEmpty</a> validator</li>
            <li>Fix <code>isValidContainer()</code> and <code>validateContainer()</code> methods to support fields with the same name</li>
        </ul>
    </section>
</ChangelogLayout>

<script>
import ChangelogLayout from '../../../components/ChangelogLayout.svelte';
import Heading from '../../../components/Heading.svelte';
</script>