## Implementing hooks & context API into react application

This is a tutorial of how to implement hooks and the context API into your react applicaton. This implementation schema is the same used by Brad Traversy on React Front to Back udemy course.



###### The tag <resource> is used as placeholder.



Here are basic steps to start implementing this solution:

* [ ] Create context folder
* [ ] separate resources 
* [ ] create <resource>Context, <resource>State and <resource>Reducer
* [ ] Create Types for actions that change state
* [ ] Wrap application in <resource>State



#### Initializing <resource>Context :

This file is just for initialization of context.

```javascript
import { createContext } from "react";

const <resource>Context = createContext();

export default <resource>Context;
```



#### Initializing <resource>State :

In this file you can define actions (functions) for do something that will return data that will be insert into the state. Also in this file we need to initialize your initial state, declaring all the fields we need and assign default values to them.

```javascript
import React, { useReducer } from "react";
import <resource>Context from "./<resource>Context";
import <resource>Reducer from "./<resource>Reducer";
import { <types> } from "../types"

const <resource>State = props => {
    const initialState = {
    	// Where you define your state
	}
    
    const [state, dispatch] = useReducer(<resource>Reducer, initialState);
    
    // Actions (functions)
    // Functions here need to return an function dispatch with object, 
    // and the object need and type: <type_imported>,
    // and a payload with data if needed: payload: data
    // example using user
    dispatch({
        type:ADD_USER, // imported type from types file
        payload: data // this data will put in state by the reducer
    });
    
    // Return provider where will be set values avaliable in the application
    // example using AppicationContext for context
    
    return <ApplicationContext.Provider
    		value={{
               	// example using users
               	// the first field is the name we will use in our application
               	// second field points to state for the value
               	users: state.users
              }}
    		>
                {props.children}
        </ApplicationContext.Provider>
}

export default <resource>State;
```



#### Initializing <resource>Reducer : 

In this file we change the state, or from data sent by actions (functions) in <resource>State, or manually.

```javascript
import { <types> } from "../types";

export default (state, action) => {
    switch(action.type){ //Create a case using the types
        case <type>:
            return {
            	...state, // Always spread the state, the state is immutable
            	// examples using received data from actions in <resource>State
            	// and if you want to set an piece of state manually
            	<var_on_State>: action.payload, // If data is provided
                <var_on_State>: true
    		};
        default:
            return state;
    }
}
```



#### Create Types :

You should have in this file every action(Function) that changes your state to use in the <resource>Reducer file.

In this example we will use a SEARCH_USERS example for implementation.

```javascript
export const SEARCH_USERS = "SEARCH_USERS";
```



#### Implementing in your application :

First you import the context, then initializing. It can be deconstructed.

```javascript
import React, { useContext } from "react";
import <resource>Context from "<path_to_context_file>";

const App = () => {
    // Initializing the context
    const <resource>Context = useContext(<resource_context_imported>);
    
    return(
    	// Elements to be rendered
    )
};

export default App;
```

