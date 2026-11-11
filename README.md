# Quoted-Printable Decoder

A lightweight, browser-based tool for decoding Quoted-Printable encoded email content and rendering the resulting HTML.

Quoted-Printable is a content-transfer encoding commonly used in email messages to safely transmit text containing non-ASCII characters and special characters.

This utility makes it easier to inspect encoded email bodies, extract readable text, and preview the decoded HTML without manually processing encoded content.

## Features

### 1. Quoted-Printable Decoding

Decode Quoted-Printable encoded content according to the encoding conventions used in MIME email messages.

- Decode hexadecimal escape sequences.
- Handle soft line breaks.
- Convert encoded characters into readable text.
- Process encoded HTML email bodies.

Examples:

```text
Encoded:
Hello=2C=20World=21

Decoded:
Hello, World!
```

```text
Encoded:
This is a long line that =
continues on the next line.

Decoded:
This is a long line that continues on the next line.
```

### 2. HTML Rendering

Preview decoded HTML directly inside the application.

- Render decoded HTML in an embedded iframe.
- Inspect the visual appearance of HTML email content.
- Open the decoded HTML in a separate browser tab.
- Useful for troubleshooting HTML email templates and formatting issues.

### 3. Plain-Text Extraction

Extract and decode the `text/plain` portion of supported multipart email content.

- Identify the `text/plain` MIME section.
- Extract its encoded content.
- Decode the extracted content.
- Display the resulting text in a separate output field.

### 4. Clipboard Integration

Copy decoded HTML directly to the clipboard.

- One-click copying.
- Visual confirmation after successful copying.
- Error handling when clipboard access fails.

## Technology Stack

| Technology | Purpose |
|---|---|
| HTML5 | Application structure |
| CSS3 | Interface styling |
| Vanilla JavaScript | Decoding and rendering logic |
| Browser APIs | Clipboard, DOM manipulation and iframe rendering |

No external JavaScript libraries or frameworks are required.

## Getting Started

### Requirements

- A modern web browser.
- No additional software or dependencies.

### Installation

Clone the repository:

```bash
git clone https://github.com/ra559/quoted-printable.git
```

Navigate into the project directory:

```bash
cd quoted-printable
```

Open the application:

```bash
xdg-open index.html
```

Alternatively, open `index.html` directly in your browser.

### Running a Local Web Server

For local development, use Python's built-in HTTP server:

```bash
python3 -m http.server 8000
```

Navigate to:

```text
http://localhost:8000
```

## Usage

1. Open the application in your browser.
2. Paste the raw Quoted-Printable encoded email content into the input field.
3. Click **Decode and Render HTML**.
4. Inspect the rendered HTML in the embedded preview.
5. Examine the extracted plain-text version.
6. Click **Copy Decoded HTML** to copy the decoded HTML.
7. Click **Open in New Page** to view the decoded HTML separately.

## Understanding Quoted-Printable Encoding

Quoted-Printable is defined by RFC 2045 as a MIME content-transfer encoding.

It represents certain bytes using an equals sign followed by two hexadecimal digits.

For example:

| Encoded | Decoded |
|---|---|
| `=3D` | `=` |
| `=20` | Space |
| `=0A` | Line feed |
| `=2C` | `,` |
| `=21` | `!` |

A soft line break is represented by an equals sign at the end of a line. It indicates that the encoded line continues on the next line and should not introduce a new line in the decoded content.

## Project Structure

```text
quoted-printable/
├── .github/
│   └── workflows/
└── index.html
```

The application is self-contained. HTML, CSS, and JavaScript are all included in `index.html`.

## Privacy

All decoding and rendering operations are performed locally in the browser.

The application does not require an account, backend, database, or external processing service.

Email content is not intentionally transmitted to a remote server by the application.

**Security note:** Only decode and render email content from sources you trust. HTML emails can contain potentially unsafe markup and scripts. The current implementation writes decoded HTML into an iframe and a newly opened browser document without a restrictive sandbox. Do not use it to preview untrusted email content.

## Limitations

The current implementation focuses on common Quoted-Printable email content.

- It does not parse complete MIME messages.
- Plain-text extraction expects specific UTF-8 `Content-Type` header formatting.
- It does not implement a complete MIME multipart parser.
- UTF-8 decoding of arbitrary multibyte encoded sequences is not fully handled by the current byte-to-character conversion.
- It does not decode Base64 MIME sections.

## Contributing

Contributions, bug reports, and feature suggestions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Implement your changes.
4. Test the application in a modern browser.
5. Submit a pull request.

## License

No license file is currently present in the repository. All rights are otherwise reserved by default unless the project owner specifies a license.

---

**Repository:** https://github.com/ra559/quoted-printable

**Related standard:** RFC 2045 — Multipurpose Internet Mail Extensions (MIME), Part One.