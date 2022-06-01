# Udhezues i pergjithshem per stilin

> This Style Guide is based on the [Universal Style Guide](https://github.com/reactjs/reactjs.org-translation/blob/master/style-guide.md)
>
> Ky udhezues per stilin eshte i bazuar ne [Universal Style Guide](https://github.com/reactjs/reactjs.org-translation/blob/master/style-guide.md)

Ky udhëzues per stilin përshkruan rregullat që duhet të zbatohen për **të gjitha** gjuhët.

## Fjalorth

Shiko [ketu](https://github.com/reactjs/sq.reactjs.org/blob/master/GLOSSARY.md)

## ID-ja e titujve (Headers)

Te gjithe titujt kane ID specifike, si per shembull:

```md
## Try React {#try-react}
```

**Mos** i perktheni keto ID! Ato perdoren per navigim dhe rrezikojne te mos funksionojne me.

Per shembull, duke pasur kete link:

```md
See the [beginning section](/getting-started#try-react) for more information.
```

✅ Keshtu eshte NE RREGULL ✅:

```md
## Provo React {#try-react}
```

❌ Keshtu eshte GABIM! ❌:

```md
## Provo React {#provo-react}
```

Me shembullin e dyte, linku pak me larte nuk do te funksionoj me.

## Teksti ne blloqet e kodit

Mos perkthe kurre tekstin ne blloqet e kodit, pervec komenteve. Mund te kesh nevoje mbase per te perkthyer dhe tekstin e strings, por ki kujdes te MOS perkthesh strings qe jane referenca per kodin.

Per shembull:
```js
// Shembull
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

✅ Keshtu eshte NE RREGULL ✅:

```js
// Shembull
const element = <h1>Hello, world!</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

✅ EDHE keshtu eshte NE RREGULL ✅:

```js
// Shembull
const element = <h1>Pershendes te gjithe boten!</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

❌ Keshtu eshte GABIM! ❌:

```js
// Shembull
const element = <h1>Pershendes te gjithe boten!</h1>;
// "root" i referohet ID-se se nje elementi
// MOS E PERKTHE!
ReactDOM.render(element, document.getElementById('rrenja'));
```

❌ KJO AKOMA EDHE ME GABIM!! ❌:

```js
// Shembull
// ABSOLUTISHT JO!
const elementi = <h1>Pershendes te gjithe boten!</h1>;
ReactDOM.gjenero(elementi, dokument.merrElementinNgaId('rrenja'));
```

## Linqe te jashtme

Nese nje link i jashtem riadreson ne nje artikull reference si [MDN] ose [Wikipedia], dhe ekziston nje version i atij artikulli ne gjuhen shqipe, i nje cilesi te mire, mund ta vleresosh te link-osh versionin e perkthyer ne gjuhen shqipe, ne vend te artikullit origjinal. 

[MDN]: https://developer.mozilla.org/en-US/
[Wikipedia]: https://en.wikipedia.org/wiki/Main_Page

Shembull:

```md
React Native is an open-source UI software framework (https://en.wikipedia.org/wiki/React_Native).
```

✅ Keshtu eshte NE RREGULL ✅:

```md
React Native eshte nje kornize e aplikacioneve mobile (https://sq.wikipedia.org/wiki/React_Native).
```

Per linqet per te cilat nuk ekziston nje version i perkthyer (StackOverflow, Youtube, etj...) perdorni thjesht linkun ne anglisht.
