<h1>>Images in HTML</h2>

**How do we put an image on a webpage?**
In order to put a simple image on a web page, we use the <img> element. This is a void element (meaning, it cannot have any child content and cannot have an end tag) that requires two attributes to be useful: src and alt. The src attribute contains a URL pointing to the image you want to embed in the page. As with the href attribute for <a> elements, the src attribute can be a relative URL or an absolute URL. Without a src attribute, an img element has no image to load.

**NOTE**: Elements like <img> and <video> are sometimes referred to as replaced elements. This is because the element's content and size are defined by an external resource (like an image or video file), not by the contents of the element itself.

**Alternative text**
The next attribute we'll look at is alt. Its value is supposed to be a textual description of the image, for use in situations where the image cannot be seen/displayed or takes a long time to render because of a slow internet connection.

The easiest way to test your alt text is to purposely misspell your filename. If for example our image name was spelled dinosooooor.jpg, the browser wouldn't display the image, and would display the alt text instead.

So, why would you ever see or need alt text? It can come in handy for a number of reasons:

The user is visually impaired, and is using a screen reader to read the web out to them. In fact, having alt text available to describe images is useful to most users.

As described above, the spelling of the file or path name might be wrong.

The browser doesn't support the image type. Some people still use text-only browsers, such as Lynx, which displays the alt text of images.

You may want to provide text for search engines to utilize; for example, search engines can match alt text with search queries.

Users have turned off images to reduce data transfer volume and distractions. This is especially common on mobile phones, and in countries where bandwidth is limited or expensive.

What exactly should you write inside your alt attribute? It depends on why the image is there in the first place. In other words, what you lose if your image doesn't show up:

Decoration. You should use CSS background images for decorative images, but if you must use HTML, add a blank alt="". If the image isn't part of the content, a screen reader shouldn't waste time reading it.

Content. If your image provides significant information, provide the same information in a brief alt text – or even better, in the main text which everybody can see. Don't write redundant alt text. How annoying would it be for a sighted user if all paragraphs were written twice in the main content? If the image is described adequately by the main text body, you can just use alt="".

Link. If you put an image inside <a> tags, to turn an image into a link, you still must provide accessible link text. In such cases you may, either, write it inside the same <a> element, or inside the image's alt attribute – whichever works best in your case.

Text. You should not put your text into images. If your main heading needs a drop shadow, for example, use CSS for that rather than putting the text into an image. However, If you really can't avoid doing this, you should supply the text inside the alt attribute.

**Width and height**
You can use the width and height attributes to specify the width and height of your image. You can find your image's width and height in a number of ways. For example on the Mac you can use Cmd + I to get the info display up for the image file.

However, you shouldn't alter the size of your images using HTML attributes. If you set the image size too big, you'll end up with images that look grainy, fuzzy, or too small, and wasting bandwidth downloading an image that is not fitting the user's needs. The image may also end up looking distorted, if you don't maintain the correct aspect ratio. You should use an image editor to put your image at the correct size before putting it on your webpage.

**NOTE**: If you do need to alter an image's size, you should use CSS instead.

**Image titles**
As with links, you can also add title attributes to images, to provide further supporting information if needed.

However, this is not recommended — title has a number of accessibility problems, mainly based around the fact that screen reader support is very unpredictable and most browsers won't show it unless you are hovering with a mouse (so e.g. no access to keyboard users).

**Annotating images with figures and figure captions**

A better solution, is to use the HTML <figure> and <figcaption> elements. These are created for exactly this purpose: to provide a semantic container for figures, and to clearly link the figure to the caption.

The <figcaption> element tells browsers, and assistive technology that the caption describes the other content of the <figure> element.

A figure doesn't have to be an image. It is an independent unit of content that:

Expresses your meaning in a compact, easy-to-grasp way.
Could go in several places in the page's linear flow.
Provides essential information supporting the main text.
A figure could be several images, a code snippet, audio, video, equations, a table, or something else.

CSS background images
You can also use CSS to embed images into webpages (and JavaScript, but that's another story entirely). The CSS background-image property, and the other background-* properties, are used to control background image placement.

The resulting embedded image is arguably easier to position and control than HTML images. So why bother with HTML images? As hinted to above, CSS background images are for decoration only. If you just want to add something pretty to your page to enhance the visuals, this is fine. Though, such images have no semantic meaning at all. They can't have any text equivalents, are invisible to screen readers, and so on. This is where HTML images shine!

Summing up: if an image has meaning, in terms of your content, you should use an HTML image. If an image is purely decoration, you should use CSS background images.

