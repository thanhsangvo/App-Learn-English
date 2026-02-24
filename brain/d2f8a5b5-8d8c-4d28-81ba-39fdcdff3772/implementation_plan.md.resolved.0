# Privacy Policy Template Web App

Create a modern, sleek, and highly reusable Privacy Policy application template utilizing Next.js, React, Tailwind CSS, and Lucide React. The application will be configuration-driven, meaning all privacy policy text, headings, and related metadata will be loaded from a single data source file.

## User Review Required
No specific user review is strictly required beyond general approval of this plan. 

## Proposed Changes

### Project Foundation
- Initialize project via Next.js App Router (TypeScript, Tailwind included).
- Install layout and functionality dependencies: `next-themes` (dark/light mode), `lucide-react` (iconography), `@tailwindcss/typography` (beautifully formatted prose text).

### Components Structure
- **Theme Provider**: A wrapper component for `next-themes` to manage light/dark modes.
- **Layout Shell (`src/app/layout.tsx`)**: Global wrapper with standard fonts, SEO metadata placeholders, header, footer, and the theme provider.
- **Header (`src/components/Header.tsx`)**: Top navigation bar with Logo placeholder, 'Back to App' link, and Theme Toggle icon button.
- **Footer (`src/components/Footer.tsx`)**: Bottom section with copyrights and potential sub-links.
- **TableOfContents (`src/components/TableOfContents.tsx`)**: Sticky desktop sidebar mapping out policy sections and acting as a quick-navigation menu.
- **MobileNav (`src/components/MobileNav.tsx`)**: Collapsible drop-down version of the TableOfContents for smaller screens.
- **ContentRenderer (`src/components/ContentRenderer.tsx`)**: Renders HTML/Markdown structures beautifully using Tailwind's Prose.

### Content Configuration
- **`src/content/privacy-data.ts`**: The sole data source for the application. Contains:
  - `appName`
  - `companyName`
  - `contactEmail`
  - `lastUpdatedDate`
  - `policySections`: Array of sections (e.g., `{ id: 'info-collection', title: 'Information Collection', content: '...' }`).

### Design System
- Utilize Slate/Gray scales for primary surfaces.
- Accent colors (e.g., Indigo/Blue) for highlights, active links, and buttons.
- Smooth transitions on dark/light mode toggle and link hover effects.

## Verification Plan
### Automated Tests
- Validate TypeScript compilation (`npm run build`).
- Ensure no ESLint errors (`npm run lint`).

### Manual Verification
- Run local dev server (`npm run dev`) and visually ensure the UI matches the clean/premium goal.
- Verify sticky sidebar functions smoothly on desktop and switches to a collapsible format on mobile.
- Verify dark/light toggle correctly adjusts all surfaces and typography.
- Verify clicking sidebar links jumps gracefully to corresponding sections.
