# hugo-theme-onionskin

![The theme logo](assets/logo.png)

This is a Hugo theme intended for building Tor sites.

* Allow inlining everything, including CSS and the favicon, to provide a page in a single request
* No JavaScript or webfonts, which increase attack surface of your users
* No external dependencies, including build-time dependencies or code served from CDNs
* Optional link annotations to indicate whether a given link is on the same page (anchor),
  a different page on the same site (internal), an external link on the clearnet,
  or an external link to an onion site.
* A light and dark color scheme

## Installing

You can use this theme as a submodule,
but I actually recommend vendoring it by downloading the source code and saving it as `themes/onionskin/`.

As this theme is designed for a single-user Hugo site with no untrusted code,
and as it uses no JavaScript and retrieves no third-party code
(meaning no external JavaScript, no webfonts, no external CSS),
there are no security concerns with this.

## Options

You can set these options in your site's configuration to customize the default behaviour.

* Options are listed with their default values.
* All image filenames are relative to your site's "assets/" directory
* By default, no annotations are set
* A favicon of a scroll is included
* If both a string and an image are specified for link annotation, the image takes priority

```toml
[params]

# Inline CSS, favicon, and logo
# Also inline any images specified with the inlineableImage.html partial
OnionskinInlineEverything = false

# Specify the CSS color scheme we use
# Onionskin has two built-in color schemes, 'light' and 'dark'.
OnionskinTheme = "light"

# The filename for the logo
OnionskinLogo = "logo.svg"

# Whether to enable link annotations at all
OnionskinLinkAnnotations = true

# Annotate links with strings or images
OnionskinLinkAnnotationInternalString = ""
OnionskinLinkAnnotationInternalImage = ""
OnionskinLinkAnnotationClearnetString = ""
OnionskinLinkAnnotationClearnetImage = ""
OnionskinLinkAnnotationOnionString = ""
OnionskinLinkAnnotationOnionImage = ""
OnionskinLinkAnnotationAnchorString = ""
OnionskinLinkAnnotationAnchorImage = ""
```

I recommend the following as default link annotations, which you can customize as you like:

```toml
OnionskinLinkAnnotationInternalString = "📜 "
OnionskinLinkAnnotationClearnetString = "⚠️ "
OnionskinLinkAnnotationOnionString = "🧅 "
OnionskinLinkAnnotationAnchorString = "# "
```

## Link annotations

Here's a screenshot of emoji link annotations for clearnet, onion, and anchor links,
and a custom favicon for internal links:

![A screenshot of link annotations](assets/link-annotations.png)

## Short codes

### `details.html`

A simple collapsable `<details>` element.

```go-html-template
{{< details "Click here to exapand" >}}
Wow, I can type a lot here and it is all hidden by default.
{{< /details >}}
```

### `doublink.html`

Show a clearnet link and a Tor link for sites that offer both.

```go-html-template
{{< doublink "Tor Browser" "https://www.torproject.org/" "http://2gzyxa5ihm7nsggfxnu52rck2vv4rvmdlkiu3zzui5du4xyclen53wid.onion" >}}
```

### `infobox.html`

A simple standout info/warn/error box.

```go-html-template
{{< infobox "error" >}}
**WARNING**:
Something could go wrong!
{{< /infobox >}}
```

### `inlineableImage.html`

An image that is inlined to HTML if `OnionskinInlineEverything` is set,
or referenced by its link otherwise.

A simple standout info/warn/error box.

```go-html-template
{{< inlineableImage "logo.svg" >}}.
```

### `inlineCode.html`

A code block from the contents of a file in your post's directory,
with syntax highlighting.

```go-html-template
{{< inlineCode "script.sh" "sh" >}}
```
