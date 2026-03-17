# WebUnlocker Skill

A skill for the Scrapeless platform that enables you to bypass website blocks and scrape web content using the Scrapeless Universal Scraping API. It supports JavaScript rendering, CAPTCHA solving, IP rotation, and intelligent request retries.

## Overview

The WebUnlocker skill provides a high-level interface for bypassing website blocks and scraping web content. It leverages the Scrapeless API to handle complex web scraping tasks, including solving CAPTCHAs, rendering JavaScript, and rotating proxies.

## Installation

1. Clone the repository:

```bash
git clone https://github.com/scrapeless-ai/webunlocker-skill.git
```

2. Install dependencies for WebUnlocker:

```bash
cd webunlocker-skill
pip install -r requirements.txt
```

## Environment Configuration

1. Create a `.env` file in the root directory based on the `.env.example` file:

```bash
cp .env.example .env
```

2. Add your Scrapeless API token to the `.env` file:

```
X_API_TOKEN=your_api_token_here
```

You can obtain an API token from the [Scrapeless website](https://www.scrapeless.com).

## Key Features

- Bypass Cloudflare protection and other website blocks
- Solve CAPTCHAs automatically (reCaptcha V2, Cloudflare Turnstile, Cloudflare Challenge)
- JavaScript rendering for dynamic content
- Multiple response formats (HTML, plaintext, markdown, PNG, JPEG, network, content)
- Proxy rotation and country selection
- Content extraction for specific types (emails, phone numbers, images, etc.)

## Response Types

### HTML
Returns the full HTML content of the page as an escaped string.

### Plaintext
Returns the plain text content of the page, removing all HTML tags.

### Markdown
Returns the page content formatted as Markdown for better readability.

### PNG/JPEG
Returns a base64 encoded string of the page screenshot.

### Network
Returns all network requests made during page load, including URLs, methods, status codes, and headers.

### Content
Returns specific content types extracted from the page, such as emails, phone numbers, headings, images, audios, videos, links, hashtags, metadata, tables, and favicon.

## Usage Examples

```bash
# Scrape HTML content
python3 scripts/webunlocker.py --url "https://httpbin.io/get"

# Scrape as Markdown
python3 scripts/webunlocker.py --url "https://example.com" --response-type markdown

# Take a screenshot
python3 scripts/webunlocker.py --url "https://example.com" --response-type png

# Extract specific content types
python3 scripts/webunlocker.py --url "https://example.com" --response-type content --content-types emails,links,images

# Use a US proxy
python3 scripts/webunlocker.py --url "https://example.com" --country US

# Use POST method
python3 scripts/webunlocker.py --url "https://httpbin.org/post" --method POST --data '{"key": "value"}'

# Add custom headers
python3 scripts/webunlocker.py --url "https://example.com" --headers '{"User-Agent": "Mozilla/5.0"}'

# Use custom proxy
python3 scripts/webunlocker.py --url "https://example.com" --proxy-url "http://your-proxy-url:port"

# Enable JavaScript rendering
python3 scripts/webunlocker.py --url "https://example.com" --js-render

# Bypass Cloudflare Turnstile challenge
python3 scripts/webunlocker.py --url "https://2captcha.com/demo/cloudflare-turnstile-challenge" --js-render --headless --response-type markdown
```

## Common Issues

### Rate Limits
If you encounter 429 errors, you've exceeded the rate limit. Reduce request frequency or upgrade your Scrapeless plan.

### Timeouts
- Page load timeout: 30 seconds
- Global execution timeout: 180 seconds

### CAPTCHA Solving
WebUnlocker automatically handles reCaptcha V2, Cloudflare Turnstile, and Cloudflare Challenge, but complex CAPTCHAs may occasionally fail.

### Billing
- Charges are applied on a per-request basis
- Only successful requests will be billed

## Acknowledgements

- [Scrapeless API](https://www.scrapeless.com) - For providing the underlying scraping infrastructure
- All contributors who have helped improve this project

## Contact Us
For questions, suggestions, or collaboration inquiries, feel free to contact us via:
- Email: market@scrapeless.com
- Official Website: https://www.scrapeless.com
- Community Forum: [MCP Server Discord](https://discord.com/invite/xBcTfGPjCQ)
