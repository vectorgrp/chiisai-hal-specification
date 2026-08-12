[![license](https://img.shields.io/badge/license-Apache%202.0-blue)](https://github.com/vectorgrp/chiisai-hal-specification/blob/main/LICENSE)

# Chiisai HAL Specification

A standardised, open, resource‑conscious **Hardware Abstraction Layer (HAL)** for small,
low‑power microcontrollers with tight memory budgets — the kind used in cost‑sensitive
embedded systems such as sensors and actuators in automotive E/E architectures.

**This repository publishes the rendered specification as a browsable HTML site.** 
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

