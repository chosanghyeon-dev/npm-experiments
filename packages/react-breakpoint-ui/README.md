# react-breakpoint-ui

A breakpoint-based component library for React responsive UI

> ⚠️ **ESM Only Package** - This package is ESM only. CommonJS is not supported.

## Table of Contents

- [Overview](#overview)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Server-side Rendering (SSR) Usage](#server-side-rendering-ssr-usage)
  - [Next.js Page Router](#nextjs-page-router)

## Overview

When writing responsive components, it's common to use media queries to adjust the display when certain conditions are met. Historically this has taken place directly in CSS/HTML:

```css
@media screen and (max-width: 767px) {
  .my-container {
    width: 100%;
  }
}

@media screen and (min-width: 768px) {
  .my-container {
    width: 50%;
  }
}
```

```html
<div class="my-container" />
```

However, managing responsive behavior in React often requires complex conditional logic or multiple hooks. `react-breakpoint-ui` simplifies this by providing a declarative, component-based approach to responsive design.

By defining your breakpoints once and using them as props, you can easily create responsive components without writing CSS media queries or complex JavaScript logic:

```tsx
<Responsive
  xs={<div>Mobile (0px~)</div>}
  m={<div>Tablet (1024px~)</div>}
  xl={<div>Desktop (1536px~)</div>}
/>
```

## Installation

```bash
npm install react-breakpoint-ui
```

## Quick Start

### Step 1: Define breakpoints

```tsx
// ./lib/react-breakpoint-ui.ts
import { createFresnelMedia } from "react-breakpoint-ui";

// Define breakpoints (numbers in px units)
export const { Responsive, MediaContextProvider, rootMediaStyle } =
  createFresnelMedia({
    xs: 0,
    s: 600,
    m: 1024,
    l: 1366,
    xl: 1536,
    xxl: 1920,
    xxxl: 2560,
  });
```

### Step 2: Use in your component

```tsx
// App.tsx
function App() {
  return (
    <MediaContextProvider>
      <Responsive
        xs={<div>Mobile (0px~)</div>}
        m={<div>Tablet (1024px~)</div>}
        xl={<div>Desktop (1536px~)</div>}
      />
    </MediaContextProvider>
  );
}

ReactDOM.render(<App />, document.getElementById("react"));
```

## Server-side Rendering (SSR) Usage

#### Next.js Page Router

```tsx
// _document.tsx
import { Html, Head, Main, NextScript } from "next/document";

export default function Document() {
  return (
    <Html lang="en">
      <Head>
        {/* Inject styles (required) If you support Server Side, put it in a common file that supports Server Side (e.g. next.js _document.tsx) */}
        <style
          type="text/css"
          dangerouslySetInnerHTML={{ __html: rootMediaStyle }}
        />
      </Head>
      <body>
        <Main />
        <NextScript />
      </body>
    </Html>
  );
}
```
