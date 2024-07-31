
# Server for Proxying Requests

## Introduction

This project is an educational HTTP proxy server written in Golang. It accepts requests from clients, forwards them to specified external services, and returns the responses in JSON format.

## How to Install

1. Clone the repository:
   ```sh
   git clone https://github.com/Slowspeaker/proxy_server
   ```
   Navigate to the project directory:
   ```sh
   cd proxy_server
   ```

2. Build and run using Docker:
   ```sh
   make build
   ```
   Start the server:
   ```sh
   make up
   ```

3. Run the server:
   ```sh
   make run
   ```

## Deployed on Render

### Base URL
https://proxy-server-12ae.onrender.com/proxy

### Request Body:
Send a POST request with the following JSON structure:
```json
{
  "method": "GET",           
  "url": "http://example.com", 
  "headers": { "Authorization": "Bearer token" }
}
```

### Response:
The server responds with JSON containing:
```json
{
  "id": "requestId",         
  "status": 200,            
  "headers": { /* array of headers from the third-party service response */ },
  "length": 1234             
}
```

### Example Request and Response:

#### Request:
```json
{
  "method": "GET",
  "url": "http://google.com",
  "headers": { "Authorization": "Bearer token" }
}
```

#### Response:
```json
{
  "id": "52d5966f-b2dd-4cd3-8949-7949c5cb3d18",
  "status": 200,
  "headers": {
    "Cache-Control": "private, max-age=0",
    "Content-Security-Policy-Report-Only": "object-src 'none';base-uri 'self';script-src 'nonce-0qpsjpe1eaXGNAd545gnpQ' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp",
    "Content-Type": "text/html; charset=ISO-8859-1",
    "Date": "Tue, 09 Jul 2024 08:25:33 GMT",
    "Expires": "-1",
    "P3p": "CP=\"This is not a P3P policy! See g.co/p3phelp for more info.\",
    "Server": "gws",
    "Set-Cookie": "AEC=AVYB7crN-RFuiKsAueY3wqwawBhzXgR5AzoWkmHva-EIdBWcjsidirIbmfU; expires=Sun, 05-Jan-2025 08:25:33 GMT; path=/; domain=.google.com; Secure; HttpOnly; SameSite=lax",
    "X-Frame-Options": "SAMEORIGIN",
    "X-Xss-Protection": "0"
  },
  "length": 21189
}
```
