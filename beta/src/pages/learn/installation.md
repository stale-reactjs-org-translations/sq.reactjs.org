---
title: Instalimi
---

<Intro>

React është projektuar që në fillim për adoptim gradual. Ju mund të përdorni aq pak ose aq shumë React sa ju nevojitet. Pavarësisht nëse dëshironi thjesht t'i hidhni një sy React, të shtoni pak interaktivitet në një faqe HTML ose të filloni një aplikacion kompleks të mundësuar nga React, ky seksion do t'ju ndihmojë si pikënisje.

</Intro>

<YouWillLearn isChapter={true}>

* [Si të shtoni React në një faqe HTML](/learn/add-react-to-a-website)
* [Si të filloni një projekt të pavarur React](/learn/start-a-new-react-project)
* [Si të konfiguroni redaktorin tuaj](/learn/editor-setup)
* [Si të instaloni "React Developer Tools"](/learn/react-developer-tools)

</YouWillLearn>

## Provo React {/*try-react*/}

Nuk keni nevojë të instaloni asgjë për të luajtur pak me React. Provoni të redaktoni këtë sandbox!

<Sandpack>

```js
function Përshëndetje({ emri }) {
  return <h1>Çkemi, {emri}</h1>;
}

export default function App() {
  return <Përshëndetje emri="Emilian" />
}
```

</Sandpack>

Mund ta modifikoni drejtpërdrejt ose ta hapni në një skedë të re duke shtypur butonin "Fork" në këndin e sipërm djathtas.

Shumica e faqeve në dokumentacionin React përmbajnë sandbox si ky. Jashtë dokumentacionit React, ka shumë sandboxe në internet që mbështesin React: për shembull, [CodeSandbox](https://codesandbox.io/s/new), [StackBlitz](https://stackblitz.com/fork/react), ose [CodePen](https://codepen.io/pen?&editors=0010&layout=left&prefill_data_id=3f4569d1-1b11-4bce-bd46-89090eed5ddb).

### Provo React në nivel lokal {/*try-react-locally*/}

Për të provuar React në nivel lokal në kompjuterin tuaj, [shkarkoni këtë faqe HTML](https://raw.githubusercontent.com/reactjs/reactjs.org/main/static/html/single-file-example.html). Hapeni atë në redaktorin tuaj dhe në browserin (shfletuesin) tuaj!

## Shto React në një faqe {/*add-react-to-a-page*/}

Nëse jeni duke punuar me një sajt ekzistues dhe duhet të shtoni "pak" React, ju mund të [shtoni React me një etiketë skripti.](/learn/add-react-to-a-website)

## Filloni një projekt React {/*start-a-react-project*/}

Nëse jeni gati të [filloni një projekt të pavarur](/learn/start-a-new-react-project) me React, mund të konfiguroni një toolchain minimal për një përvojë të këndshme zhvilluesi. Gjithashtu mund të filloni me një framework që merr shumë vendime për ju jashtë skemave.

## Hapat e ardhshëm {/*next-steps*/}

Drejtohuni te udhëzuesi [Fillim i Shpejtë](/learn) për një turne në konceptet më të rëndësishme të React që do të hasni çdo ditë.

