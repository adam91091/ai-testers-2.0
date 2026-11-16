# Trace
Interaktywny podgląd przebiegu i wyniku testów ze stanem aplikacji i całym ruchem sieciowym.

w playwright.config.ts mamy ustawienie:
- wlaczenie na on jest ryzykowne, bo to zajmuje duzo miejsca. dlatego domyslnie jest 'on-first-retry'
```
use: {
    baseURL: "...",
    trace: 'on',
}
```

Uruchomienie:
`npx playwright show-trace .\test-results\example-get-started-link-chromium\trace.zip`

# UI Mode
- npx playwright test --ui

# Raporty
Domyślnie jest robiony html.

playwright.config.ts:
```ts
reporter: [[ 'html'], ['list'], ['json'], ['junit']]
```
Również we wtyczce playwright jaktestowac jest zakladka reports.

# Timeouty
w playwright.config.ts możemy ustawić różne maksymalne czasu dla:
- trwania jednego testu
- trwania całego zestawu testów
- asercji
- akcji na stronach
```ts
    globalTimeout: 60000, // 60 s - uruchomienie wszystkich testów musi sie zmiescic w 60s
    timeout: 30000, //ile dany test moze maksymalnie trwac
    expect {
        timeout: 5000, //dla web asercji timeout 5s
    },
    use: {
        actionTimeout: 10000 //timeout na jedną akcję testu
    }
```