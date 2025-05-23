---
layout: post
title: "Trying GitHub Pages for a personal technical blog"
date: 2025-05-23
categories: [github-pages, jekyll, minima, blogging]
---

Today I started experimenting with **GitHub Pages** to set up my own personal technical blog. My goal was to use Jekyll with the minima theme and document the process, including the challenges I encountered along the way.
I also used Github Copilot *Agent mode* to ***vibe-code*** my way through this experience.

## Getting Started

Setting up a GitHub Pages site was straightforward, but customizing it to fit my needs required a bit more effort. I wanted to:
- Use the minima theme as the default.
- Organize content with markdown files for projects and blog posts.
- Enable pagination for blog posts.
- Override the default navigation to better suit my site structure.

## Challenges Faced
I overcame the following challenges using Github Copilot as my tutuor in Agent mode.

### 0. Learning how Jekyll works with a tight feedback loop.

- Used a dev container with `"image": "mcr.microsoft.com/devcontainers/jekyll:2-bookworm"` to allow local testing of the site generation
- Live Reload and Development
    - Using `bundle exec jekyll serve --livereload` made local development much easier, automatically rebuilding and refreshing the browser on changes.
    - Reload doesn't always works but it does help. Sometimes needed to Ctrl-C and start again. I wonder if this is for things like the liquid templates more than the markdown pages?

### 1. Navigation Customization
The minima theme provides a default navigation bar, but I wanted to override it. I learned that:
- The theme's navigation is controlled by the layout and can be replaced by creating a custom `_includes/nav.html` and referencing it in a custom `_layouts/default.html`.
- Adding navigation links directly to content files (like `index.html`) can result in duplicate links if the theme's navigation is still active.

### 2. Pagination Setup
I enabled pagination in `_config.yml`, but Jekyll requires an `index.html` (not `index.md`) at the root for pagination to work. I had to:
- Create a minimal `index.html` with pagination logic using Liquid tags.
- Move or adjust content from `index.md` as needed.

### 3. Blog Post URLs
I initially linked to blog posts using their path in the `_posts` folder, but Jekyll generates URLs based on the post's date and title. The correct format is `/YYYY/MM/DD/post-title/`.

Jekyll does not publish posts dated in the future by default, so the post is not available for linking. I was getting the error message below which didn't give me much clue
Liquid Exception: Could not find post "2025-06-13-future-date-post" in tag 'post_url'. Make sure the post exists and the name is correct. in index.md

- Copilot suggested the following solution which worked great. Set `future: true` in your _config.yml to allow future-dated posts to be published.

### 4. File Redundancy and Best Practices
- I learned that `Gemfile.lock` should not be committed for GitHub Pages sites, as the build environment is managed by GitHub.
- Platform-specific gems like `wdm` and `tzinfo-data` are not needed in a Linux-based dev container.

### 4. Custom domain
Since I own the tinan.net domain I wanted to try using www.tinan.net as a custom domain for this site instead of the default mgholls.github.io
- I needed to add tinan.net as a verified domain at the user account / profile pages level first https://github.com/settings/pages. This required adding a TXT record to my tinan.net domain.
- I then created a CNAME record from www to mgholls.github.io on my DNS provider (Amazon Route 53) before adding this to the repo settings pages https://github.com/mgholls/mgholls.github.io/settings/pages.
- This seems to be working fine and I see a message saying that www.tinan.net is valid but also one saying there is a problem with the apex domain tinan.net.
When I come back to the Settings -> Pages later I see a message *DNS Check in Progress*. Since it is working I have moved on.
- I also checked the enforce HTTPS option. 

## Useful Links

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Jekyll on GitHub Pages](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)
- [Jekyll Official Documentation](https://jekyllrb.com/docs/)
- [minima Theme Documentation](https://github.com/jekyll/minima)

## Conclusion

Despite a few hurdles, setting up a technical blog with GitHub Pages, Jekyll, and the minima theme has been a great learning experience. The flexibility of Jekyll and the power of GitHub Pages make it a solid choice for personal blogging.
