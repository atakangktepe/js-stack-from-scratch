# 1 - Node, NPM, Yarn, ve package.json

Bu bölümde Node, NPM ve Yarn kurup, basit bir `package.json` dosyası oluşturacağız.

İlk olarak, Her zaman back-end için kullanılmayan modern Front-End çatısı için ihtiyacımız olan araçlarımız için Node kurmalıyız.

[İndirme sayfasının](https://nodejs.org/en/download/current/) üst tarafında macOS veya Windows için kurulum dosyalarını bulabilir ya da [paket yöneticisi ile kurulum](https://nodejs.org/en/download/package-manager/) sayfasından Linux dağıtımları için kuruluma ulaşabilirsiniz.

Örnek olarak, **Ubuntu / Debian** üzerinde, Node kurmak için aşağıdaki komutları çalıştırmalısınız:

```bash
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
```

`npm` Node için yapılmış Node ile birlikte gelen paket yöneticisidir. Yani ayriyetten kurmanıza gerek yok.

**Not**: Eğer daha önceden Node kurduysanız, `nvm` ([Node Version Manager](https://github.com/creationix/nvm)) kurarak Node'un son sürümünü kurup kullanabilirsiniz.

[Yarn](https://yarnpkg.com/) ise NPM'den daha hızlı olan bir paket yöneticisidir. Paketleri çevrimdışı kurmak için önbellekler. Ekim 2016'dan çıktığından bu yana çok hızlı adapte olmuş ve JavaScript topluluğunun yeni paket yöneticisi haline gelmektedir. Bu yazıda biz Yarn kullanacağız. Eğer NPM kullanmaya devam etmek isterseniz basitçe tüm `yarn add` ve `yarn add --dev` komutlarını `npm install --save` ve `npm install --dev` ile değiştirebilirsiniz.

- Yarn'ı [talimatları](https://yarnpkg.com/en/docs/install) takip ederek kurabilirsiniz. Yarn'ı `npm install -g yarn` veya `sudo npm install -g yarn` komutlarını çalıştırarak da kurmanız mümkün (Evet, Yarn'ı kurmak için NPM kullanıyoruz, tıpkı Chrome kurmak için Internet Explorer veya Safari kullandığımız gibi).
- Yeni bir klasör oluşturup `cd` komutuyla içeri girin.
- `yarn init` komutunu çalıştırıp tüm soruları `package.json` dosyası oluşturmak için cevaplayın (`yarn init -y` komutu tüm soruları otomatik cevaplar).
- `console.log('Hello world')` kodunu içeren bir `index.js` dosyası oluşturun.
- `node .` komutunu bu klasör içinde çalıştırın (`index.js` dosyası Node'un bulunan klasörde baktığı varsayılan dosyadır). Bu komut "Hello world" çıktısını vermeli.

`node .` komutunu çalıştırmak bizim programımız için birazcık düşük seviye. Biz bunun yerine bir NPM/Yarn script'i yazıp kodumuzu çalıştırmasını sağlayalım. Bu bize kodumuz daha karmaşık hâle geldiğinde `yarn start` komutuyla çalıştırmamıza yardım edecek.

- `package.json` dosyasında ana objenin içerisine bir `scripts` objesi oluşturun, yani:

```
"scripts": {
  "start": "node ."
}
```

`package.json` geçerli bir JSON dosyası olmalı. Yani el ile editlerken dikkatli olmalısınız.

- `yarn start` komutunu çalıştırın. Bu komut `Hello world` çıktısını vermeli.

- Bir `.gitignore` dosyası oluşturun ve aşağıdaki kodları içerisine ekleyin:

```
npm-debug.log
yarn-error.log
```

**Not**: Eğer benim size sağladığım `package.json` dosyasına bakarsanız her bölümde bir `tutorial-test` script'i göreceksiniz. Bu scriptler benim bütün bölümlerin `yarn && yarn start` komutunu çalıştırdığımda iyi çalıştığını test etmek için var. Kendi projelerinizde bunu silebilirsiniz.

Sonraki bölüm: [2 - Bir paket kurup kullanma](/tutorial/2-packages)

[İçindekilere](https://github.com/verekia/js-stack-from-scratch) geri dön.
