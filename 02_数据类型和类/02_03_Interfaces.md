


# 5 Interfaces 

```ts
interface Person {
  firstname: string;
  lastname: string;
}

function printBadge(person: Person) {
  console.log(person.firstname+" "+person.lastname)
}

let max={firstname: "Max", lastname: "Müller"};
printBadge(max);

let moritz={firstname: "Moritz", lastname: "Maier", alter: 22};
printBadge(moritz);

let idefix={firstname: "Idefix", alter: 7};
printBadge(idefix);   // Fehler 
```

- Interfaces legen die Signatur von Objekten fest, d.h. die Namen und Datentypen ihrer Eigenschaften
- Interfaces werden verwendet, um eigene Datentpyen zu erstellen
- Interfaces werden auch als _**strukturelle Verträge**_ (_**structural contracts**_) bezeichnet, welche die Eigenschaften von Objekten erzwingen
- Interfaces können nicht instanziiert werden - sie haben keinen ausführbaren Code und keine konkreten Werte als Eigenschaften
- JavaScript kennt das Konzept der Interfaces nicht, es wird in TypeScript ausschliesslich zum Type Checking verwendet
- Um den "Vertrag des Interfaces zu erfüllen", muss das Objekt mindestens die definierten Eigenschaften und ihre Datentypen haben, optional kann das Objekt aus weiteren Eigenschaften bestehen


