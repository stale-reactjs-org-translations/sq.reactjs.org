---
title: Filloni një projekt të ri me React
---

<Intro>

Nëse po filloni një projekt të ri, ju rekomandojmë të përdorni një *toolchain* ose një *framework*. Këto mjete ofrojnë një mjedis të rehatshëm zhvillimi, por kërkojnë një instalim në nivel lokal të Node.js.

*Toolchain* është grup mjetesh për zhvillimin e softuerit të përdorur në kombinim me njëri-tjetrin për të përfunduar detyra komplekse të zhvillimit të softuerit.
*Framework* në programim është një mjet që ofron komponentë të gatshëm ose zgjidhje që janë të personalizuara për të përshpejtuar zhvillimin.


</Intro>

<YouWillLearn>

* Si ndryshojnë toolchains nga frameworks
* Si të filloni një projekt me toolchain minimal
* Si të filloni një projekt me një framework me funksione të plota
* Çfarë ka në brendi të toolchain-ëve dhe framework-ëve më të njohur

</YouWillLearn>

## Zgjidhni vetë aventurën tuaj {/*choose-your-own-adventure*/}

React është një librari që ju lejon të organizoni kodin UI (ndërfaqja e përdoruesit) duke e ndarë atë në pjesë të quajtura komponentë. React nuk kujdeset për routing (rrugëzim) ose menaxhimin e të dhënave. Kjo do të thotë se ka disa mënyra për të nisur një projekt të ri me React:

* [Filloni me një **skedar HTML dhe një etiketë skripti **.](/learn/add-react-to-a-website) Kjo nuk kërkon konfigurimin e Node.js, por ofron veçori të kufizuara.
* Filloni me një **toolchain minimal,** duke shtuar më shumë veçori në projektin tuaj me kalimin e kohës. (E shkëlqyeshme për të mësuar!)
* Filloni me një *opinionated framework* që ka veçori të zakonshme si fetching e të dhënave (marrja e të dhënave) dhe built-in routing (rrugëzim të pre-integruar/instaluar).

*Opinionated Framework* është një framework i ndërtuar që t'i bëj gjërat në një mënyrë të caktuar (mënyra e duhur). Ndaj epiteti opinionated = "kokëfortë".

## Të fillosh me një *toolchain* minimal {/*getting-started-with-a-minimal-toolchain*/}

Nëse po mësoni React, ne ju rekomandojmë [Create React App](https://create-react-app.dev/). Është mënyra më e zakonshme për të provuar React dhe për të ndërtuar një aplikacion *single-page client-side* (një-faqëshe në anën e klientit). Është krijuar për React, por nuk është *opinionated* për *routing* ose *fetching* të të dhënave.

Së pari, instaloni [Node.js](https://nodejs.org/en/). Pastaj hapni terminalin dhe ekzekutoni këtë rresht kodi për të krijuar një projekt:

<TerminalBlock>

npx create-react-app my-app

</TerminalBlock>

Tani mund ta ekzekutoni aplikacionin tuaj me:

<TerminalBlock>

cd my-app
npm start

</TerminalBlock>

Për më shumë informacion, [shikoni udhëzuesin zyrtar](https://create-react-app.dev/docs/getting-started).

> Create React App nuk menaxhon llogjiken e backend apo të databazës. Mund ta përdorni me çdo backend.  Kur të ndërtoni një projekt, do të keni një dosje me HTML statike, CSS dhe JS. Për shkak se Create React App nuk mund të ketë avantazhet e një serveri, ai nuk ofron performancën më të mirë. Nëse jeni duke kërkuar për kohë më të shpejta ngarkimi (*loading*) dhe veçori të integruara *routing* dhe llogjikën *server-side* (të serverit), ju rekomandojmë të përdorni një *framework*.

### Alternativa të përhapura {/*popular-alternatives*/}

* [Vite](https://vitejs.dev/guide/)
* [Parcel](https://parceljs.org/)

## Të ndërtosh me frameworks me funksione të plota {/*building-with-a-full-featured-framework*/}

Nëse po kërkoni të **filloni një projekt të gatshëm për prodhim,** [Next.js](https://nextjs.org/) ja vlen të konsiderohet. Next.js është një framework goxha i njohur, dhe i lehtë, për aplikacionet e ndërtuara me React, që janë statike dhe *server-rendered* (gjeneruara në server). Ai vjen i para-paketuar me veçori të tilla si *routing*, *styling* (stilim), dhe *server-side rendering*, duke e bërë funksional projektin tuaj kollaj dhe shpejt.

Tutoriali i [Next.js Foundations](https://nextjs.org/learn/foundations/about-nextjs) është një udhëzues i mirë si fillim, për kë do të ndërtoj me React dhe Next.js.

### Alternativat më të përhapura {/*popular-alternatives*/}

* [Gatsby](https://www.gatsbyjs.org/)
* [Remix](https://remix.run/)
* [Razzle](https://razzlejs.org/)

## Toolchains të personalizuara {/*custom-toolchains*/}

Ju mund të preferoni të krijoni dhe konfiguroni *toolchain*-in tuaj. Një *toolchain* zakonisht përbëhet nga:

* Një *package manager* (menaxher paketash) ju lejon të instaloni, përditësoni dhe menaxhoni *packages* (paketat) e palëve të treta. Disa *package manager* të njohur janë: [npm](https://www.npmjs.com/) (ndërtuar në Node.js), [Yarn](https://yarnpkg.com/), [pnpm](https://pnpm.io/).
* Një *compiler* (kompilator) ju lejon të bëni *compile* (të kompiloni) veçori të gjuhës moderne, bashkë me sintaksën si puna e JSX, apo *type annotations* (indikues të llojit të të dhënave) për *browser*-in, si: [Babel](https://babeljs.io/), [TypeScript](http://typescript.org/), [swc](https://swc.rs/).
* Një *bundler* ju lejon të shkruani kod modular dhe ta bëni *bundle* atë, pra ta bashkoni atë në paketa të vogla për të optimizuar kohën e ngarkimit (*loading*). Disa *bundlers* të njohur janë: [webpack](https://webpack.js.org/), [Parcel](https://parceljs.org/), [esbuild](https://esbuild.github.io/), [swc](https://swc.rs/).
* Një *minifier* (minifikues) e bën kodin tuaj më kompakt në mënyrë që të ngarkohet më shpejt. Disa *minifier* të njohur janë: [Terser](https://terser.org/), [swc](https://swc.rs/).
* Një *server* trajton *server requests* (kërkesat e server-it) në mënyrë që të bësh *render* (gjenerosh) komponentët në HTML. Një server i njohur është: [Express](https://expressjs.com/).
* Një *linter* kontrollon kodin tuaj për gabime të zakonshme. Një *linter* i njohur është: [ESLint](https://eslint.org/).
* Një *test runner* (testues) ju lejon të kryeni teste për kodin tuaj. Një testues i njohur është: [Jest](https://jestjs.io/).

Nëse preferoni të konfiguroni *toolchain*-in tuaj të JavaScript nga e para, shikoni këtë udhëzues që rikrijon disa nga funksionet e aplikacionit Create React. Një *framework* zakonisht do të sigurojë gjithashtu një *routing* dhe një zgjidhje për *fetching* të të dhënave. Në një projekt më të madh, mund të dëshironi gjithashtu të menaxhoni *packages* të shumta në një *repository* (depo) të vetme me një mjet si [Nx](https://nx.dev/react) or [Turborepo](https://turborepo.org/).

