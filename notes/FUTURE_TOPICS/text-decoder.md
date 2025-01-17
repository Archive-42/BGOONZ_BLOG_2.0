EN

-   <a href="https://ar.javascript.info/"
-   <a href="text-decoder.html"
-   <a href="https://es.javascript.info/text-decoder"
-   <a href="https://fr.javascript.info/text-decoder"
-   <a href="https://it.javascript.info/text-decoder"
    text-decoder"

<!-- -->

-   <a href="https://ko.javascript.info/text-decoder"
-   <a href=text-decoder"
-   <a href="https://tr.javascript.info/text-decoder"
    ext-decoder"

We want to make this open-source project available for people all around the world.

[Help to translate](translate.html) the content of this tutorial to your language!

<a href="index.html" class="sitetoolbar__link sitetoolbar__link_logo"><img src="img/sitetoolbar__logo_en.svg" class="sitetoolbar__logo sitetoolbar__logo_normal" width="200" /><img src="img/sitetoolbar__logo_small_en.svg" class="sitetoolbar__logo sitetoolbar__logo_small" width="70" /></a>

<a href="ebook.html" class="buy-book-button"><span class="buy-book-button__extra-text">Buy</span>EPUB/PDF</a>

Search

Search

<a href="tutorial/map.html" class="map">

<span class="share-icons__title">Share</span><a href="https://twitter.com/share?url=https%3A%2F%2Fjavascript.info%2Ftext-decoder" class="share share_tw"></a><a href="https://www.facebook.com/sharer/sharer.php?s=100&amp;p%5Burl%5D=https%3A%2F%2Fjavascript.info%2Ftext-decoder" </a>

1.  <a href="index.html" class="breadcrumbs__link"><span class="breadcrumbs__hidden-text">Tutorial</span></a>
2.  <span id="breadcrumb-1"><a href="binary.html" Binary data, files</span></a></span>

7th December 2020

# TextDecoder and TextEncoder

What if the binary data is actually a string? For instance, we received a file with textual data.

The build-in [TextDecoder](https://encoding.spec.whatwg.org/#interface-textdecoder) object allows to read the value into an actual JavaScript string, given the buffer and the encoding.

We first need to create it:

    let decoder = new TextDecoder([label], [options]);

-   **`label`** – the encoding, `utf-8` by default, but `big5`, `windows-1251` and many other are also supported.
-   **`options`** – optional object:
    -   **`fatal`** – boolean, if `true` then throw an exception for invalid (non-decodable) characters, otherwise (default) replace them with character `\uFFFD`.
    -   **`ignoreBOM`** – boolean, if `true` then ignore BOM (an optional byte-order Unicode mark), rarely needed.

…And then decode:

    let str = decoder.decode([input], [options]);

-   **`input`** – `BufferSource` to decode.
-   **`options`** – optional object:
    -   **`stream`** – true for decoding streams, when `decoder` is called repeatedly with incoming chunks of data. In that case a multi-byte character may occasionally split between chunks. This options tells `TextDecoder` to memorize “unfinished” characters and decode them when the next chunk comes.

For instance:

<a href="text-decoder.html#"
<a href="text-decoder.html#" class="toolbar__button toolbar__button_edit" title="open in sandbox"></a>

    let uint8Array = new Uint8Array([72, 101, 108, 108, 111]);

    alert( new TextDecoder().decode(uint8Array) ); // Hello

<a href="text-decoder.html#"
<a href="text-decoder.html#" class="toolbar__button toolbar__button_edit" title="open in sandbox"></a>

    let uint8Array = new Uint8Array([228, 189, 160, 229, 165, 189]);

    alert( new TextDecoder().decode(uint8Array) ); // 你好

We can decode a part of the buffer by creating a subarray view for it:

<a href="text-decoder.html#"
<a href="text-decoder.html#" class="toolbar__button toolbar__button_edit" title="open in sandbox"></a>

    let uint8Array = new Uint8Array([0, 72, 101, 108, 108, 111, 0]);

    // the string is in the middle
    // create a new view over it, without copying anything
    let binaryString = uint8Array.subarray(1, -1);

    alert( new TextDecoder().decode(binaryString) ); // Hello

## <a href="text-decoder.html#textencoder" id="textencoder" class="main__anchor">TextEncoder</a>

[TextEncoder](https://encoding.spec.whatwg.org/#interface-textencoder) does the reverse thing – converts a string into bytes.

The syntax is:

    let encoder = new TextEncoder();

The only encoding it supports is “utf-8”.

It has two methods:

-   **`encode(str)`** – returns `Uint8Array` from a string.
-   **`encodeInto(str, destination)`** – encodes `str` into `destination` that must be `Uint8Array`.

<a href="text-decoder.html#"
<a href="text-decoder.html#" class="toolbar__button toolbar__button_edit" title="open in sandbox"></a>

    let encoder = new TextEncoder();

    let uint8Array = encoder.encode("Hello");
    alert(uint8Array); // 72,101,108,108,111

<a href="arraybuffer-binary-arrays.html" class="page__nav page__nav_prev"><span class="page__nav-text"><span class="page__nav-text-shortcut"></span></span><span class="page__nav-text-alternate">Previous lesson</span></a><a href="blob.html" class="page__nav page__nav_next"><span class="page__nav-text"><span class="page__nav-text-shortcut"></span></span><span class="page__nav-text-alternate">Next lesson</span></a>

<span class="share-icons__title">Share</span><a href="https://twitter.com/share?url=https%3A%2F%2Fjavascript.info%2Ftext-decoder" class="share share_tw"></a><a href="https://www.facebook.com/sharer/sharer.php?s=100&amp;p%5Burl%5D=https%3A%2F%2Fjavascript.info%2Ftext-decoder" </a>

<a href="tutorial/map.html" class="map">

## <a href="text-decoder.html#comments" id="comments">Comments</a>

<span class="comments__read-before-link">read this before commenting…</span>

-   If you have suggestions what to improve - please [submit a GitHub issue](https://github.com/javascript-tutorial/en.javascript.info/issues/new) or a pull request instead of commenting.
-   If you can't understand something in the article – please elaborate.
-   To insert few words of code, use the `<code>` tag, for several lines – wrap them in `<pre>` tag, for more than 10 lines – use a sandbox ([plnkr](https://plnkr.co/edit/?p=preview), [jsbin](https://jsbin.com), [codepen](http://codepen.io)…)

<a href="tutorial/map.html" class="map"></a>

#### Chapter

-   <a href="binary.html" class="sidebar__link">Binary data, files</a>

#### Lesson navigation

-   <a href="text-decoder.html#textencoder" class="sidebar__link">TextEncoder</a>

-   <a href="text-decoder.html#comments" class="sidebar__link">Comments</a>

Share

<a href="https://twitter.com/share?url=https%3A%2F%2Fjavascript.info%2Ftext-decoder" class="share share_tw sidebar__share"></a><a href="https://www.facebook.com/sharer/sharer.php?s=100&amp;p%5Burl%5D=https%3A%2F%2Fjavascript.info%2Ftext-decoder" class="share share_fb sidebar__share"></a>

<a href="https://github.com/javascript-tutorial/en.javascript.info/blob/master/4-binary/02-text-decoder" class="sidebar__link">Edit on GitHub</a>

-   <a href="about.html" class="page-footer__link">about the project</a>
-   <a href="about.html#contact-us" class="page-footer__link">contact us</a>
-   <a href="terms.html" class="page-footer__link">terms of usage</a>
-   <a href="privacy.html" class="page-footer__link">privacy policy</a>
