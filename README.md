# A reducer for redux which shares data

Sharing data between slice reducers in Redux can cause some troubles. With this package you can easily share
data beween reducers.

## Installation

To install the latest version of shared-combine-reducers:
```
npm install shared-combine-reducers --save
```

## Usage

Replace:

```javascript
import { combineReducers } from 'redux'
  
const rootReducer = combineReducers({
    reducerA,
    reducerB,
    reducerC
});
```

with:

```javascript
import sharedCombineReducers from 'shared-combine-reducers'
  
const rootReducer = sharedCombineReducers({
    reducerA,
    reducerB,
    reducerC
});
```

in each reducer you now have access to the full previous state and a partial next state:

```javascript
const reducerC = (state, action, previousFullState, nextState) => {
    
    switch(action.type) {
        case 'ACTION_X1':
            const stateA = nextState.reducerA
            
            // ..
            
            
            return newState
        default:
            return state    
    }
}
```

