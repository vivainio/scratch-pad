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

## A table

| Control | Action |
|---|---|
| Click | Open the diagram full screen |
| `+` / `-` | Zoom in / out |
| `0` | Fit to window |
| Ctrl + wheel | Zoom around the pointer |
| Drag | Pan |
| `Esc` | Close |
