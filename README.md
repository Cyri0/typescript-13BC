# TypeScript
## Mi a TypeScript?

A TypeScript egy objektum-orientált script nyelv, amit a Microsoft készített. Legfőbb filozófiája nyelvnek az, hogy "legyen a TypeScript bővebb halmaza a Javascript-nek". A Javascript-től eltérően, legnagyobb újdonsága, hogy statikusan típusos a nyelv.

Célja egy olyan eszköz megalkozása volt, mely segíti a fejlesztőket az igazán nagy projektek elkészítésében is. Legfőbb tulajdonságai:

1. **Statikus típusellenőrzés:** A TypeScript statikus típusellenőrzést biztosít, ami azt jelenti, hogy a változók típusát már a kódszerkesztés közben meghatározhatod (pl. string, number, boolean stb.). Ez segít elkerülni a futásidejű hibákat, amelyeket a nem megfelelő típusok okozhatnak.
2. **Jobb hibakezelés fejlesztés közben:** A TypeScript már a kód írása közben figyelmeztet a lehetséges hibákra, ami gyorsabb hibajavítást tesz lehetővé, mivel a hibákat még a kód futtatása előtt megtalálhatod.
3. **IntelliSense és jobb IDE támogatás:** A TypeScript használatával a modern fejlesztői környezetek (IDE-k) jobb IntelliSense támogatást biztosítanak, vagyis automatikus kiegészítést, dokumentációs segítséget, és a hibák könnyebb megtalálását teszik lehetővé.
4. **Tisztább, karbantarthatóbb kód:** A típusok használata segít jobban strukturálni és dokumentálni a kódot. Ez különösen fontos nagyobb projekteknél, ahol több fejlesztő dolgozik együtt.
5. **Backwards compatibility:** A TypeScript visszafele kompatibilis a JavaScripttel, ami azt jelenti, hogy bármelyik JavaScript kód TypeScriptben is működni fog, de további típusdefiníciókat adhatsz hozzá, hogy kihasználd a TS előnyeit.
6. **Nagyobb skálázhatóság:** Nagyobb projektek esetén a típusbiztonság segít a kódot jobban szervezni és könnyebben skálázhatóvá tenni, mivel a típusok segítenek meghatározni, hogyan kell a különböző komponenseknek együttműködniük.

## TypeScript project létrehozása
Először is győződj meg róla, hogy telepítve van a Node.js, az npm (Node Package Manager) és a tsc. Ezeket a 
- `node -v`

- `npm -v`

- `tsc -v`

parancsokkal tesztelheted le.

Ha nincs tsc akkor azt a 
`npm install -g typescript` 
paranccsal teheted meg.

Ezután inicializáld a projektet (ez egy package.json fájlt fog létrehozni). Ez a fájl tartalmazni fogja a projekt függőségeit és konfigurációit.

`npm init -y`

Majd telepítsd a TypeScriptet

`npm install typescript –save-dev`

A TypeScript beállításokat tartalmazó tsconfig.json fájlt a
`tsc –init`
paranccsal tudod létrehozni.

 Ezután hozz létre egy index.ts fájlt, majd fordítsd le a tsc paranccsal. A létrejövő index.js fájlt a a node-al lefuttathatod, vagy egy html fájlba importálhatod. A fordítás és node-al futtatás egy sorban:
`$ tsc && node index.js`

## Beépített típusok
A teljesség igénye nélkül...
### Primitív típusok
string: Bármilyen karakterlánc.

```typescript
let name: string = "John";
```

number: Bármilyen szám, beleértve az egész és lebegőpontos számokat.
```typescript
let age: number = 25;
```
boolean: Igaz (true) vagy hamis (false) érték.
```typescript
let isStudent: boolean = true;
```
null: Egy speciális típus, amely csak a null értéket tartalmazza.
```typescript
let empty: null = null;
```
undefined: Egy változó, amely nem rendelkezik értékkel.
```typescript
let notAssigned: undefined = undefined;
```
### Komplex típusok
any: Bármilyen típusú értéket elfogad. Ha nem tudod, milyen típusú adatot fog kapni a változó, használhatod az any típust. De általában érdemes elkerülni, mert nem biztosít típusbiztonságot.
```typescript
let anything: any = 42;
anything = "Hello";
```
void: Akkor használatos, amikor egy függvény nem ad vissza semmilyen értéket.
```typescript
function logMessage(): void {
  console.log("This is a message");
}
```

### Összetett típusok
array: Típusdefiníció egy tömbhöz, amely egy adott típusú elemekből áll. Ha a típusa any akkor mixelt típusok is lehetnek.
```typescript
let numbers: number[] = [1, 2, 3, 4];
```
```typescript
let strings: Array<string> = ["one", "two", "three"];
```
object: Tárgyak vagy objektumok típusai, amelyeket kulcs-érték párok határoznak meg.
```typescript
let person: { name: string; age: number } = {
  name: "Alice",
  age: 30
};
```
## Függvények
Függvények típusainak meghatározása: A függvények bemeneti paramétereinek és visszatérési értékének típusát is megadhatod.
```typescript
function add(a: number, b: number): number {
  return a + b;
}
```
```typescript
let subtract: (x: number, y: number) => number = function (x, y) {
  return x - y;
};
```
## Típusok
type: Használhatod komplex típusok definiálására is. Hasonló az interface-hez. Később nem lehet módosítani a mezőit.
```typescript
type Point = {
  x: number;
  y: number;
};

let point: Point = { x: 10, y: 20 };
```

## Interfészek
interface: Olyan struktúrát határoz meg, amely meghatározza, hogy milyen mezői és metódusai lehetnek egy objektumnak. Később további mezők adhatóak hozzá.
```typescript
interface Person {
  name: string;
  age: number;
}

let user: Person = {
  name: "John",
  age: 25
};
```

## Generikusok

A TypeScript generikusai lehetővé teszik a típusbiztonság megőrzését úgy, hogy közben rugalmas és újrafelhasználható kódszerkezeteket írhatunk. Generikus típusokkal olyan függvényeket, osztályokat vagy interfészeket készíthetünk, amelyek különböző típusokkal működnek anélkül, hogy konkrét típusokat kellene előre meghatározni.

Miért fontosak a generikusok?

1. **Típusbiztonság:** A generikus típusok segítségével a függvények és osztályok megtartják az erős típusellenőrzést, így elkerülhetők a futásidejű típushibák.
2. **Újrafelhasználhatóság:** A generikusokkal olyan általános megoldásokat hozhatunk létre, amelyek különböző típusokkal is működnek, anélkül, hogy újra és újra kellene írni a kódot.
3. **Rugalmasság:** A generikus típusokkal írt függvények vagy osztályok bármilyen típusú adatot kezelhetnek, de közben továbbra is szigorú típusellenőrzés alatt állnak.

### Generikus függvények
A generikus típusokkal rendelkező függvények olyan típusparamétereket fogadnak, amelyek bármilyen típusúak lehetnek. A leggyakoribb jelölés T típus használata (de bármi lehet).

```typescript
function identity<T>(arg: T): T {
  return arg;
}
```

```typescript
let output1 = identity<string>("Hello");
let output2 = identity<number>(42);
```

*Egyelőre elég ennyi... 😉*