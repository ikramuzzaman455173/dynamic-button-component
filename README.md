### DynamicButton Component Documentation

The `DynamicButton` component is a flexible, reusable, and professional button component for Next.js and TypeScript applications. It can be used as both a button and a link, with support for icons, loading states, disabled states, and customization options for design and behavior.

---

### Table of Contents

- [Installation](#installation)
- [Usage](#usage)
  - [Basic Button](#basic-button)
  - [Button with Icon](#button-with-icon)
  - [Link Button](#link-button)
  - [Loading Button](#loading-button)
  - [Disabled Button](#disabled-button)
  - [Custom Styles](#custom-styles)
- [Props](#props)
- [Examples](#examples)
  - [Icon on Right](#icon-on-right)
  - [Custom Button Styles](#custom-button-styles)
- [Accessibility](#accessibility)
- [Conclusion](#conclusion)

---

### Installation

Ensure you have `react-icons` installed for handling the optional icons:

```bash
npm install react-icons
```

You can install the `DynamicButton` component directly into your project as part of your component library.

### Usage

#### Basic Button

This is a simple button with default styles and behavior:

```tsx
import DynamicButton from './DynamicButton';

<DynamicButton text="Click Me" onClick={() => console.log('Button clicked!')} />;
```

#### Button with Icon

You can add an icon using the `icon` prop. Icons are passed as React components from libraries like `react-icons`:

```tsx
import { FaCartPlus } from 'react-icons/fa';

<DynamicButton
  text="Add to Cart"
  icon={FaCartPlus}
  onClick={() => console.log('Added to cart')}
/>;
```

#### Link Button

If you need the button to act as a link, simply pass the `link` prop:

```tsx
<DynamicButton text="Go to Shop" link="/shop" />;
```

#### Loading Button

You can display a spinner when the button is in a loading state:

```tsx
<DynamicButton
  text="Processing..."
  loading={true}
  onClick={() => console.log('Processing')}
/>;
```

#### Disabled Button

Use the `disabled` prop to disable the button:

```tsx
<DynamicButton
  text="Disabled Button"
  disabled={true}
  onClick={() => console.log('This will not fire')}
/>;
```

#### Custom Styles

You can fully customize the button using the `buttonStyles` and `hoverStyles` props:

```tsx
<DynamicButton
  text="Custom Button"
  buttonStyles="bg-purple-600 text-white"
  hoverStyles="hover:bg-purple-800"
/>;
```

---

### Props

| **Prop**           | **Type**                                  | **Default**                                                                                           | **Description**                                                                                                                                                                                                 |
|--------------------|-------------------------------------------|-------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text`             | `string`                                  | `'Click Me'`                                                                                           | Text to display inside the button.                                                                                                                                                                               |
| `icon`             | `FC<{ className?: string }>`              | `undefined`                                                                                           | Optional icon component (e.g., from `react-icons`).                                                                                                                                                             |
| `link`             | `string`                                  | `''`                                                                                                  | If provided, the button will render as a Next.js `<Link />`.                                                                                                                                                    |
| `buttonStyles`     | `string`                                  | `'px-6 py-3 bg-primary text-white rounded-full transition-all duration-300 ease-in-out'`               | Tailwind CSS classes for button styles.                                                                                                                                                                          |
| `hoverStyles`      | `string`                                  | `'hover:bg-primary-dark'`                                                                              | Tailwind CSS classes for hover effect styles.                                                                                                                                                                    |
| `textSize`         | `string`                                  | `'text-base md:text-lg'`                                                                               | Font size classes for button text.                                                                                                                                                                               |
| `iconSize`         | `string`                                  | `'text-lg sm:text-xl'`                                                                                 | Tailwind CSS classes for icon size.                                                                                                                                                                              |
| `iconPosition`     | `'left' | 'right' | 'hidden'`              | `'left'`                                                                                               | Controls whether the icon is displayed on the left, right, or hidden entirely.                                                                                                                                   |
| `onClick`          | `() => void`                              | `undefined`                                                                                           | Click handler for the button (not applicable when `link` is provided).                                                                                                                                           |
| `loading`          | `boolean`                                 | `false`                                                                                               | If `true`, shows a loading spinner and disables the button.                                                                                                                                                     |
| `disabled`         | `boolean`                                 | `false`                                                                                               | If `true`, disables the button (applying opacity and disabling hover/click interactions).                                                                                                                        |
| `type`             | `'button' | 'submit' | 'reset'`            | `'button'`                                                                                             | Specifies the button type (useful for form submissions).                                                                                                                                                        |

---

### Examples

#### Icon on Right

By default, icons are placed on the left. You can move them to the right:

```tsx
<DynamicButton
  text="Checkout"
  icon={FaShoppingCart}
  iconPosition="right"
  onClick={() => console.log('Checkout clicked')}
/>;
```

#### Custom Button Styles

You can fully control the button's appearance using custom Tailwind CSS classes:

```tsx
<DynamicButton
  text="Subscribe"
  buttonStyles="px-8 py-3 bg-blue-500 text-white rounded-lg"
  hoverStyles="hover:bg-blue-600"
/>;
```

#### Loading and Disabled States

Combining loading and disabled states ensures proper button behavior:

```tsx
<DynamicButton
  text="Submit"
  loading={true}
  disabled={true}
/>;
```

---

### Accessibility

The `DynamicButton` component has several accessibility features built in:

- **Keyboard Interactivity**: Buttons are focusable and respond to keyboard events.
- **Aria Attributes**: The button uses `aria-disabled` to indicate when it’s disabled and `aria-busy` during loading states.
- **Accessible Links**: When using the `link` prop, the button will be rendered as an accessible `<a>` element.

---

### Conclusion

The `DynamicButton` component is designed to be flexible, reusable, and easy to integrate into any Next.js or React project. With its support for loading states, icons, custom styling, and accessibility, it offers a professional and scalable solution for creating buttons and links.
