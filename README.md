### **DynamicButton Component Documentation**

---

#### **Overview:**
The `DynamicButton` component is a fully customizable and reusable button designed for flexibility in styling, events, and interactivity. It allows developers to dynamically pass properties such as text, icons, styles, animations, and event handlers.

---

#### **Component Structure:**

```jsx
import { motion } from 'framer-motion';
import { Link } from 'react-router-dom';

const DynamicButton = ({
  text = 'Click Me',
  icon: Icon, // Passing an icon component dynamically
  link = '#',
  buttonStyles = 'px-10 py-5 bg-secondary-800 text-white rounded-full',
  hoverStyles = 'hover:bg-secondary-900',
  textSize = 'text-xl',
  iconSize = 'text-2xl',
  whileHover = { scale: 1.1, boxShadow: '0px 0px 10px rgba(0, 0, 0, 0.15)' },
  whileTap = { scale: 0.95 },
  transition = { duration: 0.3 },
  onClick, // Dynamic event handler
  disabled = false, // Optionally handle disabled state
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

---

#### **Props:**

1. **`text`** (String, default: `'Click Me'`):  
   The label for the button.

2. **`icon`** (React component, optional):  
   A dynamic icon component passed to display within the button (e.g., `FaShoppingCart`).

3. **`link`** (String, default: `'#'`):  
   The URL path for the button link.

4. **`buttonStyles`** (String, default: `'px-10 py-5 bg-secondary-800 text-white rounded-full'`):  
   The styles for the button. You can customize padding, background color, text color, etc.

5. **`hoverStyles`** (String, default: `'hover:bg-secondary-900'`):  
   Additional hover styles.

6. **`textSize`** (String, default: `'text-xl'`):  
   The size of the text in the button.

7. **`iconSize`** (String, default: `'text-2xl'`):  
   The size of the icon.

8. **`whileHover`** (Object, default: `{ scale: 1.1, boxShadow: '0px 0px 10px rgba(0, 0, 0, 0.15)' }`):  
   Animation for the button when hovered.

9. **`whileTap`** (Object, default: `{ scale: 0.95 }`):  
   Animation for the button when tapped or clicked.

10. **`transition`** (Object, default: `{ duration: 0.3 }`):  
    Transition time for the hover/tap animations.

11. **`onClick`** (Function, optional):  
    Event handler for the button's click event.

12. **`disabled`** (Boolean, default: `false`):  
    Disables the button and changes its appearance.

---

#### **Usage Example:**

```jsx
import { FaShoppingCart } from 'react-icons/fa';

const SomeComponent = () => {
  const handleClick = () => {
    console.log('Button clicked!');
    // Add your event logic here
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
