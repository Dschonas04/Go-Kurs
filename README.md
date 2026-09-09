# Go-Kurs

Go in vier Leveln, geprüft von `go test` -- also mit demselben Werkzeug,
mit dem in Go wirklich gearbeitet wird.

## Aufbau

Jedes Level ist ein Paket:

| Datei              | Zweck                                             |
| ------------------ | ------------------------------------------------- |
| `theorie.txt`      | Konzepte lesen und verstehen                      |
| `aufgabe.go`       | Funktionen mit `// TODO` -- hier arbeitest du      |
| `aufgabe_test.go`  | die Tests. **Nicht ändern**, sie sind die Aufgabe |

Die Musterlösungen liegen unter `loesungen/` und werden von denselben
Tests geprüft. Wer nachsieht, bevor er es versucht hat, betrügt sich
selbst -- der Test sagt dir vorher schon genau, was fehlt.

## Los geht es

```bash
./pruefen.sh             # alle Level
./pruefen.sh 2           # nur Level 2
./pruefen.sh abschluss   # die Abschlussaufgabe
./pruefen.sh --loesung   # prüft die Musterlösungen, muss grün sein
```

Oder direkt mit Go:

```bash
go test ./level1_grundlagen/
go test -run TestAddiere ./level1_grundlagen/   # ein einzelner Test
go test -v ./level2_sammlungen/                 # ausführlich
```

## Level

| Level                                        | Thema                                    |
| --------------------------------------------- | ---------------------------------------- |
| [Level 1](level1_grundlagen/)                  | Werte, Funktionen, mehrere Rückgaben, Fehler |
| [Level 2](level2_sammlungen/)                  | Slices, Maps, Structs, Methoden, Sortieren |
| [Level 3](level3_schnittstellen/)              | Schnittstellen, eigene Fehler, errors.Is/As |
| [Level 4](level4_nebenlaeufigkeit/)            | Goroutinen, Kanäle, WaitGroup, Context   |
| [Abschluss](abschluss/)                        | ein Wortzähler über mehrere Quellen      |

## Warum -race

Der Prüfer ruft `go test -race` auf. Zwei Goroutinen, die dieselbe
Variable schreiben, sind ein Fehler, auch wenn es meistens gutgeht --
solcher Code läuft monatelang und fällt dann unter Last um. Der
Race-Detector zeigt ihn sofort.

In Level 4 und im Abschluss ist das eingebaut: eine Lösung ohne Mutex
oder ohne getrennte Schreibplätze wird rot, selbst wenn die Zahlen am
Ende zufällig stimmen.

## Voraussetzungen

Go 1.22 oder neuer. Prüfen mit `go version`.
