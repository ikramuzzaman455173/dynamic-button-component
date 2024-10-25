# DynamicButton Component Documentation

## Table of Contents
1. [Overview](#overview)
2. [JavaScript Version](#javascript-version)
   - [Props](#javascript-props)
   - [Usage Example](#javascript-usage-example)
3. [TypeScript Version](#typescript-version)
   - [Type Definitions](#typescript-type-definitions)
   - [Usage Example](#typescript-usage-example)
4. [Notes](#notes)

---

## Overview
The `DynamicButton` component is a highly customizable and reusable button built using React. It leverages `framer-motion` for animations and allows developers to pass dynamic properties for text, icons, styles, animations, and event handling. 

---

## JavaScript Version

```jsx
import { motion } from 'framer-motion';
import { Link } from 'react-router-dom';

const DynamicButton = ({
  text = 'Click Me',
  icon: Icon,
  link = '#',
  buttonStyles = 'px-10 py-5 bg-secondary-800 text-white rounded-full',
  hoverStyles = 'hover:bg-secondary-900',
  textSize = 'text-xl',
  iconSize = 'text-2xl',
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
| `whileHover`| `Object`            | `{ scale: 1.1, boxShadow: '0px 0px 10px rgba(0, 0, 0, 0.15)' }` | Animation for the button when hovered.                     |
| `whileTap`  | `Object`            | `{ scale: 0.95 }`                | Animation for the button when tapped.                      |
| `transition` | `Object`           | `{ duration: 0.3 }`              | Transition time for hover/tap animations.                  |
| `onClick`   | `Function`          | `undefined`                      | Event handler for the button's click event.               |
| `disabled`  | `Boolean`           | `false`                          | Disables the button and changes its appearance.            |

### JavaScript Usage Example

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
      whileHover={{ scale: 1.1, boxShadow: '0px 0px 10px rgba(0, 0, 0, 0.15)' }}
      whileTap={{ scale: 0.95 }}
      transition={{ duration: 0.3 }}
      onClick={handleClick}
      disabled={false}
    />
  );
};
```

---

## TypeScript Version

```tsx
import { motion } from 'framer-motion';
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
  whileHover?: object;
  whileTap?: object;
  transition?: object;
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
| `whileHover`| `object`            | `{ scale: 1.1, boxShadow: '0px 0px 10px rgba(0, 0, 0, 0.15)' }` | Animation for the button when hovered.                     |
| `whileTap`  | `object`            | `{ scale: 0.95 }`                | Animation for the button when tapped.                      |
| `transition` | `object`           | `{ duration: 0.3 }`              | Transition time for hover/tap animations.                  |
| `onClick`   | `function`          | `undefined`                      | Event handler for the button's click event.               |
| `disabled`  | `boolean`           | `false`                          | Disables the button and changes its appearance.            |

### TypeScript Usage Example

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
      whileHover={{ scale: 1.1, boxShadow: '0px 0px 10px rgba(0, 0, 0, 0.15)' }}
      whileTap={{ scale: 0.95 }}
      transition={{ duration: 0.3 }}
      onClick={handleClick}
      disabled={false}
    />
  );
};
```

---

## Notes
- Ensure you have `framer-motion` and `react-router-dom` installed in your project to utilize this component effectively.
- The component is designed for high flexibility, allowing customization for various use cases in your application.
