# State Forms - Lab

### Steps

1. **Set Up Your Project:**

Ensure you have a React project set up. If not, create one using `create-react-app`.

2. **Install Bootstrap:**

- In the terminal, install Bootstrap by running:

```bash
npm install bootstrap
```

- Import Bootstrap into your project. In **/src/index.js** or **/src/App.js**, add the following line:

```javascript
import 'bootstrap/dist/css/bootstrap.min.css';
```

3. **Create the Form Component:**

- In the **/src/** folder, create a new file named `Form.js`.
- Inside this file, define a functional component named `Form`.
- Add a form structure with fields for:
  - Recipient's Name
  - Sender's Name
  - Message
  - Occasion (with options like Birthday, Anniversary, Holiday, etc.)
  - Include Personal Note (checkbox)

4. **Initialize State for the Form Fields:**

- Inside the `Form` component, use `useState` to create a state object to manage all form fields:
  - `recipientName`
  - `senderName`
  - `message`
  - `occasion`
  - `includePersonalNote`
- Define a single dynamic handler function to update the state based on the form field name and value.

5. **Handle Form Submission:**

- Define a function to handle form submission. This function should prevent the default form action and log the form data to the console for now.
- In the `App` component, render the `Form` component and pass down a function to handle the submission.

6. **Create the Greeting Card Component:**

- In the **/src/** folder, create a new file named `GreetingCard.js`.
- Inside this file, define a functional component named `GreetingCard`.
- This component will receive the form data as props and display it in a styled greeting card format using Bootstrap.

7. **Define the Greeting Card Structure:**

- Structure the Greeting Card with Bootstrap classes. Include sections for:
  - Recipient's Name
  - Sender's Name
  - Message
  - Occasion
  - Whether a Personal Note is included

8. **Update the Form Submission Handler:**

- Modify the form submission handler to pass the form data up to the `App` component.
- In the `App` component, manage the state for the submitted form data and pass it down to the `GreetingCard` component.

9. **Render the Greeting Card:**

- In the `App` component, conditionally render the `GreetingCard` component only if there is submitted form data.
- Use Bootstrap classes to style the card, making it visually appealing.

10. **Check Your Browser:**

- Save all your files and check your browser. You should be able to enter data into the form, submit it, and see it displayed in a styled greeting card format.
