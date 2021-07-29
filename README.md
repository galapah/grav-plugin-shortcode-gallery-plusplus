# Shortcode Gallery++ Plugin

## About

The **Shortcode Gallery++** Plugin is an extension for [Grav CMS](http://github.com/getgrav/grav). A shortcode extension
to add sweet galleries to your Grav website.  
It combines [Justified-Gallery](https://github.com/miromannino/Justified-Gallery) by Miro Mannino and [GLightbox](https://github.com/biati-digital/glightbox) by biati digital.

## Usage

It's quite simple. Just wrap some image links in `[gallery]` tags:

### With one markdown tag per image

```markdown
[gallery]
![Alt text 1](image.jpg "Some description to be used in the lightbox")
![Alt text 2](/images/image.jpg "<strong>Descriptions</strong> can also<br>be <i>HTML</i> formatted.")
![relative link](../image.jpg)
![remote link](https://remotesite.com/image.jpg)
...
[/gallery]
```

### With one CSV file

Alternatively, you can specify the images with one CSV file containing information about the pictures, e.g.:

```markdown
[gallery]
source="pics/pic_list.csv"
[/gallery]
```

#### Sample CSV file

```
filename;description;title
image1.jpg;"picture from vacation";"my vacation"
image2.jpg;"me and my friends";"with friends"
```

#### Requirements

1. the definition string startswith "source="
2. the file extension is CSV
3. the definition is case insensitive
4. the CSV file must be in the same directory as the pictures
5. the CSV file contains at least two columns: image filename and description as the 'alt' title
6. if there is a third column, it is used for the 'title' property, otherwise 'title'='alt'
7. the first column is file basename, without directory
8. the first row is ignored as a header
9. the field delimiter can be comma or semicolon

## Okay, what does it look like?

This plugin combines a nice justified gallery layout with an eye-pleasing lightbox.  
All images get nicely aligned. After a click on one of them, a sweet popup appears, showing it full-screen.
Just have a look for yourself:

![Demo](assets/demo.webp)

* You can of course create several galleries on the same page.
* You have plenty of settings you can change in the admin panel.
* You can also change everything for a single galleries via shortcode. For example:  
```markdown
[gallery rowHeight=230 margins=25 lastRow="justify" captions="false" border=0]
![Alt text 1](image.jpg "Some description to be used in the lightbox")
![Alt text 2](/images/image.jpg "<strong>Descriptions</strong> can also<br>be <i>HTML</i> formatted.")
![relative link](../image.jpg)
![remote link](https://remotesite.com/image.jpg)
...
[/gallery]
```

## Gallery settings

| parameter   | possible values | description |
|-------------|-----------------| ------------|
| `rowHeight` | dimension in pixel | The preferred rows height.
| `margins`   | dimension in pixel | The margins between the images.
| `lastRow`   | `justify`, `hide`, `nojustify`, `center`, `right` | `justify`: justifies the last row; `hide`: hides the row if it can't be justified; `nojustify`: align the last row to the left; `center`: align the last row to the center; `right`: align the last row to the right 
| `captions`  | `true`, `false` | Enable captions that appear when the mouse hovers an image. **For caption, the alt-text of an image is used: `![caption](image.jpg)`** 
| `border`    | dimension in pixel | The border size of the gallery. With a negative value the border will be the same as `margins`.

## Lightbox settings

| parameter             | possible values | description |
|-----------------------|-----------------| ------------|
| `openEffect`          | `zoom`, `fade`, `none` |
| `closeEffect`         | `zoom`, `fade`, `none` |
| `slideEffect`         | `slide`, `zoom`, `fade`, `none` |
| `closeButton`         | `true`, `false` | Show or hide the close button.
| `touchNavigation`     | `true`, `false` | Enable touch navigation (swipe).
| `touchFollowAxis`     | `true`, `false` | Image follow axis when dragging on mobile.
| `keyboardNavigation`  | `true`, `false` | Enable or disable the keyboard navigation.
| `closeOnOutsideClick` | `true`, `false` | Close the lightbox when clicking outside the active slide.
| `loop`                | `true`, `false` | Loop slides on end.
| `draggable`           | `true`, `false` | Enable or disable mouse drag to go to previous and next slide.
| `descEnabled`         | `true`, `false` | **For description, the title-text of an image is used: `![](image.jpg "description")`**
| `descPosition`        | `bottom`, `top`, `left`, `right` | The position for slides description.


---

## Installation

### Preferred way: GPM Installation

To install the plugin via the [GPM](http://learn.getgrav.org/advanced/grav-gpm), navigate to the root of your
Grav-installation, and enter:

    bin/gpm install shortcode-gallery-plusplus

### Alternatively: via Admin Plugin

If you use the Admin Plugin, you can install the plugin directly by browsing the `Plugins`-menu and clicking on
the `Add` button.

### If you wish so: Manual Installation

> NOTE: This plugin is a modular component for Grav which requires the [Grav Shortcode Core Plugin
](https://github.com/getgrav/grav-plugin-shortcode-core) to be installed.

To install the plugin manually, download the zip-version of this repository and unzip it
under `/your/site/grav/user/plugins`. Then rename the folder to `shortcode-gallery-plusplus`. You can find these files
on [GitHub](https://github.com/sal0max/grav-plugin-shortcode-gallery-plusplus) or
via [GetGrav.org](http://getgrav.org/downloads/plugins#extras).

## Configuration

Before configuring this plugin, you should copy
the `user/plugins/shortcode-gallery-plusplus/shortcode-gallery-plusplus.yaml`
to `user/config/plugins/shortcode-gallery-plusplus.yaml` and only edit that copy.

**Preferably**, use the Admin Plugin. It takes care of creating a file with your configuration
named `shortcode-gallery-plusplus.yaml` to be created in the `user/config/plugins/`-folder once the configuration is
saved in the Admin.

---

## Credits

Couldn't be possible without those awesome libraries:

* [Justified-Gallery](https://github.com/miromannino/Justified-Gallery) by Miro Mannino
* [GLightbox](https://github.com/biati-digital/glightbox) by biati digital
