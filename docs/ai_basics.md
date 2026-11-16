# AI
Artificial Intelligence - dziedzina, której celem jest tworzenie systemów symulujących wybrane aspekty inteligencji.

# LLM
- Large Language Model - wielki model do pracy z językiem naturalnym.
Za pomocą tokenizera, można podejrzeć jak zdanie algorytm rozbija na tokeny.

# Model AI
- wytrenowany system na ogromnych zbiorach danych do realizacji określonych zadań

# Agent
To system, który używa modelu/LLM, ale dodatkowo planuje kroki i wykonuje akcje.

## Model knowledge
- model nie widzi internetu (tzw. knowledge cutoff - wytrenowane na danych publicznych do konkretnej daty)
- nie zna prywatnych plików

1. Jak przygotować dane:
- crawling - pobieranie surowych bajtów
- filtrowanie - usuwanie reklam i śmieci
- usunięcie duplikatów - usuwanie kopii
- dataset - gotowy do treningu

2. Tokenizacja
Prosta wizualizacja przestrzeni dwuwymiarowej polega na tym, że tokeny wyciągnięte ze zdania:
- token to numer, a wektor to lista liczb przypisanych do tego numeru
- wektor tokenu zaczyna jako losowy zestaw liczb i jest stopniowo poprawiany podczas treningu

3. Sieć neuronowa i transformer
Transformer to ogromna sieć neuronowa, któa wykonuje operacje matematyczne na tych liczbach. W środku znajdują się wagi
Tu model nie widzi już słów, tylko wektory liczb (embeddingi z poprzedniego kroku)
Zadanie transformera: na podstawie kontekstu przewidzieć następny token.
Model nie zgaduje na czuja - wylicza prawdopodobieństwo i wybiera najlepszą opcję.

4. System prompt ("reżyser")
To wbudowana instrukcja, która określa jak model ma się zachowywać. Tzw. persona.
Przykłąd obrazujacy to ustawienie:
- prompt: jak zrobić kawę
- Odp persona = pirat: "Aye, szrzuce lądowy, kawa to eliksir dla prawdziwych żeglarzy, miel kawy, woda z oceanu i gotowe"
- Odp persona = nauczyciel: "Ziarna zawierają ponad 1000 związków chemicznych. parzenie to ekstrakcja. Eksperyment: zmieniaj czas parzenia i obserwuj różnice."

5. RAG - Retrieval-Augmented Generation - podpinane własnej wiedzy (dokumenty)
To opcja szczegónie używana w biznesie, gdy chcemy nakarmić AI specyficznym kontekstem bizensowym.

6. Narzędzia
- API, Web, MCP (Model-Context Protocol)
