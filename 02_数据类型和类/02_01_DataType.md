
# 1 Die Typhierarchie von TypeScript

![](image/Pasted%20image%2020250106110747.png)



# 2 Typannotationen


 Originales Typescript
```js
let alter: number=32;
let teilnehmer: string="Michael Maier";
let bezahlt: boolean=true;

function addiere(a: number, b: number): number {
  return a+b;
}

let vorlesung: {
  id: number,
  name: string,
  einschreibepflichtig: boolean
}

vorlesung={
  id: 122,
  name: "Webtechnologien",
  einschreibpflichtig: true
}
```

Kompiliertes JavaScript
```js
let alter=32;
let teilnehmer="Michael Maier";
let bezahlt=true;

function addiere(a, b) {
  return a+b;
}

let vorlesung;
vorlesung={
  id: 122,
  name: "Webtechnologien",
  einschreibpflichtig: true
}
```


- TypeScript ist eine typisierte Sprache, bei der die Datentypen von Variablen, Funktionsparametern und Objekteigenschaften (optional) explizit spezifiziert werden können (_**Typannotationen**_)
- Angabe des Datentyps erfolgt hinter dem Namen der Variablen/des Parameters/der Eigenschaft getrennt durch einen Doppelpunkt


# 3 Variablendeklaration


```ts
let vorlesung: string = "Webtechnologien";  // 1: Deklaration und Initialisierung in einer Anweisung
let vorlesung: string;  // 2 Deklaration aber keine Initialisierung – Wert wird auf **`undefined`** gesetzt
let vorlesung="Webtechnologien";  // 3: Keine Deklaration aber Initialisierung – Datentyp wird durch Typinferenz während der Kompilierung aus dem zugewiesenen Wert abgeleitet
let vorlesung;   // 4: Keine Deklaration, keine Initialisierung – Datentyp wird auf `**undefined**` gesetzt und Wert wird auf `**undefined**` gesetzt

```

## 3.1 Typinferenz  数据类型的推导

![](image/Pasted%20image%2020250106111625.png)

- Bei den Methoden 3 und 4 der Variablendeklaration wird der Datentyp mittels Typinferenz während der Compilierung bestimmt
- Bei Methode 3 erfolgt die Typinferenz bei der Deklaration der Variablen (Abbildung linke Seite), und die Variable muss den abgeleiteten Datentyp bis zum Ende der Laufzeit behalten
- Bei Methode 4 erfolgt die Typinferenz bei der ersten Zuweisung eines Wertes (Abbildung rechte Seite), und der Datentyp der Variablen kann sich zur Laufzeit ändern