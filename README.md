# WAF Simulator

A lightweight web application that simulates the behavior of a Web Application Firewall (WAF) to demonstrate how common web attacks are detected and blocked.

## Overview

WAF Simulator provides an interactive environment where users can enter HTTP requests and see how a WAF would process and respond to potential security threats. This tool is designed for educational purposes to help developers and security professionals understand how WAFs protect web applications from common attack vectors.

## Features

- **Real-time WAF Simulation**: Enter any HTTP request and see immediately how a WAF would handle it
- **Customizable Rules**: Enable or disable different protection mechanisms:
  - SQL Injection Detection
  - Cross-Site Scripting (XSS) Detection
  - Malicious Path Detection
- **Visual Feedback**: Clear visual indication of whether a request would be allowed or blocked
- **Educational Tool**: Perfect for security training and awareness

## Technology Stack

- HTML5
- CSS (Tailwind CSS)
- JavaScript (Vanilla)

## Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Safari, Edge)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/rohitcraftsyt/waf-simulator.git
   ```

2. Navigate to the project directory:
   ```bash
   cd waf-simulator
   ```

3. Open `index.html` in your web browser.

Alternatively, you can set up a simple HTTP server:

```bash
# Using Python 3
python -m http.server

# Using Node.js
npx serve
```

Then access the application at `http://localhost:8000` or the port specified by your server.

## Usage

1. Enter an HTTP request in the text area (e.g., `GET /login?username=admin' OR 1=1 --`)
2. Select which WAF rules you want to enable (SQL Injection, XSS, Malicious Path)
3. Click "Simulate WAF"
4. View the result to see if your request would be allowed or blocked by the WAF

### Example Requests to Try

#### SQL Injection Attempts
```
GET /products?id=1 OR 1=1
POST /login username=admin'--&password=anything
```

#### XSS Attempts
```
GET /search?q=<script>alert('XSS')</script>
GET /profile?name=john&bio=<img src="x" onerror="alert(1)">
```

#### Malicious Path Attempts
```
GET /admin/.env
GET /../../etc/passwd
```

## WAF Rules

The simulator includes the following detection patterns:

### SQL Injection Detection
- SQL keywords like SELECT, UNION, etc.
- Common SQL attack patterns like OR 1=1
- SQL comment markers (--)
- Command execution attempts

### XSS Detection
- Script tags
- JavaScript protocol handlers
- Event handlers (onclick, onload, etc.)
- Common JavaScript functions like alert()

### Malicious Path Detection
- Sensitive file extensions (.php, etc.)
- Common sensitive directories (wp-admin, etc.)
- System file access attempts (/etc/passwd)
- Configuration file access (.env)

## Customization

You can easily extend the WAF rules by modifying the `wafRules` object in the JavaScript code:

```javascript
const wafRules = {
    sqlInjection: [
        // Add your custom SQL injection patterns here
        /your_pattern/i,
    ],
    xss: [
        // Add your custom XSS patterns here
        /your_pattern/i,
    ],
    maliciousPath: [
        // Add your custom malicious path patterns here
        /your_pattern/i,
    ]
};
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Disclaimer

This simulator is meant for educational purposes only. It demonstrates basic WAF functionality but should not be used as an actual security measure for production environments.
