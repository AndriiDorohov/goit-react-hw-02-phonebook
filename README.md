# Phonebook

Create an application for storing contacts in a phonebook.

## Step 1

The application should consist of a form and a list of contacts. At this stage, implement adding a contact's name and displaying the list of contacts. The application should not retain contacts between different sessions (page refreshes).

Use this input markup with built-in validation for the contact's name.

```html
<input
  type="text"
  name="name"
  pattern="^[a-zA-Zа-яА-Я]+(([' -][a-zA-Zа-яА-Я ])?[a-zA-Zа-яА-Я]*)*$"
  title="Name may contain only letters, apostrophe, dash, and spaces."
  required
/>
```

The state stored in the parent component <App> must look like this, and adding new properties is not allowed.

```bash
state = {
  contacts: [],
  name: ''
}
```

Each contact should be an object with properties `name` and `id`. Use any suitable package like [nanoid](https://www.npmjs.com/package/nanoid) to generate identifiers. After completing this step, the application should look something like this.

![preview](./mockup/step-1.png)

## Step 2

Enhance the application's functionality by allowing users to add phone numbers. To achieve this, add `<input type="tel">` to the form and a property to store its value in the state.

```bash
state = {
  contacts: [],
  name: '',
  number: ''
}
```

Use this input markup with built-in validation for the contact number.

```html
<input
  type="tel"
  name="number"
  pattern="\+?\d{1,4}?[-.\s]?\(?\d{1,3}?\)?[-.\s]?\d{1,4}[-.\s]?\d{1,4}[-.\s]?\d{1,9}"
  title="Phone number must be digits and can contain spaces, dashes, parentheses and can start with +"
  required
/>
```

After completing this step, the app should look something like this.

![preview](./mockup/step-2.png)

## Step 3

Add a search field that can be used to filter the list of contacts by name.

- The search field is an input without a form, and its value is stored in the state (a controlled component).
- The filtering logic should be case-insensitive.


```bash
state = {
  contacts: [],
  filter: '',
  name: '',
  number: ''
}
```

![preview](./mockup/step-3.gif)

When working on new functionality, it can be convenient to hardcode certain data into the state. This eliminates the need to manually input data into the interface for testing the new functionality. For instance, you can use such an initial state.

```bash
state = {
  contacts: [
    {id: 'id-1', name: 'Rosie Simpson', number: '459-12-56'},
    {id: 'id-2', name: 'Hermione Kline', number: '443-89-12'},
    {id: 'id-3', name: 'Eden Clements', number: '645-17-79'},
    {id: 'id-4', name: 'Annie Copeland', number: '227-91-26'},
  ],
  filter: '',
  name: '',
  number: ''
}
```

## Step 4

If your application is implemented within a single `<App>` component, refactor by extracting relevant parts into separate components. Only the properties `contacts` and `filter` should remain in the state of the root `<App>` component.

```bash
state = {
  contacts: [],
  filter: ''
}
```

To refactor, just distinguish four components: contact form, contact list, contact list item, and search filter.

After the refactoring, the root component of the program will look like this.


```jsx
<div>
  <h1>Phonebook</h1>
  <ContactForm ... />

  <h2>Contacts</h2>
  <Filter ... />
  <ContactList ... />
</div>
```
## Step 5

Prohibit the user from adding contacts whose names are already present in the phone book. When attempting to perform such an action, display an `alert` with a warning.

![preview](./mockup/step-5.png)

## Step 6

Expand the application's functionality by allowing the user to delete previously saved contacts.

![preview](./mockup/step-6.gif)
