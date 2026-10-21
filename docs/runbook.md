# Runbook

## Start locally

```bash
npm install
npm run dev
```

## Check that it works

Open http://localhost:9000 in your browser.

You should see the application's home page without errors.

## Run the tests

```bash
npm test
```

## When something breaks

1. Check that dependencies are installed:
   ```bash
   npm install
   ```

2. Check that required environment variables and `.env` files are present.

3. Check terminal logs and run the test suite:
   ```bash
   npm test
   ```
