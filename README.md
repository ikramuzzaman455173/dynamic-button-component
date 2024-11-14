### DynamicButton Component Documentation

The `DynamicButton` component is a highly flexible, reusable, and modern button component for Next.js and TypeScript applications. It supports buttons, links, icons, loading states, disabled states, and extensive customization through Tailwind CSS classes.

---

### Table of Contents

1. [Installation](#installation)
2. [Component Code](#component-code)
3. [Usage](#usage)
   - [Basic Button](#basic-button)
   - [Button with Icon](#button-with-icon)
   - [Link Button](#link-button)
   - [Loading Button](#loading-button)
   - [Disabled Button](#disabled-button)
   - [Custom Styles](#custom-styles)
4. [Props](#props)
5. [Examples](#examples)
6. [Accessibility](#accessibility)
7. [Conclusion](#conclusion)

---

### Installation

First, ensure you have `react-icons` (if using icons) installed in your project:

```bash
npm install react-icons
```

### Component Code

Here's the complete code for the `DynamicButton` component:

```tsx
import { FC } from 'react';
import Link from 'next/link';
import { IconType } from 'react-icons';

interface DynamicButtonProps {
  text?: string;
  icon?: IconType;
  link?: string;
  buttonStyles?: string;
  hoverStyles?: string;
  textSize?: string;
  iconSize?: string;
  iconPosition?: 'left' | 'right' | 'hidden';
  loading?: boolean;
  onClick?: () => void;
  disabled?: boolean;
  type?: 'button' | 'submit' | 'reset';
}

const DynamicButton: FC<DynamicButtonProps> = ({
  text = 'Click Me',
  icon: Icon,
  link = '',
  buttonStyles = 'px-6 py-3 bg-blue-500 text-white rounded-full transition-all duration-300 ease-in-out',
  hoverStyles = 'hover:bg-blue-600',
  textSize = 'text-base md:text-lg',
  iconSize = 'text-lg sm:text-xl',
  iconPosition = 'left',
  loading = false,
  onClick,
  disabled = false,
  type = 'button',
}) => {
  const content = (
    <>
      {loading && <span className="loader mr-2"></span>}
      {!loading && iconPosition === 'left' && Icon && <Icon className={`${iconSize} mr-2`} />}
      <span className={textSize}>{text}</span>
      {!loading && iconPosition === 'right' && Icon && <Icon className={`${iconSize} ml-2`} />}
    </>
  );

  const commonClasses = `flex items-center justify-center gap-2 ${buttonStyles} ${hoverStyles} ${disabled ? 'opacity-50 cursor-not-allowed' : 'hover:scale-105'}`;

  return link ? (
    <Link href={link}>
      <a className={commonClasses} aria-disabled={disabled}>
        {content}
      </a>
    </Link>
  ) : (
    <button
      type={type}
      className={commonClasses}
      onClick={disabled || loading ? undefined : onClick}
      disabled={disabled}
      aria-busy={loading}
    >
      {content}
    </button>
  );
};

export default DynamicButton;
```

### Usage

#### Basic Button

This is the simplest form of the button with default text and style:

```tsx
<DynamicButton text="Click Me" onClick={() => alert('Button Clicked')} />
```

#### Button with Icon

You can pass an icon component from `react-icons` as a prop:

```tsx
import { FaCartPlus } from 'react-icons/fa';

<DynamicButton
  text="Add to Cart"
  icon={FaCartPlus}
  onClick={() => console.log('Added to cart')}
/>
```

#### Link Button

The button can also be a link by providing the `link` prop:

```tsx
<DynamicButton
  text="Go to Shop"
  link="/shop"
/>
```

#### Loading Button

You can display a loading spinner while the button is in a loading state:

```tsx
<DynamicButton
  text="Processing..."
  loading={true}
/>
```

#### Disabled Button

A disabled button prevents user interaction:

```tsx
<DynamicButton
  text="Disabled Button"
  disabled={true}
/>
```

#### Custom Styles

You can customize the button's appearance with your own styles:

```tsx
<DynamicButton
  text="Custom Button"
  buttonStyles="bg-green-500 text-white rounded-lg px-4 py-2"
  hoverStyles="hover:bg-green-600"
/>
```

### Props

| **Prop**           | **Type**                        | **Default**                                             | **Description**                                                                                                      |
|--------------------|---------------------------------|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| `text`             | `string`                        | `'Click Me'`                                             | Text to display inside the button.                                                                                   |
| `icon`             | `IconType`                      | `undefined`                                             | Optional icon component (e.g., from `react-icons`).                                                                  |
| `link`             | `string`                        | `''`                                                    | If provided, the button will render as a Next.js `<Link />` instead of a button.                                      |
| `buttonStyles`     | `string`                        | `'px-6 py-3 bg-blue-500 text-white rounded-full'`        | Tailwind CSS classes for the button's base styles.                                                                   |
| `hoverStyles`      | `string`                        | `'hover:bg-blue-600'`                                   | Tailwind CSS classes for hover effect.                                                                                |
| `textSize`         | `string`                        | `'text-base md:text-lg'`                                | Font size classes for button text.                                                                                   |
| `iconSize`         | `string`                        | `'text-lg sm:text-xl'`                                  | Tailwind CSS classes for the icon size.                                                                               |
| `iconPosition`     | `'left' | 'right' | 'hidden'`   | `'left'`                                                | Position of the icon: left, right, or hidden.                                                                        |
| `loading`          | `boolean`                       | `false`                                                 | Displays a loading spinner if true.                                                                                  |
| `onClick`          | `() => void`                    | `undefined`                                             | Function to handle the button's click event.                                                                          |
| `disabled`         | `boolean`                       | `false`                                                 | Disables the button if true (applies opacity and prevents interaction).                                               |
| `type`             | `'button' | 'submit' | 'reset'` | `'button'`                                              | Sets the button type (useful for forms).                                                                              |

### Examples

#### Button with Icon on Right

To position the icon on the right side:

```tsx
import { FaShoppingCart } from 'react-icons/fa';

<DynamicButton
  text="Checkout"
  icon={FaShoppingCart}
  iconPosition="right"
  onClick={() => alert('Checkout clicked')}
/>
```

#### Custom Button with Icon and Link

A fully styled button with a custom icon and link:

```tsx
import { FaArrowRight } from 'react-icons/fa';

<DynamicButton
  text="Proceed"
  icon={FaArrowRight}
  link="/next-step"
  buttonStyles="bg-red-500 text-white px-8 py-3 rounded-lg"
  hoverStyles="hover:bg-red-700"
/>
```

### Accessibility

The `DynamicButton` component includes accessibility features:

- **Keyboard Interaction**: The button is focusable and responds to keyboard inputs.
- **ARIA Attributes**: It uses `aria-disabled` when the button is disabled, and `aria-busy` when loading.
- **Semantic HTML**: The button is rendered as either a `<button>` or an anchor `<a>` tag when used as a link.

### Conclusion

The `DynamicButton` component provides a modern, reusable solution for creating buttons and links in Next.js applications. With its flexibility, support for icons, loading states, and custom styles, it's a versatile choice for building dynamic user interfaces.
