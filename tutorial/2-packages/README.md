# 2 - Bir paket kurup kullanmak

Bu bölümde bir paket kurulumu yapıp bunu kullanacağız. Bir "paket" başka bir kişi tarafından yazılan basıt bir kod parçacığıdır ve siz bunu kendı kodunuzda kullanabilirsiniz. Bu herhangi bir şey olabilir. Burada biz yeni bir paket deniyoruz, bu paket size renkleri manipüle etmenize yardımcı olacak örnek bir paket.

- `color` isimli topluluk-yapımı paketi `yarn add color` komutunu kullanarak kurun.

`package.json` dosyasını açın ve Yarn'ın nasıl `color` paketini otomatik olarak `dependencies` objesine eklediğine bakın.

`node_modules` klasörü paketleri barındırmak için oluşturulmuştur.

- `node_modules/` satırını `.gitignore` dosyanıza ekleyin (eğer henüz bir git reposu oluşturmadıysanız `git init` komutuyla oluşturun) 

Ayrıca Yarn tarafından `yarn.lock` dosyasının oluşturulduğu hakkında bir bildirim alacaksınız. Bunu bütün takım üyelerinizin aynı paket versiyonunu kullanması için commitlemeniz lazım. Eğer Yarn yerine NPM kullanmayı tercih ettiyseniz, *shrinkwrap* dosyası buna eşdeğerdir.

- `const Color = require('color');` satırını `index.js` dosyanıza ekleyin.
- Paketi bu örnekte olduğu gibi kullanın: `const redHexa = Color({r: 255, g: 0, b: 0}).hexString();`
- `console.log(redHexa)` kodunu ekleyin.
- `yarn start` komutunu çalıştırdığınızda `#FF0000` çıktısını alacaksınız.

Kutlarım, bir paket kurup bunu kullandınız!

Bu örnekte `color` paketi size sadece basit bir paketin nasıl kullanıldığını öğretmek içindi. Buna daha fazla ihtiyacımız yok, yani bunu kaldırabiliriz.

- `yarn remove color` komutuyla kaldırabilirsiniz.

**Not**: 2 tip paket bağımlılık tipi vardır, `"dependencies"` ve `"devDependencies"`. `"dependencies"` tipi `"devDependencies"` tipinden daha geneldir. `"devDependencies"` sadece geliştirme yaparken ihtiyaç duyduğunuz tiptir (tipik olarak, build-related paketler, linters gibi). `"devDependencies"` kurmak için biz `yarn add --dev [paket]` komutunu kullanacağız. 

Sonraki bölüm: [3 - Babel ve Gulp ile ES6 sözdizimini kullanmak](/tutorial/3-es6-babel-gulp)

[Bir önceki bölüme](/tutorial/1-node-npm-yarn-package-json) veya [içindekilere](https://github.com/verekia/js-stack-from-scratch) geri dön.
