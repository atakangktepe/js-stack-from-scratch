# 3 - Babel ve Gulp ile ES6 sözdizimini kullanmak

Şimdi eski ES5 sözdizimi üzerinden büyük bir gelişme geçirmiş ES6 sözdizimini kullanacağız. Tüm tarayıcılar ve JS ortamları ES5'i anlayabilir fakat ES6'yı anlayamazlar. Bu yüzden Babel olarak çağırılan ES6 kodlarını ES5'e çeviren Babel isimli aracı kullanacağız. Babel çalıştırmak için Gulp kullanacağız, Gulp bir görev çalıştırıcı. Gulp `package.json` dosyasındaki `scripts` ile benzer fakat görevlerinizi bi JS dosyasına yazmak JSON dosyasına yazmaktan daha basit ve temiz. Yani Gulp kurup, Babel eklentisini Gulp için kuracağız:

- `yarn add --dev gulp` komutunu çalıştırın.
- `yarn add --dev gulp-babel`  komutunu çalıştırın.
- `yarn add --dev babel-preset-latest` komutunu çalıştırın
- Babel ayarlamaları için `package.json` dosyasına `babel` alanı ekleyin. Babel'i son presets'ı(?) kullanacak şekilde ayarlayın:

```json
"babel": {
  "presets": [
    "latest"
  ]
},
```

**Not**: Projenizin kök dizininize bir `.babelrc` dosyası `package.json`'da olan `babel` alanı yerine kullanılabilir. Fakat ilerleyen zamanlarda kök dizininiz çok çok şişmiş olacak, yani Babel konfigürasyonunuzu `package.json`'da tutun.  

- `index.js` dosyanızı yeni bir `src` klasörü oluşturup içine taşıyın. Bu sizin ES6 sözdizimi kullanarak kod yazacağınız yeni dosyanız. Kodlarınız ES5 sözdizimine derlenip `lib` klasörüne yazılacak. Gulp ve Babel bununla ilgilenecek. Önceki kodlarınızı `index.js` dosyasından temizleyip yenisi ile değiştirin:

```javascript
const str = 'ES6';
console.log(`Hello ${str}`);
```

Burada bir ES6 özelliği olan *template string* kullandık, *template string*'ler bize `+` karakteri olmadan direk olarak değişken enjekte etmemizde yardımcı oluyor. Not: *template strings* **ters tırnak** kullanılarak yazılır.

- Aşağıdaki kodları içeren bir `gulpfile.js` oluşturun:

```javascript
const gulp = require('gulp');
const babel = require('gulp-babel');
const del = require('del');
const exec = require('child_process').exec;

const paths = {
  allSrcJs: 'src/**/*.js',
  libDir: 'lib',
};

gulp.task('clean', () => {
  return del(paths.libDir);
});

gulp.task('build', ['clean'], () => {
  return gulp.src(paths.allSrcJs)
    .pipe(babel())
    .pipe(gulp.dest(paths.libDir));
});

gulp.task('main', ['build'], (callback) => {
  exec(`node ${paths.libDir}`, (error, stdout) => {
    console.log(stdout);
    return callback(error);
  });
});

gulp.task('watch', () => {
  gulp.watch(paths.allSrcJs, ['main']);
});

gulp.task('default', ['watch', 'main']);

```

Tüm bunları anlamak için biraz zaman ayıralım.

Gulp'ın kendi API'ı oldukça basit. `gulp.task` kodu görevi tanımlıyor ve `gulp.src` dosyaları referans veriyor ve bunları `.pipe()` fonksiyonu ile işliyor (tıpkı bizim durumumuzdaki `babel()` gibi) ve `gulp.dest` ile çıktı verecek yol belirleniyor. Ayrıca Gulp `gulp.watch` koduyla sizin sistemde ki kodlarınızı izleyip çalıştırıyor. Daha fazlası için [dökümantasyon](https://github.com/gulpjs/gulp)'a bakın.

İlk olarak `paths` objesine bizim bütün farklı yollarımızı belirtiyor ve zihnimizi temiz tutuyoruz.

Daha sonra 5 adet görev belirtiyoruz: `build`, `clean`, `main`, `watch`, ve `default`.

- `build` Babel'ın `src` klasöründeki dosyaları `lib` klasörüne dönüştürülmüş şekilde yerleştirmesi için bir komut.
- `clean` görevi ise bizim her `build` komutunda `lib` klasöründe ki otomatik-oluşturulmuş dosyaları temizler. Bu tipik olarak bizim `src` klasöründe sildiğimiz veya yeniden adlandırdığımız dosyalardan kurtulmak için veya `lib` klasörümüzün `src` klasörü ile senkronize olduğundan emin olmamız için yazdığımız bir görev. Dosyaları silmek için `del` paketini kullanacağız, bu bir bakıma Gulp'ın stream'ı ile iyi entegre olur (Bu Gulp ile dosyaları silmek için  [önerilen](https://github.com/gulpjs/gulp/blob/master/docs/recipes/delete-files-folder.md) yoldur). Kurmak için `yarn add --dev del` komutunu çalıştırın.
- `main` görevi bir önceki bölümde gördüğümüz `node .` komutuyla eşdeğer, biz bu komutu `lib/index.js` içerisinde çalıştırmak istiyoruz. Hatırlarsanız `index.js` Node'un varsayılan olarak baktığı dosyaydı, biz bunu basit olarak `node lib` olarak değiştirdik (`libDir` değişkenini düşüncelerimizi temiz tutmak için atadık). Görev içerisindeki `require('child_process').exec` ve `exec` komutları native Node fonksiyonları, bu shell komutları çalıştırır. Çıktıyı görebilmek için ise `stdout` değişkenini `console.log()`'a gönderdik ve olası hataları `gulp.task`'in callback'i ile gönderdik. Eğer bu bölüm size çok temiz gelmediyse endişelenmeyin, hatırlayın bu sadece temel olarak `node lib` komutunu çalıştırıyor.
- `watch` komutu belirtilen dosyalarda bir değişiklik olduğunda `main` görevini çalıştırır.
- `default` görevi özel bir görev, bu siz eğer CLI üzerinden `gulp` komutunu çalıştırırsanız çalışır. Bizim durumumuzuda bunun `watch` ve `main` (sadece ilk çalıştırmada) görevinin her ikisini de çalıştırmak istiyoruz.

**Not**: Bizim ES6 kodlarını nasıl Gulp dosyasında kullandığımızı merak etmiş olabilirsiniz, bu ES5 sözdizimine Babel tarafından dönüştürlmüyor. Bunu yapabiliyoruz çünkü bizim kullandığımız Node ES6 özelliklerini destekliyor (`node -v` komutunu kullanarak Node versiyonunuzun 6.5.0 versiyonundan yüksek olduğundan emin olun). 

Tamam! Bu işe yarıyor mu görelim.

- `package.json` dosyanızda `start` kodunuzu `"start": "gulp"` kodu ile değiştirin.
- `yarn start` komutunu çalıştırın. Bu "Hello ES6" çıktısını vermeli ve değişiklikler için izlemeye geçmeli. `src/index.js` dosyanıza saçma bir kod yazmayı deneyin, Gulp size otomatik olarak hatanın nerede olduğunu dosyayı kaydettiğinizde gösterecektir.
- `/lib/` klasörünü `.gitignore` dosyanıza ekleyin.


Sonraki bölüm: [4 - ES6 sözdizimini bir class ile kullanmak](/tutorial/4-es6-syntax-class)

[Bir önceki bölüme](/tutorial/2-packages) veya [içindekilere](https://github.com/atakangktepe/js-stack-from-scratch) geri dön.
