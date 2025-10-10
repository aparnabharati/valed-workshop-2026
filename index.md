---
title: Home
---

# Visual Art, Generative AI, and the Legal/Ethical Dilemma Workshop @ WACV 2026

{% include figure.html img="uidaho-workshop.jpg" alt="intro image here" caption="Library workshop" width="75%" %}

Generative AI has transformed how visual art is created and circulated. Text-to-image generation systems such as Stable Diffusion, DALL·E, and Midjourney can instantly produce artworks inspired by centuries of human creativity. While these technologies democratize access to artistic tools, they also raise urgent questions about copyright, artistic integrity, and provenance. Recent controversies underscore the dilemma:

• In 2023, artists filed lawsuits alleging that diffusion models trained on datasets like LAION-5B in- fringed their copyrights by replicating distinctive styles without consent.

• High-profile controversies have emerged around “style mimicry,” where AI systems can reproduce the brushwork and palette of living artists—prompting protests under hashtags like #ProtectArtists.

• Legal uncertainty persists in landmark U.S. cases (e.g., Andersen v. Stability AI) and in international contexts, where courts debate whether AI-generated art constitutes a derivative work or violates the substantial similarity test.

• Questions of authorship, provenance, and authenticity now intersect with computer vision and foren- sics—how do we trace whether a generated work contains identifiable fragments of training data?

This workshop will bring together researchers, artists, legal scholars, and industry practitioners to crit- ically examine the technical, legal, and societal challenges of visual art in the age of generative AI. By hosting this dialogue at WACV, we seek to bridge the computer vision community with the creative and legal domains, and to set a research agenda that safeguards artistic integrity while enabling innovation

<div class="toc" markdown="1">
## Contents:

{% for lesson in site.pages %}
{% if lesson.nav == true %}- [{{ lesson.title }}]({{ lesson.url | relative_url }}){% endif %}
{% endfor %}
</div>

Hosted by [University of Idaho Library](http://www.lib.uidaho.edu/), {{ site.pub_year }}.
 
> built using [Jekyll](https://jekyllrb.com/) and [GitHub Pages](https://pages.github.com/)
>
> images and content: cc-by-sa <a href="https://github.com/{{ site.github_username }}">{{ site.author }}</a> {{ site.pub_year}} (get [source code]({{ site.repo }})).
> Last build date: {{ site.time | date: "%Y-%m-%d" }}.
>
> <a href="http://creativecommons.org/licenses/by-sa/4.0/" rel="license"><img style="border-width: 0;" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" alt="Creative Commons License" /></a>
