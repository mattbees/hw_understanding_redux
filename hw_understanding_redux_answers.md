# Homework: Getting Familiar with Redux

### Learning Objectives
- Know Redux's data flow
- Be able to identify pure and impure functions
- Understand the relationship between actions, reducers, the store and state.

## Brief

So far we have looked at Redux the library, without using any front-end frameworks. Tomorrow we will be seeing how to use Redux in a React application, which will involve using another library. Your task for tonight is to make yourself as familiar with Redux as possible, so that when we add React into the mix, you are clear about the Redux's foundational principles.

Please submit answers the the questions below.

### MVP

#### Part 1

1. What are actions used for?
2. What type of object must an action be?
3. At a minimum, what is the one property the action should have? And what is this property used for?

Actions are sent by the UI. They call the store's dispatch method to return a simple JS object which has a 'type' property at minimum. This instructs the store to update the state accordingly using the reducer function.

4. What is the responsibility of the reducer?

The reducer sets the initial state. When an action signals that a state update is required, the reducer takes the action and the current state as arguments, and updates the state with a new state object as appropriate.

5. What is the responsibility of the store?

The store maintains the state.

#### Part 2

When working with Redux, the reducers must be pure functions. One of the qualities that makes a function pure is that is doesn't modify (or 'mutate') objects outside their scope. When a reducer is passed the state, it must not mutate the state, but instead return a newly created state object. Read the following page on common ways patterns for not mutating state in reducers:

[https://redux.js.org/recipes/structuring-reducers/immutable-update-patterns](https://redux.js.org/recipes/structuring-reducers/immutable-update-patterns)

Which of the following functions are pure:

```js
const reducer1 = (action, state) => {
  return state + 1;
}
// PURE

const reducer2 = (action, state) => {
  state.push("Cat");
  return state;
}
// IMPURE

const reducer3 = (action, state) => {
  return [...state, "Dog"];
}
// PURE

const reducer4 = (action, state) => {
  return state.map(pet => {
    pet.price /= 2;
    return pet;
  });
}
// PURE

const reducer5 = (action, state) => {
  return state.map(pet => {
    return { ...pet, pet.price: pet.price / 2 }
  });
}
// PURE
```

### Extensions

Do one (or all!) of the following:

- Create another Redux application from scratch.
- Add additional features the to applications we have been building today.
- Complete the [basics tutorial on the Redux website](https://redux.js.org/basics/basic-tutorial).
