
```ts
//katalog w którym będą testy PW  
testDir: './tests',
//odpalanie testów równolegle - testy sa puszczane rownloegle
fullyParallel: true,
// to zapobiega przypadkowemu commitowaniu test.only z developowania - PW na CI bedzie failowac, gdy ma ustawione true 
forbidOnly: !!process.env.CI

retries: process.env.CI ? 2: 0 // na CI 2 razy PW powtorzy, lokalnie 0s
workers: process.env.CI ? 1 : undefined, // lokalnie liczba workerow zalezy od liczby procesorow jakie mamy na lokalnej maszynie

// domyslnie to jest html, ale mozna zmienic na liste list:
// reporter: [[ 'html', { outputFile: 'test-results.html' }], ['list']]
reporter: 'html',

use: {
    baseURL: 'http://localhost:3000', // adres bazowy aplikacji
    trace: 'on-first-retry'
}

projects: [
{
    name: 'chromium',
    use: { ...devices['Desktop Chrome'] },
},

{
    name: 'firefox',
    use: { ...devices['Desktop Firefox'] },
},

{
    name: 'webkit',
    use: { ...devices['Desktop Safari'] },
},
]

```

test.only - tylko test z taka adnotacja bedzie uruchomiony - gdy chcemy tylko jeden test uruchomic

# tsconfig.json
Warto stworzyc pusty plik z {}, bo wtedy VSC prawidlowo bedzie podpowiadac ze skrotem ctrl + spacja 
np obok obiektu page