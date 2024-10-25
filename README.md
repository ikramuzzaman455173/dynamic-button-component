# DynamicButton Component Documentation

## Table of Contents
1. [Overview](#overview)
2. [Features](#features)
3. [JavaScript Version](#javascript-version)
   - [Props](#javascript-props)
   - [Usage Example](#javascript-usage-example)
   - [CSS Animation Styles](#css-animation-styles)
4. [TypeScript Version](#typescript-version)
   - [Type Definitions](#typescript-type-definitions)
   - [Usage Example](#typescript-usage-example)
   - [CSS Animation Styles](#typescript-css-animation-styles)
5. [Framer Motion Version](#framer-motion-version)
   - [Framer Motion Props](#framer-motion-props)
   - [Framer Motion Usage Example](#framer-motion-usage-example)
6. [Notes](#notes)

---

## Overview
The `DynamicButton` component is a customizable button designed to accommodate various use cases with dynamic properties for text, icons, styles, animations, and event handling. It supports three implementations: standard JavaScript, TypeScript, and advanced animations with `framer-motion`.

---

## Features
- **Dynamic Text**: Customize the button label with any string.
- **Icon Support**: Include any React component as an icon.
- **Icon Positioning**: Choose icon positioning as left, right, or hidden.
- **Customizable Styles**: Tailwind CSS-based styling for buttons, including hover effects.
- **Accessibility**: Supports `disabled` state for improved usability.
- **Animation Effects**: Utilizes CSS animations and Framer Motion for hover and click interactions.
- **Routing Support**: Built-in support for navigation using React Router's `Link`.

---

## JavaScript Version

### Implementation

```jsx
import { Link } from 'react-router-dom';

const DynamicButton = ({
  text = 'Click Me',
  icon: Icon,
  link = '#',
  buttonStyles = 'px-10 py-5 bg-secondary-800 text-white rounded-full',
  hoverStyles = 'hover:bg-secondary-900',
  textSize = 'text-xl',
  iconSize = 'text-2xl',
  iconPosition = 'left', // 'left', 'right', or 'hidden'
  onClick,
  disabled = false,
}) => {
  return (
    <button
      className={`flex items-center gap-3 ${buttonStyles} ${hoverStyles} shadow-lg ${disabled && 'opacity-50 cursor-not-allowed'}`}
      onClick={onClick}
      disabled={disabled}
      onMouseEnter={e => e.currentTarget.classList.add('scale-105')}
      onMouseLeave={e => e.currentTarget.classList.remove('scale-105')}
      onMouseDown={e => e.currentTarget.classList.add('scale-95')}
      onMouseUp={e => e.currentTarget.classList.remove('scale-95')}
    >
      {iconPosition === 'left' && Icon && <Icon className={iconSize} />}
      <Link to={link} className={textSize}>
        {text}
      </Link>
      {iconPosition === 'right' && Icon && <Icon className={iconSize} />}
    </button>
  );
};

export default DynamicButton;
```

### JavaScript Props

| Prop         | Type                | Default Value                     | Description                                                 |
|--------------|---------------------|-----------------------------------|-------------------------------------------------------------|
| `text`      | `String`            | `'Click Me'`                     | The label for the button.                                   |
| `icon`      | `React component`    | `undefined`                      | A dynamic icon component passed to display within the button. |
| `link`      | `String`            | `'#'`                            | The URL path for the button link.                           |
| `buttonStyles`| `String`          | `'px-10 py-5 bg-secondary-800 text-white rounded-full'` | Styles for the button.                                    |
| `hoverStyles`| `String`           | `'hover:bg-secondary-900'`      | Additional hover styles.                                   |
| `textSize`  | `String`            | `'text-xl'`                      | Size of the text in the button.                            |
| `iconSize`  | `String`            | `'text-2xl'`                     | Size of the icon.                                         |
| `iconPosition` | `String`        | `'left'`                         | Position of the icon: `'left'`, `'right'`, or `'hidden'`. |
| `onClick`   | `Function`          | `undefined`                      | Event handler for the button's click event.               |
| `disabled`  | `Boolean`           | `false`                          | Disables the button and changes its appearance.            |

### Usage Example

```jsx
import { FaShoppingCart } from 'react-icons/fa';

const SomeComponent = () => {
  const handleClick = () => {
    console.log('Button clicked!');
  };

  return (
    <DynamicButton
      text="BUY NOW"
      icon={FaShoppingCart}
      link="/purchase"
      buttonStyles="px-10 py-5 bg-secondary-800 text-white rounded-full"
      hoverStyles="hover:bg-secondary-900"
      textSize="text-xl"
      iconSize="text-2xl"
      iconPosition="left" // or "right" or "hidden"
      onClick={handleClick}
      disabled={false}
    />
  );
};
```

### CSS Animation Styles

In the above implementation, the button applies the following animations using standard Tailwind CSS classes:

- **Hover Scale**: Button scales up when hovered.
- **Click Scale**: Button scales down when clicked.

These animations are handled using the `onMouseEnter`, `onMouseLeave`, `onMouseDown`, and `onMouseUp` event handlers.

---

## TypeScript Version

### Implementation

```tsx
import { Link } from 'react-router-dom';
import { FC } from 'react';

interface DynamicButtonProps {
  text?: string;
  icon?: FC<{ className?: string }>; // Icon components like FaShoppingCart
  link?: string;
  buttonStyles?: string;
  hoverStyles?: string;
  textSize?: string;
  iconSize?: string;
  iconPosition?: 'left' | 'right' | 'hidden'; // New prop for icon position
  onClick?: () => void; // Click event handler function
  disabled?: boolean;
}

const DynamicButton: FC<DynamicButtonProps> = ({
  text = 'Click Me',
  icon: Icon,
  link = '#',
  buttonStyles = 'px-10 py-5 bg-secondary-800 text-white rounded-full',
  hoverStyles = 'hover:bg-secondary-900',
  textSize = 'text-xl',
  iconSize = 'text-2xl',
  iconPosition = 'left', // Default icon position
  onClick,
  disabled = false,
}) => {
  return (
    <button
      className={`flex items-center gap-3 ${buttonStyles} ${hoverStyles} shadow-lg ${disabled && 'opacity-50 cursor-not-allowed'}`}
      onClick={onClick}
      disabled={disabled}
      onMouseEnter={e => e.currentTarget.classList.add('scale-105')}
      onMouseLeave={e => e.currentTarget.classList.remove('scale-105')}
      onMouseDown={e => e.currentTarget.classList.add('scale-95')}
      onMouseUp={e => e.currentTarget.classList.remove('scale-95')}
    >
      {iconPosition === 'left' && Icon && <Icon className={iconSize} />}
      <Link to={link} className={textSize}>
        {text}
      </Link>
      {iconPosition === 'right' && Icon && <Icon className={iconSize} />}
    </button>
  );
};

export default DynamicButton;
```

### TypeScript Type Definitions

| Prop         | Type                | Default Value                     | Description                                                 |
|--------------|---------------------|-----------------------------------|-------------------------------------------------------------|
| `text`      | `string`            | `'Click Me'`                     | The label for the button.                                   |
| `icon`      | `React component`    | `undefined`                      | A dynamic icon component passed to display within the button. |
| `link`      | `string`            | `'#'`                            | The URL path for the button link.                           |
| `buttonStyles`| `string`          | `'px-10 py-5 bg-secondary-800 text-white rounded-full'` | Styles for the button.                                    |
| `hoverStyles`| `string`           | `'hover:bg-secondary-900'`      | Additional hover styles.                                   |
| `textSize`  | `string`            | `'text-xl'`                      | Size of the text in the button.                            |
| `iconSize`  | `string`            | `'text-2xl'`                     | Size of the icon.                                         |
| `iconPosition` | `string`        | `'left'`                         | Position of the icon: `'left'`, `'right'`, or `'hidden'`. |
| `onClick`   | `function`          | `undefined`                      | Event handler for the button's click event.               |
| `disabled`  | `boolean`           | `false`                          | Disables the button and changes its appearance.            |

### Usage Example

```tsx
import { FaShoppingCart } from 'react-icons/fa';
import { FC } from 'react';

const Some

Component: FC = () => {
  const handleClick = () => {
    console.log('Button clicked!');
  };

  return (
    <DynamicButton
      text="BUY NOW"
      icon={FaShoppingCart}
      link="/purchase"
      buttonStyles="px-10 py-5 bg-secondary-800 text-white rounded-full"
      hoverStyles="hover:bg-secondary-900"
      textSize="text-xl"
      iconSize="text-2xl"
      iconPosition="right" // or "left" or "hidden"
      onClick={handleClick}
      disabled={false}
    />
  );
};
```

### CSS Animation Styles

The button uses standard CSS for animations, including:

- **Hover Scale**: Increases size slightly on hover.
- **Click Scale**: Reduces size slightly on click.

These effects create a responsive and engaging user interface.

---

## Framer Motion Version

### Implementation

```jsx
import { Link } from 'react-router-dom';
import { motion } from 'framer-motion';

const DynamicButton = ({
  text = 'Click Me',
  icon: Icon,
  link = '#',
  buttonStyles = 'px-10 py-5 bg-secondary-800 text-white rounded-full',
  hoverStyles = 'hover:bg-secondary-900',
  textSize = 'text-xl',
  iconSize = 'text-2xl',
  iconPosition = 'left', // New prop for icon position
  onClick,
  disabled = false,
}) => {
  return (
    <motion.button
      className={`flex items-center gap-3 ${buttonStyles} ${hoverStyles} shadow-lg ${disabled && 'opacity-50 cursor-not-allowed'}`}
      onClick={onClick}
      disabled={disabled}
      whileHover={{ scale: 1.05 }} // Scale up on hover
      whileTap={{ scale: 0.95 }}   // Scale down on tap
    >
      {iconPosition === 'left' && Icon && <Icon className={iconSize} />}
      <Link to={link} className={textSize}>
        {text}
      </Link>
      {iconPosition === 'right' && Icon && <Icon className={iconSize} />}
    </motion.button>
  );
};

export default DynamicButton;
```

### Framer Motion Props

| Prop         | Type                | Default Value                     | Description                                                 |
|--------------|---------------------|-----------------------------------|-------------------------------------------------------------|
| `text`      | `String`            | `'Click Me'`                     | The label for the button.                                   |
| `icon`      | `React component`    | `undefined`                      | A dynamic icon component passed to display within the button. |
| `link`      | `String`            | `'#'`                            | The URL path for the button link.                           |
| `buttonStyles`| `String`          | `'px-10 py-5 bg-secondary-800 text-white rounded-full'` | Styles for the button.                                    |
| `hoverStyles`| `String`           | `'hover:bg-secondary-900'`      | Additional hover styles.                                   |
| `textSize`  | `String`            | `'text-xl'`                      | Size of the text in the button.                            |
| `iconSize`  | `String`            | `'text-2xl'`                     | Size of the icon.                                         |
| `iconPosition` | `String`        | `'left'`                         | Position of the icon: `'left'`, `'right'`, or `'hidden'`. |
| `onClick`   | `Function`          | `undefined`                      | Event handler for the button's click event.               |
| `disabled`  | `Boolean`           | `false`                          | Disables the button and changes its appearance.            |

### Framer Motion Usage Example

```jsx
import { FaShoppingCart } from 'react-icons/fa';

const SomeComponent = () => {
  const handleClick = () => {
    console.log('Button clicked!');
  };

  return (
    <DynamicButton
      text="BUY NOW"
      icon={FaShoppingCart}
      link="/purchase"
      buttonStyles="px-10 py-5 bg-secondary-800 text-white rounded-full"
      hoverStyles="hover:bg-secondary-900"
      textSize="text-xl"
      iconSize="text-2xl"
      iconPosition="right" // or "left" or "hidden"
      onClick={handleClick}
      disabled={false}
    />
  );
};
```

### Framer Motion CSS Animation Styles

In this implementation, the button utilizes `framer-motion` for hover and click effects, creating a more engaging user experience.

---

## Notes
- Ensure to install the necessary packages for icons and Framer Motion, if using those features.
- Tailwind CSS must be set up in your project for the styles to apply correctly.
- For icons, consider using popular libraries like `react-icons`.
