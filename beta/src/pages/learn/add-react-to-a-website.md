---
title: Shto React në një website
---

<Intro>

Ju nuk keni pse të ndërtoni të gjithë website-in me React. Shtimi i React në HTML nuk kërkon instalim, zgjat një minutë dhe ju lejon të filloni menjëherë të shkruani komponentë ndërveprues.

</Intro>

<YouWillLearn>

* Si të shtoni React në një faqe HTML në një minutë
* Çfarë është sintaksa JSX dhe si ta provoni menjëherë
* Si të konfiguroni një preprocesor JSX për prodhim

</YouWillLearn>

## Shto React në një minutë {/*add-react-in-one-minute*/}

React është projektuar që në fillim për adoptim gradual. Shumica e faqeve të internetit nuk janë (dhe nuk kanë nevojë të jenë) plotësisht të ndërtuara me React. Ky udhëzues tregon se si të shtoni pak interaktivitet në një faqe ekzistuese HTML.

Provojeni këtë me faqen tuaj të internetit ose me një [skedar bosh HTML](https://gist.github.com/gaearon/edf814aeee85062bc9b9830aeaf27b88/archive/3b31c3cdcea7dfcfd38a81905a0052dd8e5f71ec.zip). Gjithçka që ju nevojitet është një lidhje interneti dhe një redaktues teksti si Notepad ose VSCode. (Ja se si të [konfiguroni redaktorin tuaj për theksimin e sintaksës!](/learn/editor-setup/) for syntax highlighting!)

### Hapi 1: Shtoni një etiketë HTML root (rrënjë) {/*step-1-add-a-root-html-tag*/}

Së pari, hapni faqen HTML që dëshironi të redaktoni.Shtoni një etiketë bosh `<div>` për të shënuar vendin ku dëshironi të shfaqni diçka me React. Jepini këtij `<div>` një `id` me vlerë të atributit unike . Për shembull:
```html {3}
<!-- ... HTML ekzistuese ... -->

<div id="like-button-root"></div>

<!-- ... HTML ekzistuese ... -->
```

Quhet "root" (rrënjë) sepse aty do të fillojë React tree (pema e React). Ju mund të vendosni një etiketë HTML root si kjo, kudo brenda etiketës `<body>`. Lëreni bosh sepse React do të zëvendësojë përmbajtjen e tij me komponentin tuaj React.

Mund të keni aq etiketa HTML rrënjë sa ju nevojiten në një faqe.

### Hapi 2: Shtoni etiketat e skriptit {/*step-2-add-the-script-tags*/}

Në faqen HTML, menjëherë përpara etiketës `</body>` mbyllëse, shtoni tre etiketa `<script>` për skedarët e mëposhtëm:

- [`react.development.js`](https://unpkg.com/react@18/umd/react.development.js) ju lejon të përcaktoni komponentët React.
- [`react-dom.development.js`](https://unpkg.com/react-dom@18/umd/react-dom.development.js) lejon që React të bëj render (gjeneroj) elementë HTML në [DOM].(https://developer.mozilla.org/docs/Web/API/Document_Object_Model).
- **`like-button.js`** është vendi ku do të shkruani komponentin tuaj në hapin tjetër!

HTML juaj tani duhet të përfundojë kështu:

```html
    <!-- fundi i faqes -->
    <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
    <script src="like-button.js"></script>
  </body>
</html>
```

<Gotcha>

Përpara se të bëni *deploy* në një website *live*, sigurohuni që të zëvendësoni `development.js` me `production.min.js`! *Development build* të React japin mesazhe error më ndihmuese, por ngadalësojnë **goxha** website-in tuaj.

</Gotcha>

### Hapi 3: Krijoni një komponent React {/*step-3-create-a-react-component*/}

Krijoni një skedar të quajtur **`like-button.js`** pranë faqes tuaj HTML, shtoni këtë copë kodi dhe ruajeni skedarin. Ky kod përcakton një komponent React të quajtur LikeButton.  (Mësoni më shumë rreth krijimit të komponentëve në [Nisje e shpejtë!](/learn))

```js
'use strict';

function LikeButton() {
  const [liked, setLiked] = React.useState(false);

  if (liked) {
    return 'You liked this!';
  }

  return React.createElement(
    'button',
    {
      onClick: () => setLiked(true),
    },
    'Like'
  );
}
```

### Hapi 4: Shtoni komponentin tuaj React në faqe {/*step-4-add-your-react-component-to-the-page*/}

Së fundmi, shtoni tre rreshta në fund të **`like-button.js`**. Këto rreshta kodi gjejnë `<div>` që keni shtuar në HTML në hapin e parë, krijojnë një React root, dhe më pas shfaqin butonin "Like" komponent React brenda tij:

```js
const rootNode = document.getElementById('like-button-root');
const root = ReactDOM.createRoot(rootNode);
root.render(React.createElement(LikeButton));
```

**Urime! Sapo keni bërë *render* komponentin tuaj të parë React në website-in tuaj!**

- [Shikoni shembullin e plotë të kodit](https://gist.github.com/gaearon/0b535239e7f39c524f9c7dc77c44f09e)
- [Shkarkoni shembullin e plotë (2KB zipped)](https://gist.github.com/gaearon/0b535239e7f39c524f9c7dc77c44f09e/archive/651935b26a48ac68b2de032d874526f2d0896848.zip)

#### Ju mund të ripërdorni komponentët! {/*you-can-reuse-components*/}

Ju mund të doni të shfaqni komponentët React në shumë vende në të njëjtën faqe HTML. Kjo është e dobishme nëse pjesët në faqen tuaj që janë me React, janë të ndara nga njëra-tjetra. Ju mund ta bëni këtë duke vendosur etiketa të shumta root në HTML-në tuaj dhe më pas duke bërë render komponentët React brenda secilit prej tyre me `ReactDOM.createRoot()`. Për shembull:

1. Në **`index.html`**, shtoni një element *container* shtesë `<div id="another-root"></div>`.
2. Në **`like-button.js`**, shtoni tre rreshta të tjerë në fund:

```js {6,7,8,9}
const anotherRootNode = document.getElementById('another-root');
const anotherRoot = ReactDOM.createRoot(anotherRootNode);
anotherRoot.render(React.createElement(LikeButton));
```

Nëse ju duhet të bëni *render* të njëjtin komponent në shumë vende, mund të caktoni një CSS *class* (klasë) në vend të id-së për secilën *root*, dhe më pas t'i gjeni të gjitha. Këtu është [një shembull që shfaq tre butona "Like" dhe i kalon të dhënat secilit.](https://gist.github.com/gaearon/779b12e05ffd5f51ffadd50b7ded5bc8)

### Hapi 5: *Minify* JavaScript për prodhim {/*step-5-minify-javascript-for-production*/}

JavaScript jo në version *minify* (e minimizuar) mund të ngadalësojë ndjeshëm kohën e ngarkimit të faqeve për përdoruesit tuaj. Përpara se të bëni *deploy* në prodhim website-in tuaj, është një ide e mirë të bëni *minify* (minimizoni) skriptet e saj.

- **Nëse nuk keni marrë një hap t'i bëni *minify*** skriptet tuaja, [këtu është një mënyrë për ta konfiguruar](https://gist.github.com/gaearon/42a2ffa41b8319948f9be4076286e1f3).
- Nëse i keni bërë *minify* tashmë skriptet e aplikacionit tuaj, faqja juaj do të jetë gati për prodhim nëse siguroheni që HTML-ja në prodhim ngarkon versionet e React që përfundojnë me production.min.js si ky *script*:

```html
<script src="https://unpkg.com/react@18/umd/react.production.min.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js" crossorigin></script>
```

## Provoni React me JSX {/*try-react-with-jsx*/}

Shembujt e mësipërm varen nga veçori që mbështeten nga *browsers* prej vetiu. Kjo është arsyeja pse **`like-button.js`** përdor një *function call* (thirrje funksioni) JavaScript për t'i treguar React se çfarë të shfaqë:

```js
return React.createElement('button', {onClick: () => setLiked(true)}, 'Like');
```

Sidoqoftë, React ofron gjithashtu një opsion për të përdorur [JSX](/learn/writing-markup-with-jsx), një sintaksë JavaScript si HTML, në vend të kësaj:

```jsx
return <button onClick={() => setLiked(true)}>Like</button>;
```

Këto dy copëza kodi janë ekuivalente. JSX është një sintaksë e njohur për të përshkruar *markup*-in në JavaScript. Shumë personave i duket familjar dhe i dobishëm për të shkruar kod për UI—si me React ashtu dhe me librarit e tjera.

> Ju mund të luani me transformimin e HTML *markup* në JSX duke përdorur [këtë konvertues online.](https://babeljs.io/en/repl#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=DwIwrgLhD2B2AEcDCAbAlgYwNYF4DeAFAJTw4B88EAFmgM4B0tAphAMoQCGETBe86WJgBMAXJQBOYJvAC-RGWQBQ8FfAAyaQYuAB6cFDhkgA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=es2015%2Creact%2Cstage-2&prettier=false&targets=&version=7.17).

### Provo JSX {/*try-jsx*/}

Mënyra më e shpejtë për të provuar JSX është të shtoni kompilatorin Babel si një etiketë `<script>` tek faqja. Vendoseni përpara **`like-button.js`**, dhe më pas shtoni atributin `type="text/babel"` në etiketën `<script>` për **`like-button.js`**:

```html {3,4}
  <script src="https://unpkg.com/react@18/umd/react.production.min.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js" crossorigin></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  <script src="like-button.js" type="text/babel"></script>
</body>
```

Tani mund të hapësh **`like-button.js`** dhe ta zëvendësosh

```js
return React.createElement(
  'button',
  {
    onClick: () => setLiked(true),
  },
  'Like'
);
```

me kodin JSX ekuivalent:

```jsx
return (
  <button onClick={() => setLiked(true)}>
    Like
  </button>
);
```

Mund të duket paksa e pazakontë në fillim të përzieni JS me markup, por do të mësoheni! Hidhini një sy [Të shkruash Markup me JSX](/learn/writing-markup-with-jsx) për një hyrje. Këtu keni [një shembull skedari HTML me JSX](https://raw.githubusercontent.com/reactjs/reactjs.org/main/static/html/single-file-example.html) të cilin mund ta shkarkoni dhe ta provoni.

<Gotcha>

Kompilatori `<script>` i Babel është i mirë për të mësuar dhe krijuar demonstrime të thjeshta. Sidoqoftë, **kjo e bën website-in tuaj të ngadaltë dhe nuk është e përshtatshme për prodhim**. Kur të jeni gati për të ecur përpara, hiqni etiketën `<script>` të Babel dhe hiqni atributin `type="text/babel"` që keni shtuar në këtë hap. Në vend të kësaj, në seksionin tjetër do të konfiguroni një paraprocesor JSX për të kthyer të gjitha etiketat tuaja `<script>` nga JSX në JS.

</Gotcha>

### Shtoni JSX në një projekt {/*add-jsx-to-a-project*/}

Shtimi i JSX në një projekt nuk kërkon mjete të komplikuara si [bundler](/learn/start-a-new-react-project#custom-toolchains) apo një server zhvillimi. Shtimi i një paraprocesori JSX është i ngjashëm me shtimin e një paraprocesori CSS.

Shkoni te dosja e projektit tuaj në terminal dhe ngjitni (paste) këto dy komanda (**Sigurohuni që keni [Node.js](https://nodejs.org/) të instaluar!**):

1. `npm init -y` (nëse dështon si komandë, [ja një zgjidhje](https://gist.github.com/gaearon/246f6380610e262f8a648e3e51cad40d))
2. `npm install babel-cli@6 babel-preset-react-app@3`

npm ju duhet vetëm për të instaluar paraprocesorin JSX. Nuk do t'ju duhet për asgjë tjetër. Si React ashtu edhe kodi i aplikacionit mund të qëndrojnë si etiketa `<script>` pa ndryshime.

Urime! Sapo keni shtuar një **konfigurim JSX gati për prodhim** në projektin tuaj.

### Ekzekutoni paraprocesorin JSX {/*run-the-jsx-preprocessor*/}

Ju mund të përpunoni paraprakisht JSX në mënyrë që sa herë që ruani një skedar me JSX në të, transformimi do të riekzekutohet, duke e kthyer skedarin JSX në një skedar të ri JavaScript të thjeshtë që browser mund ta kuptojë. Ja se si ta konfiguroni këtë:

1. Krijo një dosje të quajtur **`src`**.
2. Në terminalin tuaj, ekzekutoni këtë komandë: `npx babel --watch src --out-dir . --presets react-app/prod ` (Mos prisni që të përfundojë! Kjo komandë nis një vëzhgues të automatizuar për modifikime në JSX brenda `src`.)
3. Zhvendosni JSX-in tuaj **`like-button.js`** ([duhet të duket kështu!](https://gist.githubusercontent.com/gaearon/1884acf8834f1ef9a574a953f77ed4d8/raw/dfc664bbd25992c5278c3bf3d8504424c1104ecf/like-button.js)) në dosjen e re **`src`**.

Vëzhguesi do të krijojë një **`like-button.js`** të parapërpunuar me kodin e thjeshtë JavaScript të përshtatshëm për browser-in.

<Gotcha>

Nëse shihni një *error* që thotë "You have mistakenly installed the `babel` package" ("Keni instaluar gabimisht paketën `babel`"), mund të keni humbur [hapin e mëparshëm](#add-jsx-to-a-project). Kryeni atë në të njëjtën dosje dhe më pas provoni përsëri.

</Gotcha>

Mjeti që sapo përdorët quhet Babel dhe mund të mësoni më shumë rreth tij nga [dokumentacioni i tij](https://babeljs.io/docs/en/babel-cli/). Përveç JSX, ju lejon të përdorni veçoritë më të fundit të sintaksës JavaScript pa u shqetësuar për prishjen e browser-ve të vjetër.

Nëse ndiheni rehat me mjetet e ndërtimit dhe dëshironi që ata të bëjnë më shumë për ju, [ne përshkruajmë disa nga *toolchains* më të njohur dhe më të aksesueshëm këtu](/learn/start-a-new-react-project).

<DeepDive title="React pa JSX">

Fillimisht JSX u prezantua për të bërë shkrimin e komponentëve React të dukej po aq familjar sa shkrimi i HTML. Që atëherë, sintaksa është bërë e përhapur. Megjithatë, mund të ketë raste kur ju nuk dëshironi të përdorni ose nuk mund të përdorni JSX. Ju keni dy opsione:

- Përdorni një alternativë JSX si [htm](https://github.com/developit/htm) e cila përdor JavaScript [*template strings*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) në vend të një kompilatori.
- Përdorni [`React.createElement()`](/apis/createelement) e cila ka një strukturë të veçantë të shpjeguar më poshtë.

Me JSX, do të shkruanit një komponent si ky:

```jsx
function Hello(props) {
  return <div>Hello {props.toWhat}</div>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Hello toWhat="World" />, );
```

Me `React.createElement()`, do ta shkruanit kështu:

```js
function Hello(props) {
  return React.createElement('div', null, 'Hello ', props.toWhat);
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  React.createElement(Hello, { toWhat: 'World' }, null)
);
```

Ai pranon disa argumente: `React.createElement(component, props, ...children)`.

Ja se si funksionojnë:

1. Një **komponent**, i cili mund të jetë një *string* (germëvarg) që përfaqëson një element HTML ose një komponent funksioni
2. Një objekt i çdo [***props*** që dëshironi të kaloni](/learn/passing-props-to-a-component)
3. Pjesa tjetër janë ***children*** (fëmijë*) që mund të ketë komponenti, si *string* (germëvarg) ose elementë të tjerë

- Shënim: Një *fëmijë* është një element që është i lidhur me një element *prind* në pemën e dokumentit (*document tree*) dhe që përfshihet direkte nën të. Ne i përshkruajmë elementet në pemë si do të përshkruanim një pemë familjare. Ka paraardhës, pasardhës, prindër, fëmijë dhe vëllezër e motra.
- Në React, *children* është një *prop* i veçantë, që kalon automatikisht në çdo komponent, që mund të përdoret për të bërë *render* përmbajtjen e përfshirë midis etiketave hapëse dhe mbyllëse kur thirret një komponent. Këto lloj komponentësh identifikohen nga dokumentacioni zyrtar si "boxes" (kutia).

Nëse lodheni duke shkruar `React.createElement()`, një *pattern* (model) i zakonshëm është të caktoni një stenografi:

```js
const e = React.createElement;

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(e('div', null, 'Hello World'));
```

Pastaj, nëse preferoni këtë stil, ai mund të jetë po aq i përshtatshëm sa JSX.

</DeepDive>
