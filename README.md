
# ✅ End-to-End Playwright Testing Guide (for Beginners)

**Goal**: Automate tests for `https://example.com` using Playwright, including:
- Page title validation  
- Verifying a link  
- Clicking and checking redirection

---

## 🧩 Step 1: Install Node.js (If not already installed)

🔗 Download from: https://nodejs.org/en/download

After installation, verify with:

```bash
node -v
npm -v
```

---

## 🏗️ Step 2: Create a New Project Folder

```bash
mkdir playwright-example
cd playwright-example
```

---

## 📦 Step 3: Initialize Playwright

```bash
npm init playwright@latest
```

Choose:
- JavaScript (or TypeScript if you prefer)
- Yes to install Playwright Test
- Yes to install browser binaries

---

## 🧪 Step 4: Create Your Custom Test File

Inside the `tests` folder, create:

```bash
touch example.spec.js
```

Paste the following inside `example.spec.js`:

```javascript
const { test, expect } = require('@playwright/test');

test('Test Case 1: Validate page title', async ({ page }) => {
  await page.goto('https://example.com');
  await expect(page).toHaveTitle(/Example Domain/);
});

test('Test Case 2: Verify More Information link is visible', async ({ page }) => {
  await page.goto('https://example.com');
  const link = page.locator('text=More information');
  await expect(link).toBeVisible();
});

test('Test Case 3: Verify redirect to iana.org', async ({ page }) => {
  await page.goto('https://example.com');
  await page.click('text=More information');
  await expect(page).toHaveURL(/iana\.org/);
});
```

---

## 🚀 Step 5: Run the Test

**Run all tests:**

```bash
npx playwright test
```

**Run in UI Mode:**

```bash
npx playwright test --ui
```

---

## 🗂️ Optional: Enable Trace Viewer

Edit `playwright.config.js`:

```js
use: {
  trace: 'on-first-retry',
},
```

To view trace:

```bash
npx playwright show-trace trace.zip
```

---

## 📋 Test Case Summary

| Test Case | Description | Expected Result | Actual Result |
|-----------|-------------|-----------------|----------------|
| 1 | Visit site & check title | Title = “Example Domain” | ✅ Passed |
| 2 | Check if link is visible | Link = “More information...” | ✅ Passed |
| 3 | Click link & verify URL | URL = `https://www.iana.org` | ✅ Passed |

---

## 📚 Extra Tips for QA Projects

- Use `test.describe()` for grouping
- Use `test.beforeEach()` for setup
- Prefer `page.locator()` over direct selectors
- Add meaningful assertions with `.toHaveText()`, `.toBeVisible()`

---

## 🧾 Bonus: Common Playwright CLI Commands

| Command | Purpose |
|--------|---------|
| `npx playwright test` | Run all tests |
| `npx playwright test example.spec.js` | Run specific test |
| `npx playwright test --ui` | Run in visual mode |
| `npx playwright codegen` | Generate test code |
| `npx playwright show-trace trace.zip` | View trace |

