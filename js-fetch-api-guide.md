# JavaScript Fetch API Guide

## Overview

The **Fetch API** is a modern JavaScript interface for making HTTP requests. It is used to communicate with backend services and APIs from the browser or Node.js environments (with polyfills or modern runtimes).

This guide covers the basic usage patterns needed for real-world API interaction.

---

## Table of Contents

- Basic Syntax
- GET Requests
- POST Requests
- Handling Responses
- Error Handling
- Best Practices

---

## Basic Syntax

```javascript
fetch(url, options)
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

## GET Request

GET requests are used to retrieve data from an API.

```fetch("https://api.example.com/weather?city=Amsterdam")
  .then(response => response.json())
  .then(data => {
    console.log("Data received:", data);
  })
  .catch(error => {
    console.error("Error:", error);
  });
```

## POST Request

POST requests are used to send data to a server.

```fetch("https://api.example.com/login", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    username: "user123",
    password: "password123"
  })
})
  .then(response => response.json())
  .then(data => {
    console.log("Success:", data);
  })
  .catch(error => {
    console.error("Error:", error);
  });
```

## Handling Responses

Always check whether the response is successful before parsing data.

```fetch(url)
  .then(response => {
    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

## Error Handling

Common error types:

- Network errors  
- Invalid JSON responses  
- HTTP errors (4xx / 5xx)  

Example:

```fetch(url)
  .then(response => {
    if (!response.ok) {
      throw new Error("Request failed");
    }
    return response.json();
  })
  .catch(error => {
    console.error("Request error:", error);
  });
```

## Best Practices
**1. Always handle errors**  

Never assume requests will succeed.

**2. Validate responses**  

Check response.ok before parsing JSON.

**3. Use async/await (recommended)**  

```async function getData() {
  try {
    const response = await fetch(url);

    if (!response.ok) {
      throw new Error("Request failed");
    }

    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
```

## Summary

The Fetch API is a fundamental tool for working with APIs in JavaScript. Mastering it is essential for frontend development and integration with backend services.
