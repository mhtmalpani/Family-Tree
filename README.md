# FamilyTree — Interactive Family Tree Builder

A fully self-contained, single-file interactive family tree builder that runs entirely in your browser. No installation, no server, no build step required — just open `index.html` and start building.

---

## Features

### Canvas & Navigation
- **Infinite pan-and-zoom canvas** with a dot-grid background
- **Drag to pan** the canvas; scroll or use toolbar buttons to zoom
- **Fit to Screen** — auto-zooms to show all nodes at once (`Ctrl/Cmd + F`)
- **Reset View** — returns to the default centered position
- **Zoom indicator** showing the current zoom level (e.g. 100%)

### Person Cards
Each person is represented by a card on the canvas displaying:
- Profile photo (via URL or Google Drive link)
- Full name (first, last, maiden name, nickname)
- Gender icon
- Date of birth / date of death (with deceased indicator)
- Profession
- City & Country

### Relationships
- **Partner links** — shown as dashed lines connecting couples
- **Parent–child links** — shown as solid curved lines from parent pair to children
- Adding a child to two parents automatically links those parents as partners

### Tree Layout
- **Auto Align** — automatically arranges all nodes into a clean generational hierarchy
- **Expand All / Collapse All** — toggle the visibility of child branches globally
- **Per-branch collapse** — click the toggle button on any connector line to hide/show that branch's descendants

### Editing (Side Panel)
Click any person card to open a slide-in edit panel with fields for:
- First name, last name, maiden name, nickname
- Gender (Male / Female / Other)
- Date of birth, deceased toggle, date of death
- Profession, city, country
- Photo URL (direct links and Google Drive sharing links are both supported)
- Add partner, add child, add parent
- Reorder children via drag-and-drop
- Delete the person

### Persistence
- The tree is **automatically saved to `localStorage`** after every change — your work survives page refreshes.

### Import / Export
| Action | Format | Description |
|---|---|---|
| **Export** | `.json` | Save the full tree data to a file |
| **Import** | `.json` | Load a previously exported tree |
| **Export Image** | `.png` | Capture the visible canvas as an image |

### Keyboard Shortcuts
| Key | Action |
|---|---|
| `Escape` | Deselect card / close side panel |
| `Delete` / `Backspace` | Delete the selected person (when panel is closed) |
| `Ctrl` / `Cmd` + `F` | Fit tree to screen |

---

## Usage

1. Open `index.html` in any modern web browser.
2. Click **Add Person** to place the first node on the canvas.
3. Click a person card to open the edit panel and fill in their details.
4. Use **Add Partner** or **Add Child** inside the panel to build relationships.
5. Click **Auto Align** at any time to tidy up the layout.
6. Use **Export** to save your work as a JSON file, or **Export Image** to save a PNG snapshot.

---

## Google Drive Photo URLs

The app supports multiple Google Drive URL formats and automatically converts them to a renderable image link:

- `https://drive.google.com/file/d/FILE_ID/view`
- `https://drive.google.com/open?id=FILE_ID`
- `https://drive.google.com/uc?id=FILE_ID`

> **Note:** The shared file must have "Anyone with the link can view" permission enabled in Google Drive.

---

## JSON Format

Exported files follow this structure:

```json
{
  "version": 2,
  "nextId": 5,
  "people": [
    {
      "id": "p_1",
      "firstName": "John",
      "lastName": "Doe",
      "maidenName": "",
      "nickname": "",
      "gender": "male",
      "dateOfBirth": "1980-01-15",
      "isDeceased": false,
      "dateOfDeath": "",
      "profession": "Developer",
      "city": "",
      "country": "",
      "imageUrl": "",
      "partnerIds": ["p_2"],
      "parentIds": [],
      "childIds": ["p_3"]
    }
  ],
  "collapsedEdges": []
}
```

---

## Dependencies (loaded via CDN)

All dependencies are loaded from public CDNs — no local installation needed.

| Library | Purpose |
|---|---|
| [Tailwind CSS](https://tailwindcss.com) | Utility-first styling |
| [html-to-image](https://github.com/bubkoo/html-to-image) | PNG export |
| [SortableJS](https://sortablejs.github.io/Sortable/) | Drag-to-reorder children |
| [Inter](https://fonts.google.com/specimen/Inter) (Google Fonts) | UI typeface |

> An internet connection is required for the first load to fetch these CDN assets.

---

## Browser Compatibility

Works in all modern browsers (Chrome, Firefox, Safari, Edge). Not designed for Internet Explorer.