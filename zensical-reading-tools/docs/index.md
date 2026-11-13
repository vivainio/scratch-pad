# Reading tools demo

Click a diagram to open it full screen. Zoom with the buttons, `+` / `-` / `0`, or Ctrl + wheel
(trackpad pinch); drag to pan; `Esc` closes. Tables have a **Full screen** button, and the toolbar
toggles the navigation, the table of contents and the full-width layout.

This page is built from [`skills/zensical-publishing`](https://github.com/vivainio/agent-skills/tree/main/skills/zensical-publishing),
which installs the tools into any Zensical book.

## A small diagram

```mermaid
graph TD
    A[Write Markdown] --> B[Build with Zensical]
    B --> C[Click the diagram]
    C --> D[Zoom and pan]
```

## A large diagram

Too wide to read at column width: this is what the zoom view is for.

```mermaid
flowchart LR
    subgraph Ingest
        direction TB
        I1[Upload API] --> I2[Virus scan] --> I3[Format detection]
        I3 --> I4[OCR] & I5[XML parser] & I6[EDI mapper]
    end
    subgraph Extract
        direction TB
        E1[Header fields] --> E2[Line items]
        E2 --> E3[Tax codes]
        E3 --> E4[Supplier match]
    end
    subgraph Validate
        direction TB
        V1[Schema check] --> V2[Duplicate check]
        V2 --> V3[PO match]
        V3 --> V4[Budget check]
        V4 --> V5{Within tolerance?}
    end
    subgraph Route
        direction TB
        R1[Approval matrix] --> R2[Approver 1]
        R2 --> R3[Approver 2]
        R3 --> R4[Exception queue]
    end
    subgraph Post
        direction TB
        P1[ERP posting] --> P2[Payment run] --> P3[Archive]
    end
    I4 --> E1
    I5 --> E1
    I6 --> E1
    E4 --> V1
    V5 -- yes --> P1
    V5 -- no --> R1
    R2 --> P1
    R3 --> P1
    R4 --> E1
```

## A sequence diagram

```mermaid
sequenceDiagram
    participant U as Reader
    participant P as Page
    participant D as Zoom view
    U->>P: click diagram
    P->>D: copy rendered SVG
    D-->>U: full screen, fitted
    U->>D: Ctrl + wheel, drag
    D-->>U: zoomed, panned
    U->>D: Esc
    D-->>P: close
```

## A very wide diagram (pan sideways)

A 30-step chain, about eight times wider than tall. Open it, zoom in with `+`, then drag sideways.

```mermaid
flowchart LR
    S1[Step 1] --> S2[Step 2] --> S3[Step 3] --> S4[Step 4] --> S5[Step 5] --> S6[Step 6] --> S7[Step 7] --> S8[Step 8] --> S9[Step 9] --> S10[Step 10] --> S11[Step 11] --> S12[Step 12] --> S13[Step 13] --> S14[Step 14] --> S15[Step 15] --> S16[Step 16] --> S17[Step 17] --> S18[Step 18] --> S19[Step 19] --> S20[Step 20] --> S21[Step 21] --> S22[Step 22] --> S23[Step 23] --> S24[Step 24] --> S25[Step 25] --> S26[Step 26] --> S27[Step 27] --> S28[Step 28] --> S29[Step 29] --> S30[Step 30]
```

## A wide timeline

```mermaid
gantt
    title Release plan
    dateFormat YYYY-MM-DD
    axisFormat %b %d
    section Design
    Research            :a1, 2026-01-05, 40d
    Prototype           :a2, after a1, 35d
    Review              :a3, after a2, 20d
    section Build
    Backend             :b1, after a2, 70d
    Frontend            :b2, after a2, 85d
    Integrations        :b3, after b1, 45d
    section Ship
    Beta                :c1, after b2, 30d
    Hardening           :c2, after c1, 40d
    Launch              :milestone, after c2, 0d
```

## A wide table

22 columns: use **Full screen**, then scroll sideways.

| Region | Q1 | Q2 | Q3 | Q4 | Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec | Total | Target | Delta | Owner | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| North | 12 | 14 | 11 | 18 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 55 | 50 | +5 | Anna | On track |
| South | 9 | 10 | 13 | 12 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 44 | 50 | -6 | Ben | Behind |
| East | 15 | 16 | 17 | 20 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 68 | 60 | +8 | Cara | Ahead |

## A small table

| Control | Action |
|---|---|
| Click | Open the diagram full screen |
| `+` / `-` | Zoom in / out |
| `0` | Fit to window |
| Ctrl + wheel | Zoom around the pointer |
| Drag | Pan |
| `Esc` | Close |
