# Tactical Pitch Simulator

---

## Context

This project is an MVP validation prototype for a premium, browser-based football management simulator. The target audience is hardcore sports gamers and football tacticians. The immediate use case is an internal stakeholder demo to prove the viability of dynamic data-theming and complex frontend state management without relying on a backend.

This milestone is strictly a frontend client-side prototype. It is **NOT** a fully playable multiplayer game. The deployment target is modern desktop web browsers (Chrome, Edge, Firefox, Safari).

---

## Project Information

| Field             | Details                                                                                          |
| ----------------- | ------------------------------------------------------------------------------------------------ |
| Category          | Web Development                                                                                  |
| Project Type      | Frontend Single Page Application (SPA) Prototype                                                 |
| Platform / Medium | Desktop Web Browser (Minimum 1024x768 resolution)                                                |
| Deliverable Type  | Zipped Source Code + README.md                                                                   |
| Primary Goal      | Build a React-based 3-route dashboard that dynamically themes its UI based on a 20-team dataset. |

---

## Main Goal

The single most important outcome is a fluid, bug-free interactive web application that proves the developer can manage complex React state across multiple routes while extracting and applying design properties (hex codes and image paths) from a local dataset.

### Required Views

1. A static landing dashboard rendering a grid of 20 available football clubs.
2. A "Locker Room" squad builder where users can assign players to an 11-slot 4-3-3 formation.
3. A "Match Simulation" output screen displaying a static win probability percentage based on the active squad.

---

## Requirements

The freelancer will build a strictly frontend React application utilizing Vite, featuring 3 distinct routes and dynamic global theming based on a static JSON array.

### Core Routing & Navigation

1. The application must initialize with `react-router-dom` using `BrowserRouter`.
2. The application must feature exactly three accessible routes:

   * `/` (Dashboard)
   * `/squad` (Locker Room)
   * `/simulation` (Match Day)
3. The sidebar navigation component must remain globally persistent and visible across all three routes.

### Dynamic Theming Engine

* The global state must store the currently selected `activeClub` object from `teams.jsx`.
* When a club is selected, the application must extract the `primary_hex` string and apply it as the background color of the persistent Sidebar.
* When a club is selected, the application must extract the `logo_path` string and render it in the top-left header component at exactly `64x64 px`.

### Squad Builder State (Locker Room)

* The `/squad` route must render exactly 11 empty slots arranged visually in a 4-3-3 formation.
* The UI must restrict the user to a maximum array length of 11 selected players.
* The UI must disable the **Simulate Match** button until the `activeSquad` array contains exactly 11 items.

---

## Technical Requirements

| Item                    | Requirement                                                                        |
| ----------------------- | ---------------------------------------------------------------------------------- |
| Engine / Framework      | React 18+ initialized via Vite                                                     |
| Language                | Vanilla JavaScript (ES6+) and standard CSS (or Styled Components)                  |
| Platform / Target       | Desktop responsive (Minimum width 1024px)                                          |
| Render Pipeline         | N/A                                                                                |
| Resolution / Target FPS | 60 FPS target for UI animations                                                    |
| Physics / Storage       | React Context API or Redux for global state                                        |
| Browser Support         | Chrome, Edge, Firefox, Safari (latest versions)                                    |
| Code Quality            | Clean, commented, sensibly organized folders following standard React architecture |

### Allowed Tech Stack

1. React (via Vite)
2. `react-router-dom`
3. `framer-motion`

### Not Allowed

* Paid plugins or premium UI templates
* Backend servers (Node/Express, Python)
* Databases (Firebase, Supabase, MongoDB)
* Authentication layers
* TypeScript (Strictly vanilla JS)

---

## Design Direction

### Do

* Maintain a dark, high-contrast aesthetic using `#121212` for the main canvas background.
* Wrap all route transitions in Framer Motion's `<AnimatePresence>` for smooth cross-fading.
* Apply a `whileHover={{ scale: 1.05 }}` animation to all clickable club cards on the dashboard.

### Do Not

* Introduce heavy CSS gradients, drop shadows, or generic Bootstrap-style rounded buttons.
* Hardcode any brand colors into CSS files. All colors must be dynamically pulled from the dataset.

---

## Reference Materials

| Asset        | File / URL                                    |
| ------------ | --------------------------------------------- |
| Dataset      | `Appendix: Dataset` (Bottom of this document) |
| UI Wireframe | `reference_image.png`                         |

### Reference Usage Instructions

The `reference_image.png` dictates the mandatory spatial layout.

* Sidebar must remain on the left.
* Sidebar width must be exactly **250px**.
* You must create a `teams.jsx` file inside `/src/data/` using the exact code block provided in the **Appendix**.
* `teams.jsx` acts as the sole source of truth for club data.
* Do not alter any keys within the dataset.

---

## Deliverables

| # | Item                  | Format | Notes                       |
| - | --------------------- | ------ | --------------------------- |
| 1 | Zipped Source Code    | `.zip` | Must exclude `node_modules` |
| 2 | Project Documentation | `.md`  | Root-level `README.md`      |

### File Naming Convention

All delivered zip files must follow this exact pattern:

```text
[PREFIX]-[item-name]-[version]_[YYYY-MM-DD].[ext]

```

#### Example

```text
FENRIR_pitch-simulator-src_v1.0_2026-06-14.zip

```

### Rules

* Use lowercase and kebab-case for item names.
* No spaces.
* No alternate naming structures.

---

## Folder Structure

```text
tactical-pitch-simulator/
│
├── src/
│   ├── assets/
│   ├── components/
│   │   ├── Sidebar.jsx
│   │   ├── Dashboard.jsx
│   │   └── SquadBuilder.jsx
│   ├── data/
│   │   └── teams.jsx
│   ├── App.jsx
│   └── main.jsx
│
├── README.md
└── package.json

```

---

## Scope Boundaries

### DO

* Build a complete interactive client-side React prototype.
* Use free placeholder headshots (via URL) for player rosters.
* Strictly enforce the 11-player squad limit.

### DO NOT

* Build a backend server or API.
* Include multiplayer networking.
* Implement login or authentication systems.
* Spend time creating real football statistics.
* Use anything beyond dummy numerical values for match probabilities.

---

## Tool Requirements

### Required Tools

* Node.js
* Vite
* VS Code (or equivalent IDE)

### Acceptable Alternatives

* N/A

### Forbidden

* Next.js
* Any Server-Side Rendering (SSR) framework

---

## Quality Control / Pre-Submission Checklist

Before submission, confirm all of the following:

* [ ] The application compiles via `npm run dev` with zero terminal errors.
* [ ] The `teams.jsx` dataset is integrated without data manipulation.
* [ ] All deliverables follow the required naming convention.
* [ ] Navigation between routes works without page reloads.
* [ ] Files are organized into the exact required folder structure.
* [ ] No console errors or missing asset warnings appear in Chrome DevTools.

---

## Acceptance Checklist

* [ ] Sidebar background color updates according to the active club's `primary_hex`.
* [ ] The application prevents users from adding a 12th player.
* [ ] All route transitions trigger Framer Motion animations.
* [ ] The delivered zip archive excludes `node_modules`.

---

## Evaluation Criteria

### State Management

Efficiency and cleanliness of managing and distributing `activeClub` state throughout the application.

### Component Modularity

Logical separation of concerns, such as maintaining Sidebar as an isolated component.

### Animation Execution

Smooth route transitions without layout thrashing or noticeable UI jank.

### Following Constraints

Strict adherence to the provided `teams.jsx` schema with no hardcoded workarounds.

---

## Designer / Developer Choices

| Decision | Accepted Options |
| --- | --- |
| CSS Implementation | CSS Modules, Styled Components, Tailwind CSS |
| Match Day Graphing | Recharts, Chart.js, Native CSS Bars |

---

## Delivery Terms

### Revisions Included

* 1 round of minor revisions

### Allowed Revision Types

* CSS alignment tweaks
* Animation timing adjustments
* State management bug fixes

### Not Considered Revisions

* Complete UI redesigns
* Additional feature routes
* Scope expansion beyond the original brief

### Delivery Method

Zipped archive uploaded through a secure transfer link.

---

## Final Goal

A successfully delivered project will provide Fenrir Gaming Group with a sleek, highly responsive web dashboard that feels like a premium desktop application. By demonstrating flawless state management and dynamic UI rendering, this prototype will serve as the technical foundation required to secure stakeholder approval for future backend integration and full-scale product development.

---

## Appendix: Dataset

Please copy the following array and save it as `teams.jsx` within your `/src/data/` directory to use as the application's foundational dataset.

```javascript
export const teams = [
  {
    id: 1,
    name: "Arsenal",
    primary_hex: "#EF0107",
    secondary_hex: "#063672",
    logo_path: "[https://placehold.co/128x128/EF0107/FFFFFF?text=ARS](https://placehold.co/128x128/EF0107/FFFFFF?text=ARS)"
  },
  {
    id: 2,
    name: "Manchester City",
    primary_hex: "#6CABDD",
    secondary_hex: "#1C2C5B",
    logo_path: "[https://placehold.co/128x128/6CABDD/FFFFFF?text=MCI](https://placehold.co/128x128/6CABDD/FFFFFF?text=MCI)"
  },
  {
    id: 3,
    name: "Liverpool",
    primary_hex: "#C8102E",
    secondary_hex: "#00B2A9",
    logo_path: "[https://placehold.co/128x128/C8102E/FFFFFF?text=LIV](https://placehold.co/128x128/C8102E/FFFFFF?text=LIV)"
  },
  {
    id: 4,
    name: "Manchester United",
    primary_hex: "#DA291C",
    secondary_hex: "#FBE122",
    logo_path: "[https://placehold.co/128x128/DA291C/FFFFFF?text=MUN](https://placehold.co/128x128/DA291C/FFFFFF?text=MUN)"
  },
  {
    id: 5,
    name: "Chelsea",
    primary_hex: "#034694",
    secondary_hex: "#EE242C",
    logo_path: "[https://placehold.co/128x128/034694/FFFFFF?text=CHE](https://placehold.co/128x128/034694/FFFFFF?text=CHE)"
  },
  {
    id: 6,
    name: "Tottenham Hotspur",
    primary_hex: "#132257",
    secondary_hex: "#FFFFFF",
    logo_path: "[https://placehold.co/128x128/132257/FFFFFF?text=TOT](https://placehold.co/128x128/132257/FFFFFF?text=TOT)"
  },
  {
    id: 7,
    name: "Newcastle United",
    primary_hex: "#241F20",
    secondary_hex: "#FFFFFF",
    logo_path: "[https://placehold.co/128x128/241F20/FFFFFF?text=NEW](https://placehold.co/128x128/241F20/FFFFFF?text=NEW)"
  },
  {
    id: 8,
    name: "Aston Villa",
    primary_hex: "#670E36",
    secondary_hex: "#95BFE5",
    logo_path: "[https://placehold.co/128x128/670E36/FFFFFF?text=AVL](https://placehold.co/128x128/670E36/FFFFFF?text=AVL)"
  },
  {
    id: 9,
    name: "Everton",
    primary_hex: "#003399",
    secondary_hex: "#FFFFFF",
    logo_path: "[https://placehold.co/128x128/003399/FFFFFF?text=EVE](https://placehold.co/128x128/003399/FFFFFF?text=EVE)"
  },
  {
    id: 10,
    name: "West Ham United",
    primary_hex: "#7A263A",
    secondary_hex: "#1BB1E7",
    logo_path: "[https://placehold.co/128x128/7A263A/FFFFFF?text=WHU](https://placehold.co/128x128/7A263A/FFFFFF?text=WHU)"
  },
  {
    id: 11,
    name: "Real Madrid",
    primary_hex: "#FFFFFF",
    secondary_hex: "#FEBE10",
    logo_path: "[https://placehold.co/128x128/FFFFFF/000000?text=RMA](https://placehold.co/128x128/FFFFFF/000000?text=RMA)"
  },
  {
    id: 12,
    name: "FC Barcelona",
    primary_hex: "#004D98",
    secondary_hex: "#A50044",
    logo_path: "[https://placehold.co/128x128/004D98/FFFFFF?text=FCB](https://placehold.co/128x128/004D98/FFFFFF?text=FCB)"
  },
  {
    id: 13,
    name: "Atletico Madrid",
    primary_hex: "#CB3524",
    secondary_hex: "#272E61",
    logo_path: "[https://placehold.co/128x128/CB3524/FFFFFF?text=ATM](https://placehold.co/128x128/CB3524/FFFFFF?text=ATM)"
  },
  {
    id: 14,
    name: "Bayern Munich",
    primary_hex: "#DC052D",
    secondary_hex: "#0066B2",
    logo_path: "[https://placehold.co/128x128/DC052D/FFFFFF?text=FCB](https://placehold.co/128x128/DC052D/FFFFFF?text=FCB)"
  },
  {
    id: 15,
    name: "Borussia Dortmund",
    primary_hex: "#FDE100",
    secondary_hex: "#000000",
    logo_path: "[https://placehold.co/128x128/FDE100/000000?text=BVB](https://placehold.co/128x128/FDE100/000000?text=BVB)"
  },
  {
    id: 16,
    name: "Paris Saint-Germain",
    primary_hex: "#004170",
    secondary_hex: "#DA291C",
    logo_path: "[https://placehold.co/128x128/004170/FFFFFF?text=PSG](https://placehold.co/128x128/004170/FFFFFF?text=PSG)"
  },
  {
    id: 17,
    name: "Juventus",
    primary_hex: "#000000",
    secondary_hex: "#FFFFFF",
    logo_path: "[https://placehold.co/128x128/000000/FFFFFF?text=JUV](https://placehold.co/128x128/000000/FFFFFF?text=JUV)"
  },
  {
    id: 18,
    name: "AC Milan",
    primary_hex: "#FB090B",
    secondary_hex: "#000000",
    logo_path: "[https://placehold.co/128x128/FB090B/FFFFFF?text=ACM](https://placehold.co/128x128/FB090B/FFFFFF?text=ACM)"
  },
  {
    id: 19,
    name: "Inter Milan",
    primary_hex: "#010E80",
    secondary_hex: "#000000",
    logo_path: "[https://placehold.co/128x128/010E80/FFFFFF?text=INT](https://placehold.co/128x128/010E80/FFFFFF?text=INT)"
  },
  {
    id: 20,
    name: "Napoli",
    primary_hex: "#12A0D7",
    secondary_hex: "#FFFFFF",
    logo_path: "[https://placehold.co/128x128/12A0D7/FFFFFF?text=NAP](https://placehold.co/128x128/12A0D7/FFFFFF?text=NAP)"
  }
];

```

```

```