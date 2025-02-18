---
date_modified: 2023-01-27 13:17
date_published: 2022-02-24 10:25
description: Sage 10 comes with Tailwind CSS out of the box, but can be replaced with Bootstrap or any other CSS framework.
title: Replacing Tailwind CSS with Bootstrap
authors:
  - ben
  - code23_isaac
  - diomededavid
  - MWDelaney
---

# Replacing Tailwind CSS with Bootstrap

Sage 10 ships with [Tailwind CSS](https://tailwindcss.com), but many users may wish to use Bootstrap, or another CSS framework. 

## Removing Tailwind CSS

### 1. Remove Tailwind dependencies

Remove the `@roots/bud-tailwindcss` extension:

```shell
yarn remove @roots/bud-tailwindcss
```

### 2. Remove Tailwind from your CSS

Open `resources/styles/app.css` and **delete** the following lines:

```css
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';
```

### 3. Delete the Tailwind config file

Delete `tailwind.config.cjs` from your theme.

### 4. Remove the Tailwind `theme.json` generator from the Bud config

Open `bud.config.js` from your theme and remove the following lines:

```diff
-      .useTailwindColors()
-      .useTailwindFontFamily()
-      .useTailwindFontSize()
```

## Adding Bootstrap

### 1. Install native support for Sass

Add the `@roots/bud-sass` extension:

```shell
yarn add @roots/bud-sass --dev
```
**Note:** Verify that all Bud packages and the `@roots/sage` package versions are the same in your `package.json` to prevent build errors.

### 2. Install Bootstrap

Add Bootstrap as a dependency:

```shell
yarn add bootstrap --dev
```

#### Optional: Install Popper

To avoid an ugly error message in Bud about missing dependencies, add Popper as a dependency:

```shell
yarn add @popperjs/core --dev
```

### 3. Import Bootstrap's Javascript

Open `resources/scripts/app.js` and add:

```javascript
// Import Bootstrap
import 'bootstrap';
```

### 4. Import Bootstrap styles

In the `resources/styles` directory, rename `app.css` to `app.scss` and rename `editor.css` to `editor.scss`.

Open your theme's newly renamed `resources/styles/app.scss` and add the following lines:

```css
@import "bootstrap";
```

**Note:** You may wish to import only the parts of Bootstrap you plan to use in your theme. You can learn more about importing just the parts you need [here](https://getbootstrap.com/docs/5.1/customize/sass/#importing).
