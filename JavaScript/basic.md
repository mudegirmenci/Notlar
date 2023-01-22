## JavaScript Çalışma Notları ##

### Temeller ###

 - **var**'dan farklı olarak, **let** kullandığınızda, aynı ada sahip bir değişken yalnızca bir kez bildirilebilir. 
Örneğin:
```
var isim="Mustafa";
var isim="Ahmet";

```
bu kod hata vermeyecektir çünkü ikinci değişken tanımı ilk tanımın üzerine yazılacak ve nihai olarak **isim** değişkeni **Ahmet** değeri alacaktır. Fakat;

```
let isim="Mustafa";
let isim="Ahmet";

```
şeklinde kullanımda program hata verecektir çünkü **let** ile bir değişken sadece bir kez tanımlanabilir.

-  tıpkı **let** gibi **const** keyword'ü de ES6 ile gelmiştir. **const** sabit değer oluşturur.

-  **=** operatörünün sağındaki herşey ilk önce değerlendirilir.

```
 let myVar = 1;
 myVar += 5;
```
burada **myVar** değeri 6 dır.

-  Diğer bazı programlama dillerinden farklı olarak, JavaScript'te tek ve çift tırnak aynı şekilde çalışır.

```
const doubleQuoteStr = "This is a string"; 
const singleQuoteStr = 'This is also a string';

```
ikisi aynı dizelerde kullanılabilir fakat dikkat edilmesi gereken, en dıştaki tırnak ile içtekilerin farklı türde olması gerektiğidir.

```
const goodStr = 'Jake asks Finn, "Hey, let\'s go on an adventure?"'; 
const badStr = 'Finn responds, "Let's go!"';
```

-  JavaScript'te, Dize değerleri değişmezdir, yani oluşturulduktan sonra değiştirilemezler.
```
let myStr = "Bob";
myStr[0] = "J";

```
bütün diziyi değiştirebiliriz elbette.



- **push** dizi sonuna eleman ekler.

- **pop** dizi sonundan eleman siler ve sildiği elemanı return eder.

- **shift** dizi başından eleman siler ve sildiği elemanı return eder.

- **unshift** dizi başına eleman ekler.

- Eğer fonksiyon veya blok içindeki bir değişkeni **const**,**let** veya **var** ile atama yapmazsak, değişken her yerde global olur.

```
num1 = 18; // Global scope
function fun() {
  num2 = 20; // Global Scope
  if (true) {
    num3 = 22; // Global Scope
  }
}
```

- Aynı ada sahip hem yerel hem de küresel değişkenlere sahip olmak mümkündür.  Bunu yaptığınızda, yerel değişken genel değişkene göre önceliklidir.

- Bir işlev, dönüş ifadesini içerebilir ancak içermesi gerekmez.  İşlevin bir dönüş ifadesi olmaması durumunda, onu çağırdığınızda işlev iç kodu işler ancak döndürülen değer **undefined** olur.

### Karşılaştırmalar (==,===)###

- JavaScript'in iki farklı veri türünü (örneğin, sayılar ve dizeler) karşılaştırabilmesi için, bir türü diğerine dönüştürmesi gerekir.  Bu, Tip Zorlama(type coercion) olarak bilinir.  Ancak bunu yaptıktan sonra, terimleri şu şekilde karşılaştırabilir

```
1   ==  1  // true
1   ==  2  // false
1   == '1' // true
"3" ==  3  // true

```

- Kesin eşitlik (===) (strict equality), eşitlik operatörünün (==) karşılığıdır.  Ancak, karşılaştırılan her iki değeri ortak bir türe dönüştürmeye çalışan eşitlik işlecinin aksine, katı eşitlik işleci bir tür dönüştürmesi gerçekleştirmez.
```
3 ===  3  // true
3 === '3' // false

```
Karşılaştırılan değerler aynı türden değilse, eşitlik operatörü bir tür dönüştürmesi gerçekleştirir ve ardından değerleri değerlendirir.  Ancak katı eşitlik operatörü, bir türü diğerine dönüştürmeden hem veri türünü hem de değeri olduğu gibi karşılaştırır.

- eşitsizlik operatörü de( != ) karşılaştırma yaparken veri türlerindeki değerleri dönüştürür.
- Kesin eşitsizlik operatörü (!==), katı eşitlik operatörünün mantıksal zıttıdır.  Bu, "Kesinlikle Eşit Değil" anlamına gelir ve katı eşitliğin doğru ve tam tersi şekilde döndüğü durumlarda yanlış döndürür.  Kesin eşitsizlik operatörü, veri türlerini dönüştürmez.

### Objects ###
- Nesneler dizilere benzer, ancak verilerine erişmek ve bunları değiştirmek için dizinler kullanmak yerine, nesnelerdeki verilere properties adı verilen yollarla erişirsiniz.Örneğin:
```
const cat = {
  "name": "Whiskers",
  "legs": 4,
  "tails": 1,
  "enemies": ["Water", "Dogs"]
};
```
- Objelere **.** veya **[]** ile erişilebilir.

- Uzun **switch** **case** yapıları yerine objeleri kullanabiliriz:
```
 var result = "";
  var lookup = {
    "alpha": "Adams",
    "bravo": "Boston",
    "charlie": "Chicago",
    "delta": "Denver",
    "echo": "Easy",
    "foxtrot": "Frank"
  };
  result = lookup[val];

  return result;
```

### Bazı Trickler ###

```
function isEqual(a, b) {
  if (a === b) {
    return true;
  } else {
    return false;
  }
}

```

- Yukarıdaki fonksiyon kısaca a ile b yi karşılaştırır eşitlerse **true** değillerse **false** dönderir. Fakat bu fonksiyon kısaca şu şekilde de yazılabilir:
```
function isEqual(a, b) {
  return a === b;
}

veya a nın b den küçükse true büyükse false döndermesini istediğimizde:

function isEqual(a, b) {
  return a < b;
}

```
- Short-circuit evaluation:JavaScript mantıksal **OR ||**  operatörünü kullanırken kısa devre yapmaya izin verir. Değerleme soldan sağa doğru yapılır ve eğer sol değer **true** ise sağ taraf hiç değerlendirmeye alınmaz.

```
true || ****
// true

sağdaki değer ne olursa olsun değerlendirmeye alınmayacak.
```

```
var person = {
  name: 'Jack',
  age: 34
}console.log(person.job || 'unemployed');
// 'unemployed'

objemizin job property sine sahip olup olmadığını bilmiyoruz. Eğer varsa, o properti değeri yazılacak ama yoksa sağ taraf basılacak. Başka bir örnek:

var a;
var b = null;
var c = undefined;
var d = 4;
var e = 'five';

var f = a || b || c || d || e;

console.log(f);

burada elbette d değeri basılacak.
```




