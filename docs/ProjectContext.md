# AstroZen Project Context

## Project Overview

AstroZen is a web development project built with the Astro framework, leveraging its island architecture for optimal performance. The project is designed to create fast, SEO-friendly websites with minimal JavaScript and maximum performance.

## Core Technology Stack

- **Astro**: The core framework providing static site generation with selective hydration
- **TailwindCSS**: Used for styling all components
- **DecapCMS**: Currently implemented as the content management system
- **Markdown/MDX**: Used for content authoring

## Project Structure

The project follows Astro conventions:

```
astrozen/
├── docs/                   # Project documentation
│   ├── AstroInnerWorkings.md       # Technical documentation of Astro's architecture
│   ├── AstroExplainedSimply.md     # Simplified explanation of Astro concepts
│   ├── FutureTechConsiderations.md # Analysis of potential future technologies
│   ├── UltrazenStrategy.md         # Strategic overview of the project
│   └── ProjectContext.md           # This file - project context for next sessions
│
├── src/                    # Source code
│   ├── components/         # Reusable UI components
│   │   ├── ui/             # Basic UI elements
│   │   ├── widgets/        # Higher-level components (Service.astro, etc.)
│   │   └── blog/           # Blog-specific components
│   │
│   ├── layouts/            # Page layout templates
│   │   └── PageLayout.astro # Main page wrapper
│   │
│   ├── pages/              # Each .astro file becomes a route
│   │   ├── index.astro     # Homepage
│   │   └── services.astro  # Services page
│   │
│   ├── content/            # Content collections
│   │   └── config.ts       # Content type definitions
│   │
│   └── assets/             # Static assets
│       └── images/         # Image files
│
└── public/                 # Files served directly
    └── decapcms/           # CMS configuration
```

## Current Progress

In our previous sessions, we have:

1. **Created Documentation**: Generated comprehensive documentation about Astro and our project structure
2. **Analyzed Existing Components**: Reviewed the Service.astro component and its implementation
3. **Set Up Documentation Structure**: Organized all docs into a dedicated /docs directory
4. **Explored Astro's Architecture**: Documented the island architecture and how it benefits our project

## Key Files

The most important files in our project:

- `src/components/widgets/Service.astro`: The service component we've been analyzing
- `src/pages/services.astro`: The services page using the Service component
- `docs/AstroInnerWorkings.md`: Detailed technical documentation
- `docs/AstroExplainedSimply.md`: Simplified explanation of Astro

## Next Steps

For future sessions, we plan to:

1. **Implement Content Collections**
   - Create a proper content collection for services
   - Example implementation:
   ```typescript
   // src/content/config.ts
   export const collections = {
     services: defineCollection({
       schema: z.object({
         title: z.string(),
         description: z.string(),
         icon: z.string(),
         iconColor: z.string().optional(),
         callToAction: z.object({
           text: z.string(),
           href: z.string(),
         }).optional(),
       }),
     }),
   };
   ```

2. **Enhance Component Interactivity**
   - Add client-side functionality to the Service component
   - Implement selective hydration using Astro's client directives
   - Example:
   ```astro
   <div class="service-card" client:visible>
     <!-- Service card content -->
   </div>

   <script>
     // Client-side functionality
     document.querySelectorAll('.service-card').forEach(card => {
       card.addEventListener('click', () => {
         card.classList.toggle('expanded');
       });
     });
   </script>
   ```

3. **Create New Templates**
   - Develop a custom landing page template
   - Implement a blog detail template with rich content features

## Implementation Strategy

Our strategy involves:

1. Start with content collections implementation
2. Update the Service component to use content from collections
3. Add interactive features with minimal JavaScript
4. Create new page templates leveraging our component system
5. Document all changes and patterns

## Project Philosophy

AstroZen follows these core principles:

1. **Performance-First**: Maximize speed and minimize JavaScript
2. **Progressive Enhancement**: Start with HTML, enhance with JavaScript where needed
3. **Content-Driven**: Prioritize content management and authoring experience
4. **Maintainable Architecture**: Use component-based design for reusability

## Key Insights

- Astro's island architecture allows us to build highly performant sites with rich interactivity where needed
- The component system enables efficient development through reusable UI patterns
- Our documentation structure helps maintain knowledge about the project and onboard new team members
- The separation of content and presentation facilitates easier content management

---

*This document serves as context for future sessions working on the AstroZen project.*

ZenZen Implementation Context Summary
I'll summarize our current approach for implementing the ZenZen design system in Astro, capturing both the architectural decisions and implementation details. This will serve as a reference for future tasks.

1. Directory Structure
We're implementing a nested component structure for better organization:

src/components/
├── widgets/
│   ├── hero/
│   │   ├── ZenHero.astro       # Our ZenZen-styled hero component
│   │   └── ... (other hero variants)
│   ├── features/
│   │   └── ... (future ZenZen-styled features components)
│   └── ... (other widget categories)
├── themes/
│   └── zen/
│       └── ZenTheme.astro      # ZenZen theme styles and utilities
└── ... (other component categories)
This structure allows for:

Better organization of widget variants
Clear separation of theme-specific code
Easier addition of new theme variants in the future
2. ZenHero Component
We're creating ZenHero.astro based on the React implementation in ZenZenPage.tsx, with these key features:

---
// Key props
const {
  title = "Fast websites. <br/> <span class=\"zen-gradient-text\">Smart insights.</span>",
  subtitle = "We create websites that load instantly...",
  tagline = "Founded 2025",
  
  actions = [...],  // Call-to-action buttons
  
  statsItems = [    // Statistics displayed below the content
    { value: "300%", label: "Faster Loading", color: "purple" },
    { value: "98%", label: "Performance Score", color: "teal" },
    { value: "45%", label: "Conversion Boost", color: "purple" }
  ],
  
  visualization = true,  // Controls whether to show the right-side visualizations
} = Astro.props;
---

<section class="...">
  <!-- Background gradients -->
  <div class="absolute inset-0 bg-slate-900 z-0">
    <!-- Purple and teal gradient blurs -->
  </div>
  
  <div class="max-w-7xl mx-auto relative z-10">
    <div class="grid md:grid-cols-2 gap-12 items-center">
      <!-- Left column: Content -->
      <div>
        <!-- Tagline badge -->
        <!-- Title with gradient text -->
        <!-- Subtitle -->
        <!-- CTA buttons -->
        <!-- Stats grid -->
      </div>
      
      <!-- Right column: Visualization -->
      {visualization && (
        <div>
          <!-- Website Speed visualization -->
          <!-- Customer Insights visualization -->
        </div>
      )}
    </div>
  </div>
</section>
3. Theme System
The ZenTheme.astro component provides consistent styling variables and utility classes:

<style is:global>
  :root {
    --zen-primary: theme('colors.purple.500');
    --zen-secondary: theme('colors.teal.500');
    --zen-dark-bg: theme('colors.slate.900');
  }
  
  .zen-gradient-text {
    @apply bg-clip-text text-transparent bg-gradient-to-r from-purple-400 to-teal-400;
  }
  
  .zen-gradient-bg {
    @apply bg-gradient-to-r from-purple-500 to-teal-500;
  }
</style>
4. Type Extensions
We're extending the existing Astro types to support ZenZen-specific properties:

// In types.d.ts
interface HeroProps extends Hero {
  statsItems?: Array<{
    value: string;
    label: string;
    color?: 'purple' | 'teal';
  }>;
  visualization?: boolean;
}
5. Usage in Pages
Implementation in src/pages/homes/zenze.astro:

---
import Layout from '~/layouts/LandingLayout.astro';
import ZenHero from '~/components/widgets/hero/ZenHero.astro';
// Other imports...

const metadata = {
  title: 'ZenZen - Fast websites with smart insights',
};
---

<Layout metadata={metadata}>
  <ZenHero
    title="Fast websites. <br/> <span class=\"zen-gradient-text\">Smart insights.</span>"
    subtitle="We create websites that load instantly, are easy to manage, and help you understand your customers better."
    tagline="Founded 2025"
    
    actions={[
      {
        variant: 'primary',
        text: 'Get Started',
        href: '#contact',
        icon: 'tabler:chevron-right',
      },
      {
        variant: 'secondary',
        text: 'Explore Services',
        href: '#services',
      },
    ]}
    
    statsItems={[
      { value: "300%", label: "Faster Loading", color: "purple" },
      { value: "98%", label: "Performance Score", color: "teal" },
      { value: "45%", label: "Conversion Boost", color: "purple" }
    ]}
    
    visualization={true}
  />
  
  <!-- Other components -->
</Layout>
6. Original React Implementation
The key aspects of the ZenZenPage.tsx React implementation:

Visual Style:

Dark theme with slate background (bg-[#0F172A])
Purple and teal gradient accents
Glowing background effects with CSS blur
Clean, modern design with ample spacing
Hero Section Structure:

Two-column layout with content on left, visualization on right
Stats display with gradient-colored numbers
Call-to-action buttons with gradient backgrounds
Data visualization showing website performance metrics
Component Features:

Responsive design (stacks on mobile)
Animations on scroll using Intersection Observer
Gradient text and button styling
Clean typography with clear hierarchy
Data visualizations with comparative metrics
7. Next Steps
For completing the ZenZen theme implementation:

Update the full types.d.ts file with ZenZen-specific props for all components
Implement additional ZenZen-styled components following the same pattern:
ZenFeatures.astro
ZenServices.astro
ZenPricing.astro
ZenTestimonials.astro
ZenContact.astro
Create a complete ZenZen landing page showcasing all components
Add a ZenZen-specific layout if needed with proper navigation styling
Would you like me to add any additional context or details to this summary before we use it in future tasks?