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
