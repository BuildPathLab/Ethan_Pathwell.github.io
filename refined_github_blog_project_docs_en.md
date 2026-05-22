# BuildPath Lab — Hugo Blog Setup Notes

A practical walkthrough for building and deploying a personal development blog using:

- Hugo
- GitHub Pages
- Hugoplate Theme
- GitHub Actions
- Giscus Comments

The goal of this project is to document the process of building ideas into reality — similar to a technical version of *The Pilgrim’s Progress*.

---

# 1. Project Goal

Create a personal blog for documenting:

- DIY projects
- Development workflows
- Problems encountered during implementation
- Debugging and troubleshooting
- Engineering trade-offs and solutions
- Lessons learned during the building process

---

# 2. Initial Exploration

At the beginning, I spent a long time reading the official Hugo documentation:

```text
https://gohugo.io/documentation/
```

However, it was difficult to understand the actual installation and workflow process from the documentation alone.

Then I explored additional tutorials:

```text
https://jimmysong.io/zh/book/hugo-handbook/introduction/hugo-overview/
```

This helped me better understand:

- Why Hugo is fast
- Why static websites are useful
- How GitHub Pages deployment works
- Why many developers prefer Hugo for personal blogs

---

# 3. Download and Install Hugo

Download Hugo from the official GitHub releases page:

```text
https://github.com/gohugoio/hugo/releases/tag/v0.161.1
```

Recommended:

- Install the **Extended** version
- Add `hugo.exe` to your system environment variables

Verify the installation:

```bash
hugo version
```

If version information appears, Hugo is installed successfully.

---

# 4. Install Git

Git is used for:

- Version control
- Synchronizing the local repository with GitHub
- Tracking project history

Official website:

```text
https://git-scm.com/
```

---

# 5. Install VS Code

VS Code is used for:

- Editing files
- Running the local development server
- Previewing the website locally

Official website:

```text
https://code.visualstudio.com/
```

---

# 6. Create a GitHub Account

GitHub will be used for:

- Hosting the repository
- Deploying the website
- Running GitHub Actions

---

# 7. Choose a Hugo Theme

Browse Hugo themes:

```text
https://themes.gohugo.io/
```

Advantages:

- Most themes provide live demos
- Easy to preview the design before downloading
- Faster setup compared to building a site from scratch

Initially, I downloaded a theme that failed during local startup.

Eventually I switched to:

```text
https://github.com/zeon-studio/hugoplate
```

This theme includes:

- Better documentation
- Clear installation steps
- Easier local development
- TailwindCSS integration
- Modern responsive design

Useful commands:

```bash
npm run project-setup
npm install
npm run dev
```

---

# 8. Common Synchronization Error

While syncing the repository, I encountered:

```text
ERROR: no existing content directory
```

Cause:

- Running commands from the wrong directory

Solution:

```bash
cd your-project-directory
```

Always make sure you are inside the Hugo project root folder.

---

# 9. GitHub Pages Deployment Workflow

## Step 1 — Create a Repository

Create a GitHub repository for the website.

Example:

```text
https://github.com/BuildPathLab/Ethan_Pathwell.github.io
```

---

## Step 2 — Enable GitHub Actions Deployment

Inside the repository:

1. Open **Settings**
2. Go to **Pages**
3. Under **Source**, select:

```text
GitHub Actions
```

Instead of:

```text
Deploy from a branch
```

---

## Step 3 — Configure Git Identity

Set your Git username and email:

```bash
git config --global user.name "BuildPathLab"
git config --global user.email "your-email@example.com"
```

Rename the branch to `main`:

```bash
git branch -M main
```

---

## Step 4 — Upload the Project

Initialize Git:

```bash
git init
```

Add the remote repository:

```bash
git remote add origin https://github.com/BuildPathLab/Ethan_Pathwell.github.io.git
```

Stage files:

```bash
git add .
```

Commit changes:

```bash
git commit -m "notes"
```

Push to GitHub:

```bash
git push -u origin main
```

---

## Step 5 — Verify Deployment

After pushing:

1. Open the repository
2. Click the **Actions** tab
3. Wait for deployment to finish
4. Open the generated blog URL

---

# 10. Missing CSS / Broken Styling Issue

After deployment, the website loaded without styling.

Cause:

- Incorrect `baseURL` configuration in `hugo.toml`

Fix:

```toml
baseURL = "https://your-blog-address/"
```

The URL must match your GitHub Pages address exactly.

---

# 11. Local Development

Run the local development server:

```bash
hugo server
```

Or, for Hugoplate:

```bash
npm run dev
```

---

# 12. Hugo Security Policy Error

Newer Hugo versions introduced stricter security policies.

If `hugo server` fails, add the following configuration:

```toml
[security.exec]
allow = ['^node$', '^go$', '^tailwindcss$']

[security.node]
allow = ['tailwindcss']
allowPaths = ['.']
```

---

# 13. Optional — Google Analytics

Google Analytics setup:

```text
https://analytics.google.com/analytics/web/provision/#/provision/create
```

Example configuration:

```toml
[services]
  [services.googleAnalytics]
  id = 'G-XXXXXXXXXX'
```

---

# 14. Optional — Visual Editing

I experimented with visual editing tools, but the experience was not ideal.

```text
https://app.sitepins.com/new/clone?name=Hugoplate&repository=https%3A%2F%2Fgithub.com%2Fzeon-studio%2Fhugoplate%3Faff%3Dhugoplate
```

---

# 15. Replace Disqus with Giscus

Disqus contained too many ads, so I switched to Giscus.

## Setup Process

### 1. Create a GitHub Repository for Comments

Enable:

```text
GitHub Discussions
```

---

### 2. Install the Giscus GitHub App

```text
https://github.com/settings/installations/130726734
```

---

### 3. Configure Giscus

```text
https://giscus.app/
```

---

### 4. Add Giscus to Hugo

Create or edit:

```text
layouts/blog/single.html
```

Insert:

```html
<div class="giscus"></div>
<script src="https://giscus.app/client.js"
        data-repo="BuildPathLab/Ethan_Pathwell.github.io-comments"
        data-repo-id="R_kgDOSYTWwQ"
        data-category="Announcements"
        data-category-id="DIC_kwDOSYTWwc4C8oD2"
        data-mapping="pathname"
        data-strict="0"
        data-reactions-enabled="1"
        data-emit-metadata="0"
        data-input-position="bottom"
        data-theme="preferred_color_scheme"
        data-lang="en"
        data-loading="lazy"
        crossorigin="anonymous"
        async>
</script>
```

---

# 16. Sync Giscus with Light/Dark Mode

To make Giscus automatically follow the website theme:

```html
<div class="giscus"></div>

<script>
function initGiscusWithTheme() {
    const savedTheme = localStorage.getItem('theme');
    const targetTheme =
        (savedTheme === 'dark' || savedTheme === 'light')
        ? savedTheme
        : 'light';

    const script = document.createElement('script');

    script.src = 'https://giscus.app/client.js';
    script.setAttribute('data-repo', 'BuildPathLab/Ethan_Pathwell.github.io-comments');
    script.setAttribute('data-repo-id', 'R_kgDOSYTWwQ');
    script.setAttribute('data-category', 'Announcements');
    script.setAttribute('data-category-id', 'DIC_kwDOSYTWwc4C8oD2');
    script.setAttribute('data-mapping', 'pathname');
    script.setAttribute('data-theme', targetTheme);
    script.setAttribute('data-lang', 'zh-CN');
    script.setAttribute('data-loading', 'lazy');
    script.setAttribute('crossorigin', 'anonymous');
    script.async = true;

    const giscusContainer = document.querySelector('.giscus');

    if (giscusContainer) {
        giscusContainer.appendChild(script);
    }

    const themeObserver = new MutationObserver(() => {
        const newTheme = document.documentElement.classList.contains('dark')
            ? 'dark'
            : 'light';

        const giscusIframe = document.querySelector('iframe.giscus-frame');

        if (giscusIframe && giscusIframe.contentWindow) {
            giscusIframe.contentWindow.postMessage(
                {
                    giscus: {
                        setConfig: {
                            theme: newTheme
                        }
                    }
                },
                'https://giscus.app'
            );
        }
    });

    themeObserver.observe(document.documentElement, {
        attributes: true,
        attributeFilter: ['class']
    });
}

if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', initGiscusWithTheme);
} else {
    initGiscusWithTheme();
}
</script>
```

---

# 17. Customize Logo and Branding

I used Canva to create the logo:

```text
https://www.canva.com/
```

Important configuration files:

```text
config/
├── _default/
│   ├── hugo.toml
│   ├── params.toml
│   ├── menus.en.toml
│   ├── languages.toml
│   └── module.toml
└── development/
    └── server.toml
```

---

# 18. Customize Navigation and Announcement Bar

Modify:

```text
params.toml
```

Examples:

- Navigation button links
- Announcement bar content
- Theme settings
- Sidebar widgets

---

# 19. Customize Social Links and Footer Icons

Relevant files:

```text
data/
├── theme.json
├── social.json
└── other custom data files
```

---

# 20. Content Structure

Main content directory:

```text
content/
└── english/
    ├── _index.md
    ├── about/
    ├── blog/
    ├── authors/
    ├── contact/
    ├── pages/
    └── sections/
```

Homepage section files:

```text
content/english/sections/testimonial.md
content/english/sections/call-to-action.md
```

---

# 21. Write the First Blog Post

Example frontmatter:

```yaml
---
title: "Article Title"
meta_title: ""
description: "Article description"
date: "2026-01-01"
image: "images/example.png"
categories: ["Category 1", "Category 2"]
author: "Author Name"
tags: ["Tag 1", "Tag 2"]
draft: false
---
```

Then write the article content using Markdown.

---

# 22. Embed YouTube Videos

Example:

```markdown
{{< youtube abc123DEF >}}
```

If the video URL is:

```text
https://www.youtube.com/watch?v=abc123DEF
```

Then the video ID is:

```text
abc123DEF
```

---

# 23. Important Observation

The date configured in the article frontmatter may affect:

- Publication order
- Visibility after deployment
- Sorting on the homepage

---

# 24. Final Thoughts

This entire process involved:

- Many installation issues
- Deployment troubleshooting
- Configuration debugging
- Learning Git workflows
- Understanding Hugo architecture

Although difficult at first, the process provided valuable experience.

---

# 25. Future Improvements

Potential future upgrades:

## SEO Optimization

Possible modules:

```text
hugo-modules/seo-tools
```

Purpose:

- Better search rankings
- Improved discoverability

---

## Google Search Console

Useful for:

- Keyword traffic analysis
- Search indexing
- Website monitoring

---

## Email Subscription System

Useful after building a small audience.

For example:

- Notify subscribers about new posts
- Build long-term readers
- Maintain communication with loyal followers

---

# Supplementary Configuration Notes

Below are refined explanations for the key configuration files used in the project.

---

# hugo.toml

## Basic Site Configuration

```toml
baseURL = "https://buildpathlab.github.io/Ethan_Pathwell.github.io/"
title = "BuildPath Lab"
theme = "hugoplate"
timeZone = "America/New_York"
summaryLength = 10
```

Explanation:

- `baseURL` → Public website URL
- `title` → Website title shown in the browser
- `theme` → Hugo theme name
- `timeZone` → Website timezone
- `summaryLength` → Number of words shown in article previews

---

## Google Analytics

```toml
[services]
  [services.googleAnalytics]
    ID = 'G-S9FPCTBTCD'
```

Used for visitor tracking and analytics.

---

## Pagination

```toml
[pagination]
  pagerSize = 10
  path = 'page'
```

Controls:

- Number of posts per page
- Pagination URL structure

---

## Markdown Rendering

```toml
[markup]
  [markup.goldmark.renderer]
    unsafe = true
```

Allows raw HTML inside Markdown.

---

## Syntax Highlighting

```toml
[markup.highlight]
  style = 'monokai'
```

Controls code highlighting appearance.

---

# netlify.toml

```toml
[build]
  publish = "public"
  command = "yarn project-setup; yarn build"
```

Defines:

- Build output folder
- Deployment build commands

---

# params.toml

Controls theme behavior and UI settings.

Example:

```toml
favicon = "images/favicon_BuildPathLab.png"
logo = "images/LOGO_BuildPathLab.png"
navbar_fixed = true
theme_switcher = true
```

Used for:

- Logo configuration
- Theme switching
- Navigation behavior
- Search settings
- Widgets
- SEO metadata
- Announcement bar

---

# module.toml

Imports Hugo modules.

Example:

```toml
[[imports]]
  path = "github.com/gethugothemes/hugo-modules/search"
```

Used for:

- Search
- SEO tools
- Mermaid diagrams
- Image optimization
- PWA support
- Social sharing
- Cookie consent
- Table of contents

---

# languages.toml

Example:

```toml
[en]
  label = "En"
  locale = "en-us"
  contentDir = "content/english"
```

Defines multilingual settings.

---

# menus.en.toml

Controls:

- Top navigation
- Footer navigation
- Dropdown menus

Example:

```toml
[[main]]
  name = "Home"
  url = "/"
```

---

# theme.toml

Contains:

- Theme metadata
- License information
- Minimum Hugo version
- Theme features

---

# Final Advice

If you are building your first Hugo blog:

1. Start with a well-documented theme
2. Learn Git basics early
3. Test locally before deploying
4. Keep backups of working configurations
5. Solve one problem at a time
6. Expect deployment issues during the first setup

The learning curve is steep at the beginning, but once the workflow is understood, Hugo becomes extremely efficient for technical blogging and long-term content publishing.

