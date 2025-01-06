

# 1 Dynamische versus Statische Typisierung

![](image/Pasted%20image%2020250106110336.png)

- ==TypeScript verwendet _**statische Typisierung==**_
- Typprüfungen finden während der Compilierung (oder bereits während der Erstellung des Programms im Editor) statt
- Typprüfung basiert auf explizierter Deklaration von Datentypen (im Gegensatz zu JavaScript) oder Typinferenz (wie bei JavaScript)
- Fehler werden so häufig während der Programmierung oder spätestens bei der Compilierung erkannt


# 2 Die Übersetzung von Typescript zu JavaScript

![](image/Pasted%20image%2020250106110530.png)


- TypeScript-Programme können nicht im Browser und in Node.js ausgeführt werden, sie müssen zuvor in JavaScript übersetzt werden
- TypeScript-Quellcode wird zunächst geparst (Übersetzung in standardisierte, bereinigte Syntax) und in einen Abstract Syntax Tree übersetzt
- Anschließend überprüft der Type Checker die Korrektheit des Programms in Bezug auf Typisierung von Variablen, Parametern und Eigenschaften
- Danach wird TypeScript und JavaScript übersetzt und kann dann durch einen Browser oder Node.js ausgeführt werden
- Die Ziel-JavaScript-Version kann mit der Compiler-Option `**-target**` spezifiziert werden ("`**ES3**`" Standard, "`**ES5**`", "`**ES6**`")
- Hinweis: für Node.js existiert eine Erweiterung mit der TypeScript ohne Kompilierung ausgeführt werden kann (Installation durch `**npm install -g ts-node**`)
- Hinweis: für Google Chrome existiert das Plugin TypeScript-Console



