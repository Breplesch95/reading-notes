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

**Common image file types**
The image file formats that are most commonly used on the web are listed below.

APNG - Animated Portable Network Graphics - image/apng - .apng - Good choice for lossless animation sequences (GIF is less performant). AVIF and WebP have better performance but less broad browser support.
Supported: Chrome, Edge, Firefox, Opera, Safari.

AVIF - AV1 Image File Format - image/avif - .avif	
Good choice for both images and animated images due to high performance and royalty free image format. It offers much better compression than PNG or JPEG with support for higher color depths, animated frames, transparency, etc. Note that when using AVIF, you should include fallbacks to formats with better browser support (i.e. using the <picture> element).
Supported: Chrome, Firefox (still images only: animated images not implemented), Opera, Safari.

GIF	Graphics Interchange Format	image/gif - .gif - Good choice for simple images and animations. Prefer PNG for lossless and indexed still images, and consider WebP, AVIF or APNG for animation sequences.
Supported: Chrome, Edge, Firefox, IE, Opera, Safari.

JPEG - Joint Photographic Expert Group image - image/jpeg - .jpg, .jpeg, .jfif, .pjpeg, .pjp -
Good choice for lossy compression of still images (currently the most popular). Prefer PNG when more precise reproduction of the image is required, or WebP/AVIF if both better reproduction and higher compression are required.
Support: Chrome, Edge, Firefox, IE, Opera, Safari.

PNG	Portable Network Graphics - image/png - .png -
PNG is preferred over JPEG for more precise reproduction of source images, or when transparency is needed. WebP/AVIF provide even better compression and reproduction, but browser support is more limited.
Support: Chrome, Edge, Firefox, IE, Opera, Safari.

VG - Scalable Vector Graphics - image/svg+xml - .svg - Vector image format; ideal for user interface elements, icons, diagrams, etc., that must be drawn accurately at different sizes.
Support: Chrome, Edge, Firefox, IE, Opera, Safari.

WebP - Web Picture format - image/webp  .webp - Excellent choice for both images and animated images. WebP offers much better compression than PNG or JPEG with support for higher color depths, animated frames, transparency etc. AVIF offers slightly better compression, but is not quite as well-supported in browsers and does not support progressive rendering.
Support: Chrome, Edge, Firefox, Opera, Safari

**NOTE**: The older formats like PNG, JPEG, GIF have poor performance compared to newer formats like WebP and AVIF, but enjoy broader "historical" browser support. The newer image formats are seeing increasing popularity as browsers without support become increasingly irrelevant (i.e. have virtually zero market share).

BMP	Bitmap file	image/bmp	.bmp	Chrome, Edge, Firefox, IE, Opera, Safari

CO	Microsoft Icon	image/x-icon	.ico, .cur	Chrome, Edge, Firefox, IE, Opera, Safari

TIFF	Tagged Image File Format	image/tiff	.tif, .tiff	Safari

APNG (Animated Portable Network Graphics)
APNG is a file format first introduced by Mozilla which extends the PNG standard to add support for animated images. Conceptually similar to the animated GIF format which has been in use for decades, APNG is more capable in that it supports a variety of color depths, whereas animated GIF supports only 8-bit indexed color.

APNG is ideal for basic animations that do not need to synchronize to other activities or to a sound track, such as progress indicators, activity throbbers, and other animated sequences.

AVIF image
AV1 Image File Format (AVIF) is a powerful, open source, royalty-free file format that encodes AV1 bitstreams in the High Efficiency Image File Format (HEIF) container.

AV1 is a coding format that was originally designed for video transmission over the Internet. The format benefits from the significant advances in video encoding in recent years, and may potentially benefit from the associated support for hardware rendering. However it also has disadvantages for some cases, as video and image encoding have some different requirements.

The format offers:

Excellent lossy compression compared to JPG and PNG for visually similar compression levels (e.g. lossy AVIF images are around 50% smaller than JPEG images).

Generally, AVIF has better compression than WebP — median 50% vs. 30% compression for the same JPG set (source: AVIF WebP Comparison (CTRL Blog)).
Lossless compression.

Animation/multi-image storage (similar to animated GIFs, but with much better compression)
Alpha channel support (i.e. for transparency).

High Dynamic Range (HDR): support for storing images that can represent bigger contrasts between the lightest and darkest parts of the image.

Wide Color Gamut: Support for images that can contain a larger range of colors.

AVIF does not support progressive rendering, so files must be fully downloaded before they can be displayed. This often has little impact on real-world user experience because AVIF files are much smaller than the equivalent JPEG or PNG files, and hence can be downloaded and displayed much faster. For larger file size the impact can become significant, and you should consider using a format that supports progressive rendering.

BMP (Bitmap file)
The BMP (Bitmap image) file type is most prevalent on Windows computers, and is generally used only for special cases in web apps and content.

**NOTE**: You should typically avoid using BMP files for web site content. The most common form of BMP file represents the data as an uncompressed raster image, resulting in large file sizes compared to png or jpg image types. More efficient BMP formats exist but are not widely used, and rarely supported in web browsers.

BMP theoretically supports a variety of internal data representations. The simplest, and most commonly used, form of BMP file is an uncompressed raster image, with each pixel occupying 3 bytes representing its red, green, and blue components, and each row padded with 0x00 bytes to a multiple of 4 bytes wide.

While other data representations are defined in the specification, they are not widely used and often completely unimplemented. These features include: support for different bit depths, indexed color, alpha channels, and different pixel orders (by default, BMP is written from bottom-left corner toward the right and top, rather than from the top-left corner toward the right and bottom).

Theoretically, several compression algorithms are supported, and the image data can also be stored in JPEG or PNG format within the BMP file.

GIF (Graphics Interchange Format)
In 1987, the CompuServe online service provider introduced the GIF (Graphics Interchange Format) image file format to provide a compressed graphics format that all members of their service would be able to use. GIF uses the Lempel-Ziv-Welch (LZW) algorithm to losslessly compress 8-bit indexed color graphics. GIF was one of the first two graphics formats supported by HTML, along with XBM.

Each pixel in a GIF is represented by a single 8-bit value serving as an index into a palette of 24-bit colors (8 bits each of red, green, and blue). The length of a color table is always a power of 2 (that is, each palette has 2, 4, 8, 16, 32, 64, or 256 entries). To simulate more than 255 or 256 colors, dithering is generally used. It is technically possible to tile multiple image blocks, each with its own color palette, to create truecolor images, but in practice this is rarely done.

Pixels are opaque, unless a specific color index is designated as transparent, in which case pixels colored that value are entirely transparent.

GIF supports simple animation, in which following an initial full-size frame, a series of images reflecting the parts of the image that change with each frame are provided.

Another popular feature of GIF is support for interlacing, where rows of pixels are stored out of order so that partially-received files can be displayed in lower quality. This is particularly useful when network connections are slow.

GIF is a good choice for simple images and animations, although converting full color images to GIF can result in unsatisfactory dithering. Typically, modern content should use PNG for lossless and indexed still images, and should consider using APNG for lossless animation sequences.

JPEG (Joint Photographic Experts Group image)
The JPEG (typically pronounced "jay-peg") image format is currently the most widely used lossy compression format for still images. It's particularly useful for photographs; applying lossy compression to content requiring sharpness, like diagrams or charts, can produce unsatisfactory results.

JPEG is actually a data format for compressed photos, rather than a file type. The JFIF (JPEG File Interchange Format) specification describes the format of the files we think of as "JPEG" images.

PNG (Portable Network Graphics)
The PNG (pronounced "ping") image format uses lossless compression, while supporting higher color depths than GIF and being more efficient, as well as featuring full alpha transparency support.

PNG is widely supported, with all major browsers offering full support for its features. Internet Explorer, which introduced PNG support in versions 4–5, did not fully support it until IE 9, and had many infamous bugs for many of the intervening years, including in the once-omnipresent Internet Explorer 6. This slowed PNG adoption, but it is now commonly used, especially when precise reproduction of the source image is needed.

SVG (Scalable Vector Graphics)
SVG is an XML-based vector graphics format that specifies the contents of an image as a set of drawing commands that create shapes, lines, apply colors, filters, and so forth. SVG files are ideal for diagrams, icons, and other images which can be accurately drawn at any size. As such, SVG is popular for user interface elements in modern Web design.

SVG files are text files containing source code that, when interpreted, draws the desired image.

SVG can be used in web content in two ways:

You can directly write the <svg> element within the HTML, containing SVG elements to draw the image.

You can display an SVG image anywhere you can use any of the other image types, including with the <img> and <picture> elements, the background-image CSS property, and so forth.

SVG is an ideal choice for images which can be represented using a series of drawing commands, especially if the size at which the image will be rendered is unknown or may vary, since SVG will smoothly scale to the desired size. It's not generally useful for strictly bitmap or photographic images, although it is possible to include bitmap images within an SVG.

TIFF (Tagged Image File Format)
TIFF is a raster graphics file format which was created to store scanned photos, although it can be any kind of image. It is a somewhat "heavy" format, in that TIFF files have a tendency to be larger than images in other formats. This is because of the metadata often included, as well as the fact that most TIFF images are either uncompressed or use compression algorithms that still leave fairly large files after compression.

TIFF supports a variety of compression methods, but the most commonly used are the CCITT Group 4 (and, for older fax systems, Group 3) compression systems used for by fax software, as well as LZW and lossy JPEG compression.

WebP image
WebP supports lossy compression via predictive coding based on the VP8 video codec, and lossless compression that uses substitutions for repeating data. Lossy WebP images average 25–35% smaller than JPEG images of visually similar compression levels. Lossless WebP images are typically 26% smaller than the same images in PNG format.

WebP also supports animation: in a lossy WebP file, the image data is represented by a VP8 bitstream, which may contain multiple frames. Lossless WebP holds the ANIM chunk, which describes the animation, and the ANMF chunk, which represents a frame of an animation sequence. Looping is supported.

**Choosing an image format**
Picking the best image format for your needs is likely easier than video formats, as there are fewer options with broad support, and each tends to have a specific set of use-cases.

Photographs
Photographs typically fare well with lossy compression (depending on the encoder's configuration). This makes JPEG and WebP good choices for photographs, with JPEG being more compatible but WebP perhaps offering better compression. To maximize quality and minimize download time, consider providing both using a fallback with WebP as the first choice and JPEG as the second. Otherwise, JPEG is the safe choice for compatibility.

Icons
For smaller images such as icons, use a lossless format to avoid loss of detail in a size-constrained image. While lossless WebP is ideal for this purpose, support is not widespread yet, so PNG is a better choice unless you offer a fallback. If your image contains fewer than 256 colors, GIF is an option, although PNG often compresses even smaller with its indexed compression option (PNG-8).

If the icon can be represented using vector graphics, consider SVG, since it scales across various resolutions and sizes, so it's perfect for responsive design. Although SVG support is good, it may be worth offering a PNG fallback for older browsers.

Screenshots
Unless you're willing to compromise on quality, you should use a lossless format for screenshots. This is particularly important if there's any text in your screenshot, as text easily becomes fuzzy and unclear under lossy compression.

PNG is probably your best bet, but lossless WebP is arguably going to be better compressed.

Diagrams, drawings, and charts
For any image that can be represented using vector graphics, SVG is the best choice. Otherwise, you should use a lossless format like PNG. If you do choose a lossy format, such as JPEG or lossy WebP, carefully weigh the compression level to avoid causing text or other shapes to become fuzzy or unclear.

Providing image fallbacks
While the standard HTML <img> element doesn't support compatibility fallbacks for images, the <picture> element does. <picture> is used as a wrapper for a number of <source> elements, each specifying a version of the image in a different format or under different media conditions, as well as an <img> element which defines where to display the image and the fallback to the default or "most compatible" version.

<h1>Applying color to HTML elements using CSS</h1>

**Things that can have color**
At the element level, everything in HTML can have color applied to it. Instead, let's look at things in terms of the kinds of things that are drawn in the elements, such as text and borders and so forth. For each, we'll see a list of the CSS properties that apply color to them.

At a fundamental level, the color property defines the foreground color of an HTML element's content and the background-color property defines the element's background color. These can be used on just about any element.

**Text**
Whenever an element is rendered, these properties are used to determine the color of the text, its background, and any decorations on the text.

color
The color to use when drawing the text and any text decorations (such as the addition of under- or overlines, strike-through lines, and so forth.

background-color
The text's background color.

text-shadow
Configures a shadow effect to apply to text. Among the options for the shadow is the shadow's base color (which is then blurred and blended with the background based on the other parameters). See Text drop shadows to learn more.

text-decoration-color
By default, text decorations (such as underlines, strikethroughs, etc.) use the color property as their colors. However, you can override that behavior and use a different color for them with the text-decoration-color property.

text-emphasis-color
The color to use when drawing emphasis symbols adjacent to each character in the text. This is used primarily when drawing text for East Asian languages.

caret-color
The color to use when drawing the caret (sometimes referred to as the text input cursor) within the element. This is only useful in elements that are editable, such as <input> and <textarea> or elements whose HTML contenteditable attribute is set.

**Boxes**
Every element is a box with some sort of content, and has a background and a border in addition to whatever contents the box may have.

Borders
See the section Borders for a list of the CSS properties you can use to set the colors of a box's borders.

background-color
The background color to use in areas of the element that have no foreground content.

column-rule-color
The color to use when drawing the line separating columns of text.

outline-color
The color to use when drawing an outline around the outside of the element. This outline is different from the border in that it doesn't get space set aside for it in the document (so it may overlap other content). It's generally used as a focus indicator, to show which element will receive input events.

Borders
Any element can have a border drawn around it. A basic element border is a line drawn around the edges of the element's content. See Margins, padding, and borders to learn about the relationship between elements and their borders, and the article Styling borders using CSS to learn more about applying styles to borders.

You can use the border shorthand property, which lets you configure everything about the border in one shot (including non-color features of borders, such as its width, style (solid, dashed, etc.), and so forth.

border-color
Specifies a single color to use for every side of the element's border.

border-left-color, border-right-color, border-top-color, and border-bottom-color
Lets you set the color of the corresponding side of the element's border.

border-block-start-color and border-block-end-color
With these, you can set the color used to draw the borders which are closest to the start and end of the block the border surrounds. In a left-to-right writing mode (such as the way English is written), the block start border is the top edge and the block end is the bottom. This differs from the inline start and end, which are the left and right edges (corresponding to where each line of text in the box begins and ends).

border-inline-start-color and border-inline-end-color
These let you color the edges of the border closest to the beginning and the end of the start of lines of text within the box. Which side this is will vary depending on the writing-mode, direction, and text-orientation properties, which are typically (but not always) used to adjust text directionality based on the language being displayed. For example, if the box's text is being rendered right-to-left, then the border-inline-start-color is applied to the right side of the border.

**Other ways to use color**
CSS isn't the only web technology that supports color. There are graphics technologies that are available on the web which also support color.

The HTML Canvas API
Lets you draw 2D bitmapped graphics in a <canvas> element. See our Canvas tutorial to learn more.

SVG (Scalable Vector Graphics)
Lets you draw images using commands that draw specific shapes, patterns, and lines to produce an image. SVG commands are formatted as XML, and can be embedded directly into a web page or can be placed in the page using the <img> element, just like any other type of image.

WebGL
The Web Graphics Library is an OpenGL ES-based API for drawing high-performance 2D and 3D graphics on the Web. See our WebGL tutorial to find out more.

**Keywords**
A set of standard color names have been defined, letting you use these keywords instead of numeric representations of colors if you choose to do so and there's a keyword representing the exact color you want to use. Color keywords include the standard primary and secondary colors (such as red, blue, or orange), shades of gray (from black to white, including colors like darkgray and lightgrey), and a variety of other blended colors including lightseagreen, cornflowerblue, and rebeccapurple.

**RGB values**
There are three ways to represent an RGB color in CSS.

Hexadecimal string notation
Hexadecimal string notation represents a color using hexadecimal digits to represent each of the color components (red, green, and blue). It may also include a fourth component: the alpha channel (or opacity). Each color component can be represented as a number between 0 and 255 (0x00 and 0xFF) or, optionally, as a number between 0 and 15 (0x0 and 0xF). All components must be specified using the same number of digits. If you use the single-digit notation, the final color is computed by using each component's digit twice; that is, "#D" becomes "#DD" when drawing.

A color in hexadecimal string notation always begins with the character "#". After that come the hexadecimal digits of the color code. The string is case-insensitive.

"#rrggbb"
Specifies a fully-opaque color whose red component is the hexadecimal number 0xrr, green component is 0xgg, and blue component is 0xbb.

"#rrggbbaa"
Specifies a color whose red component is the hexadecimal number 0xrr, green component is 0xgg, and blue component is 0xbb. The alpha channel is specified by 0xaa; the lower this value is, the more translucent the color becomes.

"#rgb"
Specifies a color whose red component is the hexadecimal number 0xrr, green component is 0xgg, and blue component is 0xbb.

"#rgba"
Specifies a color whose red component is the hexadecimal number 0xrr, green component is 0xgg, and blue component is 0xbb. The alpha channel is specified by 0xaa; the lower this value is, the more translucent the color becomes.

As an example, you can represent the opaque color bright blue as "#0000ff" or "#00f". To make it 25% opaque, you can use "#0000ff44" or "#00f4".

**RGB functional notation**
RGB (Red/Green/Blue) functional notation, like hexadecimal string notation, represents colors using their red, green, and blue components (as well as, optionally, an alpha channel component for opacity). However, instead of using a string, the color is defined using the CSS function rgb(). This function accepts as its input parameters the values of the red, green, and blue components and an optional fourth parameter, the value for the alpha channel.

Legal values for each of these parameters are:

red, green, and blue
Each must be an <integer> value between 0 and 255 (inclusive), or a <percentage> from 0% to 100%.

**Alpha**
The alpha channel is a number between 0.0 (fully transparent) and 1.0 (fully opaque). You can also specify a percentage where 0% is the same as 0.0 and 100% is the same as 1.0.

HSL functional notation
Designers and artists often prefer to work using the HSL (Hue/Saturation/Luminosity) color method. On the web, HSL colors are represented using HSL functional notation. The hsl() CSS function is very similar to the rgb() function in usage otherwise.

Hue defines the actual color based on the position along a circular color wheel representing the colors of the visible spectrum. Saturation is a percentage of how much of the way between being a shade of gray and having the maximum possible amount of the given hue. As the value of luminance (or lightness) increases, the color transitions from the darkest possible to the brightest possible (from black to white).

he value of the hue (H) component of an HSL color is an angle from red around through yellow, green, cyan, blue, and magenta (ending up back at red again at 360°) that identifies what the base color is. The value can be specified in any <angle> unit supported by CSS, including degrees (deg), radians (rad), gradians (grad), or turns (turn). But this doesn't control how vivid or dull, or how bright or dark the color is.

The saturation (S) component of the color specifies what percentage of the final color is comprised of the specified hue. The rest is defined by the grey level provided by the luminance (L) component.

<h1>Using color</h1>

**Specifying colors in stylesheets**
The easiest way to apply color to elements—and the way you'll usually do it—is to specify colors in the CSS that's used when rendering elements.

HTML

This is pretty simple, using a <div> as a wrapper around the contents, which consists of two more <div>s, each styled differently with a single paragraph (<p>) in each box.

The magic happens, as usual, in the CSS, where we'll apply colors define the layout for the HTML above.

CSS
We'll look at the CSS to create the above results a piece at a time, so we can review the interesting parts one by one.

.wrapper {
  width: 620px;
  height: 110px;
  margin: 0;
  padding: 10px;
  border: 6px solid mediumturquoise;
}

The .wrapper class is used to assign styles to the <div> that encloses all of our other content. This establishes the size of the container using width and height as well as its margin and padding.

Of more interest to our discussion here is the use of the border property to establish a border around the outside edge of the element. This border is a solid line, 6 pixels wide, in the color mediumturquoise.

In brief, .box establishes the size of each box, as well as the configuration of the font used within. We also take advantage of CSS Flexbox to easily center the contents of each box. We enable flex mode using display: flex, and set both justify-content and align-items to center. Then we can create a class for each of the two boxes that defines the properties that differ between the two.

The .boxLeft class—which, cleverly, is used to style the box on the left—floats the box to the left, then sets up the colors:

The box's background color is set by changing the value of the CSS background-color property to rgb(245, 130, 130).
An outline is defined for the box. Unlike the more commonly used border, outline doesn't affect layout at all; it draws over the top of whatever may happen to be outside the element's box instead of making room as border does. This outline is a solid, dark red line that's two pixels thick. Note the use of the darkred keyword when specifying the color.
Notice that we're not explicitly setting the text color. That means the value of color will be inherited from the nearest containing element that defines it. By default, that's black.

**Note**: When you try to show it in Safari, it will not show properly. Because Safari doesn't support text-decoration: underline wavy #88ff88.

Finally, the .boxRight class describes the unique properties of the box that's drawn on the right. It's configured to float the box to the right so that it appears next to the previous box. Then the following colors are established:

The background-color is set using the HSL value specified using hsl(270deg, 50%, 75%). This is a medium purple color.
The box's outline is used to specify that the box should be enclosed in a four pixel thick dashed line whose color is a somewhat deeper purple (rgb(110, 20, 120)).
The foreground (text) color is specified by setting the color property to hsl(0deg, 100%, 100%). This is one of many ways to specify the color white.
We add a green wavy line under the text with text-decoration.
Finally, a bit of a shadow is added to the text using text-shadow. Its color parameter is set to black.

**Letting the user pick a color**
There are many situations in which your website may need to let the user select a color. Perhaps you have a customizable user interface, or you're implementing a drawing app. Maybe you have editable text and need to let the user choose the text color. Or perhaps your app lets the user assign colors to folders or items. Although historically it's been necessary to implement your own color picker, HTML now provides support for browsers to provide one for your use through the <input> element, by using "color" as the value of its type attribute.

The <input> element represents a color only in the hexadecimal string notation covered above.

HTML
The HTML here creates a box that contains a color picker control (with a label created using the <label> element) and an empty paragraph element (<p>) into which we'll output some text from our JavaScript code.

<div id="box">
  <label for="colorPicker">Border color:</label>
  <input type="color" value="#8888ff" id="colorPicker" />
  <p id="output"></p>
</div>

CSS
The CSS establishes a size for the box and some basic styling for appearances. The border is also established with a 2-pixel width and a border color.

#box {
  width: 500px;
  height: 200px;
  border: 2px solid rgb(245, 220, 225);
  padding: 4px 6px;
  font: 16px "Lucida Grande", "Helvetica", "Arial", "sans-serif";
}

JavaScript
The script here handles the task of updating the starting color of the border to match the color picker's value. Then two event handlers are added to deal with input from the <input type="color"> element.

const colorPicker = document.getElementById("colorPicker");
const box = document.getElementById("box");
const output = document.getElementById("output");

box.style.borderColor = colorPicker.value;

colorPicker.addEventListener(
  "input",
  (event) => {
    box.style.borderColor = event.target.value;
  },
  false
);

colorPicker.addEventListener(
  "change",
  (event) => {
    output.innerText = `Color set to ${colorPicker.value}.`;
  },
  false
);

The input event is sent every time the value of the element changes; that is, every time the user adjusts the color in the color picker. Each time this event arrives, we set the box's border color to match the color picker's current value.

The change event is received when the color picker's value is finalized. We respond by setting the contents of the <p> element with the ID "output" to a string describing the finally selected color.

<h1>Fundamental text and font styling</h1>

Here we'll go through all the basic fundamentals of text/font styling in detail, including setting font weight, family and style, font shorthand, text alignment and other effects, and line and letter spacing.

**What is involved in styling text in CSS?**
If you have worked with HTML or CSS already, e.g., by working through these tutorials in order, then you know that text inside an element is laid out inside the element's content box. It starts at the top left of the content area (or the top right, in the case of RTL language content), and flows towards the end of the line. Once it reaches the end, it goes down to the next line and flows to the end again. This pattern repeats until all the content has been placed in the box. Text content effectively behaves like a series of inline elements, being laid out on lines adjacent to one another, and not creating line breaks until the end of the line is reached, or unless you force a line break manually using the <br> element.

The CSS properties used to style text generally fall into two categories, which we'll look at separately in this article:

Font styles: Properties that affect a text's font, e.g., which font gets applied, its size, and whether it's bold, italic, etc.

Text layout styles: Properties that affect the spacing and other layout features of the text, allowing manipulation of, for example, the space between lines and letters, and how the text is aligned within the content box.

**NOTE**: Bear in mind that the text inside an element is all affected as one single entity. You can't select and style subsections of text unless you wrap them in an appropriate element (such as a <span> or <strong>), or use a text-specific pseudo-element like ::first-letter (selects the first letter of an element's text), ::first-line (selects the first line of an element's text), or ::selection (selects the text currently highlighted by the cursor).

**Color**
The color property sets the color of the foreground content of the selected elements, which is usually the text, but can also include a couple of other things, such as an underline or overline placed on text using the text-decoration property.

color can accept any CSS color unit, for example:

p {
  color: red;
}

This will cause the paragraphs to become red, rather than the standard browser default of black.

**Font families**
To set a different font for your text, you use the font-family property — this allows you to specify a font (or list of fonts) for the browser to apply to the selected elements. The browser will only apply a font if it is available on the machine the website is being accessed on; if not, it will just use a browser default font. A simple example looks like so:

p {
  font-family: arial;
}

This would make all paragraphs on a page adopt the arial font, which is found on any computer.

**Web safe fonts**
Speaking of font availability, there are only a certain number of fonts that are generally available across all systems and can therefore be used without much worry. These are the so-called web safe fonts.

**EXAMPLES**: Arial, Courier New, Georgia, Times New Roman, Trebuchet MS, Verdana.

**Note**: Among various resources, the cssfontstack.com website maintains a list of web safe fonts available on Windows and macOS operating systems, which can help you make your decision about what you consider safe for your usage.

There is a way to download a custom font along with a webpage, to allow you to customize your font usage in any way you want: web fonts. This is a little bit more complex, and we will discuss it in a separate article later on in the module.

Default fonts
CSS defines five generic names for fonts: serif, sans-serif, monospace, cursive, and fantasy. These are very generic and the exact font face used from these generic names can vary between each browser and each operating system that they are displayed on. It represents a worst case scenario where the browser will try its best to provide a font that looks appropriate. serif, sans-serif, and monospace are quite predictable and should provide something reasonable. On the other hand, cursive and fantasy are less predictable and we recommend using them very carefully, testing as you go.

**Font stacks**
Since you can't guarantee the availability of the fonts you want to use on your webpages (even a web font could fail for some reason), you can supply a font stack so that the browser has multiple fonts it can choose from. This involves a font-family value consisting of multiple font names separated by commas, e.g.,

p {
  font-family: "Trebuchet MS", Verdana, sans-serif;
}

In such a case, the browser starts at the beginning of the list and looks to see if that font is available on the machine. If it is, it applies that font to the selected elements. If not, it moves on to the next font, and so on.

It is a good idea to provide a suitable generic font name at the end of the stack so that if none of the listed fonts are available, the browser can at least provide something approximately suitable. To emphasize this point, paragraphs are given the browser's default serif font if no other option is available — which is usually Times New Roman — this is no good for a sans-serif font!

**NOTE**: Font names that have more than one word — like Trebuchet MS — need to be surrounded by quotes, for example "Trebuchet MS".

**A font-family example**
Let's add to our previous example, giving the paragraphs a sans-serif font:

p {
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}

**Font size**

px (pixels): The number of pixels high you want the text to be. This is an absolute unit — it results in the same final computed value for the font on the page in pretty much any situation.

ems: 1 em is equal to the font size set on the parent element of the current element we are styling (more specifically, the width of a capital letter M contained inside the parent element). This can become tricky to work out if you have a lot of nested elements with different font sizes set, but it is doable, as you'll see below. Why bother? It is quite natural once you get used to it, and you can use em to size everything, not just text. You can have an entire website sized using em, which makes maintenance easy.

rems: These work just like em, except that 1 rem is equal to the font size set on the root element of the document (i.e. <html>), not the parent element. This makes doing the maths to work out your font sizes much easier, although if you want to support really old browsers, you might struggle — rem is not supported in Internet Explorer 8 and below.
The font-size of an element is inherited from that element's parent element. This all starts with the root element of the entire document — <html> — the standard font-size of which is set to 16px across browsers. Any paragraph (or another element that doesn't have a different size set by the browser) inside the root element will have a final size of 16px. Other elements may have different default sizes. For example, an h1 element has a size of 2em set by default, so it will have a final size of 32px.

Things become more tricky when you start altering the font size of nested elements. For example, if you had an <article> element in your page, and set its font-size to 1.5 em (which would compute to 24 px final size), and then wanted the paragraphs inside the <article> elements to have a computed font size of 20 px, what em value would you use?

<!-- document base font-size is 16px -->
<article>
  <!-- If my font-size is 1.5em -->
  <p>My paragraph</p>
  <!-- How do I compute to 20px font-size? -->
</article>

You would need to set its em value to 20/24, or 0.83333333 em. The maths can be complicated, so you need to be careful about how you style things. It is best to use rem where you can to keep things simple, and avoid setting the font-size of container elements where possible.

**Font style, font weight, text transform, and text decoration**
CSS provides four common properties to alter the visual weight/emphasis of text:

font-style: Used to turn italic text on or off. Possible values are as follows (you'll rarely use this, unless you want to turn some italic styling off for some reason):
normal: Sets the text to the normal font (turns existing italics off).

italic: Sets the text to use the italic version of the font, if available; if not, it will simulate italics with oblique instead.

oblique: Sets the text to use a simulated version of an italic font, created by slanting the normal version.

font-weight: Sets how bold the text is. This has many values available in case you have many font variants available (such as -light, -normal, -bold, -extrabold, -black, etc.), but realistically you'll rarely use any of them except for normal and bold:
normal, bold: Normal and bold font weight.

lighter, bolder: Sets the current element's boldness to be one step lighter or heavier than its parent element's boldness.

100 – 900: Numeric boldness values that provide finer grained control than the above keywords, if needed.

text-transform: Allows you to set your font to be transformed. Values include:
none: Prevents any transformation.

uppercase: Transforms all text to capitals.

lowercase: Transforms all text to lower case.

capitalize: Transforms all words to have the first letter capitalized.

full-width: Transforms all glyphs to be written inside a fixed-width square, similar to a monospace font, allowing aligning of, e.g., Latin characters along with Asian language glyphs (like Chinese, Japanese, Korean).

text-decoration: Sets/unsets text decorations on fonts (you'll mainly use this to unset the default underline on links when styling them). Available values are:
none: Unsets any text decorations already present.

underline: Underlines the text.

overline: Gives the text an overline.

line-through: Puts a strikethrough over the text.

You should note that text-decoration can accept multiple values at once if you want to add multiple decorations simultaneously, for example, text-decoration: underline overline. Also note that text-decoration is a shorthand property for text-decoration-line, text-decoration-style, and text-decoration-color. You can use combinations of these property values to create interesting effects, for example: text-decoration: line-through red wavy.

**Text drop shadows**
You can apply drop shadows to your text using the text-shadow property. This takes up to four values, as shown in the example below:

text-shadow: 4px 4px 5px red;

The four properties are as follows:

The horizontal offset of the shadow from the original text — this can take most available CSS length and size units, but you'll most commonly use px; positive values move the shadow right, and negative values left. This value has to be included.

The vertical offset of the shadow from the original text. This behaves similarly to the horizontal offset, except that it moves the shadow up/down, not left/right. This value has to be included.

The blur radius: a higher value means the shadow is dispersed more widely. If this value is not included, it defaults to 0, which means no blur. This can take most available CSS length and size units.

The base color of the shadow, which can take any CSS color unit. If not included, it defaults to currentcolor, i.e. the shadow's color is taken from the element's color property.

**Multiple shadows**
You can apply multiple shadows to the same text by including multiple shadow values separated by commas, for example:

h1 {
  text-shadow: 1px 1px 1px red, 2px 2px 1px red;
}

**Text layout**
With basic font properties out of the way, let's have a look at properties we can use to affect text layout.

**Text alignment**
The text-align property is used to control how text is aligned within its containing content box. The available values are listed below. They work in pretty much the same way as they do in a regular word processor application:

left: Left-justifies the text.

right: Right-justifies the text.

center: Centers the text.

justify: Makes the text spread out, varying the gaps in between the words so that all lines of text are the same width. You need to use this carefully — it can look terrible, especially when applied to a paragraph with lots of long words in it. If you are going to use this, you should also think about using something else along with it, such as hyphens, to break some of the longer words across lines.

**Line height**
The line-height property sets the height of each line of text. This property can not only take most length and size units, but can also take a unitless value, which acts as a multiplier and is generally considered the best option. With a unitless value, the font-size gets multiplied and results in the line-height. Body text generally looks nicer and is easier to read when the lines are spaced apart. The recommended line height is around 1.5 – 2 (double spaced). To set our lines of text to 1.6 times the height of the font, we'd use:

p {
  line-height: 1.6;
}
Copy to ClipboardCopy to Clipboard
Applying this to the <p> elements in our example would give us this result:

html {
  font-size: 10px;
}

h1 {
  font-size: 5rem;
  text-transform: capitalize;
  text-shadow: 1px 1px 1px red, 2px 2px 1px red;
  text-align: center;
}

h1 + p {
  font-weight: bold;
}

p {
  font-size: 1.5rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
  line-height: 1.6;
}

**Letter and word spacing**
The letter-spacing and word-spacing properties allow you to set the spacing between letters and words in your text. You won't use these very often, but might find a use for them to obtain a specific look, or to improve the legibility of a particularly dense font. They can take most length and size units.

To illustrate, we could apply some word- and letter-spacing to the first line of each <p> element in our HTML sample with:

p::first-line {
  letter-spacing: 4px;
  word-spacing: 4px;
}

This renders our HTML as:

html {
  font-size: 10px;
}

h1 {
  font-size: 5rem;
  text-transform: capitalize;
  text-shadow: 1px 1px 1px red, 2px 2px 1px red;
  text-align: center;
  letter-spacing: 2px;
}

h1 + p {
  font-weight: bold;
}

p {
  font-size: 1.5rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
  line-height: 1.6;
  letter-spacing: 1px;
}

Other properties worth looking at
The above properties give you an idea of how to start styling text on a webpage, but there are many more properties you could use. We just wanted to cover the most important ones here. Once you've become used to using the above, you should also explore the following:

Font styles:

font-variant: Switch between small caps and normal font alternatives.
font-kerning: Switch font kerning options on and off.
font-feature-settings: Switch various OpenType font features on and off.
font-variant-alternates: Control the use of alternate glyphs for a given font-face.
font-variant-caps: Control the use of alternate capital glyphs.
font-variant-east-asian: Control the usage of alternate glyphs for East Asian scripts, like Japanese and Chinese.
font-variant-ligatures: Control which ligatures and contextual forms are used in text.
font-variant-numeric: Control the usage of alternate glyphs for numbers, fractions, and ordinal markers.
font-variant-position: Control the usage of alternate glyphs of smaller sizes positioned as superscript or subscript.
font-size-adjust: Adjust the visual size of the font independently of its actual font size.
font-stretch: Switch between possible alternative stretched versions of a given font.
text-underline-position: Specify the position of underlines set using the text-decoration-line property underline value.
text-rendering: Try to perform some text rendering optimization.

Text layout styles:

text-indent: Specify how much horizontal space should be left before the beginning of the first line of the text content.
text-overflow: Define how overflowed content that is not displayed is signaled to users.
white-space: Define how whitespace and associated line breaks inside the element are handled.
word-break: Specify whether to break lines within words.
direction: Define the text direction. (This depends on the language and usually it's better to let HTML handle that part as it is tied to the text content.)
hyphens: Switch on and off hyphenation for supported languages.
line-break: Relax or strengthen line breaking for Asian languages.
text-align-last: Define how the last line of a block or a line, right before a forced line break, is aligned.
text-orientation: Define the orientation of the text in a line.
overflow-wrap: Specify whether or not the browser may break lines within words in order to prevent overflow.
writing-mode: Define whether lines of text are laid out horizontally or vertically and the direction in which subsequent lines flow.

**Font shorthand**
Many font properties can also be set through the shorthand property font. These are written in the following order: font-style, font-variant, font-weight, font-stretch, font-size, line-height, and font-family.

Among all those properties, only font-size and font-family are required when using the font shorthand property.

A forward slash has to be put in between the font-size and line-height properties.

A full example would look like this:

font: italic normal bold normal 3em/1.5 Helvetica, Arial, sans-serif;
