[![Codacy Badge](https://app.codacy.com/project/badge/Grade/6f080031f82149f0a2f8e7ebdccfcc9f)](https://www.codacy.com/gh/dnb-hugo/debugprint/dashboard)

Hugo's missing debugging partial.

## Notes

- This is not a standalone theme. This is a Hugo module to use while you are developing your theme or website.
- The original of this module can be found at [kaushalmodi/hugo-debugprint](https://github.com/kaushalmodi/hugo-debugprint). 
- This version is adapted to work with dnb-hugo themes and components.
- If in doubt, use [@kaushalmodi's version](https://github.com/kaushalmodi/hugo-debugprint).

## Installation

Add the following code to your configuration:

```toml
[module]
[[module.imports]]
path = "github.com/dnb-hugo/debugprint"
disabled = false
```

## Usage

### In layout files

To print a variable in one of your layouts:

```gotemplate
{{ partial "debugprint" . }}
{{ partial "debugprint" .Params }}
{{ partial "debugprint" site }}
{{ partial "debugprint" site.Menus }}
{{ partial "debugprint" .GitInfo }}
{{ partial "debugprint" .Resources }}
{{ partial "debugprint" .File }}

{{/* in shortcodes */}}
{{ partial "debugprint" . }} <!-- this will debug the internals of the shortcode -->
{{ partial "debugprint" .Position }} <!-- this will show where the shortcode was called -->
```

Exchange the `.` (dot) with whatever variable you want to debug. Sub-collections or sub-slices might require extra setup to be debugged, depending on the structure and type of the values.

### In content files

To debug page data from within a Markdown file:

```markdown
{{< debug >}} <!-- the same as -->
{{< debug "page" >}} <!-- debug page variable -->
{{< debug "params" >}} <!-- debug page params -->
{{< debug "site" >}} <!-- debug site params -->
{{< debug param="bla" >}} <!-- debug .Params.bla -->
```

Debugging from within Markdown requires very explicit configuration in the shortcode template. [Open a new issue](https://github.com/dnb-hugo/debugprint/issues/new) if you require a specific debugging object.
