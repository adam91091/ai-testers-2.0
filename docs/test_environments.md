# BaseUrl pattern dla wielu środowisk testowych

Konfiguracja projektów w playwright test:
Opcja 1:
- https://playwright.dev/docs/test-projects
W playwright.config.ts dodajemy:
```ts
 projects: [
    {
      name: 'local',
      use: {
        ...devices['Desktop Chrome'],
        baseURL: 'https://localhost:3000'
      },
    },
    {
      name: 'dev',
      use: {
        ...devices['Desktop Chrome'],
        baseURL: 'http://staging.example.test/'
      },
    },
],
```
`npx playwright test --project=local`

Opcja 2: envvars
```ts
import { defineConfig } from '@playwright/test';
import dotenv from 'dotenv';
import path from 'path';
dotenv.config();
export default defineConfig({
  use: {
    baseURL: process.env.STAGING === '1' ? 'http://staging.example.test/' : 'https://localhost:3000',
  }
});
```

Plik .env:
STAGING=0

Uruchamianie testów: `$env:STAGING="1"; npx playwright test `
