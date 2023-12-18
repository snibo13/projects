---
title: "Using Latex in Hugo"
date: 2023-12-18T15:32:36-06:00
draft: false
list: true
color: "#CC2936"
math: true
---

For my last [post](../brevis/) I added some equations using a math formatting tool called LaTex. This will *NOT* be an introduction to LaTex but will explain a bit about how I integrated it into my Hugo site. I was having a bit of trouble getting everything to work, so I figured it would be convenient for other people if this little walkthrough existed.

This site is built on a custom Hugo theme and hosted on GitHub. I have it connected to a Namecheap domain. Hugo is a framework that simplifies the process of generating static content. You can find out more about the hosting and Hugo [here](https://pages.github.com/) and [here](https://gohugo.io/) respectively.

Hugo uses a concept called "partials". Partials are components of your site that you can assemble. My site has partials for the header, footer and other meta data. To add support for LaTex I added a new partial called "math". The math partial contains CDN links for a tool called KaTex. KaTex is the renderer I am using for generating the HTML associated with the LaTex. The math partial looks like this:
```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.css"
    integrity="sha384-n8MVd4RsNIU0tAv4ct0nTaAbDJwPJzDEaqSD1odI+WdtXRGWt2kTvGFasHpSy3SV" crossorigin="anonymous">

<!-- The loading of KaTeX is deferred to speed up page rendering -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.js"
    integrity="sha384-XjKyOOlGwcjNTAIQHIpgOno0Hl1YQqzUOEleOLALmuqehneUG+vnGctmUb0ZY0l8"
    crossorigin="anonymous"></script>

<!-- To automatically render math in text elements, include the auto-render extension: -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/contrib/auto-render.min.js"
    integrity="sha384-+VBxd3r6XgURycqtZ117nYw44OOcIax56Z4dCRWbxyPt0Koah1uHoK0o4+/RRE05" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
```
I copied these straight from the KaTex websites [instructions](https://katex.org/docs/browser). Be sure to check if there is a more up-to-date set of links.

The second step was to modify the single.html file. Single contains the HTML and partials used for generating a single blog page. To adjust this to work with KaTex I changed the beginning of the file to read
```
{{ define "main" }}
{{ if or .Params.math .Site.Params.math }}
{{ partial "math.html" . }}
{{ end }}
```

This checks if the set of parameters at the top of each Hugo markdown file includes math. If it does, it includes the CDN we listed in the math partial. The parameters for the Lagrange Multipliers post looks like this:
```
---
title: "Lagrange Multipliers"
date: 2023-10-02T00:28:30-04:00
draft: false
list: true
summary: "Lagrange multipliers a la Feynman"
color: "#5B9279"
math: true
---
```
Keep in mind there are a couple of custom parameters I already have like summary and color, so it's fine if yours looks different.

To use KaTex you simply write your LaTex like normal. For a block like you would see in a LaTex \begin{equation} you use double dollar signs ($$)
```
$$
\begin{equation}
\begin{aligned}
\frac{\partial \mathbf{u}}{\partial t} +
(\mathbf{u} \cdot \nabla) \mathbf{u} &= 
-\frac{1}{\rho} \nabla p + \nu \nabla^2 \mathbf{u} + \mathbf{f}, \\
\nabla \cdot \mathbf{u} &= 0,
\end{aligned}
\end{equation}
$$
```
looks like 
$$ \begin{equation}
\begin{aligned}
\frac{\partial \mathbf{u}}{\partial t} + (\mathbf{u} \cdot \nabla) \mathbf{u} &= -\frac{1}{\rho} \nabla p + \nu \nabla^2 \mathbf{u} + \mathbf{f}, \\
\nabla \cdot \mathbf{u} &= 0,
\end{aligned}
\end{equation}$$

The part that took me longer to figure out was how to do inline latex like this \\(\mathbb{E}(x\) \rightarrow 5\\). The documentation says you use `\( \)` to generate an inline LaTex command. However, the way Hugo renders it means the \ is ignored. This is a common occurence in software where certain characters are not processed the way you would expect without "escaping" them. Escaping usually just means prepending a single \ before the character so \ goes to \\\\. Following this to generate inline LaTex you use `\\( \\)` so we can generate the LaTex from before with `\\(\mathbb{E}(x\) \rightarrow 5\\)`. That's all there is to it. Hope this was helpful to anyone who stumbled upon it. 

Cheers.