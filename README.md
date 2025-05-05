# Szachy w C na NUCLEO-L476RG

## Opis

Projekt implementuje grę w szachy w języku C na płytce rozwojowej NUCLEO-L476RG. Gra wykorzystuje wyświetlacz OLED do prezentacji szachownicy i figur oraz własny, niestandardowy silnik szachowy do obsługi logiki gry i ruchów komputera.

## Sprzęt

* Płytka rozwojowa: **NUCLEO-L476RG**
* Wyświetlacz: **OLED SSD1306** (podłączony przez SPI lub I2C)
* Komunikacja: **UART** (do wprowadzania ruchów i wyboru trybu gry)

## Oprogramowanie / Funkcje

* **Język:** C
* **Silnik szachowy:**
    * Własna implementacja.
    * Algorytm **Minimax** z odcięciami alfa-beta do podejmowania decyzji przez komputer.
    * Funkcja oceny (`eval`) wykorzystująca tablice wartości pól dla poszczególnych figur (Piece-Square Tables).
* **Tryby gry:**
    * Gracz kontra Komputer
    * Gracz kontra Gracz
* **Interfejs użytkownika:**
    * Graficzna reprezentacja szachownicy i figur na wyświetlaczu OLED.
    * Wprowadzanie ruchów w notacji algebraicznej (np. "e2e4") przez terminal UART.
    * Menu startowe do wyboru trybu gry.
    * Wyświetlanie czasu dla obu graczy.
    * Informacje o stanie gry (np. Szach, Mat, Pat, Wygrana).
* **Logika gry:**
    * Walidacja ruchów (sprawdzanie poprawności notacji i legalności ruchu na szachownicy).
    * Wykrywanie szacha (`isCheck`).
    * Wykrywanie mata i pata (`isMate`).
    * Obsługa promocji pionka.
    * Obsługa poddania partii ('r').
* **Dodatkowe:**
    * Funkcja wyświetlająca autorów projektu w formie graficznej.

## Jak to działa

1.  **Inicjalizacja:** Program inicjalizuje sprzęt (zegar systemowy, GPIO, UART, I2C/SPI, wyświetlacz OLED).
2.  **Menu główne:** Wyświetla menu pozwalające wybrać tryb gry (PvP, PvC) lub wyświetlić autorów.
3.  **Pętla gry:**
    * Wyświetla aktualny stan szachownicy i figur.
    * Wyświetla czas pozostały dla graczy.
    * Sprawdza stan gry (szach, mat, pat).
    * Czeka na ruch gracza (wprowadzany przez UART) lub wykonuje ruch komputera.
    * **Ruch gracza:** Odczytuje ruch z UART, waliduje go i jeśli jest poprawny, aktualizuje stan szachownicy.
    * **Ruch komputera (w trybie PvC):** Uruchamia algorytm `minimax` do znalezienia najlepszego ruchu, a następnie aktualizuje stan szachownicy.
    * Zmienia aktywnego gracza.
    * Pętla powtarza się do zakończenia gry (mat, pat, poddanie, koniec czasu).

## 📸 Zdjecia
![6e6140be-1f8d-434f-bbc2-756d7ee9e1a0](https://github.com/user-attachments/assets/3fc0f25a-0ac2-401b-ac96-b9f288a7918a)



https://github.com/user-attachments/assets/9630485f-4461-416b-83ef-c46742a37a0d



## Autorzy 

* Jedrzej Steckiewicz
* Marcin Gieniusz
* Mateusz Maka
* Ambrozy Zubrycki
