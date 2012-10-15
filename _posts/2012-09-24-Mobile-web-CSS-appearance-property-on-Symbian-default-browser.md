---
layout: post
title: Mobile web - CSS appearance property on Symbian default browser
desc: Mobile web - CSS appearance property on Symbian default browser.
---

Good to know that you can't fully style input types: button, submit, reset, file on Symbian^3 default browser.

By default they use <code>-webkit-appearance</code> property. This property was introduced in 2004 but then was dropped in CSS3 spec: <a href="http://wiki.csswg.org/spec/css4-ui#dropped-css3-features" target="_blank">dropped-css3-features</a>.

In theory, the appearance property is used to make an element look like a standard user interface element on the platform, but it doesn't work that way at all.
Moreover, you can't adjust the look of html elements to your project because a property, such as background is ignored.

In the <a href="http://www.developer.nokia.com/Resources/Library/Web/nokia-browsers/symbian-browsers/default-css-style-sheet.html" target="_blank">Symbian Browser spec</a> you can find that <code>-webkit-appearance</code> property has a value of <code>push-button</code>.

To resolve the problem you have to change its value to <code>initial</code>, and other CSS properties will work as expected.

<pre>
<code>
    input[type="button"],
    input[type="submit"],
    input[type="reset"],
    input[type="file"]::-webkit-file-upload-button {
    -webkit-appearance: initial;
    }
</code>
</pre>

