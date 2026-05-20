# IBM Carbon Design System Theme

I've created a **custom IBM Carbon Design System theme** for your GitHub Pages site! 🎨

## ✨ What's Included

### 1. **Authentic Carbon Design**
- **IBM Plex Sans** font family (Carbon's official typeface)
- **IBM Plex Mono** for code blocks
- Carbon's color palette (Gray scale + Blue)
- Carbon spacing scale (0.5rem to 3rem)
- Carbon typography scale

### 2. **Carbon Components**
- **Header** - Dark header with navigation (like Carbon UI Shell)
- **Sidebar Navigation** - Sticky sidebar for lab pages
- **Breadcrumbs** - Carbon-style breadcrumb navigation
- **Tables** - Striped tables with hover states
- **Code Blocks** - Syntax highlighting with Carbon styling
- **Buttons** - Carbon button styles
- **Notifications** - Blockquotes styled as Carbon notifications

### 3. **Carbon Features**
- **Motion** - Carbon's cubic-bezier easing (0.2, 0, 0.38, 0.9)
- **Grid System** - Responsive 16-column grid
- **Spacing** - Consistent spacing using Carbon tokens
- **Colors** - Gray-100 (#161616) text, Blue-60 (#0f62fe) links
- **Dark Mode** - Automatic dark mode support (respects system preference)

## 🎯 Carbon Design Principles Applied

1. **Productive** - Clean, efficient layouts for documentation
2. **Clarity** - Clear hierarchy and readable typography
3. **Consistency** - Uniform spacing and styling throughout
4. **Accessibility** - Proper contrast ratios and semantic HTML

## 📁 Files Created

1. **[`assets/css/carbon-theme.css`](assets/css/carbon-theme.css)** - Complete Carbon CSS
2. **[`_layouts/carbon.html`](_layouts/carbon.html)** - Carbon layout template
3. **Updated [`_config.yml`](_config.yml)** - Disabled default theme
4. **Updated [`index.md`](index.md)** - Uses Carbon layout

## 🚀 How to Use

The Carbon theme is **already activated**! Just push to GitHub:

```bash
git add .
git commit -m "Add IBM Carbon Design System theme"
git push origin main
```

Your site will now use the Carbon theme automatically.

## 🎨 Visual Features

### Header
- Dark background (#161616)
- White text with hover effects
- Active page indicator (blue underline)
- Responsive mobile menu

### Content Area
- Max width: 1584px (Carbon's large breakpoint)
- Two-column grid (sidebar + content)
- Sticky sidebar navigation
- Clean, spacious layout

### Typography
- **Headings**: IBM Plex Sans (300-600 weight)
- **Body**: IBM Plex Sans (400 weight)
- **Code**: IBM Plex Mono
- **Sizes**: Carbon's productive heading scale

### Colors
- **Text**: Gray-100 (#161616)
- **Links**: Blue-60 (#0f62fe)
- **Backgrounds**: White / Gray-10
- **Borders**: Gray-20 (#e0e0e0)

### Interactive Elements
- **Hover**: 110ms cubic-bezier transition
- **Focus**: Blue-60 outline
- **Active**: Blue-80 background

## 📱 Responsive Design

- **Desktop (>1056px)**: Full grid with sidebar
- **Tablet (672-1056px)**: Single column, sidebar on top
- **Mobile (<672px)**: Stacked layout, smaller typography

## 🌙 Dark Mode

Automatically activates when user's system is in dark mode:
- Background: Gray-100 (#161616)
- Text: Gray-10 (#f4f4f4)
- Code blocks: Gray-90 background
- Maintains proper contrast ratios

## 🔧 Customization

### Change Colors

Edit [`assets/css/carbon-theme.css`](assets/css/carbon-theme.css):

```css
:root {
  --cds-blue-60: #0f62fe;  /* Primary color */
  --cds-gray-100: #161616; /* Text color */
}
```

### Adjust Spacing

```css
:root {
  --cds-spacing-05: 1rem;   /* Base spacing */
  --cds-spacing-07: 2rem;   /* Section spacing */
}
```

### Modify Typography

```css
:root {
  --cds-productive-heading-06: 2.625rem; /* H1 size */
  --cds-body-long-02: 1rem;              /* Body size */
}
```

## 📚 Carbon Resources

- [Carbon Design System](https://carbondesignsystem.com/)
- [Carbon Components](https://www.carbondesignsystem.com/components/overview/)
- [Carbon Color Palette](https://carbondesignsystem.com/guidelines/color/overview/)
- [Carbon Typography](https://carbondesignsystem.com/guidelines/typography/overview/)
- [IBM Plex Fonts](https://www.ibm.com/plex/)

## 🆚 Comparison with Other Themes

| Feature | Carbon Theme | Cayman | Minimal |
|---------|-------------|--------|---------|
| IBM Branding | ✅ Yes | ❌ No | ❌ No |
| Dark Mode | ✅ Auto | ❌ No | ❌ No |
| Sidebar Nav | ✅ Yes | ❌ No | ✅ Yes |
| Grid System | ✅ 16-col | ❌ Basic | ❌ Basic |
| Typography | ✅ IBM Plex | ❌ Generic | ❌ Generic |
| Motion | ✅ Carbon | ❌ Basic | ❌ None |

## 🎯 Perfect For

- ✅ IBM-related projects
- ✅ Enterprise documentation
- ✅ Professional technical guides
- ✅ watsonx workshops (like yours!)
- ✅ Anyone who loves Carbon Design System

## 💡 Pro Tips

1. **Images**: Place in `docs/lab-X/images/` - they'll work automatically
2. **Code Blocks**: Use triple backticks with language for syntax highlighting
3. **Tables**: Markdown tables get automatic Carbon styling
4. **Links**: Internal links automatically styled with Carbon blue
5. **Blockquotes**: Use `>` for Carbon-style notifications

## 🔄 Switch Back to Another Theme

If you want to try a different theme later:

1. Edit [`_config.yml`](_config.yml):
   ```yaml
   theme: jekyll-theme-minimal  # or any other theme
   ```

2. Change [`index.md`](index.md) layout:
   ```yaml
   layout: default  # instead of carbon
   ```

3. Push changes

---

**Enjoy your IBM Carbon-themed documentation site!** 🎨✨