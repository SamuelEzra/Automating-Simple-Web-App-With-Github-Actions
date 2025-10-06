# Web App Automation with GitHub Actions

This project demonstrates how to automate testing and deployment for a simple web application using GitHub Actions.

## Project Overview

This project demonstrates a basic Node.js web application with a complete CI pipeline setup using GitHub Actions. The automation handles dependency installation, building, and testing processes automatically on every code change.

## Features

- **Simple Express Server**: Basic "Hello World" web application
- **Automated Testing**: Jest and Supertest for API testing
- **Continuous Integration**: Automated testing on every push and pull request
- **Cross-Platform Testing**: Runs on Ubuntu latest environment
- **Dependency Management**: Uses npm ci for reliable dependency installation


### Pipeline Overview

### Trigger Events

The CI pipeline is automatically triggered in the following scenarios:

- **Push to main branch**: Any direct push to the main branch
- **Pull requests to main branch**: Any pull request targeting the main branch

### Build Steps

The pipeline executes the following sequential steps:

1. **Checkout**
   - Retrieves the latest code from the repository
   - Uses `actions/checkout@v5` for reliable code checkout

2. **Node.js Setup**
   - Configures Node.js version 18 environment
   - Uses `actions/setup-node@v5` for Node.js installation
   - Ensures consistent runtime environment across executions

3. **Dependency Installation**
   - Uses `npm ci` for clean, reliable dependency installs
   - Provides faster, more consistent installations than `npm install`
   - Ideal for CI/CD environments due to deterministic behavior

4. **Build**
   - Executes build script if defined in `package.json`
   - Uses `npm run build --if-present` to avoid failures if no build script exists
   - Optional step for projects requiring compilation or bundling

5. **Testing**
   - Runs the test suite using Jest and Supertest
   - Executes `npm test` command
   - Provides immediate feedback on code quality and functionality
   - Includes both unit and integration tests for comprehensive coverage

## Setup and Installation

### Prerequisites

Before you begin, ensure you have the following installed on your system:

- **Node.js** (version 18 or higher)
- **npm** (comes bundled with Node.js)
- **GitHub account** (for repository access and CI features)

### Local Development Setup

Follow these steps to set up the project locally:

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd project-directory
   ```

2. **Install dependencies** 
   ```bash
   npm install
   ```

3. **Run the application locally**
   ```bash
   npm start
   # or
   node index.js
   ```

4. **Run tests locally**
   ```bash
   npm test
   ```
### Via GitHub Actions

The testing process is fully automated through GitHub Actions:

- **Tests automatically run** on every push to the main branch
- **Tests automatically run** on every pull request to the main branch
- **View results** in the GitHub Actions tab of your repository

### Test Coverage

The test suite includes comprehensive validation:

- **HTTP status code verification** - Ensures endpoints return correct status codes
- **Response content validation** - Verifies the actual response content matches expectations
- **Async/await support for API testing** - Handles asynchronous operations in API endpoints

## GitHub Actions Monitoring

### Viewing CI Results

To monitor your CI pipeline results:

1. **Go to your repository** on GitHub
2. **Click on the "Actions" tab** in the top navigation
3. **Select the "node.js CI" workflow** from the sidebar
4. **View individual run details and test results** for each execution
