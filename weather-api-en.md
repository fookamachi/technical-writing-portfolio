# Weather API (OpenWeatherMap) — Documentation

## Overview

The **Weather API** provides access to real-time and forecast weather data via HTTPS requests. It is designed for integration into web, mobile, and backend applications.

Provider: **OpenWeatherMap**
Response format: **JSON**
Protocol: **HTTPS**

---

## Table of Contents

- [Quick Start](#quick-start)
- [Authentication](#authentication)
- [Base URL](#base-url)
- [Endpoints](#endpoints)
- [Request Parameters](#request-parameters)
- [Examples](#examples)
- [Response Format](#response-format)
- [Errors](#errors)
- [Rate Limits](#rate-limits)

---

## Quick Start

### Get current weather

```bash id="en-q1"
curl "https://api.openweathermap.org/data/2.5/weather?q=Amsterdam&appid=YOUR_API_KEY&units=metric"
```

---

### Example response

```json id="en-q2"
{
  "weather": [
    {
      "description": "light rain"
    }
  ],
  "main": {
    "temp": 18.5,
    "humidity": 82
  },
  "name": "Amsterdam"
}
```

---

## Authentication

All requests require an API key.

### API Key

An **API key** is a unique identifier used to authenticate requests to the service.

### How to obtain a key:

1. Create an account on OpenWeatherMap
2. Navigate to the API Keys section
3. Generate a new key

### Usage

The API key must be passed using the `appid` parameter:

```text id="en-a1"
appid=YOUR_API_KEY
```

---

## Base URL

```text id="en-b1"
https://api.openweathermap.org/data/2.5
```

---

## Endpoints

### Current weather

```http id="en-e1"
GET /weather
```

Returns current weather data for a specific location.

---

### 5-day forecast

```http id="en-e2"
GET /forecast
```

Returns weather forecast data in 3-hour intervals.

---

## Request Parameters

At least one location parameter is required.

| Parameter | Type   | Required | Description                  |
| --------- | ------ | -------- | ---------------------------- |
| q         | string | No*      | City name                    |
| lat       | float  | No*      | Latitude                     |
| lon       | float  | No*      | Longitude                    |
| zip       | string | No*      | ZIP code                     |
| id        | int    | No*      | City ID                      |
| appid     | string | Yes      | API key                      |
| units     | string | No       | metric / imperial / standard |
| lang      | string | No       | Response language            |

> *One location parameter (q, lat/lon, zip, or id) is required.

---

## Examples

### By city name

```bash id="en-x1"
curl "https://api.openweathermap.org/data/2.5/weather?q=London&appid=YOUR_API_KEY&units=metric"
```

---

### By coordinates

```bash id="en-x2"
curl "https://api.openweathermap.org/data/2.5/weather?lat=52.3676&lon=4.9041&appid=YOUR_API_KEY"
```

---

## Response Format

### Main fields

| Field                 | Type   | Description       |
| --------------------- | ------ | ----------------- |
| main.temp             | number | Temperature       |
| main.humidity         | number | Humidity level    |
| weather[].description | string | Weather condition |
| wind.speed            | number | Wind speed        |
| sys.sunrise           | number | Sunrise timestamp |
| sys.sunset            | number | Sunset timestamp  |

---

## Errors

### HTTP Status Codes

| Code | Meaning                        |
| ---- | ------------------------------ |
| 200  | Success                        |
| 400  | Bad Request                    |
| 401  | Unauthorized (invalid API key) |
| 404  | Location not found             |
| 429  | Rate limit exceeded            |
| 500  | Server error                   |

---

### Example error response

```json id="en-er1"
{
  "cod": "404",
  "message": "city not found"
}
```

---

## Rate Limits

### Free tier limits

* 60 requests per minute
* 1,000,000 requests per month

When exceeded:

```json id="en-er2"
{
  "cod": "429",
  "message": "Too Many Requests"
}
```

---

## Best Practices

### Caching

Cache responses locally to reduce API calls and improve performance.

### Error handling

* Always check HTTP status codes
* Handle API `cod` field
* Implement retry logic for transient errors (500 / 502)

---

## Notes

* HTTPS only
* All responses are JSON
* Time values are Unix timestamps
* Use coordinates for highest accuracy

---

## Conclusion

The Weather API enables easy integration of weather data into applications. Proper handling of authentication, parameters, and errors ensures stable and efficient usage.
