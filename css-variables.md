## CSS Variables (custom properties)

1. CSS variables are awesome.
2. They just work like normal properties.
3. They are inherited properties. (but you can change that)


Basic syntax would be

```css
:root {
  --my-custom-property: 123px;
}

div {
  width: var(--my-custom-property);
}
```

### Scope

CSS Custom Properties  (*as the specification names them*)  can do much more for you than SASS variables.

> They're properties and they cascade like normal properties.

The selector the variables are defined inside sets their scope,
with all descending selectors (elements) able to access these variables.

Defining your CSS variables inside the __:root__ selector basically makes them globally available.

### value fallback

```css
:root {
  --primary-bg: gray;
  --fallback-size: 24px;
}
section {
  background: var(--primary-bg, white); /* Normal value as fallback value */
  font-size: var(--default-size, var(--fallbacksize, 36px)); /* var() as fallback value */
}
```

### invalid variable

```css
p {
  color: var(--default-color);
}
```

Since the variable --default-color isn't available in the scope, the color property is thrown out.


### invalid value (computed value time)

> initial

```css
:root {
  --margin-small: 8px;
}
p {
  color: var(--margin-small); /* px is not a valid value for color property */
}
```
Variable exists here, but value it has is invalid for color. It would be reset to **initial**.

### Theming

```css
:root {
  --gutter: 2px;
}
section {
  margin: var(--gutter);
}
@media (min-width: 1000px) {
  :root {
    --gutter: 10px;
  }
}
```



## Referenes

https://leaverou.github.io/css-variables
