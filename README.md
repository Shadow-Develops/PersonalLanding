# Personal Landing Page

A modern, customizable landing page template for showcasing your personal brand, projects, and contact information.

## Quick Start

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd PersonalLanding
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Run the development server**

   ```bash
   npm run dev
   ```

4. **Build for production**
   ```bash
   npm run build
   ```

## Configuration

The landing page is fully customizable through the [config.json](config.json) file. Edit this file to personalize your site without touching any code.

### Structure

```json
{
  "domain": "Your site URL",
  "siteSettings": {
    "siteName": "Your site name",
    "siteDescription": "Your site description",
    "metaColor": "#4A90E2"
  },
  "footerSettings": {
    "enabled": true,
    "text": "Your footer text"
  },
  "sections": [...]
}
```

### Available Sections

Each section in the `sections` array can be toggled on/off and customized:

- **Hero** - Main landing section (variants: `centered`, `split`, `minimal`, `bold`, `card`, `links`)
- **About** - About me section with skills (variants: `centered`, `split`, `card`, `minimal`)
- **Stats** - Display statistics or achievements
- **Services** - Showcase your services or offerings
- **Projects** - Featured projects with tags and links
- **Timeline** - Experience or education timeline
- **Gallery** - Image gallery (variants: `grid`, `masonry`, `lightbox`, `carousel`)
- **Testimonials** - Client or colleague testimonials
- **FAQ** - Frequently asked questions
- **Links** - Social media and contact links (variants: `default`, `grid`, `card`, `minimal`)
- **Contact** - Contact form and email button

### Quick Tips

- Set `"enabled": false` to hide any section
- Multiple sections of the same type can be used with different variants
- Images should be placed in the `static/img/` directory
- Use markdown in footer text (e.g., `[link text](url)`)

## Documentation

For detailed setup instructions, customization options, and deployment guides, visit our comprehensive documentation:

**[https://docs.shadowdevs.com/personalLanding](https://docs.shadowdevs.com/personalLanding)**

## About

Created by [Shadow Development](https://shadowdevs.com/)

---

For issues, questions, or contributions, please refer to the documentation or contact Shadow Development.
