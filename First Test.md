# Playwright Beginner Tutorial 4 | How to write 1st Test

**Source:** [https://youtu.be/wuWLpsRwB5o](https://youtu.be/wuWLpsRwB5o)
**Channel:** Automation Step by Step
**Tags:** #Playwright #Tutorial #Testing #Automation #JavaScript #Async

---

## Summary
This video is a complete walkthrough of writing a Playwright test from scratch. It covers creating the file, importing necessary modules, writing the test syntax, understanding `async/await`, performing browser actions, and adding assertions.

---

## Steps to Write Your First Test

### 1. Create a New Test File
* Test files must be located in the `tests` directory (or the directory specified in your config).
* The file name **must** end with the `.spec.js` (or `.spec.ts`) extension for the test runner to find it.
* **Example:** `my-first-test.spec.js` [00:01:58]

### 2. Import Playwright Modules
* At the top of your file, you must import the `test` and `expect` functions from the Playwright package.
* This is done using Node.js's `require` syntax.

```javascript
const { test, expect } = require('@playwright/test');
