

# 1 BENANNTE EXPORTS

- Neben Klassen sind Module eine weitere Möglichkeit der Strukturierung großer TypeScript/JavaScript-Programme
- Module verteilen den Code eines Programms auf mehrere Dateien
- Ein Modul besteht aus einer Anzahl von Funktionen, Objekten und Variablen, die mit dem Präfix **export** gekennzeichnet sind und die somit in andere Dateien importiert werden können
- Benannte Exports können mehrfach in einem Modul vorkommen und können in der importierenden Datei unter ihrem Namen verwendet werden
- Import erfolgt mittels des Schlüsselworts import unter Angabe des Pfades der exportierenden Datei
- Verschiedene Syntaxen für import (siehe Beispiele)


./studentModule.ts
```ts
export class Student {
  firstname: string;
  lastname: string;
  studentId: number
}

export function displayStudent(student: Student):void {
  console.log(student.firstname+" "+student.lastname)
}
```

```ts
export class Student {
  firstname: string="";
  lastname: string="";
  studentId: number=0;
}

export function displayStudent(student: Student):void {
  console.log(student.firstname+" "+student.lastname)
}
```

```ts
import {Student} from "./studentModule"
import {displayStudent} from "./studentModule"

let max=new Student();
max.firstname="Max";
max.lastname="Müller";
displayStudent(max);
```


```ts
import {Student, displayStudent} from "./studentModule"
```


```ts
import * as studentHelpers from "./studentModule"

let max=new studentHelpers.Student();
max.firstname="Max";
max.lastName="Müller";
studentHelpers.displayStudent(max);
```


# 2 Default Exports

- Ein _**Default Export**_ wird mit dem Infix `**default**` gekennzeichnet und darf nur einmal pro Modul vorkommen
- Beim Import kann dem importierten Code ein frei wählbarer Name zugeordnet werden
    - 自己可以任意起个名字
- Beachte: Module mittels `**export**` und `**import**` sind in TypeScript und JavaScript ab ES6 gleichermaßen vorhanden

./studentModule.ts
```ts
export default class Student {
  firstname: string="";
  lastname: string="";
  studentId: number=0;
  
  displayStudent():void {
    console.log(this.firstname+" "+this.lastname)
}

```


```ts
import myStudentClass from "./studentModule";

let max=new myStudentClass();
max.firstname="Max";
max.lastname="Müller";
max.displayStudent(max);

```