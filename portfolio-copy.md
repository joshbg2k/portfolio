# Portfolio Copy — Joshua Berry

## Updated from resume cross-reference

---

## WORKS LIST ENTRIES

**Title:** Figma Design Handoff Plugin
**Tags:** Engineering · Design Systems · Accessibility
**Year:** 2020
**One-liner:** In 2020, built a completely original tool that mapped Amazon's Figma design system to its React component library — click any component, get exact production code and accessibility props. Figma shipped their own version of the concept in 2024. They called it Code Connect.

---

**Title:** Amazon HR Chatbot — UX Vision & Prototyping
**Tags:** Research · Design · Engineering
**Year:** 2021
**One-liner:** Led a cross-functional redesign of Amazon's employee HR chatbot — introduced the first structured CSAT measurement the product ever had, landing at 4.65/5.

---

**Title:** Amazon Affinity Groups — Employee Mobile App
**Tags:** Engineering
**Year:** 2022–2024
**One-liner:** Led front-end development for a hybrid React Native / React app serving Amazon's global employee base — production TypeScript, GraphQL, i18n, CI/CD, and full accessibility compliance.

---

**Title:** Apple.com — Product Launch Pages
**Tags:** Engineering · Motion · Front-End
**Year:** 2018–2020
**One-liner:** Senior Front-End Developer on Apple's product launch team — built the iMac, iMac Pro, Mac Pro, MacBook Pro, MacBook Air, Mac Mini, Safari, and Newsroom pages on one of the highest-trafficked sites in the world. The App Store page still runs the same design today.

---

**Title:** IBM Watson Cognitive Dress
**Tags:** Engineering · AI · Hardware
**Year:** 2016
**One-liner:** Built the software and hardware system behind an ML-powered dress worn at the Met Gala — Watson sentiment data translated into real-time LED color, live on the red carpet. Now in the Henry Ford Museum.

---

**Title:** 2020 Lincoln Continental UX
**Tags:** Engineering · Prototyping · Hardware
**Year:** 2017
**One-liner:** Built a real-time WebSocket network across 5 apps and custom Arduino hardware, embedded in a Lincoln Continental and shipped to Shanghai for user testing. Six weeks from kickoff to demo.

---

---

---

---

## CASE STUDY 1: Amazon HR Chatbot

### Headline

_Fixing a chatbot nobody trusted._

### Subhead

Amazon · Design Technologist II · 2021 · Cross-functional UX lead

---

### The Problem

The Amazon employee HR chatbot had been built without design input. Employees knew it, and they said so plainly: _"Chatbot doesn't work ever."_ _"Chatbot is no bueno."_

The goal wasn't to rebuild the underlying system — that was off the table. The challenge was to craft a scalable UX vision that could dramatically improve the experience within the existing constraints, then validate every decision before a single line of production code was written.

---

### What Was Actually Broken

An audit surfaced four distinct failure modes — not one big problem, but a cascade of small ones that compounded into distrust.

**Broken interaction model.** Button-based responses weren't captured into the chat record. Users could keep tapping buttons that should have been one-time choices, and their selections disappeared from the history entirely — making every conversation feel like it was actively gaslighting them.

**Wall-of-text responses.** Content had been copy-pasted from web pages into chat bubbles. No links, no hierarchy, no awareness that a chat message and a web paragraph are different objects. Reading them felt like work.

**Invisible feedback UI.** A satisfaction prompt accompanied every single bot message. Because it was always there, users had trained themselves to see past it — engagement was near zero.

**Conversations that never ended.** There was no concept of closing a session. Users relied on a "main menu" button that crept further and further up the scroll as the chat grew longer. There was no sense of resolution.

---

### The Approach

I led a cross-functional team of designers, researchers, and writers through a research-led, prototype-validated process.

The audit of Amazon's own customer-facing chatbot on amazon.com came first — studying a hyper-optimized, battle-tested conversation UI to understand what patterns transferred to an internal HR context and what didn't. (The finding: amazon.com's chatbot was built entirely around returns. Almost nothing carried over.)

From there, a UX vision was scoped across six areas: overall layout, message readability and animation, the feedback module, session endings, critical micro-interactions, and a "main menu" replacement. Each area had an explicit before and after — not just a mockup, but a working JavaScript prototype built to let engineering teams experience the interaction, not read a spec.

The prototype architecture was deliberate: JSON chat data in, configurable settings via URL, rendered to a mobile browser. Engineers could validate timing, animation feel, and edge cases without any back-end changes. Three distinct message delivery modes were prototyped and tested — simultaneous, cascading at a constant interval, and dynamic delivery paced to reading time. Research participants had strong, clear preferences.

For the feedback redesign, a single well-timed ask was tested against the persistent ambient prompt. User research confirmed the direction: _"If the format for providing feedback is immediately after the experience and simple to do, it is more likely that people will give feedback."_

---

### The Outcome

**4.65 / 5** average CSAT — the first structured measurement the product had ever produced. Before the redesign, the only feedback mechanism was a free-text input, which meant the only signal was people bothering to type "chatbot doesn't work ever." The new 5-point Likert scale, combined with a feedback UI people actually engaged with, produced a real number for the first time — and it was a good one.

The CSAT component was later contributed back into the org's design system, making it available to every team building on the same platform.

---

### What Made This Hard

No changes to the underlying system meant no changes to what the chatbot understood, what data it had access to, or how it responded. Every improvement had to live entirely in the presentation layer — layout, interaction, copy, animation, timing. That's a narrow aperture. Squeezing meaningful CSAT gains through it required being precise about which problems were actually solvable and which ones weren't.

---

---

## CASE STUDY 2: Figma Design Handoff Plugin

### Headline

_Click a component in Figma. Get the exact production code._

### Subhead

Amazon · Design Technologist II · 2021–2022 · Solo

---

### The Problem

Amazon's design system had two parallel universes that were supposed to be the same thing: a Figma component library that designers worked in, and a React component library (`@amzn/stencil-react-components`) that engineers built with. In theory they matched. In practice, the gap between them was where quality died.

Engineers were recreating components from Confluence screenshots — guessing at prop names, missing accessibility attributes, importing the wrong variants. Not because they were careless, but because there was no fast path from "I see this component in the mockup" to "here is exactly how to build it." Research confirmed it: around half of front-end engineers had limited familiarity with the design system. The handoff was a guessing game.

No linter catches a missing `aria-hidden`. No QA process reliably surfaces a wrong import path. These errors were introduced at the moment a designer handed off a file, and they lived in production until someone noticed.

---

### What Was Built

A Figma plugin that mapped the design system component library directly to the React code library — so that clicking any component in a mockup immediately surfaced the exact production import statement, the correct JSX with real prop values, full component documentation, and accessibility features called out explicitly.

Not a link to the docs. Not a screenshot. The actual code, populated from the selected component's properties — ready to copy into an IDE.

A designer selecting a secondary Button with a trailing icon and "Reload" label would see:

```
import { Button, ButtonColorScheme, ButtonIconPosition,
  ButtonSize, ButtonVariant } from '@amzn/stencil-react-components/button';
import { IconRefresh } from '@amzn/stencil-react-components/icons';

<Button
  icon={<IconRefresh aria-hidden="true" />}
  iconPosition="trailing"
  size="default"
  variant="secondary"
>
  Reload
</Button>
```

The plugin also surfaced all available props for each component, with accessibility-relevant ones specifically flagged — so engineers couldn't accidentally omit `aria-hidden` on a decorative icon or use the wrong focus behavior on an interactive element.

---

### What Happened Next

The concept of design-to-code fidelity as an organizational priority — not an afterthought — began spreading through the org.

The product team picked up the plugin and started developing it as an official product. The AWS design system team and the Amazon.com design system team both asked to learn how to build their own versions; both were taught. The design system team ran with the concept further, and a small informal group started pushing toward what an AI-assisted next-generation version of this tooling might look like.

The internal reaction said something about the gap that had existed: _"That right there is holy grail kind of stuff."_

---

### Why This One Matters

In 2020 there was no tool — inside Amazon or anywhere on the market — that bridged a Figma design system to a production code library this way. Everything was built from scratch: the component mapping, the code generation, the accessibility surfacing, the plugin architecture. It was a completely original solution to a problem the industry hadn't formally named yet.

Figma shipped their own version of this idea in 2024. They called it Code Connect.

Building something four years before the category existed — something that others at Amazon adopted, adapted, and taught from — is a different kind of outcome from most design technologist work. And the through-line to what's happening now is direct: in 2020 I built a static bridge between design and code inside Figma. In 2025, Figma MCP lets AI traverse that same bridge dynamically. The problem hasn't changed. The tools got dramatically more powerful.

---

---

## CASE STUDY 3: Amazon Affinity Groups — Employee Mobile App

### Headline

_Crossing over: from design technologist to production engineering lead._

### Subhead

Amazon · Design Technologist II · 2022–2024 · Front-End Engineering Lead
Internal product — visuals under NDA.

---

### The Context

After two years leading UX and emerging technology work in Amazon's PXT org, I made a deliberate move: I transitioned fully into an engineering role. Not because the design work had run out, but because I wanted to close the gap I'd always worked across — and the only way to do that completely was to own production delivery myself.

The product was Amazon's employee Affinity Groups platform — a hybrid web and native mobile experience that helped employees across the company discover and engage with internal communities organized around shared identities, interests, and backgrounds. It served a global employee base across multiple platforms and regions.

---

### The Stack

**React Native** for iOS and Android. **React** for web. **TypeScript** throughout. **GraphQL** APIs for data. Full **i18n** for internationalization across a global workforce. **Jest** for unit testing. **CI/CD pipelines** with **Cypress** integration tests. Accessibility compliance built in from the start — not audited after the fact.

This wasn't a greenfield prototype. It was a production codebase with real users, real QA processes, real deployment pipelines, and real consequences when something broke.

---

### What the Transition Taught Me

The skills that made me effective as a design technologist — systems thinking, knowing where the edge cases live, understanding what's hard to change after the fact — turned out to be exactly what made me effective as an engineering lead. The difference was that the output was now TypeScript and test coverage rather than Figma files and prototypes.

It also confirmed something I'd suspected for years: the designers who can own engineering work, and the engineers who deeply understand design intent, are the most valuable people in any product org. The goal isn't to do both jobs simultaneously — it's to speak both languages fluently enough that nothing gets lost in translation.

---

### Why It's Here

Most design technologist portfolios are all vision, no production. This entry is the counterweight. The same person who built JavaScript prototypes and Figma plugins in 2021 was leading front-end delivery in TypeScript and React Native by 2023 — with unit tests, integration tests, and a CI/CD pipeline to prove it.

---

---

## CASE STUDY 4: Apple.com — Product Launch Pages

### Headline

_Pixel-perfect, on deadline, at Apple scale._

### Subhead

Apple · Senior Front-End Developer (Contract) · 2018–2020 · Sunnyvale, CA

---

### The Work

On Apple's Product Launch team, I built the top-level marketing pages for flagship hardware and software releases — iMac, iMac Pro, Mac Pro, MacBook Pro, MacBook Air, Mac Mini, Safari, and Newsroom — on one of the highest-trafficked sites in the world.

Each page was built to Apple's exacting standard: pixel-perfect fidelity to design, proprietary animation systems, bespoke scroll interactions, and launch-day reliability at massive scale. The stack was Handlebars templating, a robust in-house SASS library, and vanilla JavaScript web components with animations powered by Apple's proprietary keyframe animation library.

The App Store page I built in 2020 still runs today.

---

### Why It's Here

Apple's production bar is one of the highest in the industry. Every pixel is deliberate, every animation frame is intentional, and the deadline is the product announcement — immovable. Building eight major product pages to that standard, across two years, is a different kind of discipline than any other engineering environment I've worked in.

---

---

## CASE STUDY 5: IBM Watson Cognitive Dress

### Headline

_We pushed code to a dress in a van on the way to the Met Gala._

### Subhead

Ogilvy & IBM · Creative Technologist · 2016 · Hardware + Software

---

### The Brief

In spring 2016 I was brought in to collaborate on the IBM Cognitive Dress — an ML-powered wearable commissioned by IBM and fashion house Marchesa, to be worn by supermodel Karolina Kurkova at the Met Gala. IBM Watson would analyze social media sentiment around the event in real time, and the dress would respond: 7 strands of full-spectrum LEDs woven into the fabric and fastened behind 80 handmade flowers, shifting color as the mood of the internet shifted.

My role covered the full technical stack — software architecture, physical fabrication, and the live integration between Watson's sentiment data and the dress's LED system.

---

### What Was Built

A Photon microcontroller embedded in the dress connected wirelessly to a Node.js service that polled IBM Watson and Twitter APIs for live social sentiment. The service translated sentiment scores into color values and pushed them to the Photon over the air, which drove the NeoPixel LED strands in real time.

The physical build was as demanding as the software. We fastened LEDs behind 80 individual handmade fabric flowers. We wove 7 strands of full-spectrum LEDs through the dress itself. Everything had to survive a red carpet — movement, heat, handling, cameras at close range.

The night before the gala we held a private VIP unveiling. My team of six produced 100 commemorative electronic flowers — identical to those on the dress, powered by Adafruit GEMMA microcontrollers and LiPo batteries — given away as keepsakes.

---

### The Ending

We were still pushing code updates to the Photon in the van on the way to the Met. Karolina Kurkova walked the red carpet at the 2016 Met Gala in a dress that was live-connected to the internet, changing color in response to what the world was saying.

The IBM Cognitive Dress is now in the permanent collection of the Henry Ford Museum of American Innovation.

Press: Wired, Fast Company, AdAge, Refinery29, QZ.

---

### Why It's Here

It's the clearest single demonstration that design technology isn't always a screen. The problem — translating live data into a physical, emotional experience — required writing software, building hardware, and making something that had to work perfectly once, under the worst possible conditions for debugging.

---

---

## CASE STUDY 6: 2020 Lincoln Continental UX

### Headline

_A real-time network inside a car, shipped to Shanghai in a Pelican case._

### Subhead

Smart Design · Design Technologist · 2017 · Hardware + React Native + WebSockets

---

### The Brief

Ford Motor Co. was introducing the Lincoln Continental to the Chinese luxury market — positioning it for business owners who ride in the back seat. Smart Design brought me in to build a high-fidelity functional prototype of the entire interior experience for user testing: touchscreen interfaces, hardware controls, and a real-time network connecting all of it, embedded physically into a late-model Lincoln Continental.

The goal was full HMI fidelity without actual car integration — a physical reskinning of the back seat that would feel like the real product.

---

### What Was Built

The system was a real-time WebSocket network: a Node.js server running on a MacBook Pro, connected to 5 client applications over a local Linksys router — four iOS apps (React Native) and one Arduino. Any value change on any device propagated instantly to all others.

The hardware was custom throughout. The primary interface was an iPad and Arduino embedded in a 3D-printed center armrest overlay, with three rotary encoders wired to the Arduino for fan speed, temperature, and volume — one with an embedded OLED display showing the current interior temperature. A second iPad mini sat in a custom 3D-printed center console overlay. Two iPhone apps handled owner and guest controls with different permission levels.

The full team was seven people: myself, an industrial designer, interaction designer, UX researcher, visual designer, mechanical engineer, and electrical engineer. Six weeks from kickoff to initial client demo.

---

### Shipped to Shanghai

After the first round of testing, the entire rig — car, hardware overlays, network equipment — was packed into Pelican cases and transported to Shanghai for several weeks of user testing in the Chinese market. I traveled with the team, iterated through two rounds of user feedback, and returned to Detroit for the final stakeholder handoff.

---

### The Engineering Decisions That Mattered

Building four separate native apps instead of one responsive app was the right call — the designs diverged enough during development that a single responsive approach would have become a debugging nightmare. Building socket listeners per-screen rather than globally solved the connectivity risk of devices dropping off the network mid-session. Not building app state at all — since the testing protocol didn't require it — kept the codebase lean and the deadline achievable.

Six weeks. Five apps. A custom hardware rig. User tested on two continents.

---

---

## ML & AI THREAD

_A through-line across the whole career — for use as a timeline section or sidebar._

---

### Building with AI since before it had a clean name

**2012 — NBC Universal**
Conceived, designed, and built a celebrity lookalike widget using ML image classification and facial recognition — matching users' Facebook friends to NBC talent and deploying it inside NBC's second-screen mobile experience. An early end-to-end application of ML to consumer UX, years before it became mainstream.

**2015 — Ogilvy & IBM**
Collaborated with IBM's creative team to concept and develop the IBM Cognitive Dress — an ML-powered wearable that used Watson text classification APIs to translate social media sentiment into real-time visual expression. Now in the permanent collection of the Henry Ford Museum of American Innovation.

**2016 — Ogilvy / Nespresso**
Built an early Alexa voice application for a Nespresso pitch — adding voice control to a hacked espresso machine. An early exploration of conversational AI and connected hardware.

**2022 — Amazon**
Developed and deployed ML-powered text classification models via Amazon Comprehend achieving 90%+ accuracy, used to evaluate UX writing quality at scale. Embedded the models in Figma plugins and internal web apps. Trained UX writers to independently build and deploy their own — an early example of human-in-the-loop AI tooling inside a large org.

**2024–Present**
Deepened hands-on expertise in AI-assisted development — spec-based and vibe coding with Claude Code, Cursor, and Roo Code. Now building Figma MCP integrations and custom Claude skills for design workflows: tooling that lets AI reason directly about design files, generate annotations, surface component code, and close the gap between design intent and production output. The problem I first approached with a Figma plugin in 2020 has a new and much more powerful set of tools in 2025.

---

---

## ABOUT BLURB

I'm a design technologist with over a decade at the intersection of UX and engineering — most recently at Amazon, before that at Apple, Smart Design, and Ogilvy. I studied at ITP at NYU, which is where I first understood that the most interesting problems don't belong entirely to any one discipline.

I've been building with AI since 2012 — facial recognition at NBC, Watson-powered wearables at Ogilvy, NLP classifiers at Amazon. I took time away from the industry to pursue something completely different, and I came back because AI has made software development feel genuinely exciting again. The tools available now — Claude Code, Figma MCP, spec-based development — are changing what it means to work at the design/engineering boundary, and I want to be building at that frontier.

I prototype things that don't exist yet. I build tools when the tools I need aren't there. And right now, for the first time in a while, it feels like the tools available are worthy of the problems worth solving.

Based in Providence, Rhode Island. Open to the right full-time or contract opportunity.

---

_— End of portfolio copy —_
