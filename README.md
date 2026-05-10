# Software Re-Engineering Project  
## Legacy Java Code Analysis & Technical Debt Assessment

**Institution:** National University of Computer and Emerging Sciences (FAST-NUCES)  
**Instructor:** Ma’am Muzzamal Asghar  

### Team Members
- Muhammad Hasnain (22F-3718) — Section SE-8A  
- Asfand Ahmed (22F-3727) — Section SE-8A  

---

# Project Overview

This repository contains the deliverables and implementation work for **Parts A, B, C, and D** of the Software Re-Engineering project.

The project focuses on analyzing and evaluating a legacy monolithic Java Swing desktop application:  
**Library-Management-System-JAVA**

The selected system demonstrates several architectural and maintainability issues commonly found in legacy software systems, including:

- Tight coupling between UI and business logic
- Direct database access inside presentation classes
- Large monolithic classes (“God Classes”)
- Excessively long methods
- Poor modular separation
- High technical debt accumulation

These characteristics made the project an ideal candidate for static code analysis, architectural evaluation, control flow graph generation, and technical debt assessment.

---

# Project Objectives

- Analyze a legacy Java desktop application
- Identify code smells and maintainability issues
- Measure architectural complexity and coupling
- Generate Control Flow Graphs (CFGs)
- Explore Abstract Syntax Trees (ASTs)
- Quantify technical debt using industry-standard tools
- Demonstrate architectural refactoring techniques

---

# Repository Structure

```plaintext
├── Library-Management-System-JAVA/
├── sonar-project.properties
├── Project_Report.pdf
└── README.md
```

---

# Repository Contents

### `Library-Management-System-JAVA/`
Contains the cloned legacy Java Swing application source code used for analysis.

### `sonar-project.properties`
Configuration file for SonarScanner containing:
- Project metadata
- SonarQube host configuration
- Authentication token settings

### `Project_Report.pdf`
Comprehensive documentation covering all project phases:

#### Part A — Project Selection & Environment Setup
- Legacy system selection
- Tool installation and configuration
- SonarQube environment setup

#### Part B — Static Analysis & Refactoring
- Detection of code smells using SonarQube
- Identification of architectural violations
- Refactoring demonstrations
- Feature Envy resolution examples

#### Part C — Architectural Metrics & CFG Analysis
- Coupling metrics (Ca/Ce)
- Dependency analysis
- Control Flow Graphs (CFGs)
- God Class identification
- Circular dependency analysis

#### Part D — Technical Debt & AST Exploration
- Technical debt prioritization
- Execution tracing using Python Tutor
- Abstract Syntax Tree (AST) analysis
- Complexity evaluation

---

# Technologies & Tools Used

## Static Code Analysis
- SonarQube
- SonarScanner CLI

## Graph & Architecture Analysis
- GraphViz Online
- AST Explorer

## Execution Tracing
- Python Tutor (Java Visualizer)

## Development Environment
- Java
- MySQL 8.0
- Docker Desktop

---

# Setup & Execution Guide

## 1. Start SonarQube Using Docker

Ensure Docker Desktop is running, then execute:

```bash
docker run -d --name sonarqube -p 9000:9000 sonarqube:latest
```

Allow a few moments for initialization.

After startup, open the following URL in your browser:

```plaintext
http://localhost:9000
```

### Default Credentials

```plaintext
Username: admin
Password: admin
```

You will be prompted to update the password after the first login.

---

## 2. Configure the SonarQube Project

Inside the SonarQube dashboard:

1. Create a new local project named:

```plaintext
LibraryManagementSystem
```

2. Generate a project analysis token.

3. Open the `sonar-project.properties` file and update the token value.

---

## Example Configuration

```properties
sonar.projectKey=LibraryManagementSystem
sonar.projectName=Library Management System
sonar.projectVersion=1.0
sonar.sources=.
sonar.host.url=http://localhost:9000
sonar.token=YOUR_GENERATED_TOKEN_HERE
```

---

## 3. Run SonarScanner

Ensure SonarScanner CLI is installed and added to your system PATH.

Navigate to the project directory containing:
- Java source files
- `sonar-project.properties`

Run:

```bash
sonar-scanner
```

---

## 4. View Analysis Results

Once scanning completes successfully, open:

```plaintext
http://localhost:9000/dashboard?id=LibraryManagementSystem
```

The dashboard provides complete project metrics including:

- Lines of code
- Code smells
- Bugs and vulnerabilities
- Cyclomatic complexity
- Duplication percentage
- Technical debt estimation
- Maintainability ratings

---

# Key Findings

The analysis identified several significant architectural and maintainability issues:

- Over 350+ code smells detected
- High cyclomatic complexity
- Presence of God Classes
- Long methods with mixed responsibilities
- Tight coupling between components
- Circular dependencies across modules
- High estimated technical debt

---

# Major Architectural Problems Identified

## God Class Problem
The `Library` class contained:
- UI rendering
- Database queries
- Business logic
- Validation logic

All within a single class, violating separation of concerns.

## Feature Envy
Several methods relied excessively on external class data, indicating misplaced responsibilities.

## Tight Coupling
Presentation, database, and business layers were strongly interconnected, reducing maintainability and scalability.

## Long Methods
Large methods performed multiple responsibilities simultaneously, increasing complexity and reducing readability.

---

# Learning Outcomes

This project provided practical experience in:

- Software re-engineering
- Legacy system analysis
- Static code analysis
- Technical debt evaluation
- Architectural refactoring
- CFG generation
- AST exploration
- Complexity measurement
- Maintainability assessment

---

# Conclusion

This project demonstrates how software re-engineering techniques and modern analysis tools can be applied to legacy systems to uncover architectural weaknesses, quantify technical debt, and guide future modernization efforts.
