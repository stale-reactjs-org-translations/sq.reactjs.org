---
title: Përdorim i Shpejtë
---

<Intro>

Mirë se vini në dokumentacionin e React! Kjo faqe do t'ju japë një hyrje të 80% të koncepteve të React që do të përdorni çdo ditë.

</Intro>

<YouWillLearn>

- Si të krijoni dhe t'i bëni *nest* komponentët
- Si të shtoni *markup* dhe stile
- Si të shfaqni të dhënat
- Si të bëni *render* kushtet dhe listat
- Si t'i përgjigjeni *event*-eve dhe të përditësoni ekranin
- Si të shpërndani të dhënat midis komponentëve

</YouWillLearn>

## Krijimi dhe *nesting* (nënvendosja/ndërfutja) e komponentëve {/*components*/}

Aplikacionet React janë përbërë nga *komponentë*. Një komponent është një pjesë e UI (ndërfaqja e përdoruesit) që ka logjikën dhe pamjen e vet. Një komponent mund të jetë aq i vogël sa një buton, ose i madh sa një faqe e tërë.

Komponentët React janë funksione JavaScript që kthejnë *markup*:

```js
function MyButton() {
  return (
    <button>I'm a button</button>
  );
}
```

Tani që keni deklaruar `MyButton`, mund ta nënvendosni atë në një komponent tjetër:

```js {5}
export default function MyApp() {
  return (
    <div>
      <h1>Welcome to my app</h1>
      <MyButton />
    </div>
  );
}
```

Vini re se `<MyButton />` fillon me një shkronjë të madhe. Kështu e dini se është një komponent React. Emrat e komponentëve React duhet të fillojnë gjithmonë me shkronjë të madhe, ndërsa etiketat HTML duhet të jenë të vogla.

Hidhini një sy rezultatit:

<Sandpack>

```js
function MyButton() {
  return (
    <button>
      I'm a button
    </button>
  );
}

export default function MyApp() {
  return (
    <div>
      <h1>Welcome to my app</h1>
      <MyButton />
    </div>
  );
}
```

</Sandpack>

Fjalët kyçe `export default` specifikojnë komponentin kryesor në skedar. Nëse nuk jeni familjar me ndonjë pjesë të sintaksës JavaScript, [MDN](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export) dhe [javascript.info](https://javascript.info/import-export) janë referencë shumë e mirë.

## Shkrimi i *markup* me JSX {/*writing-markup-with-jsx*/}

Sintaksa e *markup* që keni parë më lart quhet *JSX*. Është opsionale, por shumica e projekteve React përdorin JSX për lehtësinë e tij. Të gjitha [mjetet që rekomandojmë për zhvillimin lokal](/learn/installation) e mbështesin JSX.

JSX është më i rreptë se HTML. Ju duhet të mbyllni etiketat si `<br />`. Komponenti juaj gjithashtu nuk mund të kthejë mëshumë se një JSX. Ju duhet t'i bëni *wrap* (t'i mbështillni) ato në një *parent* (prind) të përbashkët, si p.sh. `<div>...</div>` ose një *wrapper* (mbështjellës) bosh `<>...</>` wrapper:

```js {3,6}
function AboutPage() {
  return (
    <>
      <h1>About</h1>
      <p>Hello there.<br />How do you do?</p>
    </>
  );
}
```

Nëse keni shumë HTML për të kthyer në JSX, mund të përdorni një [konvertues online](https://transform.tools/html-to-jsx).

## Shtimi i stileve {/*adding-styles*/}

Në React, ju specifikoni një klasë CSS me `className`. Funksionon në të njëjtën mënyrë si atributi HTML [`class`](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/class):

```js
<img className="avatar" />
```

Pastaj shkruani për të rregullat CSS në një skedar të veçantë CSS:

```css
/* Në CSS tuaj */
.avatar {
  border-radius: 50%;
}
```

React nuk përshkruan se si të shtoni skedarë CSS. Në rastin më të thjeshtë, do të shtoni një etiketë [`<link>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link) Nëse përdorni ndonjë lloj mjeti zhvillimi apo *framework*, konsultohuni me dokumentacionin e tij për të mësuar se si të shtoni një skedar CSS në projektin tuaj.

## Shfaqja e të dhënave {/*displaying-data*/}

JSX ju lejon të vendosni *markup* në JavaScript. Kllapat gjarpërore mundësojnë që ta ktheni kodin në JavaScript në mënyrë që të mund të futni disa ndryshore (*variables*) aty dhe t'ia shfaqni ato përdoruesit. Për shembull, kjo do të shfaqë `user.name`:

```js {3}
return (
  <h1>
    {user.name}
  </h1>
);
```

Gjithashtu, mund ta ktheni kodin në JavaScript dhe në atributet JSX, por ju duhet të përdorni kllapa gjarpërore *në vend të* thonjëzave. Për shembull, `className="avatar"` kalon germëvargun `"avatar"` si klasë CSS, por `src={user.imageUrl}` lexon vlerën e ndryshores JavaScript `user.imageUrl` dhe më pas e kalon atë vlerë si atributi  i `src`:

```js {3,4}
return (
  <img
    className="avatar"
    src={user.imageUrl}
  />
);
```

Mund të vendosni edhe shprehje më komplekse brenda kllapave gjarpërore JSX, për shembull, [string concatenation](https://javascript.info/operators#string-concatenation-with-binary) (bashkim i germëvargjeve)::

<Sandpack>

```js
const user = {
  name: 'Skënderbeu',
  imageUrl: 'https://play-lh.googleusercontent.com/NOBGFofQqTTsttDXIveKnIhSOQg8cqxk2YE7tNtSDVnFfjJ_j1f_EPYsGl-lw85VJoI',
  imageSize: 90,
};

export default function Profile() {
  return (
    <>
      <h1>{user.name}</h1>
      <img
        className="avatar"
        src={user.imageUrl}
        alt={'Photo of ' + user.name}
        style={{
          width: user.imageSize,
          height: user.imageSize
        }}
      />
    </>
  );
}
```

```css
.avatar {
  border-radius: 50%;
}

.large {
  border: 4px solid gold;
}
```

</Sandpack>

Në shembullin e mësipërm, `style={{}}` nuk është një sintaksë e veçantë, por një objekt i rregullt `{}` brenda kllapave gjarpërore JSX të `style={ }`. Ju mund të përdorni atributin `style` kur stilet tuaja varen nga ndryshoret JavaScript.

## *Conditional rendering* (Gjenerimi/Pasqyrimi i kushtëzuar) {/*conditional-rendering*/}

Në React, nuk ka sintaksë të veçantë për të shkruar pohimet e kushtëzuara. Përkundrazi, do të përdorni të njëjtat teknika që përdorni kur shkruani kodin e zakonshëm JavaScript. Për shembull, mund të përdorni pohimin e kushtëzuarn [`if`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else) për të përfshirë me kusht JSX:

```js
let content;
if (isLoggedIn) {
  content = <AdminPanel />;
} else {
  content = <LoginForm />;
}
return (
  <div>
    {content}
  </div>
);
```

Nëse preferoni kod më kompakt, mund të përdorni [operatorin e kushtëzuar `?`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator). Ndryshe nga `if`, funksionon brenda JSX:

```js
<div>
  {isLoggedIn ? (
    <AdminPanel />
  ) : (
    <LoginForm />
  )}
</div>
```

Kur nuk keni nevojë për `else`, mund të përdorni sintaksën për [operatorin logjik `&&`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND#short-circuit_evaluation):

```js
<div>
  {isLoggedIn && <AdminPanel />}
</div>
```

Të gjitha këto qasje funksionojnë edhe për specifikimin e kushtëzuar të atributeve. Nëse nuk jeni familjar me disa nga këto sintaksa JavaScript, mund të filloni duke përdorur gjithmonë `if...else`.

## *Rendering* i listave {/*rendering-lists*/}

Do të mbështeteni në veçoritë e JavaScript si [`for` loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for) dhe [array `map()` function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) për të bërë *render*  listën e komponentëve.

Për shembull, le të themi se keni një *array* produktesh:

```js
const products = [
  { title: 'Patate', id: 1 },
  { title: 'Qepë', id: 2 },
  { title: 'Mollë', id: 3 },
];
```

Brenda komponentit tuaj, përdorni funksionin `map()` për të transformuar një *array* produktesh në një *array* artikujsh `<li>`:

```js
const listItems = products.map(product =>
  <li key={product.id}>
    {product.title}
  </li>
);

return (
  <ul>{listItems}</ul>
);
```

Vini re se si `<li>` ka një atribut `key`. Për çdo artikull në një listë, duhet të kaloni një germëvarg ose një numër që e identifikon në mënyrë unike atë artikull midis artikujve të tjerë në *array*. Zakonisht, një *key* duhet të vijë nga të dhënat tuaja, siç është një ID e databazës. React do të mbështetet në këto *keys* për të kuptuar se çfarë ndodhi, nëse më vonë futni, fshini ose rirenditni artikujt.

<Sandpack>

```js
const products = [
  { title: 'Patate', isFruit: false, id: 1 },
  { title: 'Qepë', isFruit: false, id: 2 },
  { title: 'Mollë', isFruit: true, id: 3 },
];

export default function ShoppingList() {
  const listItems = products.map(product =>
    <li
      key={product.id}
      style={{
        color: product.isFruit ? 'magenta' : 'darkgreen'
      }}
    >
      {product.title}
    </li>
  );

  return (
    <ul>{listItems}</ul>
  );
}
```

</Sandpack>

## T'i përgjigjesh *event*-eve {/*responding-to-events*/}

Ju mund t'i përgjigjeni *event*-eve duke deklaruar funksionet *event handler* brenda komponentëve tuaj:

```js {2-4,7}
function MyButton() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}
```

Vini re se si `onClick={handleClick}` nuk ka kllapa në fund! Mos _thirr_ funksionin *event handler*: nevojitet vetëm ta *kaloni atë*. React do të thërras *event handler* kur përdoruesi të klikojë butonin.

## Përditësimi i ekranit {/*updating-the-screen*/}

Shpesh, do ju duhet që komponenti juaj të "kujtojë" disa informacione dhe t'i shfaqë ato. Për shembull, ndoshta ju duhet të numëroni sa herë klikohet një buton. Për ta bërë këtë, shtoni *state* në komponentin tuaj.

Së pari, importoni [`useState`](/apis/usestate) nga React:

```js {1,4}
import { useState } from 'react';
```

Tani mund të deklaroni një *ndryshore të state* brenda komponentit tuaj:

```js
function MyButton() {
  const [count, setCount] = useState(0);
```

Do të merrni dy gjëra nga `useState`: *state* (dmth gjendjen) aktuale të (`count`), (dmth të numërimit), dhe funksionin që ju lejon ta përditësoni atë (`setCount`) (dmth caktoNumërimin). Mund t'u jepni atyre çdo emër, por zakoni është që t'i quani si shembulli: `[something, setSomething]` >>  `[diçka, caktoDiçka]`.

Herën e parë që shfaqet butoni, `count` do të jetë `0` sepse i keni dhënë vlerën `0` në `useState()`. Kur t'ju duhet të ndryshoni *state*, thirrni `setCount()` dhe kaloni vlerën e re. Duke klikuar këtë buton do të rritet numëruesi:

```js {5}
function MyButton() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <button onClick={handleClick}>
      Clicked {count} times
    </button>
  );
}
```

React do të thërrasë përsëri funksionin e komponentit tuaj. Këtë herë, `numërimi` do të jetë `1`. Pastaj do të jetë `2`. Dhe kështu me radhë.

Nëse e bëni *render*  të njëjtin komponent disa herë, secili do të marrë gjendjen e vet. Provoni të klikoni secilin buton veç e veç:

<Sandpack>

```js
import { useState } from 'react';

function MyButton() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <button onClick={handleClick}>
      Klikuar {count} herë
    </button>
  );
}

export default function MyApp() {
  return (
    <div>
      <h1>Numëruesit që përditësohen veçmas</h1>
      <MyButton />
      <MyButton />
    </div>
  );
}
```

```css
button {
  display: block;
  margin-bottom: 5px;
}
```

</Sandpack>

Vini re se si çdo buton "kujton" *state*-in e tij të `count` dhe nuk ndikon në butonat e tjerë.

## Përdorimi i Hooks {/*using-hooks*/}

Funksionet që fillojnë me `use` quhen *Hooks*. `useState` është një Hook i integruar i ofruar nga React. Mund të gjeni Hooks të tjerë të integruar në referencën për [React APIs](/apis). Mundeni gjithashtu të shkruani Hooks të juajat duke kombinuar ato ekzistuese.

Hooks janë më të kufizuar se funksionet e zakonshme. Mund t'i thirrni Hooks vetëm  *në nivelin më të lartë* (*top level*) të komponentëve tuaj (ose të Hooks-ëve tjerë). Nëse doni të përdorni `useState` në një pohim të kushtëzuar ose në një *loop* (cikël), bëni ekstrakt një komponent të ri dhe vendoseni atje.

## Ndarja e të dhënave ndërmjet komponentëve {/*sharing-data-between-components*/}

Në shembullin e mëparshëm, çdo `MyButton` kishte `count`-in (numërimin) e vet të pavarur dhe kur klikohej, secili buton, ndryshonte vetëm `count` për butonin e klikuar:

<DiagramGroup>

<Diagram name="sharing_data_child" height={367} width={407} alt="Diagram showing a tree of three components, one parent labeled MyApp and two children labeled MyButton. Both MyButton components contain a count with value zero.">

Fillimisht, çdo *state* i `count` i `MyButton` është `0`.

</Diagram>

<Diagram name="sharing_data_child_clicked" height={367} width={407} alt="The same diagram as the previous, with the count of the first child MyButton component highlighted indicating a click with the count value incremented to one. The second MyButton component still contains value zero." >

`MyButton` i parë përditëson `count`-in e tij në `1`.

</Diagram>

</DiagramGroup>

Megjithatë, shpesh do t'ju duhen komponentë që *të ndajnë të dhënat dhe të përditësohen gjithmonë së bashku*..

Për të bërë që të dy komponentët `MyButton` të shfaqin të njëjtin `count`dhe të përditësohen së bashku, duhet ta zhvendosni *state* nga butonat specifik, duke e çuar "lart" në komponentin më të afërt që i përmban të dy.

Në këtë shembull, është `MyApp`:

<DiagramGroup>

<Diagram name="sharing_data_parent" height={385} width={410} alt="Diagram showing a tree of three components, one parent labeled MyApp and two children labeled MyButton. MyApp contains a count value of zero which is passed down to both of the MyButton components, which also show value zero." >

Fillimisht, *state* i `count` i `MyApp` është `0` dhe u transmetohet të dy "degëzimeve" (*children* - fëmijëve - sipas shembullit të pemës React).

</Diagram>

<Diagram name="sharing_data_parent_clicked" height={385} width={410} alt="The same diagram as the previous, with the count of the parent MyApp component highlighted indicating a click with the value incremented to one. The flow to both of the children MyButton components is also highlighted, and the count value in each child is set to one indicating the value was passed down." >

Në klikim, `MyApp` përditëson *state*-in e tij të `count` në `1` dhe ua kalon të dy "degëzimeve" (*children* - fëmijëve - sipas shembullit të pemës React).

</Diagram>

</DiagramGroup>

Tani kur klikoni njërin nga butonat, `count` në `MyApp` do të ndryshojë, gjë që do të ndryshojë të dy `count` në `MyButton`. Ja se si mund ta shprehni këtë me kod.

Së pari, *zhvendoseni lart state*  nga `MyButton` në `MyApp`:

```js {2,6-10}
function MyButton() {
  // ... po e zhvendosim kodin nga këtu ...
}

export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Numëruesit që përditësohen veçmas</h1>
      <MyButton />
      <MyButton />
    </div>
  );
}
```

Më pas, *kaloni state poshtë* nga `MyApp` te secili `MyButton`, së bashku me *click handler*. Ju mund t'i kaloni informacionet `MyButton` duke përdorur kllapat gjarpërore, ashtu siç keni bërë më parë me etiketat e integruara si `<img>`:

```js {11-12}
export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Numëruesit që përditësohen veçmas</h1>
      <MyButton count={count} onClick={handleClick} />
      <MyButton count={count} onClick={handleClick} />
    </div>
  );
}
```

Informacioni që kaloni për poshtë siç bëtë tani, quhet _props_. Tani komponenti `MyApp` përmban *state*-in e `count` dhe `handleClick` *event handler*, dhe *ja kalon të dyja poshtë si props* secilit buton.

Së fundi, ndryshoni `MyButton` për të *lexuar* *props* që keni kaluar nga komponenti i tij mëmë:

```js {1,3}
function MyButton({ count, onClick }) {
  return (
    <button onClick={onClick}>
      Klikuar {count} herë
    </button>
  );
}
```

Kur klikoni butonin, "shkrepet" `onClick` *handler*. Secilit *prop* `onClick` të butonave, ju caktua funksioni `handleClick` brenda `MyApp`, kështu që kodi brenda ktij funksioni do të ekzekutohet. Ky kod thërret `setCount(count + 1)`, duke rritur ndryshoren `count` të state. Vlera e re e `count` i kalohet si *prop* secilit buton, kështu që të gjithë ato do të tregojnë vlerën e re.

Kjo quhet "ngritja e gjendjes lart" (në origjinal në anglisht, është shprehja që do ta hasni shpesh: *lifting state up*). Duke lëvizur *state*-in lart, ne mund ta ndajmë atë midis komponentëve.

<Sandpack>

```js
import { useState } from 'react';

function MyButton({ count, onClick }) {
  return (
    <button onClick={onClick}>
      Klikuar {count} herë
    </button>
  );
}

export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Numëruesit që përditësohen së bashku</h1>
      <MyButton count={count} onClick={handleClick} />
      <MyButton count={count} onClick={handleClick} />
    </div>
  );
}
```

```css
button {
  display: block;
  margin-bottom: 5px;
}
```

</Sandpack>

## Hapat e ardhshëm {/*next-steps*/}

Tashmë, ju i dini bazat se si të shkruani kod me React!

Drejtohuni në [Të mendosh si React](/learn/thinking-in-react) për të parë se si është në praktikë të ndërtosh një UI me React.
