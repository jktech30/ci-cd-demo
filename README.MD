
## Project Setup

1.Install Node.js on your local machine (version 10.9.3 recommended)

Windows/MacOS: Download Node.js and install it.

Linux (Ubuntu)


```bash
  Sudo apt update
  sudo apt install nodejs npm
```

Verify Installation

```bash
  node -v
  npm -v
```

2.Clone the Repository(if not already done):

```bash
  git clone https://github.com/jktech30/ci-cd-demo.git
  cd ci-cd-demo
```
3.Initialize Node project:

```bash
  npm init -y
```
4.Create Main Script:

```bash
  echo 'console.log("This is my DevOps Assessment!");' > index.js
```

## Running Locally

1.Install project dependencies:

```bash
  npm install
```
2..Install dev dependencies (Jest)
```bash
 npm install --save-dev jest
```
## Testing

1.Create a test Folder and Test File:

```bash
  mkdir tests
  echo 'test("Sample test", () => { expect(2+2).toBe(4); });' > tests/sample.test.js
```
2.Run Test Locally
```bash
 npm test
```
3.Run Mock Deploy
```bash
 npm run deploy
```
4.Example of a test result:
```bash
 PASS  tests/sample.test.js
 √ Sample test (5 ms)
```

## CI/CD Workflow

The project uses GitHub Actions to automatically run tests on every push or pull request to the main branch
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
       node-version: '18'

   - name: Install dependencies
     run: npm install

   - name: Install dev dependencies
     run: npm install --save-dev jest

   - name: Run Jest tests
     run: npm test

   - name: Run main script
     run: node index.js

   - name: Deploy (Mock)
      run: echo "Deploying application..."

Note: ubuntu-latest is used in the CI runner, while locally I use Windows
```
## Command History
```yaml
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
```
## Resources

https://github.com/CleverseAcademy/nodejs-cicd

https://readme.so/editor

📘 Node.js Basics
Official Docs: https://nodejs.org/en/docs/
Node.js Tutorial for Beginners (YouTube, freeCodeCamp): https://www.youtube.com/watch?v=RLtyhwFtXQA

🧪 Jest Testing
Jest Official Docs: https://jestjs.io/docs/getting-started
Beginner Tutorial (YouTube): https://www.youtube.com/watch?v=7r4xVDI2vho

⚙️ GitHub Actions / CI/CD
GitHub Actions Official Docs: https://docs.github.com/en/actions
Quickstart Guide: https://docs.github.com/en/actions/quickstart
Simple Node.js CI/CD Tutorial: https://www.freecodecamp.org/news/ci-cd-with-github-actions/

📖 General CI/CD Concepts
CI/CD Explained for Beginners: https://www.redhat.com/en/topics/devops/what-is-ci-cd
GitHub Actions Workflow Syntax: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions

## Author
Jayzeer Bronx Laurejas

Demo DevOps CI/CD Assessment
