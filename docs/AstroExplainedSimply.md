# Astro Explained Like You're Five

## Our Building Board: Astro Framework

Imagine Astro is like our special building board where we arrange all our toys and blocks:

- It lets us create websites that load **super fast** because it only sends what's needed to your computer
- Our pages are mostly built ahead of time, like pre-assembled toys, so they're ready instantly when you want to play with them
- We only add moving parts (JavaScript) to the specific blocks that need to move - not the whole toy

## How Astro Pages Work (Like Building a Picture Book)

1. Imagine we're making a picture book together. Each page in our book is a separate file in our 'src/pages' folder.
2. When we create a file like 'about.astro', it magically becomes a page on our website at '/about'.
3. These pages are special because they have three parts:
   - The top part (between '---') is where we do our thinking and planning, but visitors can't see it
   - The middle part is what people actually see on the page
   - The bottom part with 'style' is how we make things look pretty
4. When someone visits our website, they get these pages already completely drawn and colored in - super fast!

## Components - Our Building Blocks (Like LEGO Pieces)

1. In our project, we have special LEGO pieces called 'components' in the 'src/components' folder.
2. Think of each component as a special brick that does one job really well:
   - 'Header.astro' is our page top with navigation
   - 'Footer.astro' is our page bottom with links
   - 'Hero.astro' makes big exciting banner pictures
   - 'Service.astro' shows our special services in pretty cards
3. The coolest thing is we can use these pieces over and over! Just like using the same LEGO brick in different buildings.
4. When we want to use a component, we just write its name like `<Hero />` or `<Service />` and it appears like magic!

## How Content Works (Like Magic Library Books)

1. Our website has special places where words and pictures go - like in 'src/content' and 'src/data'.
2. We can write our stories in special files ending with '.md' (markdown) or '.mdx'.
3. These are like magic library books that:
   - Have information at the top about the story (like author, date, title)
   - Have the main story written in a super simple way
   - Can be shown on our website automatically without rewriting everything
4. DecapCMS (our content helper) is like a friendly librarian who helps organize these stories:
   - It gives us a nice screen to type our stories
   - It saves them in the right place for us
   - It makes sure the information at the top is correct
   - It lets us add pictures and links easily

## How to Build Your Own Web Page (Step-by-Step)

### Step 1: Create a New Page File
- Go to 'src/pages' folder
- Make a new file like 'mypage.astro'

### Step 2: Add the Magic Recipe Parts
```astro
---
// This is where we think about what we need
import Layout from '../layouts/PageLayout.astro';
import Hero from '../components/widgets/Hero.astro';
import Features from '../components/widgets/Features.astro';

// Let's name our page
const metadata = {
  title: 'My Amazing Page',
};
---

<Layout metadata={metadata}>
  <!-- Now we add our building blocks -->
  <Hero
    title="My First Astro Page"
    subtitle="This is so cool and easy!"
    image={{ src: '~/assets/images/hero-image.png', alt: 'Hero Image' }}
  />
  
  <Features
    title="Things I Love"
    items={[
      { title: 'Fast Websites', icon: 'tabler:rocket' },
      { title: 'Easy Building', icon: 'tabler:tools' },
      { title: 'Fun Coding', icon: 'tabler:code' },
    ]}
  />
</Layout>
```

### Step 3: Visit Your Page
- Go to your website and add '/mypage' to see it
- It's already there and ready to view!

That's it! You've made a super-fast web page with just a few pieces. No complicated code, just building blocks that snap together!

## How Our Project is Organized (Our Toy Box)

```
src/
│
├── components/       <- Our LEGO pieces (reusable parts)
│   ├── ui/              <- Small basic bricks
│   ├── widgets/         <- Bigger pre-built sections  
│   └── blog/            <- Special pieces for blogs
│
├── pages/           <- Each page of our website
│   ├── index.astro      <- The homepage
│   ├── about.astro      <- About us page
│   └── services.astro   <- Services page
│
├── layouts/         <- Page templates (like paper with lines)
│   └── PageLayout.astro <- Our main page wrapper
│
├── content/         <- Our library of information
│
└── assets/          <- Pictures and decorations
    └── images/          <- All our images
```

## Why Our Website Is Super Fast

1. We build most parts ahead of time, like pre-making cookies before a party
2. We only add moving parts (JavaScript) to things that need to move
3. We use smaller, more efficient moving parts when we need them
4. Our pictures and decorations get optimized automatically to load faster

That's our Astro website - it's like a magic toy box where we can build anything by snapping together the right pieces, and it loads super fast when people come to play with it!
