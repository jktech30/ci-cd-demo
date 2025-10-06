## Project Setup
1. **Install Node.js** on your local machine (version 10.9.3 recommended):
   - **Windows/macOS**: [Download Node.js](https://nodejs.org/) and install it.
   - **Linux (Ubuntu)**:
     ```bash
     sudo apt update
     sudo apt install nodejs npm
     
   - Verify installation:
     ```bash
     node -v
     npm -v

2. **Clone the repository** (if not already done):
   ```bash
   git clone https://github.com/jktech30/ci-cd-demo.git
   cd ci-cd-demo

3.** Initialize Node project:
   ```bash
    npm init -y

4. ** Create main script:
echo 'console.log("This is my DevOps Assessment!");' > index.js

 ## Running Locally

1. Install project dependencies:
     ```bash
    npm install

2. Install dev dependencies (Jest)
     ```bash
    node index.js

## Testing

1. Create test folder and test file:
    ```bash
      mkdir tests
      echo 'test("Sample test", () => { expect(2+2).toBe(4); });' > tests/sample.test.js

2. Run tests locally
    ```bash
     npm test

3. Example of a test result:
    ```bash
     PASS  tests/sample.test.js
    √ Sample test (5 ms)


## CI/CD Workflow
- The project uses GitHub Actions to automatically run tests on every push or pull request to the main branch
    ```yaml

name: CI/CD Pipeline

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build-and-test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '10.9.3'

      - name: Install dependencies
        run: npm install

      - name: Install dev dependencies
        run: npm install --save-dev jest

      - name: Run Jest tests
        run: npm test

      - name: Run main script
        run: node index.js

Note: ubuntu-latest is used in the CI runner, while locally I use Windows

## Command History

npm init -y
echo 'console.log("This is my DevOps Assessment!");' > index.js
mkdir tests
echo 'test("Sample test", () => { expect(2+2).toBe(4); });' > tests/sample.test.js
npm install --save-dev jest
npm test
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/jktech30/ci-cd-demo.git
git push -u origin main
mkdir -p .github/workflows
# Created ci.yml workflow file
git add .github/workflows/ci.yml
git commit -m "Add CI/CD workflow"
git push


Author
Jayzeer Bronx Laurejas
Demo DevOps CI/CD project

