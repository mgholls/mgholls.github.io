# Martin Hollingsworth | Personal Technical Blog

## Purpose

This repository hosts the source code and content for my personal technical blog, built using [GitHub Pages](https://pages.github.com/) and [Jekyll](https://jekyllrb.com/). The goal is to share technical articles, project showcases, and resources related to software development and technology.

## Technologies Used

- **GitHub Pages**: Static site hosting directly from this GitHub repository.
- **Jekyll**: Static site generator for transforming markdown and HTML into a complete website.
- **minima theme**: The default Jekyll theme, providing a clean and responsive layout.
- **Markdown**: For writing blog posts and project documentation.
- **Ruby & Bundler**: For managing Jekyll and its dependencies.

## Usage Instructions

1. **Clone the repository:**
   ```sh
   git clone https://github.com/mgholls/mgholls.github.io.git
   cd mgholls.github.io
   ```
2. **Install dependencies:**
   ```sh
   bundle install
   ```
3. **Serve the site locally with live reload:**
   ```sh
   bundle exec jekyll serve --livereload
   # Or if you need to debug the build and templating include the --verbose switch
   bundle exec jekyll serve --livereload --verbose
   ```
   The site will be available at [http://localhost:4000](http://localhost:4000).
4. **Add new posts:**
   - Create new markdown files in the `_posts/` directory using the format `YYYY-MM-DD-title.md`.
5. **Customize navigation:**
   - Edit `_includes/nav.html` to update the navigation bar.
6. **Deploy:**
   - Push changes to the `main` branch. GitHub Pages will automatically build and deploy the site.
7. **Custom Domain**
   - The https://www.tinan.net/ custom domain has been configured for this site using a CNAME to mgholls.github.io

## References

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Jekyll on GitHub Pages](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)
- [minima Theme (GitHub, `v2.5.1` branch used by GitHub Pages)](https://github.com/jekyll/minima/tree/v2.5.1)

---

For questions or suggestions, please open an issue or contact me via [GitHub](https://github.com/mgholls).
