# React State Forms

### Steps

1. **Set Up Your Project:**

- Ensure you have a React project set up. If not, create one using `create-react-app`.

```bash
npx create-react-app my-app
cd my-app
```

- Open `/src/App.js`: This file is an example component that `create-react-app` starts with. You can delete everything in this file. Then at the top of the file, import React and create a functional component named `App`. Don't forget to export it.

```jsx
import React from 'react';

function App() {
    return <div className="App"></div>;
}

export default App;
```

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

```jsx
import React from 'react';

function Form() {
    return (
        <form>
            <div>
                <label>Recipient's Name:</label>
                <input type="text" name="recipientName" />
            </div>
            <div>
                <label>Sender's Name:</label>
                <input type="text" name="senderName" />
            </div>
            <div>
                <label>Message:</label>
                <textarea name="message"></textarea>
            </div>
            <div>
                <label>Occasion:</label>
                <select name="occasion">
                    <option value="Birthday">Birthday</option>
                    <option value="Anniversary">Anniversary</option>
                    <option value="Holiday">Holiday</option>
                </select>
            </div>
            <div>
                <label>Include Personal Note:</label>
                <input type="checkbox" name="includePersonalNote" />
            </div>
            <button type="submit">Submit</button>
        </form>
    );
}

export default Form;
```

4. **Initialize State for the Form Fields:**

- Inside the `Form` component, use `useState` to create a state object to manage all form fields:
  - `recipientName`
  - `senderName`
  - `message`
  - `occasion`
  - `includePersonalNote`
- Define a single dynamic handler function to update the state based on the form field name and value.

```jsx
import React, { useState } from 'react';

function Form() {
    const [formData, setFormData] = useState({ recipientName: '', senderName: '', message: '', occasion: 'Birthday', includePersonalNote: false });

    const handleChange = (e) => {
        const { name, value, type, checked } = e.target;
        setFormData({
            ...formData,
            [name]: type === 'checkbox' ? checked : value,
        });
    };

    return (
        // The rest of the form structure with each input using handleChange and accessing the appropriate field in formData
    );
}

export default Form;
```

5. **Handle Form Submission:**

- Define a function to handle form submission. This function should prevent the default form action and log the form data to the console for now.
- In the `App` component, render the `Form` component and pass down a function to handle the submission.

```jsx
import React from 'react';
import Form from './Form';

function App() {
    const handleFormSubmit = (formData) => {
        console.log(formData);
    };

    return (
        <div className="App">
            <Form onSubmit={handleFormSubmit} />
        </div>
    );
}

export default App;
```

Update the `Form` component to call the `onSubmit` prop on form submission:

```jsx
import React, { useState } from 'react';

function Form({ onSubmit }) {
    const [formData, setFormData] = useState({ recipientName: '', senderName: '', message: '', occasion: 'Birthday', includePersonalNote: false });

    const handleChange = (e) => {
        const { name, value, type, checked } = e.target;
        setFormData({
            ...formData,
            [name]: type === 'checkbox' ? checked : value,
        });
    };

    const handleSubmit = (e) => {
        e.preventDefault();
        onSubmit(formData);
    };

    return (
        <form onSubmit={handleSubmit}>
            <div>
                <label>Recipient's Name:</label>
                <input type="text" name="recipientName" value={formData.recipientName} onChange={handleChange} />
            </div>
            <div>
                <label>Sender's Name:</label>
                <input type="text" name="senderName" value={formData.senderName} onChange={handleChange} />
            </div>
            <div>
                <label>Message:</label>
                <textarea name="message" value={formData.message} onChange={handleChange}></textarea>
            </div>
            <div>
                <label>Occasion:</label>
                <select name="occasion" value={formData.occasion} onChange={handleChange}>
                    <option value="Birthday">Birthday</option>
                    <option value="Anniversary">Anniversary</option>
                    <option value="Holiday">Holiday</option>
                </select>
            </div>
            <div>
                <label>Include Personal Note:</label>
                <input type="checkbox" name="includePersonalNote" checked={formData.includePersonalNote} onChange={handleChange} />
            </div>
            <button type="submit">Submit</button>
        </form>
    );
}

export default Form;
```

6. **Create the Greeting Card Component:**

- In the **/src/** folder, create a new file named `GreetingCard.js`.
- Inside this file, define a functional component named `GreetingCard`.
- This component will receive the form data as props and display it in a styled greeting card format using Bootstrap.

```jsx
import React from 'react';

function GreetingCard({ recipientName, senderName, message, occasion, includePersonalNote }) {
    return (
        <div className="card">
            <div className="card-body">
                <h5 className="card-title">Greeting Card</h5>
                <h6 className="card-subtitle mb-2 text-muted">{occasion}</h6>
                <p className="card-text">{message}</p>
                <footer className="blockquote-footer">
                    From: {senderName}
                    {includePersonalNote && <small className="d-block mt-2">Personal Note: Have a wonderful day!</small>}
                </footer>
            </div>
        </div>
    );
}

export default GreetingCard;
```

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

```jsx
import React, { useState } from 'react';
import Form from './Form';
import GreetingCard from './GreetingCard';

function App() {
    const [submittedData, setSubmittedData] = useState(null);

    const handleFormSubmit = (formData) => {
        setSubmittedData(formData);
    };

    return (
        <div className="App container">
            <Form onSubmit={handleFormSubmit} />
            {submittedData && <GreetingCard {...submittedData} />}
        </div>
    );
}

export default App;
```

9. **Render the Greeting Card:**

- In the `App` component, conditionally render the `GreetingCard` component only if there is submitted form data.
- Use Bootstrap classes to style the card, making it visually appealing.

```jsx
import React, { useState } from 'react';
import Form from './Form';
import GreetingCard from './GreetingCard';

function App() {
    const [submittedData, setSubmittedData] = useState(null);

    const handleFormSubmit = (formData) => {
        setSubmittedData(formData);
    };

    return (
        <div className="App container">
            <Form onSubmit={handleFormSubmit} />
            {submittedData && <GreetingCard {...submittedData} />}
        </div>
    );
}

export default App;
```

9. **Render the Greeting Card:**

- In the `App` component, conditionally render the `GreetingCard` component only if there is submitted form data.
- Use Bootstrap classes to style the card, making it visually appealing.

```jsx
import React, { useState } from 'react';
import Form from './Form';
import GreetingCard from './GreetingCard';

function App() {
    const [submittedData, setSubmittedData] = useState(null);

    const handleFormSubmit = (formData) => {
        setSubmittedData(formData);
    };

    return (
        <div className="App container">
            <Form onSubmit={handleFormSubmit} />
            {submittedData && <GreetingCard {...submittedData} />}
        </div>
    );
}

export default App;
```

10. **Check Your Browser:**

- Save all your files and check your browser. You should be able to enter data into the form, submit it, and see it displayed in a styled greeting card format.
