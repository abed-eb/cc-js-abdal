## Usage

First, install `matomo-tracker` as a dependency:

```shell
npm install --save cc-js-abdal
```

Then, use it in your project:

```react
import { initCC } from "cc-js-abdal";

// Call initCC() in the ComponentDidMount of the component which you want to track.
// You can call initCC() in the index.js or app.js once to track whole project.
// pass your site_id to initCC().

// Class Component
    componentDidMount(){
       initCC(your_site_id); 
    };
// Functional Component
    useEffect(() => {
      initCC(your_site_id);
    }, []);
    
// Create your form
// Add id="signup" to the form
// Add custome-attribute="include-form-tracking" to the form which you want to track.
// Add custome-attribute="include-content-tracking" to the input which you want to track.
// Add custom-attribute="form-submit" to the submit button.

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

That's it.
```
