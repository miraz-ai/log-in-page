# PHero Login Page - AI Agent Instructions

## Project Overview
This is a **multi-page HTML/CSS login and authentication flow** for a learning project called "PHero". It demonstrates a complete user authentication journey with password reset functionality.

## Architecture & Navigation Flow

The project follows a **page-based navigation model** with these core pages:

- **login.html** → Main entry point; links to forgotten.html and main.html
- **forgotten.html** → Password recovery page; links to newpass.html  
- **newpass.html** → Password confirmation page; links back to main.html
- **main.html** → Success landing page after login

**Key Pattern**: All navigation uses `<a href>` with `target="_blank"`, creating separate windows per page. Each page independently imports its own CSS file.

## Critical Conventions

### CSS Styling Patterns
- **Container style**: `.login` / `.main-page` classes use consistent pattern: `width: 500px`, `margin: 100px auto`, `background-color: rgb(110, 110, 153)`, `box-shadow: black 10px 10px 15px`, `border-radius: 20px`
- **Background images**: Login pages reference `url('One\ Piece.jpg')` with `background-size: cover`
- **Color scheme**: Primary orange/brown buttons `rgb(192, 93, 12)`, white text `rgb(255, 255, 255)`, dark shadows
- **Input styling**: `width: 80%`, `border: none`, `border-radius: 5px`, black shadows on inputs

### Form Input Conventions
- Input fields use placeholder attributes for labels (no `<label>` elements)
- Password toggle button in newpass.html uses inline onclick handler: `togglePass(id, btn)` 
- Form actions use `<a href>` wrapper instead of traditional form submission

### JavaScript Pattern
- Single script block in newpass.html demonstrates inline password visibility toggle
- Function `togglePass()` modifies input type between "password" and "text"
- Uses emoji for visual feedback: 👁️ (visible) and 🙈 (hidden)

## File Structure Reference
```
css/
  ├── login.css        (shared by login.html & newpass.html)
  ├── main.css
  ├── forget.css
  ├── newpass.css
  └── style.css        (unused in current flow)
login.html
forgotten.html
newpass.html
main.html
css.html              (demo/learning page, not part of main flow)
```

## When Extending This Codebase

1. **Adding new pages**: Create new `.html` file in root, create matching `.css` in `css/` folder, use `.login` or `.main-page` container for consistency
2. **Modifying colors/spacing**: Update relevant CSS files - colors typically referenced as `rgb()` values, not hex
3. **Adding form validation**: Insert JavaScript before closing `</body>` tag (see newpass.html pattern)
4. **Navigation changes**: Update links in each page that references other pages (check all `<a href>` tags)
5. **External links**: Currently used for YouTube shorts in main.html; always use `target="_blank"` for external URLs

## Known Issues to Avoid
- Input fields use `placeholder` instead of `<label>` elements - accessibility consideration for future improvements
- Button styling is inline within `.login` and `.main-page` containers rather than separate classes
- `newpass.css` exists but styling may conflict with inherited `.login` class styles - verify cascade when modifying

## Development Workflows
- No build system, bundler, or server required - open `.html` files directly in browser
- CSS changes apply immediately on refresh
- Test navigation by opening pages in browser and clicking links
- For password toggle feature, open newpass.html and click eye emoji buttons to verify functionality
