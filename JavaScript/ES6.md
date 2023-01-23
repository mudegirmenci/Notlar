## ES6 ##

### Var let ###

#### Var ####

- Scope: Function Scope
- Initialize: Gerekmez, undefined dönderir.
- Tekrar tanımlanabilir
```
var a=5
var a=7
```

#### Let ####

- Scope: Block Scope
- Initialize:Gereklidir. Herhangi bir değer atamadan tanımlanırsa çağrıldığı yerde error verir.
- Tekrar tanımlanamazlar.
```
let a=5
let a=6

error
```
#### const ####

- const ile bildirilen objeler ve stringler hala değiştirilebilir.
- const bildiriminin kullanılması yalnızca değişken tanımlayıcısının yeniden atanmasını engeller.

```
const s = [5, 6, 7];
//s = [1, 2, 3];    bu satır hata üretecek
s[2] = 45;          bu satırda sorun çıkmayacak, çünkü yeniden tanımlama yapmıyoruz, dizi değeri değitiriyoruz.
console.log(s);     çıktımız [5,6,45] olacak

```
- Verilerinizin değişmemesini sağlamak için JavaScript, veri mutasyonunu önlemek için bir Object.freeze işlevi sağlar.

```
let obj = {
  name:"FreeCodeCamp",
  review:"Awesome"
};
Object.freeze(obj);
obj.review = "bad";
obj.newProp = "Test";
console.log(obj);
```

### Strict Mode ###
- Bildirilmemiş değişkenleri kullanmayı engellemek için **use strict** kullanılır.

### Arrow Function ###

-JavaScript'te, özellikle bir işlevi başka bir işleve argüman olarak geçirirken, genellikle işlevlerimizi adlandırmamız gerekmez.  Bunun yerine satır içi işlevler oluşturuyoruz.  Bu fonksiyonları başka bir yerde tekrar kullanmadığımız için isimlendirmemize gerek yok.

```
const myFunc = function() {
  const myVar = "value";
  return myVar;
}
```

- ES6 ile;
```
const myFunc = () => {
  const myVar = "value";
  return myVar;
}

hatta fonksiyon gövdemizde sadece dönüş değerimiz varsa;

const myFunc = () => "value";

```
şeklinde kullanabiliriz.

- Arrow function'a argüman geçebiliriz.
```
const doubler = (item) => item * 2;
     veya tek argüman için
const doubler = item => item * 2;

doubler(4);

sonuc 8
```

### Fonksiyonlara default parametre atayabiliriz. ###

```
const selamla = (isim="Anonim") => "Selam " + isim;

console.log(selamla("Mustafa"));
console.log(selamla());

birinci çıktı:Selam Mustafa
ikinci çıktı:Selam Anonim
```
defult parametrede sayı kısıtı yok. İstediğimiz sayıda atayabiliriz.

- Daha esnek işlevler oluşturmamıza yardımcı olmak için ES6, işlev parametreleri için rest parametresini sunar.rest parametresi ile değişken sayıda argüman alan fonksiyonlar oluşturabilirsiniz.  Bu bağımsız değişkenler, daha sonra işlevin içinden erişilebilen bir dizide saklanır.

```
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2));
console.log(howMany("string", null, [1, 2, 3], { }));
```

###  Spread operatör ###

- Math.max(arr) NaN döndürür.  Math.max() virgülle ayrılmış bağımsız değişkenler bekler, ancak bir dizi beklemez.  Yayılma operatörü, bu sözdizimini okumak ve korumak için çok daha iyi hale getirir

```
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);

max value olarak 89 döner
```
...arr returns an unpacked array. 

```
copy arr1 to arr 2

const arr1 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
let arr2 

arr2 = [...arr1];  
```

### Destructuring assignment ###

```
const user = { name: 'John Doe', age: 34 };

const name = user.name;
const age = user.age;


const { name, age } = user;

```

```
const user = { name: 'John Doe', age: 34 };

const { name: userName, age: userAge } = user;

user.name değerini al ve userName adında yeni değişken oluşturup ona ata.
aynı şekilde age değişken değerini al userAge değişkenine ata.
```

```
const LOCAL_FORECAST = {
  yesterday: { low: 61, high: 75 },
  today: { low: 64, high: 77 },
  tomorrow: { low: 68, high: 80 }
};
  
const {today: { low:lowToday,high:highToday }} = LOCAL_FORECAST
```


