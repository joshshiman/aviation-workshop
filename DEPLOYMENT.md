# GitHub Pages Deployment Guide

This guide explains how to deploy your Aviation Workshop documentation site to GitHub Pages.

## 📋 Prerequisites

- GitHub account
- Git installed on your computer
- This repository cloned locally

## 🚀 Quick Deployment (Recommended)

### Step 1: Push to GitHub

If you haven't already, push your repository to GitHub:

```bash
# Initialize git (if not already done)
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit: Aviation Workshop documentation site"

# Add remote (replace with your repository URL)
git remote add origin https://github.com/yourusername/aviation-workshop.git

# Push to main branch
git push -u origin main
```

### Step 2: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** (top right)
3. Click **Pages** in the left sidebar
4. Under **Source**, select:
   - **Source**: GitHub Actions
5. The workflow will automatically deploy your site

### Step 3: Update Configuration

Edit [`_config.yml`](_config.yml) and update these values:

```yaml
baseurl: "/aviation-workshop"  # Change to your repo name
url: "https://yourusername.github.io"  # Change to your GitHub username
repository: yourusername/aviation-workshop  # Change to your repo
```

### Step 4: Access Your Site

Your site will be available at:
```
https://yourusername.github.io/aviation-workshop/
```

The first deployment may take 2-3 minutes. Check the **Actions** tab to monitor progress.

## 🧪 Local Testing (Optional)

To test the site locally before deploying:

### Install Jekyll

**macOS:**
```bash
# Install Ruby (if not already installed)
brew install ruby

# Add Ruby to PATH
echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

# Install Bundler
gem install bundler
```

**Windows:**
1. Download and install [Ruby+Devkit](https://rubyinstaller.org/)
2. Run `ridk install` in the installer
3. Install Bundler:
   ```bash
   gem install bundler
   ```

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get install ruby-full build-essential zlib1g-dev
gem install bundler
```

### Run Locally

```bash
# Install dependencies
bundle install

# Serve the site locally
bundle exec jekyll serve

# Or with live reload
bundle exec jekyll serve --livereload
```

Open your browser to: `http://localhost:4000/aviation-workshop/`

## 📁 Site Structure

```
aviation-workshop/
├── _config.yml              # Jekyll configuration
├── _layouts/
│   └── default.html         # Custom layout with navigation
├── .github/
│   └── workflows/
│       └── jekyll-gh-pages.yml  # Auto-deployment workflow
├── docs/                    # Lab documentation
│   ├── lab-1-setup/
│   ├── lab-2-kafka/
│   ├── lab-3-agents/
│   └── lab-4-dashboard/
├── index.md                 # Home page
├── Gemfile                  # Ruby dependencies
└── DEPLOYMENT.md           # This file
```

## 🎨 Customization

### Change Theme

Edit [`_config.yml`](_config.yml):

```yaml
theme: jekyll-theme-cayman  # Current theme
# Other options:
# theme: jekyll-theme-minimal
# theme: jekyll-theme-slate
# theme: jekyll-theme-architect
```

### Modify Navigation

Edit [`_layouts/default.html`](_layouts/default.html) to add/remove navigation items:

```html
<nav class="site-nav">
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/docs/lab-1-setup/">Lab 1</a></li>
    <!-- Add more items here -->
  </ul>
</nav>
```

### Update Styles

Add custom CSS in [`_layouts/default.html`](_layouts/default.html) within the `<style>` tags.

## 🔧 Troubleshooting

### Site Not Deploying

1. Check the **Actions** tab for build errors
2. Verify [`_config.yml`](_config.yml) has correct `baseurl` and `url`
3. Ensure the workflow file exists at [`.github/workflows/jekyll-gh-pages.yml`](.github/workflows/jekyll-gh-pages.yml)
4. Check that GitHub Pages is enabled in repository settings

### 404 Errors

- Verify `baseurl` in [`_config.yml`](_config.yml) matches your repository name
- Check that all internal links use `{{ '/path' | relative_url }}`
- Ensure file paths are correct (case-sensitive)

### Images Not Loading

Images in the `docs/` folder should work automatically. If not:

1. Check image paths are relative: `images/screenshot.png`
2. Verify images are committed to the repository
3. Check file extensions match (case-sensitive)

### Local Build Fails

```bash
# Clear Jekyll cache
bundle exec jekyll clean

# Reinstall dependencies
rm -rf _site Gemfile.lock
bundle install

# Try building again
bundle exec jekyll serve
```

## 🔄 Updating the Site

After making changes:

```bash
# Stage changes
git add .

# Commit with descriptive message
git commit -m "Update lab documentation"

# Push to GitHub
git push origin main
```

The site will automatically rebuild and deploy within 2-3 minutes.

## 📚 Additional Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Jekyll Themes](https://pages.github.com/themes/)
- [Markdown Guide](https://www.markdownguide.org/)

## 🆘 Getting Help

If you encounter issues:

1. Check the [GitHub Pages status](https://www.githubstatus.com/)
2. Review the [Actions logs](https://github.com/yourusername/aviation-workshop/actions)
3. Search [GitHub Community](https://github.community/)
4. Open an issue in your repository

---

**Happy documenting!** 📖✨