# Playwright Test
- darmowy, open source (repozytorium na githubie) framework JS/TS do automatyzacji testów e2e: backend, frontend
- Sam Playwright to biblioteka do innych języków programowania
- silniki - chromium, edge
- nie nadaje sie: do mobile/desktop/nie wspiera starych przegladarek
- wbudowany mechanizm  auto-waiting (nie trzeba czekać ręcznie)
- wbudowane narzędzia: trace-viewer, codegen (do nagrywania testów)\

## Mechanizmy w Playwright
1. Dlaczego Playwright jest szybszy:
- Selenium - webdriver jest pośrednikiem, który komunikuje się z selenium po HTTP
- Playwright - bezpośrednio komunikuje się z chromium-based przeglądarkami po websockecie, wysyłając komendy po CDP (Chrome DevTools Protocol).
Może też komunikować się z Safari i Firefoxem, ale tylko ze specjalnymi wersjami tych przeglądarek, żeby też umiał rozmawiać po websockecie

2. Auto waiting
Pod spodem PW sprawdza:
- czy element jest klikalny (widoczny i aktywny)
- jak nie jest, to czeka
`await elementLocator.click();`

3. Asynchroniczność
- wbudowana w TS - wiele akcji może być wykonywanych w tym samym momencie
- w testach e2e na ogół nie chcemy z tego korzystać, dlatego trzeba używać await - metody asynchroniczne są wykonywane synchronicznie
- asynchroniczność sięprzydaje, gdy chcemy monitorować zdarzenia podczas testów, np. zalogować coś w konsoli:
```ts
page.on('console', msg => {
    if (msg.type() === 'error') {
        console.error('[console.error]', msg.text());
    }
})
```

4. Przechwytywanie ruchu sieciowego
- cały ruch sieciowy (w tym requesty do backendu) przechodzi przez PW, więc możemy monitorować i reagować na odpowiedzi backendu, a także
możemy mockować odpowiedzi backednu
