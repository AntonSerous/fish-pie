# [Styled Components](https://www.styled-components.com/) _(Cliffs Notes)_

## CSS in Javascript 😱

### Why 🤔

- ✅ **React Compositions**
- ✅ **Style Encapsulation**
- ✅ **Dynamic Styles**

### Support 👍

- ✔ [Vendor prefixing](https://www.styled-components.com/docs/basics)
- ✔ [Typescript Suport](https://www.styled-components.com/docs/api#typescript)
- ✔ [Jest Integration](https://www.styled-components.com/docs/tooling#jest-integration)
- ✔ [Enzyme Hooks](https://www.styled-components.com/docs/api#enzymefind)
- ✔ [Linting Support _(Style Lint)_](https://www.styled-components.com/docs/tooling#stylelint)

[🔽 Next](https://github.com/devonChurch/fish-pie#agenda-)

.

.

.

.

.

.

.

.

.

.

## Agenda 🗒

- 🕐 [Composition](https://github.com/devonChurch/fish-pie#composition-)
- 🕑 [Styles](https://github.com/devonChurch/fish-pie#styles-)
- 🕒 [Inheritance](https://github.com/devonChurch/fish-pie#inheritance-)
- 🕓 [Dynamic](https://github.com/devonChurch/fish-pie#dynamic-)
- 🕔 [Tagged Templates](https://github.com/devonChurch/fish-pie#tagged-templates-)
- 🕕 [Polymorphism](https://github.com/devonChurch/fish-pie#polymorphism-)
- 🕖 [Pseudo Elements](https://github.com/devonChurch/fish-pie#pseudo-elements-)
- 🕗 [Theming](https://github.com/devonChurch/fish-pie#theming-)
- 🕘 [Polished](https://github.com/devonChurch/fish-pie#polished-)

[🔽 Next](https://github.com/devonChurch/fish-pie#composition-)

.

.

.

.

.

.

.

.

.

.

## Composition 🏗

_Lets make a button..._

##### Input ✏

```javascript
const Button = styled.button``;

ReactDOM.render(<Button>Hello World</Button>, document.getElementById("app"));
```

##### Output 💎

![1](https://user-images.githubusercontent.com/15273233/54859129-723f4080-4d6e-11e9-95ab-99c12720a98e.png)

[🔽 Next](https://github.com/devonChurch/fish-pie#styles-)

.

.

.

.

.

.

.

.

.

.

## Styles 💄

_Lets add some styles..._

##### Input ✏

```javascript
const Button = styled.button`
  // Reset.
  background: transparent;
  border: 0;
  padding: 0;

  // Custom.
  background: blue;
  border-radius: 0.2rem;
  color: white;
  padding: 0.5rem 1rem;
  font-size: 1rem;
`;

const MyApp = () => <Button>Hello World</Button>;
```

##### Output 💎

![2](https://user-images.githubusercontent.com/15273233/54859430-fb0bab80-4d71-11e9-9cf8-1123fed27aea.png)

[🔽 Next](https://github.com/devonChurch/fish-pie#inheritance-)

.

.

.

.

.

.

.

.

.

.

## Inheritance ⚡

_Lets focus on structure..._

### Linear Structure 👾

##### Input ✏

```javascript
const ButtonReset = styled.button`
  background: transparent;
  border: 0;
  padding: 0;
`;

const ButtonLarge = styled(ButtonReset)`
  background: blue;
  border-radius: 0.2rem;
  color: white;
  padding: 0.5rem 1rem;
  font-size: 1rem;
`;

const ButtonSmall = styled(ButtonLarge)`
  padding: 0.25rem 0.5rem;
  font-size: 0.75rem;
`;

const MyApp = () => (
  <>
    <ButtonLarge>Large Button</ButtonLarge>
    <ButtonSmall>Small Button</ButtonSmall>
  </>
);
```

##### Output 💎

![3](https://user-images.githubusercontent.com/15273233/54859518-f7c4ef80-4d72-11e9-91a4-3cbe52c111f1.png)

[🔽 Next](https://github.com/devonChurch/fish-pie#snippet-structure-)

.

.

.

### Snippet Structure 😺

##### Input ✏

```javascript
const ButtonReset = css`
  background: transparent;
  border: 0;
  padding: 0;
`;

const ButtonLarge = styled.button`
  ${ButtonReset}
  background: blue;
  border-radius: 0.2rem;
  color: white;
  padding: 0.5rem 1rem;
  font-size: 1rem;
`;

const ButtonSmall = styled(ButtonLarge)`
  padding: 0.25rem 0.5rem;
  font-size: 0.75rem;
`;

const MyApp = () => (
  <>
    <ButtonLarge>Large Button</ButtonLarge>
    <ButtonSmall>Small Button</ButtonSmall>
  </>
);
```

##### Output 💎

![3](https://user-images.githubusercontent.com/15273233/54859518-f7c4ef80-4d72-11e9-91a4-3cbe52c111f1.png)

[🔽 Next](https://github.com/devonChurch/fish-pie#global-structure-)

.

.

.

### Global Structure 🌎

##### Input ✏

```javascript
const GlobalStyle = createGlobalStyle`
  button {
    background: transparent;
    border: 0;
    padding: 0;
  }
`;

const ButtonLarge = styled.button`
  background: blue;
  border-radius: 0.2rem;
  color: white;
  padding: 0.5rem 1rem;
  font-size: 1rem;
`;

const ButtonSmall = styled(ButtonLarge)`
  padding: 0.25rem 0.5rem;
  font-size: 0.75rem;
`;

const MyApp = () => (
  <>
    <GlobalStyle />
    <ButtonLarge>Large Button</ButtonLarge>
    <ButtonSmall>Small Button</ButtonSmall>
  </>
);
```

##### Output 💎

![3](https://user-images.githubusercontent.com/15273233/54859518-f7c4ef80-4d72-11e9-91a4-3cbe52c111f1.png)

[🔽 Next](https://github.com/devonChurch/fish-pie#dynamic-)

.

.

.

.

.

.

.

.

.

.

## Dynamic 🎈

_Adapting to component props..._

### Single Styles 👁

##### Input ✏

```javascript
const Button = styled.button`
  background: blue;
  border-radius: 0.2rem;
  color: white;
  padding: ${({ isSmall }) => (isSmall ? "0.25rem 0.5rem" : "0.5rem 1rem")};
  font-size: ${({ isSmall }) => (isSmall ? "0.75rem" : "1rem")};
`;

const MyApp = () => (
  <>
    <Button>Large Button</Button>
    <Button isSmall>Small Button</Button>
  </>
);
```

##### Output 💎

![3](https://user-images.githubusercontent.com/15273233/54859518-f7c4ef80-4d72-11e9-91a4-3cbe52c111f1.png)

[🔽 Next](https://github.com/devonChurch/fish-pie#abstract-logic-)

.

.

.

### Abstract Logic 👠

##### Input ✏

```javascript
const Button = styled.button.attrs(({ isSmall }) => ({
  padding: isSmall ? "0.25rem 0.5rem" : "0.5rem 1rem",
  fontSize: isSmall ? "0.75rem" : "1rem"
}))`
  ${ButtonReset}
  background: blue;
  border-radius: 0.2rem;
  color: white;
  padding: ${({ padding }) => padding};
  font-size: ${({ fontSize }) => fontSize};
`;

const MyApp = () => (
  <>
    <Button>Large Button</Button>
    <Button isSmall>Small Button</Button>
  </>
);
```

##### Output 💎

![3](https://user-images.githubusercontent.com/15273233/54859518-f7c4ef80-4d72-11e9-91a4-3cbe52c111f1.png)

[🔽 Next](https://github.com/devonChurch/fish-pie#style-blocks-)

.

.

.

### Style Blocks 💥

##### Input ✏

```javascript
const colors = {
  success: "green",
  error: "red",
  disabled: "gray"
};

const Button = styled.button`
  background: ${({ type }) => colors[type] || "blue"};
  border-radius: 0.2rem;
  color: white;
  padding: 0.5rem 1rem;
  font-size: 1rem;

  ${({ type }) =>
    type === "disabled" &&
    css`
      color: black;
      cursor: not-allowed;
      opacity: 0.5;
    `}
`;

const MyApp = () => (
  <>
    <Button>Standard Button</Button>
    <Button type="error">Error Button</Button>
    <Button type="disabled">Disabled Button</Button>
  </>
);
```

##### Output 💎

![4](https://user-images.githubusercontent.com/15273233/54860001-cb13d680-4d78-11e9-89fa-4b76fc3089a2.png)

[🔽 Next](https://github.com/devonChurch/fish-pie#tagged-templates-)

.

.

.

.

.

.

.

.

.

.

## Tagged Templates 💍

_[What are they](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_templates) and [how do they work](https://mxstbr.blog/2016/11/styled-components-magic-explained/)..._

##### Input ✏

```javascript
const myFnc = (
  strings, // ["↵  padding: ", ";↵  color: ", ";↵"]
  ...values // ["10px", "red"]
) =>
  (
    strings[0] +
    values[0] + // "Padding" reference.
    strings[1] +
    values[1] + // "Color" reference (plus "Paddings" trailing semicolon).
    strings[2]
  ) // "Colors" trailing semicolon
    .trim() // Remove white space.
    .replace(/\t/gm, ""); // Remove tabs.

// Create a fictitious style declaration.
myFnc`
  padding: ${"10px"};
  color: ${"red"};
`;
```

##### Output 💎

```css
padding: 10px;
color: red;
```

[🔽 Next](https://github.com/devonChurch/fish-pie#polymorphism-)

.

.

.

.

.

.

.

.

.

.

## Polymorphism 🐘

_Change the root native element type..._

##### Input ✏

```javascript
const Button = styled.button`
  ${ButtonReset}
  background: blue;
  border-radius: 0.2rem;
  color: white;
  padding: 0.5rem 1rem;
  font-size: 1rem;

  ${({ as }) =>
    as === "a" &&
    css`
      cursor: pointer;
      text-decoration: underline;
    `}
`;

const MyApp = () => (
  <>
    <Button>Generic Button</Button>
    <Button as="a" href="#">
      Link Button
    </Button>
  </>
);
```

##### Output 💎

![5](https://user-images.githubusercontent.com/15273233/54860831-aa517e00-4d84-11e9-8711-94b07588843c.png)

[🔽 Next](https://github.com/devonChurch/fish-pie#pseudo-elements-)

.

.

.

.

.

.

.

.

.

.

## Pseudo Elements 🍻

_Just like regular CSS..._

##### Input ✏

```javascript
const Button styled.button`
  background: blue;
  border: 1px solid blue;
  border-radius: 0.2rem;
  color: white;
  display: inline-block;
  padding: 0.5rem 2.25rem 0.5rem 1rem;
  position: relative;
  font-size: 1rem;
  transition: 200ms;

  &:after {
    content: " ⚙";
    position: absolute;
    right: 0.5rem;
    top: 50%;
    transform: translateY(-50%);
  }

  &:hover {
    transform: scale(1.25);
    z-index: 1;
  }

  ${({as}) => as === 'a' && css`
    color: blue;
    background: white;
    cursor: pointer;
    text-decoration: underline;

    &:after {
      content: " 🔗";
    }
  `}
`;

const MyApp = () => (
  <>
    <Button>Generic Button</Button>
    <Button as="a" href="#">Link Button</Button>
  </>
);
```

##### Output 💎

![6](https://user-images.githubusercontent.com/15273233/54862977-3d031480-4da7-11e9-82c2-8d344a8cb2a9.gif)

[🔽 Next](https://github.com/devonChurch/fish-pie#theming-)

.

.

.

.

.

.

.

.

.

.

## Theming ♻

_Light -vs- Dark, Cozy -vs Compact etc..._

##### Input ✏

```javascript
const bodyBackground = theme("mode", {
  light: "white",
  dark: "blue"
});

const GlobalStyle = createGlobalStyle`
  body {
    background: ${bodyBackground};
  }
`;

const buttonBackground = theme("mode", {
  light: "blue",
  dark: "white"
});

const buttonColor = theme("mode", {
  light: "white",
  dark: "blue"
});

const Button = styled.button`
  background: ${buttonBackground};
  border-radius: 0.2rem;
  color: ${buttonColor};
  padding: 0.5rem 1rem;
  font-size: 1rem;
`;

const MyApp = () => {
  const [isLight, setIsLight] = useState(true);
  return (
    <ThemeProvider theme={{ mode: isLight ? "light" : "dark" }}>
      <>
        <GlobalStyle />
        <Button onClick={() => setIsLight(!isLight)}>Toggle Theme</Button>
      </>
    </ThemeProvider>
  );
};
```

##### Output 💎

![7](https://user-images.githubusercontent.com/15273233/54863399-1051fb80-4dad-11e9-9849-1ab6b9229f02.gif)

[🔽 Next](https://github.com/devonChurch/fish-pie#polished-)

.

.

.

.

.

.

.

.

.

.

## [Polished](https://polished.js.org) 🌟

_SASS mixins, but in real time..._

### Color Transformations

- ✔ Is a color _Light_ or _Dark_
- ✔ Parse to `HSL` / `RGB` / `HEX`

### Measurement Transformations

- ✔ Isolate `value` and `unit`
- ✔ Add `CSS` values together

### General Helpers

- ✔ Create _retina_ image declaration
- ✔ Hide content _accessibly_

[🔽 Next](https://github.com/devonChurch/fish-pie#thanks-)

.

.

.

.

.

.

.

.

.

.

## Thanks 👍

_Any questions?..._

![](https://media.giphy.com/media/xQAkOKngoJXOw/giphy.gif)

[🔼 Back to Top](https://github.com/devonChurch/fish-pie#style-components-cliffs-notes)
