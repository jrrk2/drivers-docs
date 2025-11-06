# Driver Documentation Contribution Guide

This guide explains how to add new driver documentation, including details on file structure, image placement, and how custom CSS ensures consistent styling. This project aims to provide a comprehensive and easily navigable resource for various drivers.

## 1. Adding New Drivers

Each driver entry consists of two files: a Markdown (`.md`) file for the main content and a YAML (`.yaml`) file for metadata.

### File Structure

All driver documentation resides within `src/content/docs/`, organized by category and manufacturer:

```
src/content/docs/
├── mounts/                      # Category (lowercase slug)
│   ├── sky-watcher/            # Manufacturer (lowercase slug)
│   │   ├── eqmod.md           # Driver documentation
│   │   └── eqmod.yaml         # Driver metadata
│   └── ikarus-technologies/
│       ├── stellarmate-pro.md
│       └── stellarmate-pro.yaml
├── cameras/
│   └── altair-astro/
│       ├── altair.md
│       └── altair.yaml
└── ...
```

**Directory Naming Convention:**
- Use **lowercase** with **hyphens** for directory names (e.g., `sky-watcher`, `ikarus-technologies`)
- Category directories: `mounts`, `cameras`, `focusers`, etc.
- Manufacturer directories: `sky-watcher`, `zwo`, `qhyccd`, etc.
- Driver filenames: `eqmod.md`, `altair.md`, etc.

### YAML Metadata File

The YAML file contains driver metadata with both human-friendly display names and additional information:

```yaml
# Display Names (Human-Friendly - Required)
driver_name: EQMod Mount
category_name: Mounts
manufacturer_name: Sky Watcher

# Additional Metadata (Optional)
website: www.indlib.org
executable: indi_eqmod_telescope
family: Telescopes
platforms: Linux, BSD, OSX
author: Jean-Luc Levaire
version: 1.0
```

**Key Fields:**
- `driver_name`: Human-friendly driver name (displayed on the website)
- `category_name`: Human-friendly category name (e.g., "Mounts", "Cameras")
- `manufacturer_name`: Human-friendly manufacturer name (e.g., "Sky Watcher", "Ikarus Technologies")
- Additional fields: You can add any custom metadata that will be displayed in the driver information sidebar

**Important:** The human-friendly names in the YAML file are what users will see on the website, while the directory structure uses SEO-friendly slugs for URLs.

### Markdown Documentation File

The Markdown file contains the main driver documentation:

```markdown
---
title: EQMod Mount
category: Mounts
description: The EQMod driver for Sky Watcher mounts.
thumbnail: /images/drivers/mounts/eqmod/eqmod.webp
---

# EQMod Driver

This is the documentation for the EQMod driver...

## Features

* Feature 1
* Feature 2

## Installation

Installation instructions...
```

**Frontmatter Fields:**
- `title`: The driver name (should match `driver_name` in YAML)
- `category`: Category name (should match `category_name` in YAML)
- `description`: Brief description for SEO and previews
- `thumbnail`: (Optional) Path to the driver's main image

## 2. Image Guidelines

To maintain a consistent look and feel across the documentation, please adhere to the following image guidelines.

### Driver Images

**Path Structure:**
```
/public/images/drivers/<category-slug>/<manufacturer-slug>/<driver-slug>/<image-name>.webp
```

**Example:**
```
/public/images/drivers/mounts/eqmod/eqmod.webp
/public/images/drivers/cameras/altair-astro/altair.webp
```

**Requirements:**
- **Format**: Must be `.webp`
- **Recommended Size**: 200x200 pixels for thumbnails
- **Styling**: Images are automatically styled to fit within 200x200px while maintaining aspect ratio

### Manufacturer Logos

**Path:**
```
/public/images/manufacturers/<manufacturer-slug>.webp
```

**Examples:**
```
/public/images/manufacturers/sky-watcher.webp
/public/images/manufacturers/ikarus-technologies.webp
/public/images/manufacturers/altair-astro.webp
```

**Requirements:**
- **Format**: Must be `.webp`
- **Recommended Size**: 200x200 pixels
- **Styling**: Logos are automatically styled to fit within 200x200px

### Category Icons

**Path:**
```
/public/images/categories/<category-slug>.webp
```

**Examples:**
```
/public/images/categories/mounts.webp
/public/images/categories/cameras.webp
```

## 3. URL Structure

The site automatically generates clean, SEO-friendly URLs based on the directory structure:

**Directory Structure:**
```
src/content/docs/mounts/sky-watcher/eqmod.md
```

**Generated URL:**
```
https://drivers.indilib.org/mounts/sky-watcher/eqmod
```

**Display Names:**
The website will show "Mounts" > "Sky Watcher" > "EQMod Mount" using the human-friendly names from your YAML file, while the URL remains clean and SEO-friendly.

## 4. Markdown Features

This project supports GitHub-flavored Markdown, including special callout blocks for highlighting important information.

### Callout Blocks

You can use various types of callout blocks to emphasize different kinds of information:

```markdown
> [!NOTE]
> This is a note with general information.

> [!TIP]
> This is a helpful tip.

> [!IMPORTANT]
> This is important information.

> [!WARNING]
> This is a warning about potential issues.

> [!CAUTION]
> This is a critical caution or serious warning.
```

These callouts are rendered with custom styling to draw attention to specific content.

## 5. Step-by-Step Contribution Process

### Adding a New Driver

1. **Create the directory structure:**
   ```bash
   mkdir -p src/content/docs/<category-slug>/<manufacturer-slug>
   ```
   Example:
   ```bash
   mkdir -p src/content/docs/mounts/sky-watcher
   ```

2. **Create the YAML metadata file:**
   ```bash
   touch src/content/docs/mounts/sky-watcher/eqmod.yaml
   ```
   Add your metadata with human-friendly names:
   ```yaml
   driver_name: EQMod Mount
   category_name: Mounts
   manufacturer_name: Sky Watcher
   website: www.indlib.org
   # ... other fields
   ```

3. **Create the Markdown documentation file:**
   ```bash
   touch src/content/docs/mounts/sky-watcher/eqmod.md
   ```
   Add your documentation with frontmatter:
   ```markdown
   ---
   title: EQMod Mount
   category: Mounts
   description: Driver description here
   thumbnail: /images/drivers/mounts/eqmod/eqmod.webp
   ---
   
   Your documentation content...
   ```

4. **Add images:**
   - Driver images: `public/images/drivers/mounts/sky-watcher/`
   - Manufacturer logo: `public/images/manufacturers/sky-watcher.webp`

5. **Test locally:**
   ```bash
   npm run dev
   ```
   Visit `http://localhost:4321/mounts/sky-watcher/eqmod`

6. **Submit a pull request** with your changes.

## 6. Important Notes

- **Consistency**: Always use lowercase with hyphens for directory and file names
- **Human-Friendly Names**: Use proper capitalization and spacing in YAML metadata
- **Images**: Convert images to `.webp` format for optimal performance
- **Documentation**: Write clear, comprehensive documentation with examples
- **Testing**: Always test your contribution locally before submitting

## Contribution

We welcome contributions from the community! If you have new driver documentation to add or improvements to existing ones, please follow this guide. Your contributions help make this resource more valuable for everyone.

For questions or issues, please open an issue on the GitHub repository.
