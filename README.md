# MUIPlacesAutocomplete
[![Travis CI](https://img.shields.io/travis/Giners/mui-places-autocomplete/master.svg)](https://travis-ci.org/Giners/mui-places-autocomplete/builds)

# Features
* Easy to use input for searching for places
* Place suggestions displayed in realtime
* Google Material Design styling provided by next version of Material-UI (v1)
* Safe to render on the server (SSR)
* Thoroughly tested

# Installation
To install this component run the following command:

```
yarn add mui-places-autocomplete --ignore-scripts
```

or

```
npm install mui-places-autocomplete --save --ignore-scripts
```

Note that if you exclude the `--ignore-scripts` option when installing a package then the `prepublish` script in `package.json` is ran after installing locally. Tests are ran as part of the `prepublish` script and they will fail if you haven't yet set a Google API key to the enivronment variable `GOOGLE_API_KEY` (see [setup section](#setup)).

# Demo
**Note that you must have followed the [setup steps](#setup) to run the demo as it depends on services provided by Google.**

To see a demo of this component locally clone this repository and run:

```
yarn demo
```

or

```
npm run demo
```

# Usage
```javascript
import React from 'react'
import SomeCoolComponent from 'some-cool-component'
import MUIPlacesAutocomplete from 'mui-places-autocomplete'

class Example extends React.Component {
  constructor() {
    super()

    this.onSuggestionSelected = this.onSuggestionSelected.bind(this)
  }

  onSuggestionSelected(suggestion) {
    // Add your business logic here. In this case we just log...
    console.log('Selected suggestion:', suggestion)
  }

  render() {
    // Use 'renderTarget' prop to render a component/target we want the suggestions to popover

    return (
      <MUIPlacesAutocomplete
        onSuggestionSelected={this.onSuggestionSelected}
        renderTarget={() => (<SomeCoolComponent />)}
      /> 
    )
  }
}

export default Example
```

<a name="setup"></a>
### Setup
This component relies on some basic setup before usage. It makes use of services provided by Google. To properly make use of the services you will need to do three things:
1. Enable the Google Places API Web Service
2. Enable the Google Maps JavaScript API
3. Obtain a Google API key

You can do all of these things from your Google developers console here: https://console.developers.google.com

The component relies on the Places library in the Google Maps JavaScript API. To load the Places library on the client you must add the following to the HTML document you deliver to your clients:

```html
<script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places"></script>
```

Be sure that you replace `YOUR_API_KEY` with the one you just created or obtained previously.

This component also has testing which makes use of the Places library in the Google Maps JavaScript API. Rather than loading the Places library it uses a module provided by Google. It also requires an API key. This key can be provided to a file @ `test/api-key.js`. If you would like it can also be provided as an environment variable named `GOOGLE_API_KEY`.

### Props

| Prop | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| [`onSuggestionSelected`](#onSuggestionSelected) | Function | ✓ | Callback that provides the selected suggestion. |
| [`renderTarget`](#renderTarget) | Function | ✓ | Renders the components/elements that you would like to have the list of suggestions popover. |

<a name="onSuggestionSelected"></a>
#### onSuggestionSelected (required)

This function will be called everytime a user has selected a suggestion. It has the following signature:

```javascript
function onSuggestionSelected(suggestion)
```

<a name="renderTarget"></a>
#### renderTarget (required)

This function is invoked during rendering. It ought to return the components/elements that you want the list of suggestions to render (pop) over.

# Feedback
This was my first open-source project that I undertook while I was teaching myself full-stack development (JS (ES6)/HTML/CSS, Node, Express, NoSQL (DynamoDB), GraphQL, React, Redux, Material-UI, etc.). I'm very interested in taking feedback to either improve my skills (i.e. correct errors :)) or to make this component more useful in general/for your use case. Please feel free to provide feedback by opening an issue or messaging me.

# References
* Info about the Google Maps JavaScript API: https://developers.google.com/maps/documentation/javascript/libraries
* Overview and examples for the Autocomplete features in the Places library: https://developers.google.com/maps/documentation/javascript/places-autocomplete

# License
[MIT](https://gine.mit-license.org/)
