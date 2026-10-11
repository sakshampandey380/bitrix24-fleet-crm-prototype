# DealFlow — Deal, Estimate & Task Management UI

A standalone, front-end demonstration of a deal-management workspace inspired by CRM workflows. It brings together deal details, estimate/order positions, a commercial proposal (КП), operational task builders, file references, task discussions, and workflow status indicators in one large HTML application.

> **Project type:** Front-end prototype / interactive demo  
> **Interface language:** Russian  
> **Runtime:** Browser only — no build step required  
> **Integration status:** Demo data and simulated actions; not connected to a live Bitrix24 instance or a production backend

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Main Workflows](#main-workflows)
- [Interface and UX Details](#interface-and-ux-details)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Run Locally](#run-locally)
- [How to Explore the Demo](#how-to-explore-the-demo)
- [Data, Persistence, and Integrations](#data-persistence-and-integrations)
- [Known Limitations](#known-limitations)
- [Ideas for Future Improvements](#ideas-for-future-improvements)

## Overview

The application is a single-file HTML prototype for exploring how a CRM deal could connect commercial calculations with downstream operational work. The interface is organized around a sample deal and includes deal information, estimate/order data, a commercial proposal view, work-stage task constructors, document references, and a task/chat workspace.

The source combines the page markup, CSS design system, demo records, and client-side JavaScript in one `.html` file. It is intended for interface demonstrations, workflow discussions, and front-end experimentation rather than as a production CRM.

## Features

### 1. Deal workspace

- Deal header with deal identification and workflow context.
- Deal qualification and customer/contact information sections.
- Deal-related task and document areas.
- File list with category/context fields and preview-oriented UI.
- Lead/source information area.
- Expandable cards and accordion sections to keep long forms manageable.
- Contextual help describing workflow stages and automation concepts.

### 2. Estimate and order editor

- Tabular order-position editor with grouped positions.
- Editable fields for position details and operational parameters.
- Add-position and add-group controls in the estimate/order view.
- Group-level organization, including controls to collapse, copy, reorder, or remove groups where supported by the interface.
- Drag/reorder affordances and horizontal scrolling for wide tables.
- Sticky leading columns so position identifiers and names remain visible while scrolling.
- Resizable table columns.
- “For all” synchronization controls that can copy selected field groups from the first position to other positions in the same group.
- Visual indication of the synchronization source and fields controlled by synchronization.
- Field-level changed-state styling and validation cues.
- A summary/footer area for totals and save/status feedback.

### 3. Commercial proposal (КП) view

- Switch between estimate/order and commercial-proposal modes.
- Mode-specific columns and fields.
- Proposal-oriented calculation blocks for area and technology-related values.
- Values pulled or derived from order-position data in the demo workflow.
- The proposal view hides estimate-only controls such as adding new groups or positions.

### 4. Operational task constructors

The interface includes dedicated workflow areas for:

- **Measurement (Замер)**
- **Design (Дизайн)**
- **ЦП**
- **Production (Производство)**
- **Claims / complaints (Рекламации)**

The constructors organize order positions into groups and provide stage-specific fields and task controls. The code tracks created tasks and whether a task needs to be rewritten after source data changes. Some workflow controls model creating or updating tasks for selected groups or all groups.

### 5. Task workspace

- Task list with sample task records, assignees, statuses, and deadlines.
- Search and filtering controls.
- Task details panel with description, role/assignee information, related records, and file references.
- Deadline editing in the interface.
- Pinned tasks and unread counters.
- Alternative timeline/Gantt-style and calendar views.
- Keyboard handling for closing certain overlays and panels.

### 6. Task discussions and reactions

- Task-linked and channel-style sample conversations.
- Message bubbles with sender, timestamp, and optional file references.
- Emoji reaction picker with sample reaction counts.
- Unread-message indicators and refresh helpers.

These interactions operate on in-memory demo objects in the supplied file; they do not provide real-time multi-user messaging.

### 7. File manager and previews

- File table with sample file metadata, categories, and associations to workflow areas.
- Add-row and URL-oriented controls in the interface.
- Selection and preview pane.
- Full-screen viewer with zoom/pan-oriented controls for supported preview content.
- Download behavior for embedded demo data where available.
- Explicit demo feedback for file operations that would require a real product/API integration.

### 8. Themes and responsive layout

- Light theme.
- Night theme.
- Neon theme.
- CSS custom properties for shared colors, surfaces, borders, status colors, and shadows.
- Responsive grids and layout adjustments for narrower screens.
- Horizontal scrolling for dense data tables.
- Visible keyboard focus styles and reduced-motion handling for selected animations.

## Main Workflows

### Estimate → Order → Proposal

1. Review or edit the deal's sample order positions.
2. Organize positions into groups.
3. Use the synchronization controls when fields should be shared across positions in a group.
4. Switch to the commercial-proposal view to inspect proposal-specific fields and calculations.
5. Review the footer/status area for the current UI state.

The prototype models these interactions locally. It does not create a real order or send a proposal to a customer.

### Order → Operational stages

1. Open a stage-specific constructor such as Measurement, Design, ЦП, or Production.
2. Review the groups and position details.
3. Select the relevant task-creation or update action where available.
4. Review task status indicators and the task list.

The code models task creation and stale/rewrite states in demo data. Actual task creation in Bitrix24 requires an implemented and authorized integration.

### Task → Discussion → Files

1. Select a sample task.
2. Inspect its description, deadline, participants, and related files.
3. Open the discussion area.
4. Explore the reaction picker and file-preview interactions.

Messages and reactions are demo interactions, not a server-backed collaboration service.

## Interface and UX Details

The supplied source includes several usability-oriented implementation details:

- **Design tokens:** CSS custom properties centralize colors and visual states.
- **Semantic state styling:** badges and status colors distinguish success, warning, informational, and error states.
- **Dirty-state feedback:** edited controls can be highlighted so unsaved changes are easier to notice.
- **Validation feedback:** invalid fields receive visual emphasis, and selected forms include character-limit indicators.
- **Responsive forms:** CSS grid layouts adapt field groups to available width.
- **Wide-table usability:** horizontal scrolling, sticky identifier/name columns, and column resizing help navigate dense data.
- **Progressive disclosure:** expandable cards, accordions, modals, and preview panes reduce visual clutter.
- **Keyboard support:** Escape closes several transient UI elements, and focus-visible styling helps keyboard navigation.
- **Reduced motion:** selected pulse animations are disabled when the user prefers reduced motion.

These are observations from the provided source. They should not be interpreted as a formal accessibility audit or a guarantee that every component is fully keyboard- or screen-reader-accessible.

## Technology Stack

- **HTML5** — page structure and controls.
- **CSS3** — layout, responsive behavior, custom properties, themes, transitions, and component styling.
- **Vanilla JavaScript (ES6+)** — rendering, UI state, event handling, sample data, calculations, and interactive behavior.
- **Inline SVG** — interface icons and demo visual assets.

No framework, package manager, bundler, or external JavaScript dependency is required to open the supplied file.

## Project Structure

The supplied project currently consists of one self-contained HTML file:

```text
dealflow-crm-demo/
└── index.html
```

For a GitHub repository, rename the supplied file to `index.html` and place it at the repository root. The application source contains:

- HTML markup for the deal, estimate/order, proposal, workflow, task, chat, and file interfaces.
- CSS styles and theme definitions.
- JavaScript demo records and interaction logic.
- Rendering and event handlers for the different workspaces.

The original uploaded filename is in Russian. Renaming it to `index.html` makes the repository easier to navigate and allows GitHub Pages to serve it as the default page.

## Run Locally

### Option 1: Open directly

1. Download or clone the repository.
2. Open `index.html` in a modern browser.
3. Explore the interface.

### Option 2: Use VS Code

1. Open the project folder in Visual Studio Code.
2. Open `index.html`.
3. Use your preferred local static server extension if you want to serve the page over `http://localhost` rather than opening the file directly.
4. Refresh the browser after editing the source.

There is no `npm install`, compilation, or backend startup command in the supplied version.

## How to Explore the Demo

- Use the left navigation rail to switch between workspace areas such as tasks, chats, files, and knowledge/help.
- Switch between the light, night, and neon themes using the theme control.
- Expand and collapse deal cards to inspect their fields.
- Open the estimate/order area and try editing, grouping, reordering, or synchronizing sample positions.
- Switch between the estimate/order and КП modes.
- Explore the Measurement, Design, ЦП, Production, and Claims areas.
- Open a task to inspect its details and discussion.
- Try file selection, preview, and viewer controls.
- Observe the unsaved-change, validation, and task-rewrite indicators.

Some buttons intentionally display demo feedback or model behavior that would be handled by an external service in a real deployment.

## Data, Persistence, and Integrations

**Important:** the supplied file is a front-end demonstration, not a connected production application.

- The source includes hard-coded sample deals, tasks, file metadata, messages, dates, and people.
- The visible implementation does not contain `fetch()` or `XMLHttpRequest` calls and does not use `localStorage` for persistence.
- Most interactive state is maintained in JavaScript objects while the page is running. Reloading the page can reset those changes.
- Comments in the source describe Bitrix24 as the intended product/API source for some operations. The supplied HTML does not itself establish a working Bitrix24 connection.
- File download behavior depends on whether a demo file has embedded data. Some file actions show explanatory demo feedback instead of retrieving a real remote file.
- No authentication, authorization service, database, backend API, or server-side validation is implemented in this standalone file.

Do not enter real customer, employee, contact, or commercial information into this prototype. Replace sample records and add appropriate security, privacy, and persistence controls before using a production dataset.

## Known Limitations

- The interface is in Russian.
- Sample records and workflow dates are embedded in the source.
- Some buttons represent or simulate actions that would normally be performed by a CRM backend.
- No shared multi-user state or real-time synchronization is provided.
- Data is not saved to a database or browser storage by the supplied implementation.
- File management is a demonstration and is not a secure document-storage system.
- The project has not been accompanied by a test suite, build pipeline, or deployment configuration.

## Ideas for Future Improvements

- Split the single HTML file into maintainable HTML, CSS, and JavaScript modules.
- Add a backend API and persistent database.
- Implement authenticated Bitrix24 integration with explicit configuration and permission handling.
- Add server-side validation and role-based access control.
- Add automated unit and browser tests for calculations, synchronization, task-state handling, and forms.
- Add loading, empty, error, and retry states for real network operations.
- Improve keyboard navigation and screen-reader semantics, then perform an accessibility audit.
- Add English localization and a clear configuration layer for demo data.
- Configure GitHub Pages for a public, static demonstration.

## License

No license is specified in the supplied source. Add a `LICENSE` file before allowing others to reuse, modify, or distribute the project.
