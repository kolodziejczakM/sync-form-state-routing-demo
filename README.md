## Just a quick demo to answer the question:

### In what way traditional synchronous form preserves data during server routing?

1. Chrome 103 Windows 11:
   1.1. Data is preserved when navigating via browser's back & forward buttons (even for password input [1] and even when form has attribute: autocomplete="off" [2])
   1.2. Data is NOT preserved when going back to filled form via anchor
   1.3. After refreshing (CTRL + R) data is NOT preserved

[1] autocomplete="new-password" or "current-password" directly on input type="password" changes nothing - password is preserved
[2] autocomplete="off" only disables suggestions from browser after focusing form input

2. Firefox 102 Windows 11:
   2.1. Like in 1.1
   2.2. Like in 1.2
   2.3. After refreshing (CTRL + R) data is preserved excluding password input

3. Edge 103, Windows 11:
   3.1. Data is preserved when navigating via browser's back & forward buttons excluding password input which becomes empty (even without autocomplete="current-password" or autocomplete="new-password")
   3.2. Data is NOT preserved when going back to filled form via anchor
   3.3. Data is NOT preserved when form has attribute autocomplete="off"
   3.4. Like in 1.3

#### Conclusions:

1. Only Edge respects autocomplete attribute values when it comes to filling data
2. Only Edge never fills password input
3. When navigating back and forth Chrome and Firefox behave the same way yet they differ during refresh - Chrome behaves like Edge here
4. All browsers behave the same way when user returns to form via anchor - it becomes empty.
5. All browsers don't fill password input after refresh

---

To start testing: `pnpm install` (installing dependencies) & `pnpm start` (running a server on localhost:3000)
