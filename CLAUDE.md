# render-md

A single-file borderless markdown viewer for Linux using GTK 3 and WebKit2.

## Project structure

- `render-md` — the entire application (single Python script)
- `README.md` — user-facing documentation

## How it works

1. Reads a markdown file from the command line argument
2. Converts to HTML using python-markdown (fenced_code + tables extensions)
3. Counts `<img` tags and picks image size constraints accordingly
4. Wraps HTML in a dark-themed template
5. Displays in a borderless GTK window with an embedded WebKit2 webview
6. Closes on `q` or `Escape` keypress

## Key details

- Application ID: `com.github.render-md`
- Window title: `render-md`
- Default window size: 932x666
- Base URI is set to the markdown file's directory so relative image paths resolve correctly
- No external CSS or JS — everything is inlined in the HTML template

## Guidelines

- Keep it as a single file — that's the appeal
- No config files — sensible defaults only
- Dark theme is intentional — don't add theme switching
