# React useEffect Infinite Loop Bug
This repository demonstrates a common error in React's `useEffect` hook: creating an infinite loop by incorrectly managing dependencies.  The `bug.js` file shows the problematic code, while `bugSolution.js` provides the corrected version.

## Bug Description
The `useEffect` hook in `MyComponent` attempts to increment the `count` state variable within the callback function.  Crucially, the dependency array `[count]` includes `count` itself.  This means that every time the `count` changes (which happens inside the useEffect itself), the effect runs again, causing an infinite loop.

## Solution
The corrected code in `bugSolution.js` demonstrates how to resolve the issue. Removing `count` from the dependency array prevents the infinite loop.  The effect will only run once after the initial render because the dependency array is empty (`[]`). If you need to run an effect based on other variables, add them to the array instead.