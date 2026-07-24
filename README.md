# Chiisai HAL Specification

A standardised, open, resource‑conscious **Hardware Abstraction Layer (HAL)** for small,
low‑power microcontrollers with tight memory budgets — the kind used in cost‑sensitive
embedded systems such as sensors and actuators in automotive E/E architectures.

**This repository publishes the rendered specification as a browsable HTML site.** It is the
generated output of a documentation‑as‑code toolchain; the reStructuredText / C‑header sources are
maintained separately.

> **Status:** work in progress. Content and requirement identifiers may still change between
> releases.

---

## Viewing the specification

- **Online:** *hosted site link to be added here (GitHub Pages).*
- **Offline:** download or clone this repository and open **`index.html`** in a web browser. All
  pages, search, diagrams, and cross‑links work from the local files — no server or build step
  required.

## What the Chiisai HAL is

The Chiisai HAL abstracts hardware‑dependent functionality — especially communication
peripherals — so that middleware and application code run across different MCU platforms without
tight hardware coupling or restrictive licensing. Each driver encapsulates hardware‑specific
access behind a hardware‑independent API and configuration, giving upper layers a unified
interface for the core functionality while staying flexible enough to expose platform‑specific
features.

Across modules, a Chiisai HAL driver typically provides:

- initialisation and de‑initialisation of the underlying hardware;
- configuration of module‑ and channel‑specific parameters;
- data I/O relevant to the hardware domain (transmit/receive, pin control, memory
  read/write/erase/blank‑check, …);
- status reporting, error indication, and optional notification (event or polling).

### Who it is for

- **Silicon vendors** implementing a conformant driver (primary audience for the normative parts).
- **Application developers** consuming a driver (primary audience for the guides).

## Scope

The specification covers only the hardware elements commonly required by middleware layers, which
keeps the standard small while remaining extensible:

| Module | Domain |
| --- | --- |
| **Can** | CAN controller interface |
| **Lin** | LIN interface |
| **Spi** | SPI (controller / target) |
| **I2c** | I²C (controller / target) |
| **Uart** | UART / serial |
| **Mcu** | MCU clock, reset, core services |
| **Mem** | Memory (read / write / erase / blank‑check) |
| **Port** | GPIO / pin configuration |
| **Wdg** | Watchdog |

**Out of scope** (deliberately excluded): application logic, operating‑system components and
low‑level driver internals; and specialised peripherals such as **ADC** and **PWM**, which are
left to silicon vendors as differentiators.

## How the specification is organised

The site is structured as **About → General → Driver Modules → Appendix**.

Each **driver module** uses a three‑tier layout so a reader can follow one capability (e.g.
*transmit*) from how it is used, to its exact API, to the rules that govern it:

| Tier | Audience | Content |
| --- | --- | --- |
| **Guide** | Application developers | *Informative.* Quickstart, configuration, and task pages by capability (initialise, transmit, receive, …). |
| **Reference** | Both | The precise API and configuration surface, extracted from the driver headers so code and docs stay in sync. |
| **Requirements** | Silicon vendors | *Normative.* The behavioural contract as traceable requirements, clustered by severity. |

Plus connective material per module: **Overview**, **Concepts** (state machines, sequence
diagrams), and **Design Decisions** (the "why").

**Normative vs. informative.** Every page declares its kind. *Normative* content (Reference,
Requirements) defines what a conformant driver **MUST** do; *informative* content (Overview,
Concepts, Guide, Design Decisions) shows how upper‑layer software *uses* a driver and never
constrains internal implementation.

## Requirements, IDs, and conformance

- Requirements carry short, stable identifiers of the form **`CHI-<MODULE>-<NN>`** (for example
  `CHI-CAN-01`). One identifier is one functional rule.
- Keywords follow **RFC 2119** (MUST / MUST NOT / SHOULD / SHOULD NOT / MAY). Within a module,
  requirements are grouped under **Mandatory (MUST)**, **Recommended (SHOULD)** and
  **Optional (MAY)**.
- **Conformance is claimed per module.** An implementation is a conformant Chiisai HAL driver for
  a module if, and only if, it satisfies every **Mandatory** requirement of that module. SHOULD /
  MAY requirements do not affect conformance. Conformance intentionally does **not** require any
  particular OS/RTOS, coding‑rule regime, or tool‑specific configuration format.

The **Appendix** collects the glossary and abbreviations; terms used throughout the site link back
to their definitions there.

## Feedback

Corrections, clarifications, and suggestions are welcome —TBD!!!
