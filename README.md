# 📚 Librio

**A dependency-free library management system that runs entirely in your browser.**

Librio lets you browse a book catalog, borrow and return books, place reservations, and request new titles, all through a clean single-page interface with light and dark themes. It's built with plain HTML, CSS, and JavaScript (ES modules): no framework, no build step, no backend.

<!-- Add a screenshot or GIF here:
![Librio dashboard](./docs/screenshot.png)
-->

## ✨ Features

- **Sign-in with demo accounts** for admin, staff, and student users
- **Dashboard** with live stats (total books, available copies, active loans, requests), recent loans, and quick actions
- **Catalog** with a book grid showing per-title availability (`available / total`)
- **Borrow and return** books; borrowing creates a loan due one month out and updates available copies automatically
- **Reservations** for titles you want to hold
- **Book requests** for titles the library doesn't have yet
- **Add books** to the catalog
- **Dark mode** toggle, remembered between visits
- **Toast notifications** for instant feedback on every action
- **Persistent data** saved in the browser's local storage, synced across open tabs
- **Responsive layout** that adapts from desktop sidebar to a compact mobile nav
- **Safe rendering**: all user-entered text is HTML-escaped before display

## 🚀 Getting Started

### Prerequisites

- A modern browser (Chrome, Firefox, Safari, or Edge)
- Any static file server. One is required because the app loads JavaScript as an ES module, which browsers block when a page is opened directly from `file://`.

### Run locally

```bash
# Clone the repository
git clone https://github.com/HeindrichMacalinao/Librio.git
cd Librio

# Start a static server (pick one)
python3 -m http.server 8000
# or
npx serve .
```

Then open **http://localhost:8000**.

### Demo accounts

| Role    | Account        | Password     |
| ------- | -------------- | ------------ |
| Admin   | `admin`        | `admin123`   |
| Staff   | `staff`        | `staff123`   |
| Student | `12-34567-890` | `student123` |

> ⚠️ These credentials are seed data for demo purposes only. Librio has no server, so passwords are stored in plain text in the browser and in the source code. Do not use it to protect real data.

### Resetting the demo data

All data lives in your browser under the `librio` local-storage key. To restore the original sample books and loans, clear that key from your browser's dev tools (Application → Local Storage) and reload the page.

## 🗂️ Project Structure

```
Librio/
├── index.html      # App shell: #app mount point, #toasts, #modal-root
├── styles.css      # Theming (light/dark), layout, and components
└── src/
    ├── main.js     # Entry point: routing, event handling, actions
    ├── state.js    # Seed data, localStorage persistence, theme handling
    └── views.js    # Template functions for the login screen and each page
```

### How it works

- **State** (`state.js`) holds users, books, loans, reservations, requests, and the current session in one object, saved to `localStorage` after every change.
- **Views** (`views.js`) are pure functions that take the state and return HTML strings.
- **Controller** (`main.js`) uses event delegation: buttons declare `data-action` attributes, and a single click handler updates the state and re-renders.
- **Routing** is hash-based (`#catalog`, `#loans`, …), so pages can be bookmarked and the back button works.

## 🛠️ Tech Stack

HTML5 · CSS3 (custom properties for theming) · Vanilla JavaScript (ES modules) · Web Storage API

## 👤 Author

**Heindrich Macalinao** · [@HeindrichMacalinao](https://github.com/HeindrichMacalinao)
