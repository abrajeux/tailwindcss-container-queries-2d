# Tailwind Container Queries 2D

[![npm](https://img.shields.io/npm/v/tailwind-container-queries-2d.svg)](https://www.npmjs.com/package/tailwind-container-queries-2d)
[![npm](https://img.shields.io/npm/dt/tailwind-container-queries-2d.svg)](https://www.npmjs.com/package/tailwind-container-queries-2d)

A plugin for Tailwind CSS v3.2+ that provides utilities for container queries both for width and height values.

## Installation

Install the plugin from npm:

```sh
npm install tailwind-container-queries-2d
```

Then add the plugin to your `tailwind.config.js` file:

```js
// tailwind.config.js
module.exports = {
  theme: {
    // ...
  },
  plugins: [
    require('tailwind-container-queries-2d'),
    // ...
  ],
}
```

## Usage

Start by marking an element as a container using the `@container` class. You can now apply styles based on the container’s width or height using the new `@w-*` and `@h-*` modifiers, in addition to the width-based container breakpoints like `@md:`, `@lg:`, and `@xl:`.

### Applying Width and Height Breakpoints

With this version, you can target styles based on either the width or height of the container. Use `@w-*` for width-based breakpoints and `@h-*` for height-based breakpoints. This allows for more granular control over responsive design.

#### Width-Based Breakpoints
For width-based styles, use the `@w-` prefix:

```html
<div class="@container">
  <div class="@w-lg:text-black">
    <!-- This text turns black when the container width is larger than `32rem` -->
  </div>
</div>
```

#### Height-Based Breakpoints
For height-based styles, use the `@h-` prefix:

```html
<div class="@container">
  <div class="@h-lg:text-black">
    <!-- This text turns black when the container height is larger than `32rem` -->
  </div>
</div>
```

By default we provide [container sizes](#configuration) from `@5xs` (`4rem`) to `@7xl` (`80rem`).

### Named containers

You can optionally name containers using the `@container/{name}` class and use that name in container variants. With the new width- and height-based prefixes, you can specify named containers as well, such as `@w-lg/{name}` and `@h-lg/{name}`:

```html
<div class="@container/main">
  <!-- ... -->
  <div class="@w-lg/main:text-red-500 @h-lg/main:bg-green-500">
    <!-- This text turns red when the "main" container is wider than `32rem` -->
    <!-- The background turns green when the "main" container is taller than `32rem` -->
  </div>
</div>
```

### Arbitrary container sizes

In addition to using one of the [container sizes](#configuration) provided by default, you can also create one-off sizes using any arbitrary value for the container width or height:

```html
<div class="@container">
  <div class="@w-[20rem]:underline @h-[30rem]:bg-yellow-200">
    <!-- This text is underlined when the container width exceeds `20rem` -->
    <!-- The background is yellow when the container height exceeds `30rem` -->
  </div>
</div>
```

### Removing a container

To stop an element from acting as a container, use the `@container-normal` class.

<div class="@container xl:@container-normal">
  <!-- ... -->
</div>

### With a prefix

If you have configured Tailwind to use a prefix, make sure to prefix both the `@container` class and any classes where you are using a container query modifier:

```html
<div class="tw-@container">
  <!-- ... -->
  <div class="@w-lg:tw-underline">
    <!-- ... -->
  </div>
</div>
```

## Configuration

By default we ship with the following configured values:

| Name   | CSS                                          |
| ------ |----------------------------------------------|
| `@5xs` | `@container (min-width: 4rem /* 64px */)`    |
| `@4xs` | `@container (min-width: 8rem /* 128px */)`   |
| `@3xs` | `@container (min-width: 12rem /* 192px */)`  |
| `@2xs` | `@container (min-width: 16rem /* 256px */)`  |
| `@xs`  | `@container (min-width: 20rem /* 320px */)`  |
| `@sm`  | `@container (min-width: 24rem /* 384px */)`  |
| `@md`  | `@container (min-width: 28rem /* 448px */)`  |
| `@lg`  | `@container (min-width: 32rem /* 512px */)`  |
| `@xl`  | `@container (min-width: 36rem /* 576px */)`  |
| `@2xl` | `@container (min-width: 42rem /* 672px */)`  |
| `@3xl` | `@container (min-width: 48rem /* 768px */)`  |
| `@4xl` | `@container (min-width: 56rem /* 896px */)`  |
| `@5xl` | `@container (min-width: 64rem /* 1024px */)` |
| `@6xl` | `@container (min-width: 72rem /* 1152px */)` |
| `@7xl` | `@container (min-width: 80rem /* 1280px */)` |

You can configure which values are available for this plugin under the `containers` key in your `tailwind.config.js` file:

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      containers: {
        '8xl': '88rem',
      },
    },
  },
}
```

## Credits

This plugin is based on the original work in [tailwindcss/container-queries](https://github.com/tailwindlabs/tailwindcss-container-queries) by [Tailwind Labs](https://github.com/tailwindlabs).

Special thanks to [@kieranm](https://github.com/kieranm) for the [initial PR](https://github.com/tailwindlabs/tailwindcss-container-queries/pull/7) that inspired height-based queries.

