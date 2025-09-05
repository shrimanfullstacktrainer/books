----------
applyTo: "**/*.ts, **/*.js"
-----------
###Abstract

The instructions are for React and Javascript code. The instructions assist in the following tasks:

- Developing and reviewing React and Javascript code.

- Best Practices for logging, exception handling, API integration and efficient coding, following React Standards

The goal is to ensure high-quality, maintainable, and secure code that adheres to industry standards.

### Instructions for Writing React Code


##Service Layer Design

- Implement a dedicated service layer to separate business logic from UI components

- Structure services by domain (e.g., authService.js , userService.js)

- Use dependency injection patterns for better testability

- Ensure the service layer is modular and reusable.

- Centralize API configuration (base URLs, headers, interceptors) in a single place

- Implement retry logic and request cancellation for critical API calls

- Implement proper error handling in service methods and propagate error messages to the calling components.

Example of a service layer function:

```javascript

//filepath: services/apiService.js

export const fetchUserData async (userId) => {

try {

const response await axios.get('/users/$(userId)');

return response.data:

) catch (error) {

log.error('Error fetching user data:', error);

throw new Error('Failed to fetch user data');

};
```

### API Integration

- Use axios or the Fetch API for making HTTP requests.

- Centralize API calls in a service layer to keep components clean.

- Handle loading and error states for API calls:

```javascript


const [loading, setLoading] useState(false);

const fetchData async () => {

setLoading(true);

try {

const response await api.get('/endpoint');

setData(response.data);

} catch (error) {

log.error('API Error:', error);

} finally {

setLoading(false);

}

};
```

-  Validate API responses and handle unexpected data formats.

## Best Practices

### Logging

- Avoid console logs.

- Avoid logging sensitive information such as passwords, tokens, or PII data. SSN, Date Of Birth, Account Number are restricted from printing in logs.

- Ensure use of info and error statements in logs over debug statements.


### Error Handling

-  Implement proper error boundaries for React components using ErrorBoundary.

-  Use try-catch blocks for asynchronous operations and handle errors gracefully:

```javascript

try {

const response await fetchData();

setData(response);

} catch (error) {

log.error('Error fetching data:', error);

setError('Failed to fetch data');

}
```

-  Display user-friendly error messages in the UI.

### Efficient Coding

-  Use functional components and React hooks (useState, 'useEffect, etc.) instead of class components where possible.

-  Optimize rendering by using React.memo and useCallback for performance-critical components.

-  Follow a modular structure for components and keep them reusable.

-  Use lazy loading (React.lazy and Suspense') for components to reduce initial load time.

-  Optimize images and use responsive formats like SVG or Webp.

### Code Quality

-  Use meaningful variable and function names, use camel casing.

-  Keep components small and focused on a single responsibility.

-  Avoid deeply nested JSX; break down complex UIs into smaller components.

-  Commented code should not exist.

-  Only add appropriate short comment statements to explain complex functions as needed.

-  Use environment variables for sensitive data like API keys and never expose them in the frontend.

### State Management

-  Use `React Context` or state management libraries like `Redux` and `Zustand` for managing global state.

-  Avoid prop drilling by leveraging context or component composition.

-  Keep state updates immutable and predictable.


### Project Structure

-  Organize by feature rather than type for larger applications

-  Implement a consistent folder structure, for e.g.

src/
├── assets/					# Static files (images, fonts)
├── components/				# Reusable UI components
│   ├── common/				# Shared components (Button, Input, etc.)
│   └── [features]/			# Feature-specific components
├── hooks/						# Custom React hooks
├── pages/						# Page components (route endpoints)
├── services/					# API and business logic
├── store/						# State management (Redux/Context)
├── utils/						# Helper functions and constants
├── styles/					# Global styles and themes
├── tests/						# Test files

-  Ensure proper separation of concerns between components, services, and utilities.

-  Keep related files close together (component, styles, tests)

### Documentation


-  Ensure all components, hooks, and utility functions are well-documented.

-  Use **JSDoc** for documenting functions, props, and return values.

-  Maintain a README.md file for the project with:

	-  Setup instructions.

	-  Usage examples.

	-  Project structure overview.

-  Add inline comments only for complex logic or non-obvious code sections.

-  Example of JSDoc for a React component:


```javascript

/**

* Button component for user interactions.

*

* @param {Object} props Component props.

@param {string) props.label The text to display on the button.

* * @param {Function} props.onClickCallback function when the button is clicked.

* @returns {JSX.Element} The rendered button component.


*/

const Button = ({ label, onClick}) => {

return <button onClick={onClick}>{label}</button>;

};

export default Button;
```

### Styling

-  Avoid inline styles; use CSS modules or Tailwind CSS for styling.

-  Adhere to the styling standards specified in the project context.

-  Prefer using Material-UI (MUI) for styling unless a different library is specified in the project context.



## Non-Functional Requirements

### NFR: Client UI errors are logged

-  Ensure to log UI errors to backend 

services.

```javascript

function logErrorToServer(logMessage, logLevel) {

}

fetch('/api/logs', {

method: 'POST',

headers: { 'Content-Type': 'application/json'),

body: JSON.stringify({ level: logLevel, message: logMessage, timestamp: new Date().toISOString()})

}).catch(err => console.error('Failed to 

send log to server:', err));

// Example usage

window.onerror = function (message, source, lineno, colno, error) {

logErrorToServer(${message} at ${source): ${lineno}:${colno}, 'ERROR');

};
```

## Code Review Checklist

-  Check for proper error handling and logging.

-  Ensure all new code is covered by tests.

-  Confirm no sensitive data is exposed in 

the code.

-  Check for code structure and suggest modifications as needed.

-  Check if any simplifications are possible in the code

-  Validate that the code is optimized for performance, including efficient rendering and minimal resource usage.

-  Ensure the application is fully responsive and functions correctly across various screen sizes, devices and browsers.

-  Check that all components, functions, and modules are well-documented, including inline comments for complex logic.
