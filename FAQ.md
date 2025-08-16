# Frequently Asked Questions (FAQ)

**Q1: How do I run the RoboFriends application locally?**

**A:** Follow these steps:

1.  Clone the repository: `git clone https://github.com/awesome-kartikey/robofriends.git`
2.  Navigate into the directory: `cd robofriends`
3.  Install dependencies: `npm install`
4.  Start the development server: `npm start`
5.  Open `http://localhost:3000` in your browser.

**Q2: Where does the robot data come from?**

**A:** The robot user data (name, username, email) is fetched dynamically from the public REST API [JSONPlaceholder](https://jsonplaceholder.typicode.com/users) when the application mounts. The robot images are generated based on the user ID using the [RoboHash.org](https://robohash.org/) service.

**Q3: Is the `src/robots.js` file used?**

**A:** No, the application currently fetches live data from the JSONPlaceholder API in the `App.js` component's `componentDidMount` method. The `src/robots.js` file contains static robot data that might have been used for initial development or testing, but it's not the active data source in the running application.

**Q4: Can I add my own custom robots to the list?**

**A:** Not directly through the user interface. To add custom robots, you would need to modify the data source:

- If you wanted to use local data, you could modify `App.js` to import and use the `robots` array from `src/robots.js` instead of fetching from the API.
- Alternatively, you could set up your own API endpoint that serves the robot data you want to display.

**Q5: What is Tachyons?**

**A:** [Tachyons](https://tachyons.io/) is a CSS toolkit based on the concept of utility classes. Instead of writing custom CSS rules, you apply pre-defined classes directly in your HTML (or JSX in this case) to style elements (e.g., `pa3` for padding, `ma2` for margin, `tc` for text-align center, `grow` for a hover effect). This project uses Tachyons for quick and consistent styling.

**Q6: Why is the main `App` component a Class component instead of a Functional component with Hooks?**

**A:** This project uses a Class component (`App.js`) for managing state (`robots`, `searchfield`) and lifecycle methods (`componentDidMount`). This was the standard way to handle state and lifecycle events in React before the introduction of Hooks (like `useState` and `useEffect`). The application could be refactored to use Functional components and Hooks, which is often considered the more modern approach in React development.

**Q7: How does the search functionality work?**

**A:**

1.  The `SearchBox` component has an `onChange` event handler.
2.  When the user types in the search box, this handler (`onSearchChange` in `App.js`) is called.
3.  The `onSearchChange` method updates the `searchfield` state in the `App` component with the current input value.
4.  In the `render` method of `App.js`, the `robots` array is filtered based on the `searchfield` state. Only robots whose names include the search term (case-insensitive) are kept.
5.  This filtered list is then passed down to the `CardList` component for display.

**Q8: How do I build the application for production?**

**A:** Run the following command in your project directory:

```bash
npm run build
```

This will create an optimized production build in the `build/` folder, which can then be deployed to a web server or hosting platform.
