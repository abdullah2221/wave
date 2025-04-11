# Angular 18 with Tailwind CSS Setup Guide

This guide will walk you through setting up a new Angular 18 project with Tailwind CSS integration.

## Prerequisites

- Node.js (v18 or later)
- npm (v9 or later)
- Angular CLI (v18 or later)

## Step 1: Install Angular CLI

```bash
npm install -g @angular/cli
```

## Step 2: Create a New Angular Project

```bash
ng new angular-tailwind-demo
cd angular-tailwind-demo
```

When prompted:
- Choose "Yes" for routing
- Select "SCSS" for stylesheet format

## Step 3: Install Tailwind CSS and Dependencies

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init
```

## Step 4: Configure Tailwind CSS

Create or update `tailwind.config.js`:

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./src/**/*.{html,ts}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

## Step 5: Update Angular Styles

Add Tailwind directives to `src/styles.scss`:

```scss
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## Step 6: Create a Sample Component

```bash
ng generate component components/sample
```

Update `src/app/components/sample/sample.component.html`:

```html
<div class="min-h-screen bg-gray-100 py-6 flex flex-col justify-center sm:py-12">
  <div class="relative py-3 sm:max-w-xl sm:mx-auto">
    <div class="relative px-4 py-10 bg-white shadow-lg sm:rounded-3xl sm:p-20">
      <div class="max-w-md mx-auto">
        <div class="divide-y divide-gray-200">
          <div class="py-8 text-base leading-6 space-y-4 text-gray-700 sm:text-lg sm:leading-7">
            <h1 class="text-3xl font-bold text-indigo-600 mb-4">Welcome to Angular + Tailwind!</h1>
            <p class="text-gray-600">This is a sample component styled with Tailwind CSS.</p>
            <button class="mt-4 px-4 py-2 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 transition-colors">
              Click Me
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

## Step 7: Update App Component

Update `src/app/app.component.html` to use the sample component:

```html
<app-sample></app-sample>
```

## Step 8: Start the Development Server

```bash
ng serve
```

Visit `http://localhost:4200` to see your application running with Tailwind CSS styling.

## Additional Configuration (Optional)

### Customizing Tailwind Theme

You can customize the Tailwind theme by updating `tailwind.config.js`:

```javascript
module.exports = {
  content: [
    "./src/**/*.{html,ts}",
  ],
  theme: {
    extend: {
      colors: {
        primary: {
          50: '#f0f9ff',
          100: '#e0f2fe',
          200: '#bae6fd',
          300: '#7dd3fc',
          400: '#38bdf8',
          500: '#0ea5e9',
          600: '#0284c7',
          700: '#0369a1',
          800: '#075985',
          900: '#0c4a6e',
        },
      },
    },
  },
  plugins: [],
}
```

### Adding Custom Components

You can create custom Tailwind components in `styles.scss`:

```scss
@layer components {
  .btn-primary {
    @apply px-4 py-2 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 transition-colors;
  }
  
  .card {
    @apply bg-white rounded-lg shadow-md p-6;
  }
}
```

## Troubleshooting

If you encounter any issues:

1. Make sure all dependencies are installed correctly
2. Check that the Tailwind directives are properly added to `styles.scss`
3. Verify that the `tailwind.config.js` content paths are correct
4. Clear the Angular cache if needed: `ng cache clean` 