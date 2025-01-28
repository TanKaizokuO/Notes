**Status:**  #Incomplete  
**Tags:**  [[frontend]] 
**Reference:** [Tailwind Docs](https://tailwindcss.com/docs/installation)
## Installation

- Install Tailwind CSS as a development dependency:
    
    ```bash
    npm install -D tailwindcss
    ```
    
- Initialize Tailwind CSS configuration:
    
    ```bash
    npx tailwindcss init
    ```
    

## Tailwind Configuration File

The configuration file (`tailwind.config.js`) contains:

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

## CSS Directives

Include Tailwind's layers in your CSS:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## Building Tailwind CSS

Run the following command to watch and build CSS:

```bash
npx tailwindcss -i ./src/input.css -o ./src/output.css --watch
```

## Linking Tailwind Output in HTML

```html
<link href="./output.css" rel="stylesheet">
```

---

## Layout Utilities

### Containers

- `container mx-auto`: Center content horizontally.

### Flexbox

- Basic:
    - `flex`, `flex-row`, `flex-col`
- Alignment:
    - `justify-start`, `justify-center`, `justify-end`
    - `items-start`, `items-center`, `items-end`
- Gaps:
    - `gap-x-{n}`, `gap-y-{n}`

### Grid

- `grid`, `grid-cols-{n}`, `gap-{n}`

### Spacing

- Padding:
    - `p-{n}`, `px-{n}`, `py-{n}`
- Margin:
    - `m-{n}`, `mx-{n}`, `my-{n}`

### Width & Height

- Width:
    - `w-{n}`, `w-full`, `w-auto`
- Height:
    - `h-{n}`, `h-full`, `h-auto`
- Minimum dimensions:
    - `min-w-{n}`, `min-h-{n}`

---

## Typography Utilities

### Text Alignment

- `text-left`, `text-center`, `text-right`

### Font Size

- `text-xs`, `text-sm`, `text-base`, `text-lg`, `text-xl`, `text-2xl`, `text-3xl`

### Font Weight

- `font-light`, `font-normal`, `font-bold`, `font-extrabold`

### Line Height

- `leading-{n}`, `leading-tight`, `leading-loose`

### Text Colors

- Examples:
    - `text-gray-500`, `text-blue-500`, `text-red-500`

### Text Decoration

- `underline`, `line-through`, `no-underline`

---

## Background Utilities

### Background Colors

- Examples:
    - `bg-gray-100`, `bg-blue-500`, `bg-green-500`, `bg-transparent`

### Background Gradients

- `bg-gradient-to-r`, `bg-gradient-to-b`

### Background Position

- `bg-center`, `bg-cover`, `bg-contain`

---

## Border Utilities

### Border Width

- `border`, `border-0`, `border-2`, `border-4`

### Border Colors

- Examples:
    - `border-gray-500`, `border-blue-500`

### Border Radius

- `rounded`, `rounded-full`, `rounded-lg`, `rounded-none`

---

## Shadow Utilities

- `shadow-sm`, `shadow-md`, `shadow-lg`, `shadow-xl`, `shadow-none`

---

## Color Utilities

### Text Colors

- Examples:
    - `text-gray-500`, `text-blue-700`

### Background Colors

- Examples:
    - `bg-gray-100`, `bg-indigo-600`

### Hover States

- Examples:
    - `hover:text-white`, `hover:bg-red-500`

---

## Positioning Utilities

### Position

- `relative`, `absolute`, `fixed`, `sticky`

### Alignment

- `top-{n}`, `left-{n}`, `right-{n}`, `bottom-{n}`

### Z-Index

- `z-0`, `z-10`, `z-50`

---

## Flex and Grid Utilities

### Flexbox

- `flex`, `inline-flex`, `flex-wrap`, `flex-nowrap`

### Grid

- `grid-cols-1`, `grid-cols-2`, `grid-cols-3`

---

## Transitions and Animations

### Transition

- `transition`, `duration-{n}`, `ease-in-out`

### Hover Effects

- Examples:
    - `hover:opacity-75`, `hover:scale-110`

---

## Other Utilities

### Opacity

- `opacity-0`, `opacity-50`, `opacity-100`

### Cursor

- `cursor-pointer`, `cursor-not-allowed`

### Overflow

- `overflow-hidden`, `overflow-scroll`

---

## Example: Sticky Navbar

```html
<div id="navbar" class="sticky top-0 overflow-hidden bg-gray-800">
  <!-- Navbar links -->
  <a href="#" class="float-left block text-center text-gray-200 px-4 py-3 no-underline">Home</a>
  <a href="#" class="float-left block text-center text-gray-200 px-4 py-3 no-underline">About</a>
  <a href="#" class="float-left block text-center text-gray-200 px-4 py-3 no-underline">Contact</a>
</div>
```