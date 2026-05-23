# Lab: Form Storage

## Overview
This app demonstrates a custom React hook (`useLocalStorage`) that persists form data in the browser's local storage. Built for a repair company, the form retains user input between page refreshes without storing sensitive data in a backend database.

## Screenshot

![App Screenshot](./screenshot.png)

## Setup

Run `npm install` to install dependencies.

Start the app:

```bash
npm run dev
```

Run the test suite:

```bash
npm run test
```

## Features

- **Persistent form data** — Input data is saved to localStorage and restored on page refresh.
- **Custom hook** — `useLocalStorage` abstracts all localStorage read/write logic into a reusable hook.
- **No backend required** — Data is stored client-side only.

## Custom Hook: `useLocalStorage`

Located in `src/hooks/useLocalStorage.js`.

```js
useLocalStorage(key, initialValue)
```

| Parameter | Type | Description |
|---|---|---|
| `key` | string | The localStorage key to read/write |
| `initialValue` | any | Fallback value if no localStorage data exists (defaults to `null`) |

Returns `[state, setState]` — same API as `useState`, but synced to localStorage.

## How It Works

1. On mount, the hook checks localStorage for an existing value under the given key.
2. If found, it initializes state with that value. If not, it uses `initialValue`.
3. A `useEffect` watches for state changes and writes the updated value back to localStorage.
4. The form fields (`name` and `serviceNumber`) each use the hook with their respective keys.

## Tools and Resources

- [React Custom Hooks](https://react.dev/learn/reusing-logic-with-custom-hooks)
- [MDN localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)

## Best Practices
- Custom hook encapsulates all localStorage logic — components stay clean.
- No unnecessary console logs or commented-out code.
- Sensitive data never sent to a backend.

## Submission
Once all tests pass and code is pushed to GitHub, submit the repo through Canvas using CodeGrade.