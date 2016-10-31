# 4 - ES6 sözdizimini bir class ile kullanmak

- Aşağıdaki ES6 ile yazılmış sınıfı içeren kodu, `src/dog.js` adında yeni bir dosya oluşturup içerisine yazın:

```javascript
class Dog {
  constructor(name) {
    this.name = name;
  }

  bark() {
    return `Wah wah, I am ${this.name}`;
  }
}

module.exports = Dog;
```

Eğer geçmişte herhangi bir dilde OOP yazdıysanız bu sizin için şaşırtıcı olmamalı. Sınıfı `module.exports` atamasıyla dış dünyaya açıyoruz.

Tipik ES6 kodu sınıflar, `const`, `let`, "template strings" (ters tırnak ile) `bark()` fonskiyonunun içindeki gibi ve `arrow functions` kullanıyor olsa bile biz herhangi birini bu örnekte kullanmıyoruz.

`src/index.js` içersine, aşağıdakileri yazın:

```javascript
const Dog = require('./dog');

const toby = new Dog('Toby');

console.log(toby.bark());
```
Gördüğünüz gibi, toplululuğun yaptığı paket olan `color` aksine bizim yaptığımız dosyayı `require()` fonksiyonu içerisinde `./` kullanarak çağırdık.

- `yarn start` komutunu çalıştırın. Bu 'Wah wah, I am Toby' çıktısını vermeli.

- Derlenmiş dosyanıza `lib` klasörü altında bir göz atın. (Örnek olarak `const` yerine `var` kullanıldığını görebilirsiniz.)

Sonraki bölüm: [5 - The ES6 modules syntax](/tutorial/5-es6-modules-syntax)

[Bir önceki bölüme](/tutorial/3-es6-babel-gulp) veya [içindekilere](https://github.com/atakangktepe/js-stack-from-scratch) geri dön.
