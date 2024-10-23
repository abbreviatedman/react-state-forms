# State Forms - Lab

**Objective:**

Learn how to use `useState` to manage form state in React and dynamically render a Contact Card with the entered data. This assignment will guide you through creating a form, managing its state, and displaying the form data in a styled Contact Card using Bootstrap.

**Requirements:**

1. **Application Structure:**

- **App Component:** The main component where the form will be managed and the Contact Card will be displayed.
- **Form Component:** A component to handle the form inputs and submission.
- **Contact Card Component:** A component to display the entered form data as a contact card.

2. **Form State Management:**

- Use state to manage form fields.
- Optional but recommended: Manage all form fields in a single state object.

### Steps

1. **Set Up Your Project:**

- Ensure you have a React project set up. If not, create one using `create-react-app`.

2. **Install Bootstrap:**

- In the terminal, install Bootstrap by running:

```bash
npm install bootstrap
```

- Import Bootstrap into your project. In **/src/index.js** or **/src/App.js**, add the following line:

```javascript
import "bootstrap/dist/css/bootstrap.min.css";
```

3. **Create the Form Component:**

- In the **/src/** folder, create a new file named `Form.js`.
- Inside this file, define a functional component named `Form`.
- Add a form structure (the HTML is below) with fields for:
  - Name
  - Email
  - Age
  - Gender (with inclusive options)
  - Whether to subscribe the user to a newsletter.

Here’s the HTML structure for the form:

```html
<form>
  <div>
      <label>Name:</label>
      <input type="text" name="name" />
  </div>
  <div>
      <label>Email:</label>
      <input type="email" name="email" />
  </div>
  <div>
      <label>Age:</label>
      <input type="number" name="age" />
  </div>
  <div>
      <label>Gender:</label>
      <div>
          <label>
              <input type="radio" name="gender" value="male" /> Male
          </label>
          <label>
              <input type="radio" name="gender" value="female" /> Female
          </label>
          <label>
              <input type="radio" name="gender" value="non-binary" /> Non-binary
          </label>
          <label>
              <input type="radio" name="gender" value="prefer-not-to-say" /> Prefer not to say
          </label>
      </div>
  </div>
  <div>
      <label>Subscribe to newsletter:</label>
      <input type="checkbox" name="isSubscribed" />
  </div>
  <button type="submit">Submit</button>
</form>
```

4. **Initialize State for the Form Fields:**

- Inside the `Form` component, use `useState` to create a state object to manage all form fields:
  - `name`
  - `email`
  - `age`
  - `gender`
  - `isSubscribed`
- Either define a separate function to handle a change in each one, updating the state for that field, or define a single dynamic handler function to update the state based on the form field name and value.

5. **Handle Form Submission:**

In the App component:

- Define a function to handle form submission. For now, this function should _just_ a) prevent the default form action and b) log the form data to the console.
- Render the `Form` component and pass down the above function as a prop.

6. **Create the Contact Card Component:**

- In the **/src/** folder, create a new file named `ContactCard.js`.
- Inside this file, define a functional component named `ContactCard`.
- This component will receive the form data as props and display it in a styled contact card format using Bootstrap.

7. **Define the Contact Card Structure:**

In the Contact Card component, take the data in as props and display it in interface elements for the following fields:

- Name
- Email
- Age
- Gender
- Subscribe to newsletter status

8. **Update the Form Submission Handler:**

In the Form component:

- Set the form submission handler function to call App's function, which should be on the props object.
- In the `App` component, change the form submission function so that instead of logging the data, it passes it down as props to the `ContactCard` component.

9. **Render the Contact Card:**

- In the `App` component, render the `ContactCard` component. Don't render it if there is no submitted form data (i.e., conditionally render it)
- Use Bootstrap classes to style the card, making it visually appealing.

10. **Check Your Browser:**

- Save all your files and check your browser. You should be able to enter data into the form, submit it, and see it displayed in a styled contact card format.
