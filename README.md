# Craft Studio — Portfolio Platform

A modern, responsive single-page application for showcasing a creative agency's portfolio. Built with React and Vite, featuring dynamic project management, search, filtering, and a polished editorial design system.

---

## Features

- **Landing Page** — Hero section with agency stats, followed by a full project grid
- **Dynamic Project Grid** — Displays projects as interactive cards with category badges, tags, year, and client info
- **Live Search** — Filters projects in real-time across titles, descriptions, and tags
- **Category Filtering** — One-click filter buttons for All, Branding, Web, Print, Digital, and Packaging
- **Add Project Form** — Modal form with validation to add new projects dynamically; supports custom colors
- **Project Detail View** — Slide-up panel with full project info when clicking any card
- **Responsive Design** — Mobile-first layout that adapts from single-column on mobile to 3-column grid on desktop
- **Accessible** — Keyboard navigable cards and modals, ARIA roles and labels throughout
- **Unit & Integration Tests** — Vitest + React Testing Library covering components and user flows

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| React 18 | UI framework |
| Vite 4 | Build tool & dev server |
| CSS Modules (plain CSS) | Component-scoped styles |
| Vitest | Test runner |
| React Testing Library | Component/integration testing |
| Google Fonts (Syne + DM Sans) | Typography |

---

## Getting Started

### Prerequisites

- Node.js 18+ and npm

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/craft-studio-portfolio.git
cd craft-studio-portfolio

# Install dependencies
npm install

# Start the development server
npm run dev
```

The app will be available at `http://localhost:5173`.

### Build for Production

```bash
npm run build
npm run preview
```

### Run Tests

```bash
# Run all tests
npm test

# Run tests with UI
npm run test:ui
```

---

## Project Structure

```
src/
├── components/
│   ├── Navbar.jsx          # Sticky top navigation with Add Project button
│   ├── Hero.jsx            # Landing hero section with stats
│   ├── ProjectGrid.jsx     # Grid container, receives filtered projects
│   ├── ProjectCard.jsx     # Individual project card with detail trigger
│   ├── ProjectDetail.jsx   # Slide-up detail panel (modal)
│   ├── SearchBar.jsx       # Controlled search input
│   ├── FilterBar.jsx       # Category filter pill buttons
│   ├── AddProjectModal.jsx # Validated form modal to add projects
│   └── Footer.jsx          # Site footer
├── data/
│   └── projects.js         # Seed data for initial projects
├── styles/
│   ├── global.css          # Design tokens, resets, font imports
│   ├── Navbar.css
│   ├── Hero.css
│   ├── ProjectGrid.css
│   ├── ProjectCard.css
│   ├── ProjectDetail.css
│   ├── SearchBar.css
│   ├── FilterBar.css
│   ├── AddProjectModal.css
│   └── Footer.css
├── tests/
│   ├── setup.js            # Jest DOM setup
│   ├── components.test.jsx # Unit tests for SearchBar, FilterBar, AddProjectModal
│   └── App.test.jsx        # Integration tests for full app flows
├── App.jsx                 # Root component, global state management
└── main.jsx                # React DOM entry point
```

---

## Component Tree & State

```
App (state: projects[], searchQuery, activeFilter, isModalOpen)
├── Navbar             → onAddProject (prop)
├── Hero
├── main
│   └── ProjectGrid    → projects[], searchQuery, onSearchChange,
│       │                activeFilter, onFilterChange, categories[]
│       ├── SearchBar  → value, onChange
│       ├── FilterBar  → categories[], active, onSelect
│       └── ProjectCard[] → project (prop)
│           └── ProjectDetail → project, onClose
├── Footer
└── AddProjectModal (conditional) → onClose, onSubmit, categories[]
```

State is owned at the `App` level and passed down as props. No external state library is needed given the app's scope.

---

## Known Limitations

- **No persistence** — Projects added via the form are stored in React state only. Refreshing the page resets to seed data. Adding a backend (e.g. `json-server` or Firebase) would solve this.
- **Images are CSS/icon placeholders** — Real project imagery would require an image upload feature or a CDN integration.
- **No routing** — All views are managed via modal/conditional rendering. Adding `react-router-dom` would enable deep-linkable project URLs.
- **No edit/delete** — The current scope covers adding projects. CRUD completion is a natural next step.

---

## License

MIT
