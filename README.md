## Usage

First, install `cc-js-abdal` as a dependency:

```shell
npm install --save cc-js-abdal
```

Then, use it in your project:

1. Call initCC(your_site_id) in the ComponentDidMount for any component which you want to track its form. 
   * initCC only loads and initialize our library, for adding trackers follow bellow steps
3. You can call initCC(your_site_id) in the index.js or app.js once.
4. Pass your site_id to initCC(your_site_id).
   * You can get your_site_id from app.crossclassify.com after creating a new app in your project.

```react
import { initCC } from "cc-js-abdal";

Class Components
componentDidMount(){
   //get your_site_id from app.crossclassify.com, after creating an app in a project
   initCC(your_site_id); 
};

Functional Components
useEffect(() => {
  // get your_site_id from app.crossclassify.com, after creating an app in a project
  initCC(your_site_id);
}, []);
```

4. Create your form.
5. Add property "name" to your <form> tag. 
   * Note: Your form name must contains "signup" word, examples: "signup-form", "my-signup", ... .
   * Note: DO NOT USE SPACE OR DASH FOR "SIGNUP" (sign-up and sign up are not allowed)
6. Add custom-attribute="include-form-tracking" to the form which you want to track.
7. Add custom-attribute="include-content-tracking" to the input which you want to track its content.
   * NOTE: Your signup form must include an input with the name="email" (do not use "username", etc)
   * NOTE: You must add custome-attribute="include-content-tracking" for the email field
   * NOTE: Its ok to not including content of private fields like password, etc.
8. Add custom-attribute="form-submit" or type="submit" to the submit button.
8. Use onSubmit={submitHandler} for you button NOT onClick={clickHandler}.
    
```
// Sample usage of the package
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
    // get your_site_id from app.crossclassify.com, after creating an app in a project
    initCC(your_site_id);
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

* If you are not using pure HTML tags (form, input and button), consider adding the mentioned attributes to the rendered HTML tags like using "inputProps".
 Pay attention to the following example of Matrial UI (MUI) "TextField".
```
   //simple MUI "textField" tracking integration
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
Now go to dashboard and check if your signup submits show in the "Registrations" menu
Congratulations! your done.

