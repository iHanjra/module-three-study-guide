# React Forms

| Term | Definition |
| ---- | ---------- |
| __Controlled components__ | React inputs that are controlled by React state, ensuring that the state and view are synchronized. |
| __Uncontrolled components__ | Inputs in React that are not explicitly controlled by React, meaning their state is managed by the browser rather than React. |

---

## Checkboxes

- What is `checked={checked}` doing? Passing the default state to the input element 
- What is `setChecked(!checked)` doing? Changing state to true
- What happens if we forget the `onChange` event listener? Nothing will happen when the user clicks on checkbox. React will throw an error.
- What's controlling the checkbox: React or the Browser? React because it's controlled by state.

```js
// State
const [checked, setChecked] = useState(false);

// Event Handler
function handleCheckboxChange() {
  setChecked(!checked);
}

// JSX
<input type="checkbox" checked={checked} onChange={handleCheckboxChange} />
```

## Select Dropdowns

- What is the default value of `selectOption`? Why? Empty because the default state was set to empty string.
- Why are we setting the `selectOption` to `event.target.value`? 
- The option value `cats` doesn't match the option display `Cats!`. Is that ok? Yes because the value is the only that 

```js
// State
const [selectOption, setSelectOption] = useState("");

// Event Handler
function handleSelectChange(event) {
  setSelectOption(event.target.value);
}

// JSX
<select value={selectOption} onChange={handleSelectChange}>
  <option value=""></option>
  <option value="cats">Cats!</option>
  <option value="dogs">Dogs!</option>
</select>
```

## Text Inputs

- What is missing from this text input? value={nickName}. also needs name and id.
- When does the `onChange` event trigger? Whenever the user types into the form field.

```js
// State
const [nickName, setNickName] = useState("");

// Event Handler
function handleNickNameChange(event) {
  setNickName(event.target.value);
}

// JSX
<input type="text" onChange={handleNickNameChange} />
```

## Form Submission

- When does the `onSubmit` event trigger? When the user clicks on submit.
- What does `event.preventDefault()` do? Stop the page from reloading on submit, reset the form, or add form info to url.

```jsx
// Event Handler
function handleSubmit(event) {
  event.preventDefault();
  console.log("form submitted");
}

// JSX
<form onSubmit={handleSubmit}>
  <input type="submit" />
</form>
```

## Multiple text inputs with a shared change handler

- What data type is the `user` state? Object
- Why are we using curly braces when we invoke `setUser({...})`? Creates a new object
- What does `...user` accomplish? The key value pairs from the original user is added to the new user object
- What's is this `[event.target.id]: event.target.value` doing? Updating the key value pairs in the new user object.
- What other input attribute could you use instead of `id`? Name

```js
// State
const [user, setUser] = useState({
  firstName: "",
  lastName: "",
  zip: "",
  email: "",
  password: "",
});

// Event Handler
function handleTextChange(event) {
  setUser({
    ...user,
    [event.target.id]: event.target.value,
  });
}

// JSX
<form onSubmit={handleSubmit}>
  <input type="text" value={user.firstName} onChange={handleTextChange} id="firstName" />
  <input type="text" value={user.lastName} onChange={handleTextChange} id="lastName" />
  <input type="number" value={user.zip} onChange={handleTextChange} id="zip" />
  <input type="email" value={user.email} onChange={handleTextChange} id="email" />
  <input type="password" value={user.password} onChange={handleTextChange} id="password" />
  <input type="submit" />
</form>
```

## Resetting the form

- What is the `resetForm()` doing to the state?
- Are we updating the object directly? How can you tell?

```js
function resetForm() {
  setUser({
    firstName: "",
    lastName: "",
    zip: "",
    email: "",
    password: "",
  });
}

function handleSubmit(event) {
  event.preventDefault();
  console.log("form submitted");
  resetForm();
}
```
