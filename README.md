# frontend-cheatsheet-polish
Ściąga z podstawowymi materiałami dotyczącymi Frontendu (HTML, CSS, JS, REACT) 

<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 2.323 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β33
* Wed Oct 05 2022 05:55:07 GMT-0700 (PDT)
* Source doc: Notatki Frontend
* Tables are currently converted to HTML tables.

WARNING:
You have 5 H1 headings. You may want to use the "H1 -> H2" option to demote all headings by one level.

----->


<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 1; ALERTS: 0.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p>
<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>



[TOC]


GIT


```
Git workflow:
git fetch //update danych (nie plików) z repo zdalnego
git pull origin NAZWA_BRANCHA //pobiera pliki z brancha zdalnego do lokalnego
git branch NAZWA_BRANCHA //tworzenie nowego brancha
git branch --all //pokazuje wszystkie branche na repo
git branch -d nazwa_brancha //usuwanie gałęzi po merge
git branch -D nazwa_brancha //usuwanie gałęzi bez merge
gitk --all //pokazuje wizualnie repo
git checkout NAZWA_BRANCHA //wchodzenie na danego brancha
git checkout -b NAZWA_BRANCHA //tworzenie i przechodzenie od razu na nowego brancha
git add . //dodawanie wszystkich plików na staging brancha
git status //sprawdzanie statusu zmian
git commit -m"KOMENTARZ" //commit 
git push origin NAZWA_BRANCHA //push na brancha
```



# Gulp 

Skopiować package.json i glup.js z template do folderu z projektem, wpisać npm install i gulp żeby wystartować.


# HTML


## Viewport

Pozwala na działanie RWD przy urządzeniach mobilnych (standardowo emmet)


```
  <meta name="viewport" content="width=device-width, initial-scale=1" />
```



## IMG/VIDEO właściwości

fluid-video

aspect-ratio


# Flex


## Flex-grow


# Sass/CSS

<span style="text-decoration:underline;">Dopasowanie img do kontenera</span>

Object-fit:cover działa analogicznie do background-size:cover; position mówi o parametrach w osi XY. 


```
.card-img-top {
    height: 250px;
    object-fit: cover;
    object-position: 50% 50%;
```


<span style="text-decoration:underline;">Przesuwający się  background-image podczas scrollowania</span>


```
   background-attachment: fixed;
```



## <span style="text-decoration:underline;">Przyciemnianie background-image</span>

Poprzez linear-gradient:


```
background: linear-gradient(rgba(0, 0, 0, 0.527),rgba(0, 0, 0, 0.6)) , url("../img/conferen.jpg");
```


Inne opcje (wymagają z-indexów)

https://dev.to/nazanin_ashrafi/how-to-darken-an-image-with-css-4f5h


## <span style="text-decoration:underline;">Media queries</span>

, stosujemy min-width/max-width w pixelach


```
@media (max-width: 600px) {
	body {
width: 500px }
}
```



## <span style="text-decoration:underline;">Używanie wartości/funkcji:</span>

Na samej górze dokumentu!

Listy zaczynają się od 1 [nie od 0] \



```
 @use "sass:color"; 
 @use "sass:list";
```



## <span style="text-decoration:underline;">Używanie partials/moduls</span>


## <span style="text-decoration:underline;">Interpolacja</span>

Zmienne mogą być wrzucane do styli poprzez zastosowanie `#{$name}`

@for $i from 1 through 3 {

  h#{$i} { \
 font-size: list.nth($font-sizes, $i);

  }}


## <span style="text-decoration:underline;">Listy</span>

Listy zapisujemy tak samo jak zmienne $lista: wartość1, wartość2; 

Listy zaczynają się od 1 [nie od 0]

I korzystamy poprzez list.nth($lista, nr_wartości) 


```
@use "sass:list"; //na samej górze style.scss
$font-sizes: 100px, 50px, 6px;
font-size: list.nth($font-sizes, 1) //otrzymamy 100px
```



## <span style="text-decoration:underline;">Mapy</span>

Mapa  $map:(); przyjmuje klucze “key”: i wartości value.

Używamy do kosntrukcji nawiasów okrągłych (), a wewnętrzne pary klucz-wartość oddzielamy przecinkami.

Mapę wywołujemy korzystając z map.get($mapa, “element”)


```
//na samej górze
@use "sass:map";


//mapa
$font-weights: ("regular": 400, "medium": 500, "bold": 700);

//wywołanie
font-weight: map.get($regular, "400");
```


Funkcje map:[ https://www.tutorialsteacher.com/sass/sass-map-functions](https://www.tutorialsteacher.com/sass/sass-map-functions)

Przez mapy można iterować używając list lub używając pętli each 


```
//tworzymy listę z mapy
$colors-list: map-values($colors);

@for $i from 1 through list.length($colors-list) {
  el-#{$i} {
    background-color: list.nth($colors-list, $i);
  }
}

$colors: (
  "gold": #f9c00c,
  "blue": #00b9f1,
  "purple": #7200da,
  "red": #f9320c,
  "green": #75d701,
);

//name odnosi się do "klucza" a color do wartości, dowolne nazwy, ważna kolejność zapisu

@each $name, $color in $colors {


}
```



## <span style="text-decoration:underline;">Pętle</span>

For - używamy wyrażenia $nowa_zmienna from wartość_początkowa through wartość_końcowa.


```
@for $i from 1 through 3
```


Each - nadajemy parametr elementowi ($size) by iterować przez zbiór ($sizes)


```
@each $size in $sizes
```


<span style="text-decoration:underline;">Mixiny</span>

Mixiny - prostsze mapy, które mozemy umieszczać do danych klas/id dodając @include \
Mozemy dodawać wartości do zmiennych poprzez wartość w nawiasie ($wartość) lub dodawać je na sztywno \



```
@mixin arrow ($color, $direction) {
  color: $color;
  direction: $direction;
  size: 16px;
}
```



# JavaScript


## Pobieranie elementów z HTML


```
const btn = document.querySelector(".page-burger");
```



## Dodawanie nasłuchiwania na klik do elementu


```
btn.addEventListener("click", function () {
  body.classList.toggle("menu-open");
});
```


Tworzenie obiektu

Używamy klucz-wartość - używać grawisów by móc interpolować i wstawiać apostrofy.


```
const obiekt = {
 klucz1: `wartosc1`,
 klucz2: `wartosc2`,
 metoda() {
   console.log(obiekt.klucz1);
 },
};

obiekt.metoda(); //wywolanie
```


W metodach możemy używać “this” by odnieść się do obiektu. 

Konstruktory obiektu

Funkcje tworzące obiekt. Mają klucze przypisane  do obiektu (this)  i “puste” wartości, do których możemy coś przypisać tworząc nowe obiekty na ich podstawie. Są to właściwości instancji. Każdy obiekt stworzony za pomocą konstruktora to instancja. Możemy to sprawdzić za pomocą instanceof (powinno być true)

. Konstruktory zaczynamy z wielkiej litery, a nowe obiekty tworzymy używając “new”. 


```
console.log("hello");

const obiekt = {
 klucz1: `wartosc1`,
 klucz2: `wartosc2`,
 metoda() {
   console.log(obiekt.klucz1);
 },
};

obiekt.metoda();

function Konstruktor(wartosc1, wartosc2) {
 this.klucz1 = wartosc1;
 this.klucz2 = wartosc2;
}

const nowyObiekt = new Konstruktor("NowaWartosc1", "NowaWartosc2");

console.log(nowyObiekt);

console.log(nowyObiekt instanceof Konstruktor); //true
console.log(obiekt instanceof Konstruktor); //false
```


Prototyp

Wszystkie obiekty połączone z danym prototypem mogą używać jego funkcji (nie powinniśmy tworzyć funkcji w konstruktorze ). Obiekty (instancje, stworzone z konstruktora) dziedziczą właściwości/funkcje(metody) z prototypu. 


```
function Konstruktor(wartosc1, wartosc2) {
 this.klucz1 = wartosc1;
 this.klucz2 = wartosc2;
}

const nowyObiekt = new Konstruktor("NowaWartosc1", "NowaWartosc2");
const bardzoNowyObiekt = new Konstruktor("SzalonaWartosc", "SuperWartosc");

Konstruktor.prototype.metodaPrint = function () {
 console.log(this.klucz1, this.klucz2);
};

nowyObiekt.metodaPrint();
bardzoNowyObiekt.metodaPrint();

console.log(nowyObiekt);
console.log(Konstruktor) //wewn obiektu ani konstruktora nie ma bezposrednio metody, ale jest przypisana do prototypu = deklarujemy i tworzymy jedna funkcje, a nie funkcje do kazdego obiektu osobno
```


Wyszukiwanie wartości w tabeli array

indexOf zwraca pozycje w tabeli, jeśli brak zwraca -1


```
unction getNumber(number, array) {
 if (array.indexOf(number) >= 0) {
   console.log(true);
   return true;
 } else {
   console.log(false);
   return;
 }
}
```


Nowsz metoda bezpośrednio sprawdzenie za pomocą includes, zwraca true lub false


```
function getNumber(number, array) {
 if (array.includes(number)) {
   console.log(true);
   return true;
 } else {
   console.log(false);
   return;
 }
}
```



## Zatrzymywanie propagacji eventListenera



* e.stopImmediatePropagation() stops any further handler from being called for this event, no exceptions
* e.stopPropagation() is similar, but does still call all handlers for _this phase_ on _this element_ if not called already [phase = bubbling do góry w przypadku wyjścia z funkcji, lub capture w dół w środku funkcji (np. jeśli na jednym obiekcie klika eventów)


## Gdy nie działa this

event.currentTarget (to jest this) – zwraca element, na którym wywołane zostało zdarzenie,

event.target (to jeśli chcemy wyjść do wyższego elementu)  – zwraca element, który spowodował wywołanie eventu; w przypadku propagacji jest to element potomka,


```
b.addEventListener("click", function (event) {
 // Tutaj this wskazuje na element DOM o id b

 console.log("b: ", this);

 function innerFuncOne() {
   // Tutaj this wskazuje na element Window, bo funkcja została
   //wywołana bez żadnego kontekstu.
   event.target.style.backgroundColor = "red";
//to wskazuje na b
   console.log("innerFuncOne: ", this);
 }

 innerFuncOne();
});

lub dodać const = self;  //pod listenerem
this, self //w funkcji

const Basket = function(prices) {
  this.prices = prices;
};
Basket.prototype.calculatePrices = function() {
  this.sum = 0;
  const self = this;
  this.prices.forEach(function(element) {
     self.sum += element;
  });
  console.log(this.sum.toFixed(2));
}
const basket = new Basket([9.99, 7.77]);
basket.calculatePrices(); // 17.76
```


Metody tablicowe [https://devinduct.com/cheatsheet/8/array-operations](https://devinduct.com/cheatsheet/8/array-operations)

Tworzenie Arraya liczb


```
const res = Array.from(Array(10)).map((x,i) => i);
console.log(res)
```


Losowanie random liczb


```
const res = [...Array(6)].map(() => {
 return Math.floor(Math.random() * 10);
});
```



## Export & import

Export default bez {}, może być jeden na plik

Export zwykły z {}

W index.html 

**&lt;script type=”module” src=”” >&lt;/script>**


```
const name = "Jesse";
const age = 40;
const message = () => {
const name = "Jesse";
const age = 40;
return name + ' is ' + age + 'years old.';
};
export default message;
export {name, age};

//importy
import { name, age } from "./person.js";
import message from "./message.js";
```



## Callback

Callback to funkcja, którą przekazujemy jako argument do wywoływanej funkcji 


## Funkcja strzałkowa

Stosujemy const zamiast function jeśli tworzymy funkcję nieanonimową. Przy jednym argumencie i jednym poleceniu nie musimy wstawiać nawiasów okrągłych ani klarmowych


```
const foo = a =>  a*2

to samo co
function foo(a) {
a*2
};

ray = [1,2,3,4]

array.forEach(function(element) {
 console.log(element + 1)
})

to samo co

array.forEach(e => console.log(e + 1))
```


Funkcja strzałkowa nie zmienia kontekstu i nie tworzy this (wskazuje na this obiektu, a nie funkcji)


```
Basket.prototype.calculatePrices = function() {
 this.sum = 0;
 this.prices.forEach(element =>  this.sum += element);
//this wskazuje na sum, a w normalnej funkcji na obiekt window

 console.log(this.sum);
}
```


Funkcje strzałkowe zachowują się zupełnie inaczej niż tradycyjne funkcje:



* są zawsze „związane” z najbliższym kontekstem, w którym zostały wywołane, to znaczy, że nie jest dla nich tworzone wyrażenie this,
* Arrow functions są zawsze anonimowe,
* Nie mogą być konstruktorami tzn. nie mogą być wywoływane z użyciem operatora new,
* Nie mają własności prototype.

.filter

array.filter(funkcja)

Po elementach funkcji:

array.filter(element => funkcja(element))

Jeśli funkcja zwraca true to filtruje


```
const state = {
 invoiceSection: false,
 availableYears: [1990, 1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998, 1999, 2000, 2001, 2002, 2003, 2004, 2005],
 formStatus: "failed",
 isUserLogged: false
};

const dates = (element, x) => element >= x;

// console.log(dates(14, 100))

const stateCopy = {
 ...state,
 availableYears: state.availableYears.filter(element => dates(element, 2002)),
};
```


.forEach


```
const getAvarage = (...arg) =>  {
let x = 0;
arg.forEach((element) =>  x += element/arg.length)
return x;
}
console.log(getAvarage(3,4))
```


Reduce


```
array = [2,2,5];
// tablica.reduce(funkcja, (wynikKońcowy[zaczyna sie od punktuPoczątkowego], elementTablicy)
// , punktPoczątkowy)
const sum = array.reduce((finalValue, arrayElement) => {
 return finalValue + arrayElement;
}, 0);

console.log(sum)
```



## Obiektowość ES6

Klasy i dziedziczenie (extends)


```
class Animal {
 constructor(name) {
   this.name = name;
 }
 getName() {
   return this.name;
 }
}
class Cat extends Animal {
 constructor(name, age) {
   super(name);
   this.age = age;
 }
}
let cat = new Cat("Filemon", 4);
console.log(cat);
// Cat {name: "Filemon", age: 4}
```


Łączenie metod tablicowych na obiektach array of objects


```
const users = [
   {
       id: 1,
       firstName: "Idalia",
       lastName: "Franses",
       email: "ifranses0@mapy.cz",
       ipAddress: "180.153.67.217",
       language: "French",
       nin: "3033798411",
   },
   {
       id: 2,
       firstName: "Frederick",
       lastName: "Prince",
       email: "fprince1@huffingtonpost.com",
       ipAddress: "6.239.37.95",
       language: "English",
       nin: "3884188887",
   },
   {
       id: 3,
       firstName: "Iago",
       lastName: "MacCathay",
       email: "imaccathay2@wix.com",
       ipAddress: "244.252.97.163",
       language: "Italian",
       nin: "4502080942",
   },
   {
       id: 4,
       firstName: "Biddie",
       lastName: "Liddard",
       email: "bliddard3@noaa.gov",
       ipAddress: "6.107.79.145",
       language: "French",
       nin: "2931819395",
   },
   {
       id: 5,
       firstName: "Colas",
       lastName: "Moffett",
       email: "cmoffett4@purevolume.com",
       ipAddress: "200.4.236.255",
       language: "French",
       nin: "1288790260",
   },
];

const parseUserData = (arr) => {
   const newArr = arr.filter(e => e.language === "French");
const arrMapped = newArr.map(e => {
   return {
       id: e.id,
       fullName: e.firstName + " " + e.lastName,
       email: e.email,
       nin: e.nin,
   }
})
   return arrMapped.sort((a, b) => a.nin - b.nin)
}

console.log(parseUserData(users))
```


Includes - Sprawdzanei czy element zawiera się w drugim


```
const without = (data, ...x) =>  data.filter(element => !x.includes(element));

const data = [1,2,3];
console.log(without(data, 1)) //2,3
```


Conditional (ternary) operator “?”


## Jeśli coś ? zrób to : zrób coś innego


```


## function oldResult(number) {


## if(number < 50) {


##  return 'it is not 50 [old]';


## } else {


##  return "50 or more [old]";


## }};



## //to samo co


## const newResult = (number) => number < 50 ? 'it is not 50' : "50 or more";
```


Spread Operator (rozproszenie)

W przypadku gdy znajduje się on przed dowolnym obiektem iterowanym (np. tablicą), to powoduje rozdzielenie każdego elementu tablicy na osobny byt. To rozwiązanie bardzo ułatwia nam przekazanie wszystkich elementów tablicy jako kolejne parametry funkcji.


```
arr = [1,2,3];

//cały arraj
console.log(arr);

//tylko jego elementy
console.log(...arr)

//tak jakbysmy napisali

console.log(arr[0],arr[1], arr[2]);

//Żeby rozdzilić string
const string = 'string';
console.log(string)

const array = [...string]
console.log(array)
//zwraca array liter

//Tworzenie kopii tablicy i obiektów
const users = ["Ben", "Anna", "John"];
console.log(users)
const usersCopy = [...users]; //robi tylko kopie tablicy
console.log(usersCopy)
console.log(users === usersCopy) //false
console.log(...users) //rozdziela na pojedyncze wartości

const obiekt = {
 isActive: "false",
 name: "kurczak",
 age: 0
}

//Obiekt kopia i modyfikacja
console.log(obiekt)

const kopiaObiektu = {
 ...obiekt
}
console.log(kopiaObiektu)
const modyfikacjaObiektu = {
 ...obiekt,
 name: "indyk"
}
console.log(modyfikacjaObiektu)
```


Rest Operator (reszta)

Forma jak spread tj. “...reszta”, ale znajduje się jako ostatni argument funkcji, przyjmuje dowolną ilość i typ wartości


```
//działa w funkcjach i musi być zawsz na końcu, nazwa dowolona
function example(number1, number2, ...rest) {
 console.log(number1, number2, ...rest)
}
example(1,2,3,'reszta',5,6,7,8,9,'a');

const arrowExample = (...rest) => console.log(...rest);
arrowExample(1,2,3,4,5,6,'reszta')
```


Destrukturyzacja

Przypisywanie wartości do zmiennych od tyłu

W tablicach dowolne nazwy zmiennych i stosujemy [ ]

[ zmienna1, zmienna2, zmiennaN ] = nazwaTablicy; 

Możemy omijać wartości dając puste przecinki

Iterując po obiektach nazwy zmiennych muszą być takie same jak w obiekcie i używamy {}, możemy je zmienić stosując **zmienna: naszaNazwa**


```
let fruits = ["Banana", "Apple", "orange"];
let [nazwaWart1, b, c] = fruits;
console.log(nazwaWart1);
console.log(c)

const funk = () => [1,2,3]
const [a, ,b] = funk(); //pominięcie 2 
console.log(a) //1
console.log(b) //3 

//ze spread operatorem
const rest = () => [1,2,3]
const [a, ...b] = rest();
console.log(a) // 1
console.log(b) // [2,3]

//obiekty

const rest = {first: 1, second: 2, third: 3};
const {first, third} = rest;
console.log(first) //1
console.log(third) //3 

//glebsze zagniezdzenia 

const user = {
  name: "John",
  lastTimeLogged: "10-11-2022 13:44:21",
  address: {
    city: "Warsaw",
    postcode: "00-001"
  }
};

const {address, address: {city}} = user;
console.log(address, city);

//zmiana nazwy po przypisaniu w obiektach
const chicka = {name: "Alicja", age: 24}
const {name: chickasName, age} = chicka;
console.log(chickasName, age)
```


Web Storage - Local Storage

setItem(string,string)

 Ta metoda pozwala na zapisanie klucza oraz wartości w localStorage.   

Możemy więc zapisać wartość zmiennej ​userName ​w localStorage pod nazwą ​"name"​w następujący sposób:  

var​userName = ​"Yanush"​; 

localStorage.setItem(​"name"​, userName)

Wartości jakie zapisujemy mogą być wyłącznie typu ​string. ​Możemy zapisywać bardziej skomplikowane dane jak tablice lub obiekty konwertując je na tekst: 

  var​salad = {

 id: ​1​, ​// id przepisu

 title: ​"Sałatka owocowa"​, ​// nazwa przepisu

 ingredients: [​"jabłko"​, ​"ananas"​, ​"banan"​] ​// składniki przepisu };

Do dyspozycji mamy obiekt JSON, który pozwoli nam na zamianę obiektów w zapis tekstowy i z powrotem.   

localStorage.setItem(​"recipe"​, ​JSON​.stringify(salad));

getItem(string) Metoda getItem pozwala na odczytanie wartości z localStorage przechowanej pod nazwą klucza, jeśli klucz nie istnieje w localStorage, metoda zwraca wartość ​null​.   Możemy użyć klucza jak pola obiektu:  localStorage.name; ​//Yanush  Wywołać metodę getItem:  localStorage.getItem(​"name"​); ​//Yanush  Jeśli chcemy pobrać zapisany obiekt lub tablicę z localStorage:  localStorage.getItem(​"recipe"​);

Metoda parse() obiektu JSON pozwoli nam na konwersję formatu JSON do obiektu (lub 

tablicy): 

 

JSON


```
​
```


.parse(localStorage.getItem(


```
​
```


"recipe"


```
​
```


))

Metoda parse() obiektu JSON pozwoli nam na konwersję formatu JSON do obiektu (lub 

tablicy): 

 

JSON


```
​
```


.parse(localStorage.getItem(


```
​
```


"recipe"


```
​
```


))


## React

Konwersja tekstu


```
<pre>{JSON.stringify(tasks, null, 2)}</pre>
```


Podstawowy boilerplate 


```
import React from "react";
import { createRoot } from "react-dom/client";

const container = document.getElementById("app");
const root = createRoot(container);
root.render(<h1> treść { kod js } </h1>);
```


Stylowanie JSX


```
const style = {
 color: "blue",
 backgroundColor: "green"
};
<div style={style}><∕div>

lub

<div style={{color: "blue", backgroundColor: "green"}}><∕div>
```


React fragment

Elementy musimy otoczyć jednym rodzicem np. div lub fragment 


```
import React, {Fragment} from "react";
<Fragment>
 <span>Anna Kowalska</span>
 <span>Jan Kowalski</span>
</Fragment>

React.Fragment
Zapis skrótowy bez importu
<>
 <span>Anna Kowalska</span>
 <span>Jan Kowalski</span>
</>
```


Zagnieżdżanie wielu elementów


```
Tworzymy tablicę z tagami JSX:

const people = [
 <span>Anna Kowalska</span>,
 <span>Jan Kowalski</span>
];

Przekazujemy jako 
<>
 {people}
</>
```


Założenia renderowania React

Założenie I

Elementy różnego typu produkują różne wyjście. W praktyce oznacza to, że jeżeli zmieniasz w jakimś miejscu drzewa DOM element na inny, to React zakłada, że zmienia się całe rozgałęzienie od tego elementu w dół.

Założenie II

Programista może wskazać, które elementy mogą być stabilne pomiędzy zmianami za pomocą atrybutu key.

Używanie funkcji strzałkowych w komponentach klasowych

babel \



```
"plugins": [
   ["@babel/plugin-proposal-class-properties", { "loose": true }]
 ]
}
```


Importowanie styli do komponentów

Na górze komponentu, plik css powinien być w tym samym folderze co komponent


```
import "./nazwaKomponentu.css";
<div className="expense-item">
     <div>{props.date.toISOString()}</div>
```


Przekazywanie propsów

Analogiczne do atrybutów w html, odnosimy się podobnie jak do wartości obiektów


```
function Welcome(props) {             //dodajemy props do funkcji tj. komponentu
 return <h1>Hello, {props.name}</h1>;     //odnosimy sie do wartości
}

const root = ReactDOM.createRoot(document.getElementById('root'));

const element = <Welcome name="Sara" />;  //wartość deklarujemy w elemencie
root.render(element);
```

