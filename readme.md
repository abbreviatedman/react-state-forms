Assignment: Using useState with a Form
Objective: Learn how to use useState to manage form state in React. This assignment will show you how to refactor from multiple state variables to a single state object, and from separate handlers for each form field to a single dynamic handler.

Requirements:

Application Structure:

App Component: The main component where the form will be managed.

Form Component: A component to handle the form inputs and submission.

Form State Management:

Use useState to manage the form state as an object.

Use a single dynamic handler to update form fields.

Steps:
Set Up Your Project:

Make sure you have a React project set up. If not, create one using create-react-app.

Open /src/App.js:

Delete everything inside this file.

Import React and create a functional component named App. Don’t forget to export it.

```jsx
import React from 'react';

function App() {
    return <div className="App"></div>;
}

export default App;
```

Create the Form Component:

In the /src/ folder, create a new file named Form.js.

Import React and create a function called Form that returns a form structure inside of parentheses. Don’t forget to export the function at the bottom of the file.

```jsx
import React from 'react';

function Form() {
    return (
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
                <input type="checkbox" name="subscribe" />
            </div>
            <button type="submit">Submit</button>
        </form>
    );
}

export default Form;
```

Initialize State for Each Form Field:

In /src/Form.js, import useState from React and create state variables for each form field.

```jsx
import React, { useState } from 'react';

function Form() {
    const [name, setName] = useState('');
    const [email, setEmail] = useState('');
    const [age, setAge] = useState('');
    const [gender, setGender] = useState('');
    const [subscribe, setSubscribe] = useState(false);

    return (
        <form>
            <div>
                <label>Name:</label>
                <input type="text" name="name" value={name} onChange={(e) => setName(e.target.value)} />
            </div>
            <div>
                <label>Email:</label>
                <input type="email" name="email" value={email} onChange={(e) => setEmail(e.target.value)} />
            </div>
            <div>
                <label>Age:</label>
                <input type="number" name="age" value={age} onChange={(e) => setAge(e.target.value)} />
            </div>
            <div>
                <label>Gender:</label>
                <div>
                    <label>
                        <input type="radio" name="gender" value="male" checked={gender === 'male'} onChange={(e) => setGender(e.target.value)} /> Male
                    </label>
                    <label>
                        <input type="radio" name="gender" value="female" checked={gender === 'female'} onChange={(e) => setGender(e.target.value)} /> Female
                    </label>
                    <label>
                        <input type="radio" name="gender" value="non-binary" checked={gender === 'non-binary'} onChange={(e) => setGender(e.target.value)} /> Non-binary
                    </label>
                    <label>
                        <input type="radio" name="gender" value="prefer-not-to-say" checked={gender === 'prefer-not-to-say'} onChange={(e) => setGender(e.target.value)} /> Prefer not to say
                    </label>
                </div>
            </div>
            <div>
                <label>Subscribe to newsletter:</label>
                <input type="checkbox" name="subscribe" checked={subscribe} onChange={(e) => setSubscribe(e.target.checked)} />
            </div>
            <button type="submit">Submit</button>
        </form>
    );
}

export default Form;
```

Render the Form Component:

In /src/App.js, import the Form component and render it inside the App component.

```jsx
import React from 'react';
import Form from './Form';

function App() {
    return (
        <div className="App">
            <Form />
        </div>
    );
}

export default App
```
