# Astro Component Structure and CMS Integration Guide

*Last Updated: March 30, 2025*

## Understanding Component Data Flow in Astro

When working with Astro components, understanding how data flows from pages to components and how this can integrate with a CMS is crucial for building maintainable websites.

## Component Structure in Astro

Astro components follow this structure:

```astro
---
// 1. Frontmatter (JavaScript/TypeScript code)
import { SomeComponent } from 'some-package';
import type { MyComponentProps } from '~/types';

// Props definition with defaults
const {
  title = "Default title",
  subtitle = "Default subtitle",
  // More props with default values...
} = Astro.props as MyComponentProps;
---

<!-- 2. Template (HTML with component tags) -->
<section class="my-component">
  {title && <h1>{title}</h1>}
  {subtitle && <p>{subtitle}</p>}
</section>

<style>
  /* 3. CSS styles (scoped to this component) */
  .my-component {
    /* styles */
  }
</style>
```

## How Component Props Work

When you look at a component like ZenHero.astro, you'll see this pattern:

```astro
const {
  title = "Fast websites. <br /> <span class=\"zen-gradient-text\">Smart insights.</span>",
  subtitle = "We create websites that load instantly...",
  // More props with default values...
} = Astro.props as Props;
```

This is doing three important things:
1. **Receiving props**: `Astro.props` contains all data passed to the component
2. **Setting defaults**: The `= "value"` syntax provides fallback content if no prop is passed
3. **Type checking**: `as Props` ensures the data matches the expected structure

## CMS Integration with Astro Components

With a CMS, you'd be able to directly edit component props. Here's how it works with the two CMS options mentioned in our strategy document:

### 1. Git-based CMS Integration (Decap/TinaCMS)

These store content as data files (JSON/YAML/Markdown) in your repository:

```
/content/
  /home/
    hero.json  <-- Contains title, subtitle, etc.
    services.json
```

**Content Flow:**
1. CMS edits → data files in Git repository
2. Data files → imported in Astro page
3. Imported data → passed as props to components

```astro
---
// In zenze.astro
import heroContent from '~/content/home/hero.json';
---

<ZenHero {...heroContent} />
```

### 2. API-based CMS Integration (Contentful, Sanity, etc.)

**Content Flow:**
1. CMS edits → stored in CMS database
2. Astro page → fetches data via API
3. API data → passed as props to components

```astro
---
// In zenze.astro
const response = await fetch('https://api.cms.com/hero');
const heroContent = await response.json();
---

<ZenHero {...heroContent} />
```

## TinaCMS Integration (Our Selected Approach)

TinaCMS is particularly effective because it offers visual editing capabilities:

1. Editors can see the actual page in a preview mode
2. Click on the hero section to edit its properties
3. Make changes to title, subtitle, etc. in a sidebar
4. Save changes directly to your Git repository

The key advantage is that your components don't need to change - TinaCMS maps the CMS fields to your component props structure, making the development experience seamless.

## Content Collections in Astro

Astro also provides Content Collections, which are a built-in way to manage content with type safety:

```
/src/content/
  /heroes/
    home.md
    about.md
  /services/
    service1.md
    service2.md
```

These can be queried and used in components:

```astro
---
import { getCollection } from 'astro:content';
const heroes = await getCollection('heroes');
const homeHero = heroes.find(h => h.id === 'home');
---

<ZenHero {...homeHero.data} />
```

This approach works exceptionally well with Git-based CMS systems.

## Best Practices

1. **Keep components clean**: Components should not contain business logic for fetching their own data
2. **Single source of truth**: Pages should fetch all data and pass it down to components
3. **Type everything**: Use TypeScript interfaces for all component props
4. **Sensible defaults**: Always provide default values for component props
5. **Content separation**: Keep content separate from presentation logic

Following these patterns will ensure your Astro site remains maintainable and CMS-friendly as it grows.
