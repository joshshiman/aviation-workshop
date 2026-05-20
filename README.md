# ✈️ Aviation Workshop Documentation Site

A comprehensive GitHub Pages documentation site for the Aviation Workshop - building a real-time aviation warning system with Kafka, watsonx Orchestrate, and AI agents.

## 🌐 Live Site

Once deployed, your site will be available at:
```
https://yourusername.github.io/aviation-workshop/
```

## 📚 What's Included

This documentation site includes:

- **Home Page** - Workshop overview and navigation
- **Lab 1: Environment Setup** - Get started with credentials and dependencies
- **Lab 2: Kafka Consumer** - Build real-time data streaming
- **Lab 3: AI Agents** - Create intelligent analysis tools with watsonx Orchestrate
- **Lab 4: Interactive Dashboard** - Visualize data with maps and alerts

## 🚀 Quick Start

### Deploy to GitHub Pages

1. **Update Configuration**
   
   Edit [`_config.yml`](_config.yml) and replace:
   ```yaml
   baseurl: "/aviation-workshop"  # Your repo name
   url: "https://yourusername.github.io"  # Your GitHub username
   repository: yourusername/aviation-workshop  # Your repo
   ```

2. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Initial commit: Aviation Workshop docs"
   git push origin main
   ```

3. **Enable GitHub Pages**
   - Go to repository **Settings** → **Pages**
   - Under **Source**, select **GitHub Actions**
   - Wait 2-3 minutes for deployment

4. **Access Your Site**
   ```
   https://yourusername.github.io/aviation-workshop/
   ```

For detailed instructions, see [`DEPLOYMENT.md`](DEPLOYMENT.md).

### Test Locally (Optional)

```bash
# Install dependencies
bundle install

# Run local server
bundle exec jekyll serve

# Open browser to:
# http://localhost:4000/aviation-workshop/
```

## 📁 Repository Structure

```
aviation-workshop/
├── _config.yml              # Jekyll configuration
├── _layouts/
│   └── default.html         # Custom layout with navigation
├── .github/
│   └── workflows/
│       └── jekyll-gh-pages.yml  # Auto-deployment
├── docs/                    # Lab documentation (existing)
│   ├── lab-1-setup/
│   │   ├── README.md
│   │   └── images/
│   ├── lab-2-kafka/
│   │   └── README.md
│   ├── lab-3-agents/
│   │   └── README.md
│   └── lab-4-dashboard/
│       └── README.md
├── index.md                 # Home page
├── Gemfile                  # Ruby dependencies
├── DEPLOYMENT.md           # Deployment guide
└── README.md               # This file
```

## 🎨 Features

- **Responsive Design** - Works on desktop, tablet, and mobile
- **Navigation Menu** - Easy access to all labs
- **Breadcrumb Navigation** - Know where you are
- **Code Syntax Highlighting** - Beautiful code blocks
- **Image Support** - All lab images included
- **Search Engine Friendly** - Proper meta tags and structure
- **IBM Carbon Inspired** - Professional enterprise styling
- **Auto-Deployment** - Push to main branch and it deploys automatically

## 🛠️ Technologies

- **Jekyll** - Static site generator
- **GitHub Pages** - Free hosting
- **Cayman Theme** - Clean, professional design
- **GitHub Actions** - Automated deployment
- **Markdown** - Easy content editing

## 📝 Editing Content

All lab content is in the `docs/` folder. Each lab has its own directory with a `README.md` file:

- [`docs/lab-1-setup/README.md`](docs/lab-1-setup/README.md)
- [`docs/lab-2-kafka/README.md`](docs/lab-2-kafka/README.md)
- [`docs/lab-3-agents/README.md`](docs/lab-3-agents/README.md)
- [`docs/lab-4-dashboard/README.md`](docs/lab-4-dashboard/README.md)

To edit:
1. Modify the markdown files
2. Commit and push changes
3. Site rebuilds automatically

## 🎯 Customization

### Change Theme

Edit [`_config.yml`](_config.yml):
```yaml
theme: jekyll-theme-cayman  # Current
# Other options: minimal, slate, architect, etc.
```

### Modify Navigation

Edit [`_layouts/default.html`](_layouts/default.html) to add/remove menu items.

### Update Styles

Add custom CSS in the `<style>` section of [`_layouts/default.html`](_layouts/default.html).

## 🔧 Troubleshooting

### Site Not Deploying?
- Check **Actions** tab for build errors
- Verify `baseurl` in [`_config.yml`](_config.yml)
- Ensure GitHub Pages is enabled in Settings

### 404 Errors?
- Check `baseurl` matches repository name
- Verify file paths are correct (case-sensitive)

### Images Not Loading?
- Ensure images are in `docs/lab-X/images/`
- Check paths are relative: `images/screenshot.png`

For more help, see [`DEPLOYMENT.md`](DEPLOYMENT.md).

## 📚 Resources

- [GitHub Pages Docs](https://docs.github.com/en/pages)
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Markdown Guide](https://www.markdownguide.org/)
- [Cayman Theme](https://github.com/pages-themes/cayman)

## 🤝 Contributing

To contribute to the workshop documentation:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This workshop is provided for educational purposes.

## 🆘 Support

For issues or questions:
- Open an issue in this repository
- Check the [DEPLOYMENT.md](DEPLOYMENT.md) guide
- Review existing documentation

---

**Built with ❤️ for the Aviation Workshop**