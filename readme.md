# Bruno API Testing Project

This repository contains a Proof of Concept for API testing using Bruno, an open-source API client that makes testing and debugging APIs easy and efficient.

## Table of Contents

- [Installation](#installation)
- [Running Tests](#running-tests)
- [Generating Reports](#generating-reports)

## Installation

### Desktop Application

1. Download the latest version of Bruno desktop application from the official website:
   - [Bruno Downloads](https://www.usebruno.com/downloads)
   - Available for macOS, Windows, and Linux

2. Install the downloaded application following your operating system's standard installation procedures.

### Command Line Interface

Install Bruno CLI globally using npm:

```bash
npm install -g @usebruno/cli
```

Or using Homebrew (macOS):

```bash
brew install usebruno/tap/bruno
```

Verify installation:

```bash
bru --version
```
## Running Tests

### Using Desktop Application

1. Open Bruno desktop application
2. Click on "Open Collection"
3. Navigate to your `JsonPlaceholder` directory
4. Select any request in the sidebar to run it
5. Click the "Send" button to execute the request

### Using Command Line Interface

Run a single request:

```bash
bru run get-users.bru --env Production
```

Run all requests in a directory:

```bash
bru run . --env Production
```

## Generating Reports

Bruno CLI allows generating reports in various formats to document test results.

### HTML Reports

Generate an HTML report:

```bash
bru run . --env Production --reporter-html results.html 
```

This creates a visually appealing HTML report with all request details, responses, and test results.

### JSON Reports

Generate a JSON report:

```bash
bru run . --env Production --reporter-json results.json 
```

The JSON report can be used for integration with other tools or custom processing.

### JUnit Reports (for CI/CD integration)

Generate a JUnit XML report for CI/CD pipeline integration:

```bash
bru run . --env Production --reporter-junit results.xml
```

## Continuous Integration

To run Bruno tests in CI/CD pipelines, add the following to your workflow:

```yaml
- name: Install Bruno CLI
  run: npm install -g @usebruno/cli

- name: Run API Tests
  run: bru run collection --reporter junit --output reports/junit-report.xml

- name: Publish Test Results
  # Add your CI-specific step to publish JUnit results
```
