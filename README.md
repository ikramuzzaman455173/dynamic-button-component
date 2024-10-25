# DynamicButton Component Documentation

## Table of Contents
1. [Overview](#overview)
2. [JavaScript Version](#javascript-version)
   - [Props](#javascript-props)
   - [Usage Example](#javascript-usage-example)
   - [CSS Animation Styles](#css-animation-styles)
3. [TypeScript Version](#typescript-version)
   - [Type Definitions](#typescript-type-definitions)
   - [Usage Example](#typescript-usage-example)
   - [CSS Animation Styles](#typescript-css-animation-styles)
4. [Framer Motion Version](#framer-motion-version)
   - [Framer Motion Props](#framer-motion-props)
   - [Framer Motion Usage Example](#framer-motion-usage-example)
5. [Notes](#notes)

---

## Overview
The `DynamicButton` component is a customizable button that supports dynamic properties for text, icons, styles, animations, and event handling. This component is available in two implementations: one using standard Tailwind CSS animations and the other using `framer-motion` for advanced animations.

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
      {Icon && <Icon className={iconSize} />}
      <Link to={link} className={textSize}>
        {text}
      </Link>
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
import { FC } from 'react'; // Importing necessary types from React

// Define the type for props
interface DynamicButtonProps {
  text?: string;
  icon?: FC<{ className?: string }>; // Icon components like FaShoppingCart
  link?: string;
  buttonStyles?: string;
  hoverStyles?: string;
  textSize?: string;
  iconSize?: string;
  onClick?: () => void; // Click event handler function
  disabled?: boolean;
}

// TypeScript version of the DynamicButton component
const DynamicButton: FC<DynamicButtonProps> = ({
  text = 'Click Me',
  icon: Icon,
  link = '#',
  buttonStyles = 'px-10 py-5 bg-secondary-800 text-white rounded-full',
  hoverStyles = 'hover:bg-secondary-900',
  textSize = 'text-xl',
  iconSize = 'text-2xl',
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
      {Icon && <Icon className={iconSize} />}
      <Link to={link} className={textSize}>
        {text}
      </Link>
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
| `onClick`   | `function`          | `undefined`                      | Event handler for the button's click event.               |
| `disabled`  | `boolean`           | `false`                          | Disables the button and changes its appearance.            |

### Usage Example

```tsx
import { FaShoppingCart } from 'react-icons/fa';
import { FC } from 'react';

const SomeComponent: FC = () => {
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
      onClick={handleClick}
      disabled={false}
    />
  );
};
```

### TypeScript CSS Animation Styles

The CSS animation styles in the TypeScript version are identical to those in the JavaScript version, utilizing Tailwind CSS for hover and click effects.

---

## Framer Motion Version

### Implementation

If you want to implement the button using `framer-motion` for advanced animations, here’s how you can do it.

```jsx
import { motion } from 'framer-motion';
import { Link } from 'react-router-dom';

const DynamicButtonMotion = ({
  text = 'Click Me',
  icon: Icon,
  link = '#',
  buttonStyles = 'px-10 py-5 bg-secondary-800 text-white rounded-full',
  hoverStyles = 'hover:bg-secondary-900',
  textSize = 'text-xl',
  iconSize = 'text-2

xl',
  whileHover = { scale: 1.1, boxShadow: '0px 0px 10px rgba(0, 0, 0, 0.15)' },
  whileTap = { scale: 0.95 },
  transition = { duration: 0.3 },
  onClick,
  disabled = false,
}) => {
  return (
    <motion.button
      whileHover={!disabled && whileHover}
      whileTap={!disabled && whileTap}
      transition={transition}
      className={`flex items-center gap-3 ${buttonStyles} ${hoverStyles} shadow-lg ${disabled && 'opacity-50 cursor-not-allowed'}`}
      onClick={onClick}
      disabled={disabled}
    >
      {Icon && <Icon className={iconSize} />}
      <Link to={link} className={textSize}>
        {text}
      </Link>
    </motion.button>
  );
};

export default DynamicButtonMotion;
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
| `whileHover`| `Object`            | `{ scale: 1.1 }`                 | Animation properties when hovered.                          |
| `whileTap`  | `Object`            | `{ scale: 0.95 }`                | Animation properties when clicked.                          |
| `transition` | `Object`           | `{ duration: 0.3 }`              | Transition properties for animations.                       |
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
    <DynamicButtonMotion
      text="BUY NOW"
      icon={FaShoppingCart}
      link="/purchase"
      buttonStyles="px-10 py-5 bg-secondary-800 text-white rounded-full"
      hoverStyles="hover:bg-secondary-900"
      textSize="text-xl"
      iconSize="text-2xl"
      onClick={handleClick}
      disabled={false}
    />
  );
};
```

---

## Notes
- Ensure you have `react-router-dom` installed in your project to utilize the Link component.
- The `DynamicButton` can be easily customized for various use cases in your application.
- The Framer Motion version requires `framer-motion` to be installed in your project.
