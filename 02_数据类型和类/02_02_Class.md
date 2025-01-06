

# 1 Basics

Originales Typescript
```ts
class Student {
    firstname: string="";
    lastname: string="";
    studentId: number=0;
}

let max=new Student();

max.firstname="Max";
max.lastname="Müller";
max.studentId=123456;

console.log(max.firstname+" "+max.lastname+", "+max.studentId);
```
- Konstruktoren und prototypische Vererbung (nicht behandelt) ermöglichen die Programmierung wiederverwendbarer Komponenten
- Dritte Möglichkeit: Programmierung von _**Klassen**_ (classes)
- Alle Objekte mit denselben Eigenschaften gehören zur selben Klasse
- Einleitung mit dem Schlüsselwert `**class**`



Kompiliertes JavaScript
```js
"use strict";
var Student = /** @class */ (function () {
    function Student() {
        this.firstname = "";
        this.lastname = "";
        this.studentId = 0;
    }
    return Student;
}());
var max = new Student();
max.firstname = "Max";
max.lastname = "Müller";
max.studentId = 123456;
console.log(max.firstname + " " + max.lastname + ", " + max.studentId);
```
- Klassen definieren die Eigenschaften in Form von Eigenschaftsname und Datentyp und optional einen Konstruktor
- Wird kein Konstruktor definiert, wird bei der Compilierung zu JavaScript ein leerer Konstruktor erzeugt
- Instanziierung eines Objektes von seiner Klasse erfolgt durch Aufruf des zugehörigen Konstruktors


# 2 Klassen mit Konstruktoren und anderen Methoden


Originales Typescript
```ts
class Student {
  firstname: string;
  lastname: string;
  studentId: number;

  display(): void {
    console.log(this.firstname+" "+
                this.lastname+", "+
                this.studentId)
  }

  constructor(fn:string, ln:string, id:number) {
    this.firstname=fn;
    this.lastname=ln;
    this.studentId=id;
  }
}

let max=new Student("Max", "Müller", 123456);
max.display();
```
- Beispiel zeigt die Definition einer Klasse mit einem Konstruktor und einer Funktion
- Der Konstruktor wird innerhalb der Klasse mit dem Schlüsselwort `**constructor**` definiert und nicht mit dem Namen der Klasse



Kompiliertes JavaScript
```js
"use strict";
var Student = /** @class */ (function () {
  function Student(fn, ln, id) {
    this.firstname = fn;
    this.lastname = ln;
    this.studentId = id;
  }
  Student.prototype.display = function () {
    console.log(this.firstname + " " + 
                this.lastname + ", " + 
                this.studentId);
  };
  return Student;
}());
var max = new Student("Max", "Müller", 123456);
max.display();
```


# 3 Zugriffsmodifikatoren (get Function)


```ts
class Student {
  private firstname: string;
  private lastname: string;
  private studentId: number;
  protected studienfach: string;

  public getFirstname(): string {
    return this.firstname;
  }
  
  public getLastname(): string {
    return this.lastname;
  }
  
  public getStudentId(): number {
    return this.studentId;
  }

  constructor(fn:string, ln:string, id: number) {
    this.firstname=fn;
    this.lastname=ln;
    this.studentId=id;
  }
}

```

- Die Eigenschaften einer Klasse können um Zugriffsmodifikatoren (Access Specifiers) ergänzt werden
- Zugriffsmodifikatoren legen fest, aus welchen Umgebungen (globale Ebene, andere Objekte) auf die Eigenschaften zugegriffen werden kann
- public: auf die Eigenschaft kann von überall aus zugegriffen werden - dies ist der Standardzugriff für alle Eigenschaften, die keinen Zugriffsmodifikator haben
- private: auf die Eigenschaft kann nur von innerhalb des Objektes zugegriffen werden, welches die Eigenschaft enthält
- protected: auf die Eigenschaft kann nur von den Objekten zugegriffen werden, die von der derselben Klasse (oder ihrer Unterklassen) instanziiert wurden

# 4 Vererbung 

```ts
class Person {
  private firstname: string;
  private lastname: string;

  public getFirstname(): string {
    return this.firstname;
  }
  
  public getLastname(): string {
    return this.lastname;
  }

  constructor(fn:string, ln:string) {
    this.firstname=fn;
    this.lastname=ln;
  }
}

class Student extends Person {
  private studentId: number=0;
  protected studienfach: string="";

  public setStudentId(id: number):void {
    this.studentId=id;
  }
  public getStudentId(): number {
    return this.studentId;
  }
}

let max=new Student("Max", "Müller");
max.setStudentId(123456);
```

- Klassen können die Eigenschaften anderer Klassen mithilfe des Schlüsselworts `**extends**` erben
- Die vererbende Klasse ist die _**Superklasse**_ (_**Vaterklasse**_), die erbende Klasse die _**Unterklasse**_ (_**Kindklasse**_)
- TypeScript und JavaScript unterstützen nur die einfache Vererbung, d.h. jede Klasse kann maximal nur eine direkte Superklasse haben
- Definiert die Unterklasse keinen Konstruktor, so wird der Konstruktor der Superklasse aufgerufen, allerdings mit dem Namen der Unterklasse

---

## 4.1 Zugriffsmodifikator in Vererbung 


```ts
class Person {
...
}

class Student extends Person {
  private studentId: number=0;
  protected studienfach: string="";

  public setStudentId(id: number):void {
    this.studentId=id;
  }
  public getStudentId(): number {
    return this.studentId;
  }

  public getFirstname(): string {
    return super.getFirstname().toUpperCase();
  }

  public getLastname(): string {
    return super.getLastname().toUpperCase();
  }

  constructor(fn: string, ln: string, id: number) {
    super(fn, ln);
    this.studentId=id;
  }
}

let max=new Student("Max", "Müller", 123456);
max.setStudentId(123456);
```


- Eine Unterklasse kann die Eigenschaften ihrer Superklasse _**überschreiben**_ (_**overriding**_)
- Überschreibende und überschriebene Eigenschaft müssen denselben Namen, Datentyp und Zugriffsmodifikator haben
- Eigenschaften mit dem Zugriffsmodifikator `**private**` dürfen nicht überschrieben werden
- Der Datentyp eines Rückgabeparameters einer überschreibenden Funktion muss derselbe Datentyp wie der Rückgabeparameter der überschriebenen Funktion sein
- Die überschriebene Funktion einer Superklasse kann anstelle der überschreibenden Funktion durch den Präfix **`super.`**  aus der Unterklasse aufgerufen werden
- Wird der Konstruktor der Superklasse überschrieben, so muss der Konstruktor der Unterklasse den der Superklasse durch `**super(...)**` als erste Anweisung aufrufen
