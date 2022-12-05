# 20221205 工作筆記

## React Hooks

> A Hook is a special function that lets you "hook into" React features. `useState` is a Hook that lets you add React state to function components.

If we need to add some to it, previously you had to convert it to a class. Now you can use a Hook inside the existing function.

### useEffect

> `useEffect` is a hook lets you synchronize a component with an external system.

```javascript
useEffect(setup, dependencies?)
```

Usage

- Connecting to an external system
- Wrapping Effects in custom Hooks
- Controlling a non-React widget
- Fetching data with Effects
- Specifying reactive dependencies
- Updating state based on previous state from an Effect
- Removing unnecessary object and function dependencies
- Reading the latest props and state from an Effect
- Displaying different content on the server and the client

### useRef(待補)

### useMemo(待補)

### 參考文章

- [Using the State Hook](https://reactjs.org/docs/hooks-state.html)

---
