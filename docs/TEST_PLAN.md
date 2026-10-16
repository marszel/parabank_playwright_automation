#Master Test Plan – ParaBank Automation Project

## 1. Test Plan Identifier
PB-PLAYWRIGHT-MTP-V1.0

## 2. Introduction & Purpose
This document describes the Master Test Plan for the ParaBank automation project. The goal is to design and execute an automated regression test suite using Python and Playwright, built with Page Object Pattern and ready for CI/CD pipelines.

## 3. Test Item
The test item is the ParaBank web application, which includes:
* Customer Portal: https://parabank.parasoft.com/parabank/index.htm
* Administration Console: https://parabank.parasoft.com/parabank/admin.htm

## 4. Scope of Testing
### 4.1 Features in Scope
Core Banking Modules (Customer-Facing)
* User Registration: Creating a new customer account with form validation.
* Authentication: Successful log in, negative paths (invalid credentials), and secure log out.
* Account Overview: Checking account balances and viewing transaction history.
* Transfer Funds: Transferring money between internal accounts.

Administration Console (/admin.htm)
* Database Control: Automating state reset using the "Initialize" and "Clean" buttons to ensure clean test data.
* JMS Service Management: Switching the JMS Service status between "Running" and "Shutdown" to test system behavior during service downtime. 
* Data Access Mode Switching: Changing backend communication methods between SOAP, REST (XML), REST (JSON), and JDBC, and verifying application stability.
* Application Settings Customization: Changing global bank thresholds such as Initial Balance, Minimum Balance, and Loan Providers to test dynamic bank behavior.

### 4.2 Out of Scope
* Security Testing: Performing penetration testing, SQL injection checks, or vulnerability scans, as the focus is strictly on functional verification.
* Performance & Load Testing: Measuring server response times, stress testing endpoints, or evaluating application stability under heavy user load.
* Mobile UI Compatibility Testing: Verifying responsive designs, mobile layouts, or native mobile browser views (testing is strictly limited to desktop Chromium).

## 5. Environmental Needs
* Operating System: Linux Ubuntu 26.04 (for both local development and CI/CD GitHub Actions runner).
* Programming Language: Python 3.11+ (using isolated virtual environment .venv).
* Testing Frameworks: Pytest (as the test runner and assertion library) with pytest-asyncio.
* Automation Tool: Playwright (Python async API).
* Target Browser: Desktop Chromium (running in headful mode for local debugging and headless mode for pipelines).

## 6. Entry & Exit Criteria
### 6.1 Entry Criteria
* Network Accessibility: Continuous access to the internet and availability of the public ParaBank platform.
* Environment Configuration: Successful creation of the local virtual environment (.venv) with all required Python libraries installed.
* Repository Readiness: Active and verified connection to the public GitHub repository for code management.

### 6.2 Exit Criteria
* Execution Rate: 100% of the planned automated test scenarios are developed and executed.
* Pass Rate: Achieving a minimum 95% Pass Rate in the automated regression suite, with any failures analyzed and confirmed as external environment instability.
* Framework Architecture: Successful structuring of all code according to the Page Object Model (POM) design pattern.
* Code Deployment: All final code, including configurations and GitHub Actions workflows, successfully pushed to the main branch.

## 7. Suspension & Resumption Criteria
### 7.1 Suspension Criteria
* Immediate suspension of automated test execution if the ParaBank application is down (returning 5xx HTTP server errors) or if major UI changes completely break element locators across multiple test suites.

### 7.2 Resumption Criteria 
* Resuming test execution once the test environment is verified as stable or after updated element locators are successfully deployed and verified in the repository.

## 8. Risks & Mitigations
* Risk 1 (Shared Public Environment): Other global users modifying bank settings or cleaning the database at the same time, causing test failures.
    * Mitigation: Resetting the database using the "Initialize" button in /admin.htm before running critical tests.
* Risk 2 (Network Flakiness): Internet connection drops causing sudden timeout errors during tests.
	* Mitigation: Using built-in Playwright smart waiting (expect assertions) instead of hardcoded sleep commands.

