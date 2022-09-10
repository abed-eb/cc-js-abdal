# Matomo Tracker [![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url]

> A wrapper for the Matomo Tracking HTTP API

## Usage

First, install `matomo-tracker` as a dependency:

```shell
npm install --save cc-js-abdal
```

Then, use it in your project:

```react
import { initCC } from "cc-js-abdal";

// Call initCC in the ComponentDidMount of the component which you want to track or call it in index.js or App.js once. Also, pass your site_id to it.

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
     <form
        id="signup"
        onSubmit={handleSubmit}
        custom-attribute="include-form-tracking"
      >
        <label>
          Name:
          <input
            custom-attribute="include-content-tracking"
            type="text"
            name="name"
            onChange={handleChange}
          />
        </label>
        <div style={{ width: "100%" }}></div>
        <label>
          Family Name:
          <input
            custom-attribute="include-content-tracking"
            type="text"
            name="family_name"
            onChange={handleChange}
          />
        </label>
        <div style={{ width: "100%" }}></div>
        <label>
          Username:
          <input
            custom-attribute="include-content-tracking"
            type="text"
            name="username"
            onChange={handleChange}
          />
        </label>
        <div style={{ width: "100%" }}></div>
        <label>
          email:
          <input
            custom-attribute="include-content-tracking"
            type="email"
            name="email"
            onChange={handleChange}
          />
        </label>
        <div style={{ width: "100%" }}></div>
        <button custom-attribute="form-submit" type="submit">
          submit
        </button>
      </form>

```

That's it.
```
