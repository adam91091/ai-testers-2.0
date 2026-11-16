# Instalacja Playwright
- node --version
- npm init playwright@latest
- npx playwright test

Playwright instaluje przegladarki w katalogu C:\Users\kfea\AppData\Local\ms-playwright\..
np. firefox-1555

# Skrypt
- package.json: scripts {"test": "npx playwright test"}
- potem: npm run test

# Rozszerzenia w VSC
- playwright test for VSCode
- jaktestowac - playwright helpers

## Test w Playwright
```ts
import { test, expect } from '@playwright/test';

// deklaracja testu - funkcja strzałkowa
// destrukturyzacja - PW wstrzykuje do funkcji różne potrzebne obiekty, m in page
// page reprezentuje stronę w przeglądarce - playwright uruchamia przegladarke, gdy ma podpiety obiekt page!!
test('get started link', async ({ page }) => {
    // cialo testu
    await page.goto('https://playwright.dev/');

    // Create a locator for the "Get started" link.
    const elementLocator = page.getByRole('link', { name: 'Get started'});

    // Click the get started link.
    await elementLocator.click();

    await expect(page.getByRole('heading', { name: 'Installation'})).toBeVisible();
});
```

### Inne obiekty: request (do api)
```ts
import { test, expect } from '@playwright/test';

// deklaracja testu - funkcja strzałkowa
// destrukturyzacja - PW wstrzykuje do funkcji różne potrzebne obiekty, m in page
// page reprezentuje stronę w przeglądarce
test('get started link', async ({ request }) => {

    // Create a locator for the "Get started" link.
    const response = await request.get("/api");

    await expect(response.status()).toBe(200);
});
```

## Lokatory
- tworzony za pomoca roznych metod
```ts
const elementLocator = page.getByRole('link', {name: "Get started"})
```

## Selektory
#### CSS
- krotszy i latwiejszy do zapisu, powszechnie uzywany, ale mniej mozliwosci niz XPath
Na ogól używa się CSS, a XPath w rzadkich przypadkach.

##### Atrybut id
- Latwy do zastosowania w CSS, ale nie zawsze unikalny i stosowany
- "#id-label-element"

##### data-testid
- podobny do ID, ale stworzony z mysla o testach
- latwy do zazstosowania w CSS, ale nie zawsze unikalny i stosowany
- "[data-testid=dit-btn-element]"
- page.getByTestId(selectorValue);

### XPath
- trudniejszy i dluzszy w zapisie, ale ma czasem wiecej mozliwosci
- XPath: - "//*[@id='id-label-element']"

## Skroty
- ctrl + spacja

## Asercje
### Podstawowa
```ts
expect(await page.getByText('welcome').isVisible()).toBe(true)
```

### Web First Assertions
- PW czeka na dany element w asercji + automatyczne ponawianie sprawdzenia stanu elementu
- Czekanie odbywa sie tylko gdy do asercji przekażemy lokator
```ts
await expect(page.getByText('welcome')).toBeVisible();
```

