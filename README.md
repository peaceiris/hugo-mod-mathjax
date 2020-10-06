## hugo-mod-mathjax

[MathJax] packaged as a Hugo Module ([Hugo Modules]).

[MathJax]: https://www.mathjax.org/
[Hugo Modules]: https://gohugo.io/hugo-modules



## Usage

`config/_default/config.yaml`

```yaml
module:
  imports:
    - path: github.com/peaceiris/hugo-mod-mathjax
```

In a Hugo template file.

```html
<script defer>
  MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']]
    }
  };
</script>

{{ $js := resources.Get "mod/mathjax/tex-mml-chtml.js" }}
{{ $secureJS := $js | resources.Fingerprint "sha512" }}
<script defer type="text/javascript" id="MathJax-script" src="{{ $secureJS.Permalink }}" integrity="{{ $secureJS.Data.Integrity }}"></script>
```
