# render-md

A single-file markdown viewer. Uses GTK 3 and WebKit2 on Linux, falls back to a local HTTP server + default browser on macOS/Windows.

## Project structure

- `render-md` — the entire application (single Python script)
- `README.md` — user-facing documentation

## How it works

1. Reads a markdown file from the command line argument
2. Converts to HTML using python-markdown (fenced_code + tables extensions)
3. Counts `<img` tags and picks image size constraints as a percentage of screen size
4. Wraps HTML in a dark-themed template
5. On Linux: detects screen resolution via GDK, displays in a borderless GTK/WebKit2 window, closes on `q`/`Escape`
6. On other platforms: starts a local HTTP server on a random port and opens the default browser

## Key details

- Application ID: `com.github.render-md`
- Window title: `render-md`
- Default window size: 932x666
- Base URI is set to the markdown file's directory so relative image paths resolve correctly
- No external CSS or JS — everything is inlined in the HTML template
- `--no-scale` flag sets image max-width/max-height to `none` in CSS
- Falls back to 1920x1080 if screen detection fails

## Guidelines

- Keep it as a single file — that's the appeal
- No config files — sensible defaults only
- Dark theme is intentional — don't add theme switching
