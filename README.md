# How To Create a Shopify Theme

Creating a Shopify theme for an Online Store 2.0 (JSON Templates) using Shopify CLI, Liquid, & TailwindCSS.

## Initial Theme Setup

- Create a basic theme structure:

  `shopify theme init ThemeName --clone-url RepositoryThemeUrl`

- Login Shopify Store:

  `shopify login --store UrlOfShopifyStoreAdmin`

- Select partner organization

- Update/Sync theme to your development store

  `shopify theme serve`

## Tailwind CSS 2.2.7 setup

- Check if you are logged in

  `shopify whoami`

- Update/Sync theme to your development store

  `shopify theme serve`

- Initialize npm package manager

  `npm init -y`

- Install Tailwind CSS

  `npm install -D tailwindcss postcss autoprefixer`

- Create a new postcss.config.js file adding the following code
  ```jsx
  module.exports = {
    plugins: {
      tailwindcss: {},
      autoprefixer: {},
    },
  };
  ```
- Initialize tailwind.config.js

`npx tailwindcss init`

- Create new folder src

- Create new file src/tailwind.css injecting the following tailwind features

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- Delete /assets/application.css.liquid file

- Setup the Tailwind input and output css files
  `npx tailwindcss -i ./src/tailwind.css -o ./assets/application.css`

- Edit layout/theme.liquid file adding this code to the header

```liquid
{{ content_for_header }}
    <!-- Header hook for plugins -->
    {{ 'application.css' | asset_url | stylesheet_tag }}
    <script src="{{ 'application.js' | asset_url }}" async></script>
```

## Tailwind CSS 3.0 setup

- Check if you are logged in

  `shopify whoami`

- Update/Sync theme to your development store

  `shopify theme serve`

- Initialize npm package manager

  `npm init -y`

- Install Tailwind CSS

  `npm install -D tailwindcss postcss autoprefixer`

- Create a new postcss.config.js file adding the following code
  ```jsx
  module.exports = {
    plugins: {
      tailwindcss: {},
      autoprefixer: {},
    },
  };
  ```
- Initialize tailwind.config.js

`npx tailwindcss init`

- Add the following code to tailwind.config.js

```js
module.exports = {
  content: [
    "./assets/*.liquid",
    "./layout/*.liquid",
    "./sections/*.liquid",
    "./snippets/*.liquid",
    "./templates/*.liquid",
    "./templates/**/*.liquid",
    // you can also directly select all the liquid and json files
    // "./**/*.{liquid,json}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

- Create new folder src

- Create new file src/tailwind.css injecting the following tailwind utility classes

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- Delete /assets/application.css.liquid file

- Setup the Tailwind input and output css files with the utility classes with the watch flag
  `npx tailwindcss -i ./src/tailwind.css -o ./assets/application.css --watch`

- Edit layout/theme.liquid file adding this code to the header

```liquid
{{ content_for_header }}
    <!-- Header hook for plugins -->
    {{ 'application.css' | asset_url | stylesheet_tag }}
    <script src="{{ 'application.js' | asset_url }}" async></script>
```
