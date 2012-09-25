---
layout: post
title: Mobile web - CSS appearance property on Symbian default browser
desc: Mobile web - CSS appearance property on Symbian default browser.
---

Good to know that you can't fully style input types: button, submit, reset, file on Symbian^3 default browser.

By default they use <abbr>-webkit-appearance</abbr> property. This property was instoduced in 2004 but was dropped in CSS3 spec: <a href="http://wiki.csswg.org/spec/css4-ui#dropped-css3-features" target="_blank">dropped-css3-features</a>.

In theory, the appearance property is used to make an element look like a standard user interface element on the platform, but it doesn't work that way at all.
Moreover, you can't adjust look of html elements to your project, because property, such as background is ignored.

In the <a href="http://www.developer.nokia.com/Resources/Library/Web/nokia-browsers/symbian-browsers/default-css-style-sheet.html" target="_blank">Symbian Browser spec</a> you can find that <abbr>-webkit-appearance</abbr> property has a value of <abbr>push-button</abbr>.

To resolve the problem you have to change its value to <abbr>initial</abbr>, and other CSS properties will work as you expecting.

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

