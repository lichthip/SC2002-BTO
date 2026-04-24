# SC2002 BTO Management System

A Java-based Command Line Interface (CLI) application for managing the allocation and tracking of Build-To-Order (BTO) flats in Singapore, developed as part of the Object-Oriented Design & Programming course.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [User Roles](#user-roles)
- [OOP Design](#oop-design)
- [Folder Structure](#folder-structure)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Running the Application](#running-the-application)
  - [Generating Javadocs](#generating-javadocs)
- [Default Login Credentials](#default-login-credentials)
- [Data Files](#data-files)

---

## Project Overview

The BTO Management System is a console-based application that simulates the real-world HDB BTO flat application and allocation process. It supports multiple user roles — Applicants, HDB Officers, and HDB Managers — each with their own set of permissions and workflows.

The system is built with a strong emphasis on Object-Oriented Programming (OOP) principles including **encapsulation**, **inheritance**, **polymorphism**, and **abstraction**, following the SOLID design guidelines.

---

## Features

### Applicant
- Register an account and log in securely
- View available BTO projects and their flat types
- Submit a BTO flat application
- Check application status
- Submit, view, and manage enquiries about projects
- Request to withdraw an application

### HDB Officer
- Register to handle a specific BTO project
- Process flat bookings for successful applicants
- Generate and retrieve applicant receipts
- View and reply to project enquiries

### HDB Manager
- Create, edit, and delete BTO projects
- Set project visibility (on/off) and application windows
- Approve or reject HDB Officer registrations
- Approve or reject applicant withdrawal requests
- Generate reports on applicant data (with filtering options)
- View and reply to all project enquiries

---

## User Roles

| Role | Key Permissions |
|------|----------------|
| **Applicant** | Browse projects, apply for flats, submit enquiries, withdraw applications |
| **HDB Officer** | Book flats for applicants, manage enquiries, generate receipts |
| **HDB Manager** | Full project management, approve/reject actions, generate reports |

---

## OOP Design

The system applies core OOP concepts throughout:

- **Encapsulation** — All entity data is accessed via getters/setters; internal state is kept private
- **Inheritance** — `Applicant` and `HDBOfficer` share a common `User` base class
- **Polymorphism** — Common interfaces/abstract classes allow flexible user role handling
- **Abstraction** — Business logic is separated from UI through controller and service layers
- **Single Responsibility** — Each class handles one concern (model, controller, view, or utility)

The application follows a layered architecture pattern loosely resembling **Entity-Control-Boundary (ECB)**:

```
UI / Boundary Layer     →   Controller / Logic Layer   →   Model / Entity Layer
(CLI menus & input)         (business rules & flow)        (data structures & CSV I/O)
```

---

## Folder Structure

```
SC2002-BTO/
├── src/                   # All Java source files
│   └── main/
│       └── BTO_app.java   # Application entry point
├── bin/                   # Compiled .class binaries
├── docs/                  # Generated Javadoc HTML files
├── data/                  # Persistent data in CSV format
│   ├── ApplicantList.csv
│   ├── ApplicationHistory.csv
│   ├── EnquiryList.csv
│   ├── FlatBookingList.csv
│   ├── ManagerList.csv
│   ├── OfficerList.csv
│   └── ProjectList.csv
└── README.md
```

---

## Getting Started

### Prerequisites

- **Java Development Kit (JDK)** 17 or later
- A Java-compatible IDE (recommended: **Eclipse** or **IntelliJ IDEA**) or a terminal with `javac` available

### Running the Application

#### Option 1 — Using an IDE (Eclipse / IntelliJ)

1. Clone the repository:
   ```bash
   git clone https://github.com/lichthip/SC2002-BTO.git
   ```
2. Open the project in your IDE
3. Add the `src` folder to the build path if it isn't already:
   - **Eclipse**: Right-click project → Properties → Java Build Path → Source → Add Folder → select `src`
   - **IntelliJ**: File → Project Structure → Modules → Sources → mark `src` as Sources Root
4. Navigate to `src/main/BTO_app.java`
5. Right-click → **Run As → Java Application**

#### Option 2 — Using the Terminal

```bash
# Navigate to the project root
cd SC2002-BTO

# Compile all source files
javac -d bin -sourcepath src src/main/BTO_app.java

# Run the application
java -cp bin main.BTO_app
```

### Generating Javadocs

To generate the HTML Javadoc documentation locally:

```bash
javadoc -d docs -sourcepath src -subpackages main -private -author -version
```

Then open `docs/index.html` in your browser to browse the documentation.

---

## Default Login Credentials

Sample accounts are pre-loaded from the CSV files in the `data/` folder. Refer to the relevant CSV files for a full list of test accounts.

| Role | NRIC | Default Password |
|------|------|-----------------|
| Applicant | (see `data/ApplicantList.csv`) | `password` |
| HDB Officer | (see `data/OfficerList.csv`) | `password` |
| HDB Manager | (see `data/ManagerList.csv`) | `password` |

> **Note:** Passwords can be changed after logging in.

---

## Data Files

All application data is persisted as CSV files in the `data/` directory. These are read on startup and written on exit. The system does **not** save automatically on unexpected termination — always exit via the proper logout/exit menu option.

---
