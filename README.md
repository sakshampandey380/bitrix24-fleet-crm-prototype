Enterprise Bitrix24 Commercial Vehicle Fleet Branding CRM Engine (57299AA)
                        BITRIX24 INTEGRATED FLEET BRANDING CRM WORKSPACE
               Native Single-Page Architecture | Zero External Dependencies | ES6+

1. Executive Summary & Project AbstractThe Bitrix24 Commercial Vehicle Fleet Branding CRM Engine (Deal identifier: 57299AA) is a production-grade, client-side single-page application (SPA) architecture built entirely in pure, uncompiled standard web technologies: HTML5, CSS3, and modern ECMAScript (ES6+). It models the full enterprise lifecycle of multi-unit commercial fleet wrapping, graphic production, logistical field execution, customer relationship handling, and claims management.Commercial vehicle branding projects represent one of the most operationally demanding verticals within manufacturing CRM environments. Unlike standard e-commerce orders, vehicle branding transactions require real-time synchronization between:Sales qualification and legal billing contracts (МОП/МОС).Large-format surface area estimations ($\text{m}^2$) and pricing formulas (Смета / КП).Production scheduling and substrate material procurement (Производство / Печать / Постпечать).Physical vehicle intake, field measurements, and dispatch logistics (Замер / Монтаж / Вояж).Post-delivery quality assurance and ticket tracking (Рекламации).This repository contains the refactored, secured, and fully stabilized prototype based on the legacy Bitrix24 Russian-language prototype (Не актуально, но наглядно.html). The codebase spans thousands of lines of inlined layout logic, custom SVG vector assets, asynchronous UI managers, and reactive state stores. Every syntax anomaly, unclosed lexical block, mathematical edge case, and race condition has been eliminated, delivering a clean web workspace with 0 console errors.2. Technical Stack & Architectural DesignThe fundamental architectural principle of this system is zero external dependencies. No third-party bundlers (Webpack, Vite, Rollup), frontend component frameworks (React, Vue, Angular), CSS utility frameworks (Tailwind, Bootstrap), or utility libraries (Lodash, jQuery, Moment.js) are used. The application executes natively within modern browser rendering engines (Chromium, Gecko, WebKit) directly via local file loading (file://) or any generic static file server.+--------------------------------------------------------------------------------------------------+
|                                      BROWSER RUNTIME ROOT                                        |
+--------------------------------------------------------------------------------------------------+
   |
   +---> DOM Tree (Semantic HTML5 Scaffolding)
   |       |-- Fixed Navigation Left Rail (#rail)
   |       |-- Universal Deal Header (#dealHeader) & Breadcrumbs
   |       |-- View Switcher Engine (#pageMain, #pageSmeta, #pageZamer, etc.)
   |       +-- Modal Overlays & Viewport Portals (File Manager, Fullscreen SVG Viewer)
   |
   +---> CSS3 Styling Layer & Dynamic CSS Custom Properties
   |       |-- Root Theming Tokens (--bg, --surface, --ink, --accent, --sync)
   |       |-- Theme Engine (Day, Night, Neon Modes via data-theme attributes)
   |       |-- Strict Sticky Horizontal/Vertical Matrix Scrollers (.table-wrap, .sticky-1,2,3)
   |       +-- Responsive Micro-Animations & Invalid State Shakes (@keyframes pulse, limShake)
   |
   +---> JavaScript Reactive Core (ES6+ Engine)
           |-- Central State Container (window.AppState)
           |-- Reactive Price, Surface Area & Substrate Calculation Engine
           |-- Master-Row Parameter Propagation (🔗 для всех Synchronization)
           |-- Strict Fleet Quota Allocation Engine (.pi-qty Clamping)
           |-- Chronological Upstream Scheduling & Conflict Prevention
           |-- DOM Diffing & Two-Way Input Event Listeners
           +-- Integrated Sub-Screens (Gantt, Interactive Calendar, Kanban, Team Chats)
Component DetailsHyperText Markup Language (HTML5): Semantic document structure containing complex responsive tables, native modal dialog overlays (aria-modal="true"), inlined high-resolution SVG artwork for vehicle templates and CAD schematics, and native HTML datalists for auto-completion.Cascading Style Sheets (CSS3): Structured CSS custom property tokens (--accent, --ok, --warn, --danger, --sync) providing instant UI theming. Features sticky table headers and sticky leading columns (position: sticky), responsive layout grids via CSS Grid and Flexbox, GPU-accelerated micro-animations (transform, opacity), and responsive clamps (clamp()).JavaScript (ECMAScript 2020+): Object-oriented and event-driven reactive state management using standard event delegation, native DOM manipulation APIs, Date manipulation algorithms, and custom validator pipelines.3. High-Level System Workflow & Lifecycle StagesA fleet branding transaction inside this CRM follows a strict 10-stage funnel (Воронка сделки). The interface visually and functionally reflects each state:[Потребность выявлена] (Lead Discovery)
         |
         v
[ТЗ сформировано] (Technical Specifications Confirmed)
         |
         v
[ЗМ/ДМ/ЦП] (Measurements, Design Mockups & Color Proofs Active)
         |
         v
[Предварительный расчёт] (Preliminary Estimate Calculation)
         |
         v
[ЗМ/ДМ/ЦП Дожим] (Technical Alignment & Verification)
         |
         v
[КП отправлено] (Commercial Proposal Dispatched to Client)
         |
         v
[Дожим запущен] (Deal Closing Sequence)
         |
         v
[Договор/Счёт направлен] (Invoicing & Legal Contracts Generated)
         |
         v
[Передано МОСУ] (Handed Over to Operations & Production Execution)
         |
         v
[Закрывающие документы] (Acceptance Certificates & Final Reconciliation)
Each funnel step recalculates deadline reminders, reconfigures client interaction scripts, and checks whether dependent operational tasks can be created or updated.4. Deep Dive: Key Functional Modules====================================================================================================
                                      MODULE BREAKDOWN & SCHEMA
====================================================================================================
4.1. The Commercial Proposal & Estimate Engine (Смета / КП)The financial and operational heart of the workspace resides in the Смета/Заказ (Estimate / Order) and КП (Commercial Proposal / Quote) dual-mode table.+--------------------------------------------------------------------------------------------------+
|                                 QUOTE MODE (КП) TABLE LAYOUT                                     |
+----+-----------------------------+----------------------+----------------------+-----------------+
| №  | Vehicle & Contact           | Technologies Used    | Consumption (Расход) | Order Inclusion |
+----+-----------------------------+----------------------+----------------------+-----------------+
| 1  | VW Transporter RP33DX39     | Tech 1: Print 3640   | 1.52m x 7.0pm = 10.64m² | [X] Into Order|
|    | Driver: Alex (+7 933...)    |                      | Cost: 100,000 RUB    |                 |
+----+-----------------------------+----------------------+----------------------+-----------------+
| 2  | GAZelle Next A123BC77       | Tech 1: Print 3640   | 1.52m x 2.0pm = 3.04m²  | [X] Into Order|
|    | Driver: Sergey (+7 916...)  |                      | Cost: 50,000 RUB     |                 |
+----+-----------------------------+----------------------+----------------------+-----------------+
| 3  | Ford Transit K456MN77       | Tech 1: Print 3640   | 1.52m x 1.0pm = 1.52m²  | [X] Into Order|
|    | Driver: Alex (+7 933...)    |                      | Cost: 18,500 RUB     |                 |
+----+-----------------------------+----------------------+----------------------+-----------------+
Dual-Mode Matrix RenderingThe system uses CSS class switching on the <body> element (body.kp vs body:not(.kp)) to toggle between operational estimation details (mounting types, surface prep, dismantling, courier deliveries) and client-facing financial metrics (width, linear meters, calculated square meters, and price per technology).Mathematical Reactive LoopWhenever an operator inputs values into the roll width ($\text{w}$) or linear meters ($\text{pm}$) fields, the reactive listener recalculates:$$\text{Surface Area } (A) = \text{round}\left(w \times \text{pm} \times 100\right) / 100$$This formula automatically updates the row's area badge, recalculates total order area ($\sum A$), sums vehicle item quantities, and updates total contract pricing across the master sticky header in real time.Master Synchronization Engine (🔗 для всех)A custom sync protocol runs across the table. When the master toggle 🔗 для всех is activated on Row 1:Substrate selections (Material 1, Material 2, Print method) copy downward to rows $2 \dots N$.The UI indicates linked inheritance with a purple = позиция 1 badge.Crucially, the synchronization algorithm preserves discrete vehicle identifiers, license plate models, individual driver phone numbers, and child technology blocks without destructive overwrites.4.2. Production Task Constructor (Производство)+--------------------------------------------------------------------------------------------------+
|                              PRODUCTION CASCADE WORKFLOW PIPELINE                                |
+--------------------------------------------------------------------------------------------------+

  [Installation Target Date (Монтаж / Вояж)] = D_target
       |
       +---> [Post-Printing Finishing (Постпечать)] = D_target - 1 Day
       |
       +---> [Primary Print Production (Производство)] = D_target - 3 Days
       |
       +---> [Logistics Material Shipment (Дата отправки)] = Scheduled <= D_target
The production module groups assigned vehicles into distinct manufacturing and installation teams.Chronological Cascading EngineWhen the production supervisor selects a target montage deadline ($D_{\text{target}}$), the engine automatically computes milestone dates:Print shop completion is scheduled for $D_{\text{target}} - 3\text{ days}$.Lamination and post-print cutting are scheduled for $D_{\text{target}} - 1\text{ day}$.On-site vehicle wrapping begins on $D_{\text{target}}$.Business Trip & Voyage Validations (Командировка / Вояж)If the work type is set to Командировка (Off-site field trip / Voyage), the system requires physical materials to be dispatched via transport carriers. The engine enforces strict date sequencing:$$\text{Date}_{\text{shipment}} \le \text{Date}_{\text{installation}}$$If an operator attempts to set a shipment dispatch date that occurs after the installation start date, the date pair is marked invalid (.invalid), execution halts, and a descriptive toast notification alerts the user.Fleet Quota ProtectionTo prevent assigning more vehicles than are ordered, every row input is bounded by an allocation guard:$$\text{Assigned Qty} \le \text{Total Pool Qty} - \sum \text{Allocated Other Groups}$$Typing an excessive number (e.g., 999) immediately clamps the value back to the remaining available stock, preventing over-commitment.4.3. Unified Document & File Manager (Файловый менеджер)A centralized file portal manages proofs, vector drawings, cut contours, and contracts:Interactive Media Previews: Hovering over file table rows reveals visual preview thumbnails; clicking launches an interactive viewport viewer with pan, drag, and zoom capabilities.Two-Dimensional Matrix Tagging: Files are tagged by operational phase (Смета, Заказ, Замер, Дизайн, ЦП, ППМ/В, Рекламации) and vehicle position categories.Client-Side SHA-256 Checksums: In-browser cryptographic hashing (crypto.subtle.digest) detects duplicate file uploads in real time, preventing duplicate files from entering memory.4.4. Integrated Bitrix24 Sub-ScreensTo provide a complete enterprise CRM experience, the application includes functional operational views:+--------------------------------------------------------------------------------------------------+
|                                    WORKSPACE SUB-SCREEN MATRIX                                   |
+--------------------------------------------------------------------------------------------------+
| 1. Kanban & Deal Registry  | Pipeline funnel overview, stage filters, and revenue tracking.      |
| 2. Interactive Calendar    | Day/week/month deadline grid displaying all active shop tasks.       |
| 3. Gantt Scheduling Chart  | Interactive timeline bar displaying cascading task durations.       |
| 4. Team Chat Hub           | Persistent group chats for Office, Workshop, and Installers.       |
| 5. Claims Module (R!)      | Two-tier quality ticket system with root-cause allocation metrics.  |
+--------------------------------------------------------------------------------------------------+
5. Comprehensive Changelog: Bugs Resolved & Enhancements Made====================================================================================================
                        STABILIZATION AUDIT & COMPREHENSIVE REFACTORING LOG
====================================================================================================
During audit and refactoring of the legacy prototype (Не актуально, но наглядно.html), multiple blocking errors, memory leaks, and validation vulnerabilities were identified and resolved.Detailed Root Cause Analysis & Fix MatrixBug 1: Fatal Syntax Error — Duplicate Global IdentifierManifestation: Uncaught SyntaxError: Identifier 'POSITIONS' has already been declaredRoot Cause: The legacy codebase defined const POSITIONS = [...] near line 708 and repeated an identical global declaration inside a lower script segment near line 2234. In strict JavaScript execution, redeclaring a const variable in the same scope throws a fatal parse-time syntax error, terminating the JavaScript engine and breaking all UI interactions.Resolution: Removed the duplicate global declaration. Centralized data initialization inside AppState.init(), mapping positions into mutable object state via immutable cloning (JSON.parse(JSON.stringify(POSITIONS))).Bug 2: Fatal Syntax Error — Truncated Document & Unclosed IIFEManifestation: Uncaught SyntaxError: Unexpected end of inputRoot Cause: The script terminated abruptly at the bottom of the source file. Several event listeners (tk_vClose, vDl, tk_viewer), self-executing anonymous functions (IIFE), and the master <script> and </body> tags were cut off mid-statement.Resolution: Rebuilt the document closing lifecycle loop, bound all remaining modal controls, invoked initial render functions (renderList(''), refreshUnreadBtn()), and sealed all open functional scopes cleanly.Bug 3: Mathematical Quote Corruption on Zero/Negative InputsManifestation: Negative surface areas, negative contract totals, and NaN ₽ values in financial headers.Root Cause: The input event listeners on .kp-w (Width) and .kp-pm (Linear Meters) parsed input values directly into floating-point numbers without boundary verification:JavaScript// Defective legacy logic:
p[field] = parseFloat(inp.value);
Entering 0, -5, or invalid strings corrupted calculations and propagated bad data downstream.Resolution: Implemented input validation defenses in handleCalc:JavaScript// Hardened validation engine:
const handleCalc = (inp, field) => {
  const val = parseFloat(inp.value);
  if (isNaN(val) || val <= 0) {
    inp.classList.add('invalid');
    showToast('Ширина и П.М. не могут быть нулём или отрицательными!', 'warn');
    inp.value = p[field]; // Restore previous safe state
    setTimeout(() => inp.classList.remove('invalid'), 1400);
    return;
  }
  p[field] = val;
  renderSmetaTable();
  renderConstructors();
};
Bug 4: Chronological Voyage Scheduling InversionManifestation: Fleet wrapping crews were scheduled to depart for on-site installations after the job deadline had passed.Root Cause: The production group constructor allowed date inputs (prod-due and prod-ship) to be set independently without cross-field validation.Resolution: Added two-way date comparison logic. When work type is set to Командировка, the system checks that shipment precedes installation:JavaScriptif (e.target.value && dueVal && e.target.value > dueVal) {
  inp.classList.add('invalid');
  showToast('Дата отправки материала не может быть позже срока Вояжа/Монтажа!', 'warn');
  inp.value = '';
  AppState.constructors.prod[gi].ship = '';
  return;
}
Bug 5: Fleet Stock Over-AllocationManifestation: Operators could schedule more vehicles than existed in the customer contract (e.g., assigning 50 vehicles when only 7 were ordered).Root Cause: Input fields for position quantity (.pi-qty / .zi-qty) had no upper bound validation.Resolution: Implemented dynamic clamping that calculates unassigned vehicle balances:$$\text{Cap} = \text{Remaining Pool} + \text{Current Row Allocation}$$If an operator inputs a value exceeding this cap, the value is clamped to the maximum available count, flagged with an invalid boundary style, and accompanied by a warning toast.Bug 6: Browser Translation Extensions Breaking Local File ExecutionManifestation: net::ERR_TIMED_OUT and net::ERR_FILE_NOT_FOUND on requests to translate.googleapis.com.Root Cause: Opening HTML files locally via file:/// causes browser translation extensions (such as Google Translate) to attempt translating Russian text. Because local file security origins block standard web translation requests, the extension fails with continuous timeout errors in the developer console.Resolution: Added translation control directives to document headers:HTML<html lang="ru" class="notranslate" translate="no">
<head>
  <meta name="google" content="notranslate">
This instructs browser translation engines to skip the page, keeping the DevTools console clean.Bug 7: Persistent Stale Tasks Warning BannerManifestation: The amber banner ⚠ Задачи устарели — перезапишите через ⋯ remained visible even when data was fresh.Root Cause: Initialization routines triggered change events during table setup, running markDirty() and setting TASKS.smeta.stale = true before the operator made any edits.Resolution: Refactored setStatus() and markDirtyFor() lifecycle loops to verify that the clean state (✓ Изменений нет) displays by default upon page load until an operator makes actual edits.6. Comprehensive Verification Test SuiteTo verify the stability of the application, execute this end-to-end testing protocol:====================================================================================================
                                END-TO-END VERIFICATION RUNBOOK
====================================================================================================

TEST SUITE 1: CONSOLE INTEGRITY CHECK
  [x] Step 1.1: Open index file in Chrome, Edge, or Firefox.
  [x] Step 1.2: Launch Developer Tools (F12) -> Console Tab.
  [x] Expected Result: Zero red uncaught exceptions. 100% clean boot.

TEST SUITE 2: REACTIVE QUOTE ENGINE (КП)
  [x] Step 2.1: Navigate to 'Смета/Заказ' -> Switch to 'КП' mode.
  [x] Step 2.2: Locate Row 1 (VW Transporter). Modify linear meters (П.М.) from 7 to 10.
  [x] Expected Result: Calculated area updates to 15.20 m²; deal header total updates dynamically.
  [x] Step 2.3: In Row 1 П.М. input, enter '-5' and press Tab.
  [x] Expected Result: Red border flashes; toast displays warning; value resets safely to 10.
  [x] Step 2.4: Enter '0' in П.М. input.
  [x] Expected Result: Input blocked; value resets to safe fallback; calculation stays valid.

TEST SUITE 3: MASTER SYNCHRONIZATION (🔗 для всех)
  [x] Step 3.1: In Estimate mode, toggle '🔗 для всех' under the Technology column header.
  [x] Step 3.2: Inspect Rows 2 and 3.
  [x] Expected Result: Rows 2 and 3 display '= позиция 1' badges, syncing technology attributes
                       while preserving vehicle names, plates, and driver contact info.

TEST SUITE 4: PRODUCTION & FLEET CAPACITY GUARDS
  [x] Step 4.1: Switch to 'Производство' (Production) tab.
  [x] Step 4.2: In Group 1 header, set 'Вид работ' to 'Командировка' (Voyage).
  [x] Step 4.3: Set Installation Deadline (Срок монтажа) to '2026-10-15'.
  [x] Step 4.4: Set Dispatch Date (Дата отправки) to '2026-10-18'.
  [x] Expected Result: Date input flags red; conflict toast warns that material cannot dispatch
                       after installation starts; invalid date clears.
  [x] Step 4.5: Find vehicle quantity input (Кол-во). Enter '999'.
  [x] Expected Result: Value clamps to remaining available pool; toast displays capacity notice.

TEST SUITE 5: OPERATIONAL SUB-SCREENS
  [x] Step 5.1: Click left rail icon 3 (Задачи / Tasks). Toggle between List, Gantt, and Calendar.
  [x] Expected Result: Deadlines render accurately across timeline bars and calendar slots.
  [x] Step 5.2: Click left rail icon 4 (Чаты / Chats). Switch between Office, Workshop, and Installers.
  [x] Expected Result: Chat histories display cleanly with working message inputs.
  [x] Step 5.3: Click left rail icon 2 (Сделки / Deals). Select Deal 57299AA.
  [x] Expected Result: Returns to master workspace with full state intact.
7. Code Style & Maintainability GuidelinesWhen extending or maintaining this codebase, follow these technical conventions:Zero Dependencies: Do not introduce external libraries or node runtime requirements. Maintain plain vanilla ES6+ execution.Central State First: Never store master application state exclusively inside DOM elements. Read and update through window.AppState, then re-render through component render routines.Encapsulated Dynamic Scoping: Keep variable declarations within clear block scopes (const, let). Avoid declaring variables in the global window scope to prevent name collisions.Graceful Degradation: Always provide defensive fallbacks (|| 0, || '', Math.max()) when parsing numeric inputs from text or number inputs.Semantic ARIA Standards: Maintain accessibility guidelines across modal dialogs, tablists, and interactive custom buttons using semantic aria-* tags.8. License & IP InformationDistributed under the MIT License.Copyright (c) 2026 Fleet CRM Engineering Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
====================================================================================================
                        END OF TECHNICAL SYSTEM SPECIFICATION
====================================================================================================
