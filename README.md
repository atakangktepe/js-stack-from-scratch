# JavaScript Stack from Scratch

[![Yarn](/img/yarn.png)](https://yarnpkg.com/)
[![React](/img/react.png)](https://facebook.github.io/react/)
[![Gulp](/img/gulp.png)](http://gulpjs.com/)
[![Redux](/img/redux.png)](http://redux.js.org/)
[![ESLint](/img/eslint.png)](http://eslint.org/)
[![Webpack](/img/webpack.png)](https://webpack.github.io/)
[![Mocha](/img/mocha.png)](https://mochajs.org/)
[![Chai](/img/chai.png)](http://chaijs.com/)
[![Flow](/img/flow.png)](https://flowtype.org/)

[![Build Status](https://travis-ci.org/verekia/js-stack-from-scratch.svg?branch=master)](https://travis-ci.org/verekia/js-stack-from-scratch)

Modern Javascript yazısına hoşgeldiniz! Orjinal yazıyı buradan görebilirsiniz: [https://github.com/verekia/js-stack-from-scratch](JavaScript Stack from Scratch)

Bu minimalistik bir Javascript çatısı kurma yazısıdır. Bu yazı genel programlama ve JavaScript temelleri bilgisi gerektirir. Bu yazı araçları birbirine bağlamaya ve her araç için bir örnek vermeye odaklanmıştır. Bu yazıyı sıfırdan kendi *boilerplate*'inizi yazmak olarak düşünebilirsiniz.

Eğer biraz etkileşimli basit bir websitesi yapıyorsanız tabii ki bu çatıya ihtiyacınız yok (Babel + jQuery kombinaysonu sizin için yeterli!), fakat ölçeklenebilir bir web uygulaması yapacaksanız bu yazı sizin için mükemmel olacaktır.

Bu yazının amacı çeşitli araçları birleştirmektir, bu araçların detaylarına inip nasıl çalıştığı hakkında bilgi vermeyeceğim. Derin bilgiye ulaşmak için o araçların dökümantasyonlarına veya başka yazılara göz atabilirsiniz. 

Bu yazının büyük bir bölümünde React kullanılmıştır, Eğer başlangıçtaysanız ve sadece React öğrenmek istiyorsanız [create-react-app](https://github.com/facebookincubator/create-react-app) *repo*'su önceden hazırlanmış yapılandırmayla React ortamını hızlı kurmanıza sağlayacaktır. Bu yazıda daha önce yapılandırılmış bir ayara ihtiyacınız yok, çünkü ben sizin bütün bu yapının altında neler olduğunu anlamanızı istiyorum.

Kod örnekleri bütün bölümlerde var ve `yarn && yarn start` veya `npm install && npm start` komutlarıyla çalıştırabilirsin. Ben size sıfırdan adım adım talimatları izleyerek ilerlemenizi öneriyorum.

**Bütün bölümler bir önceki bölümün kodarını içeriyor**, yani eğer bir *boilerplate* istiyorsanız sadece son bölümü kopyalayıp devam edebilirsiniz. 

Note: The order of chapters is not necessarily the most educational. For instance, testing / type checking could have been done before introducing React. It is quite difficult to move chapters around or edit past ones, since I need to apply those changes to every following chapter. If things settle down, I might reorganize the whole thing in a better way.

Bu yazının kodları Linux, macOs ve Windows ortamında çalışır.

## İçindekiler

[1 - Node, NPM, Yarn, ve package.json](/tutorial/1-node-npm-yarn-package-json)

[2 - Bir paket kurup kullanma](/tutorial/2-packages)

[3 - Babel ve Gulp ile ES6 ayarlama](/tutorial/3-es6-babel-gulp)

[4 - ES6 sözdizimini bir class ile kullanmak](/tutorial/4-es6-syntax-class)

[5 - ES6 modül sözdizimi](/tutorial/5-es6-modules-syntax)

[6 - ESLint](/tutorial/6-eslint)

[7 - Webpack ile Client uygulaması](/tutorial/7-client-webpack)

[8 - React](/tutorial/8-react)

[9 - Redux](/tutorial/9-redux)

[10 - Immutable JS ve Redux iyileştirmeleri](/tutorial/10-immutable-redux-improvements)

[11 - Mocha, Chai, ve Sinon ile test yapma](/tutorial/11-testing-mocha-chai-sinon)

[12 - Flow ile Tip Denetleme (Type Checking)](/tutorial/12-flow)

## Sırada

Üretim/Geliştirme ortamları, Express, React Router, Server-side Rendering, Styling, Enzyme, Git Hooks.

## Çeviriler

- [Chinese](https://github.com/pd4d10/js-stack-from-scratch) by [@pd4d10](http://github.com/pd4d10)
- [Italian](https://github.com/fbertone/js-stack-from-scratch) by [Fabrizio Bertone](https://github.com/fbertone)
- [Turkish](https://github.com/atakangktepe/js-stack-from-scratch) by [Atakan Goktepe](https://github.com/atakangktepe)

Eğer kendi çevirinizi eklemek istiyorsanız, başlamak için lütfen [çeviri önerileri](/how-to-translate.md) bölümünü okuyun!

## Katkıda Bulunanlar

[@verekia](https://twitter.com/verekia) tarafından oluşturuldu – [verekia.com](http://verekia.com/).

Lisans: MIT
