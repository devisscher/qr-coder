How could you build a really simple QR code generator that allows me to have 1 qr, but change the website it directs too?

## Architecture & Implementation Plan

### Core Concept
- Create a single QR code that points to a GitHub Pages redirect service
- The redirect service reads a simple config file to determine where to redirect
- Update the redirect destination by editing the config file in your GitHub repo

### Todo List

- [ ] **Set up GitHub Pages repository**
  - Create a new GitHub repository (e.g., `qr-redirect`)
  - Enable GitHub Pages in repository settings
  - Choose a custom domain or use the default `username.github.io/qr-redirect`

- [ ] **Create redirect service files**
  - Create `index.html` with redirect logic
  - Create `config.json` with current redirect destination
  - Add basic styling and loading message

- [ ] **Implement redirect logic**
  - JavaScript to fetch `config.json` on page load
  - Automatic redirect after brief loading screen
  - Fallback error handling if config is invalid

- [ ] **Generate the QR code**
  - Use a free QR code generator (like qr-code-generator.com)
  - Point QR code to your GitHub Pages URL
  - Test the QR code with a phone

- [ ] **Create update workflow**
  - Document how to update `config.json` via GitHub web interface
  - Test the update process (change URL, commit, verify redirect)

- [ ] **Optional enhancements**
  - Add simple analytics (view count in localStorage)
  - Add a preview of destination URL before redirect
  - Create a simple admin page for easier URL updates

### File Structure
```
qr-redirect/
├── index.html          (redirect page)
├── config.json         (destination URL)
├── style.css          (basic styling)
└── README.md          (instructions)
```

### Example config.json
```json
{
  "redirectUrl": "https://example.com",
  "message": "Redirecting...",
  "delay": 2000
}
```

### Benefits
- ✅ Free hosting with GitHub Pages
- ✅ No database required
- ✅ Easy to update via GitHub web interface
- ✅ One QR code for multiple destinations
- ✅ Version control for all changes
- ✅ No backend server needed