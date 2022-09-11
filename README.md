## Usage

First, install `cc-js-abdal` as a dependency:

```shell
npm install --save cc-js-abdal
```

Then, use it in your project:

```react
import { initCC } from "cc-js-abdal";

// Call initCC(your_site_id) in the ComponentDidMount of any component which you want to track.
// You can call initCC() in the index.js or app.js once to track whole project.
// pass your site_id to initCC(your_site_id).

// Class Component
    componentDidMount(){
       initCC(your_site_id); 
    };
// Functional Component
    useEffect(() => {
      initCC(your_site_id);
    }, []);
    
// Create your form
// Add property "name" to your <form> tag, 
   *Note: your form name must contains "signup" word, examples: signup-form, my-signup, ...
   *Note: DO NOT USE SPACE OR DASH FOR "SIGNUP" (sign-up and sign up are not allowed)
// Add custome-attribute="include-form-tracking" to the form which you want to track.
// Add custome-attribute="include-content-tracking" to the input which you want to track its content.
   *NOTE: your signup form must include an input with the name="email" (do not use "username", etc)
   *NOTE: you must add custome-attribute="include-content-tracking" for the email field
   *NOTE: its ok to not include content of private fields like password, etc
// Add custom-attribute="form-submit" or type="submit" to the submit button.
// Use onSubmit={submitHandler} for you button NOT onClick.

import { useState, useEffect } from "react";
import { initCC } from "cc-js-abdal";

const initialState = {
  name: "",
  family_name: "",
  username: "",
  email: "",
};

const Form = () => {
  const [state, setState] = useState(initialState);
    
   useEffect(() => {
    initCC(187);
   }, []);
   
  const handleChange = (event) => {
    let name = event.target.name;
    let value = event.target.value;
    setState((prevState) => ({
      ...prevState,
      [name]: value,
    }));
  };

  const handleSubmit = (event) => {
    event.preventDefault();
  };

  return (
    <div>
      <form
        id="signup"
        onSubmit={handleSubmit}
        custom-attribute="include-form-tracking"
      >
        <label>Name: </label>
        <input
          custom-attribute="include-content-tracking"
          type="text"
          name="name"
          onChange={handleChange}
        />

        <div style={{ width: "100%" }}></div>

        <label>Family Name: </label>
        <input
          custom-attribute="include-content-tracking"
          type="text"
          name="family_name"
          onChange={handleChange}
        />

        <div style={{ width: "100%" }}></div>

        <label>Username: </label>
        <input
          custom-attribute="include-content-tracking"
          type="text"
          name="username"
          onChange={handleChange}
        />

        <div style={{ width: "100%" }}></div>

        <label>email: </label>

        <input
          custom-attribute="include-content-tracking"
          type="email"
          name="email"
          onChange={handleChange}
        />

        <div style={{ width: "100%" }}></div>

        <button custom-attribute="form-submit">submit</button>
      </form>
    </div>
  );
};

export default Form;

```
Other Examples (MUI and etc)
```
*If you are not using pure HTML tags, consider adding the mentioned attributes to the main HTML tags (form, input and button).
 Pay attention to the following example of MUI TextField.
 
     <TextField
      //add properties here
      inputProps={{
        "custom-attribute": "include-content-tracking",
        name: "email",
      }}
      //add properties here
      type="text"
      value={values.username}
      onChange={handleChange)}
      label="email"
    />

```
That's it.

