---
authors: 
- John Doe
date: 2025-01-20
type: "blog"
title: "Search form with React router"
description: "Exploring emerging trends and technologies shaping the web development landscape in 2025."
categories: ["Web Development"]
tags: ["web development", "trends", "technology", "future"]
draft: false
featured: true
---

## Search form with React router

Here's an example of a search form using React Router v6's `useNavigate` hook for redirection upon form submission:

### Steps

1. **Install React Router**: If you haven't already installed React Router, use the following command to add it to your project:

   ```bash
   npm install react-router-dom
   ```

2. **Create a Search Form Component**: This component uses the `useNavigate` hook to programmatically navigate to the `/search?q=searchterm` route when the form is submitted.

### SearchForm.js

```javascript
import React, { useState } from 'react';
import { useNavigate } from 'react-router-dom';

const SearchForm = () => {
  const [searchTerm, setSearchTerm] = useState('');
  const navigate = useNavigate();

  const handleSubmit = (e) => {
    e.preventDefault();
    if (searchTerm.trim()) {
      // Redirect to /search?q=searchterm
      navigate(`/search?q=${encodeURIComponent(searchTerm)}`);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={searchTerm}
        onChange={(e) => setSearchTerm(e.target.value)}
        placeholder="Search..."
        required
      />
      <button type="submit">Search</button>
    </form>
  );
};

export default SearchForm;
```

### App.js

In your main app file, set up the routes and include the `SearchForm` component. Here’s how you can define the routes:

```javascript
import React from 'react';
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import SearchForm from './SearchForm';
import SearchResults from './SearchResults'; // Assuming you have a SearchResults component

const App = () => {
  return (
    <Router>
      <div>
        <SearchForm />
        <Routes>
          <Route path="/search" element={<SearchResults />} />
        </Routes>
      </div>
    </Router>
  );
};

export default App;
```

### SearchResults.js

This component will display the search results based on the query parameter `q`.

```javascript
import React from 'react';
import { useSearchParams } from 'react-router-dom';

const SearchResults = () => {
  const [searchParams] = useSearchParams();
  const query = searchParams.get('q'); // Get the search query from the URL

  return (
    <div>
      <h1>Search Results for "{query}"</h1>
      {/* You can add logic to fetch and display search results here */}
    </div>
  );
};

export default SearchResults;
```

### Key Notes

- **useNavigate**: This hook is used for programmatic navigation. After submitting the form, it redirects the user to the `/search?q=searchterm` route.
- **useSearchParams**: This hook helps extract the query parameters from the URL in the `SearchResults` component.

This setup should handle the search and redirection flow in your React app using React Router v6.
