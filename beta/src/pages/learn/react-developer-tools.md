---
title: React Developer Tools (Mjetet e zhvilluesit të React )
---

<Intro>

Përdorni React *Developer Tools* (Mjetet e Zhvilluesit) për të inspektuar [komponentët](/learn/your-first-component) React, për të redaktuar [props](/learn/passing-props-to-a-component) dhe [state](/learn/state-a-components-memory), dhe për të identifikuar problemet e performancës.

</Intro>

<YouWillLearn>

* Si të instaloni *React Developer Tools*

</YouWillLearn>

## Browser extension {/*browser-extension*/}

Mënyra më e lehtë për të bërë *debug*  *website*-t e ndërtuara me React është të instaloni React *Developer Tools extension*. Ky është i disponueshëm për disa *browser* të njohur:

* [Instaloni për **Chrome**](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)
* [Instaloni për **Firefox**](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/)
* [Instaloni për **Edge**](https://microsoftedge.microsoft.com/addons/detail/react-developer-tools/gpphkfbcpidddadnkolkpfckpihlkkil)

Tani, nëse vizitoni një *website* **të ndërtuar me React**, do të shihni panelet _Components_ dhe _Profiler_.

![React Developer Tools extension](/images/docs/react-devtools-extension.png)

### Safari dhe browser-at e tjerë {/*safari-and-other-browsers*/}
Për *browser* të tjerë (për shembull, Safari), instaloni [`react-devtools`](https://www.npmjs.com/package/react-devtools) *npm package*:
```bash
# Yarn
yarn global add react-devtools

# Npm
npm install -g react-devtools
```

Hapni më pas *Developer Tools* nga terminali:
```bash
react-devtools
```

Më pas lidhni *website*-in tuaj duke shtuar etiketën `<script>` në fillim të `<head>`:
```html {3}
<html>
  <head>
    <script src="http://localhost:8097"></script>
```

Ringarkoni faqen në *browser* për ta parë në *developer tools*.

![React Developer Tools standalone](/images/docs/react-devtools-standalone.png)

## Mobile (React Native) {/*mobile-react-native*/}
React *Developer Tools* mund të përdoren gjithashtu për të inspektuar aplikacionet e ndërtuara me [React Native](https://reactnative.dev/).

Mënyra më e lehtë për të përdorur React *Developer Tools* është ta instaloni atë globalisht:
```bash
# Yarn
yarn global add react-devtools

# Npm
npm install -g react-devtools
```

Më pas hapni *developer tools* nga terminali.
```bash
react-devtools
```

Duhet të lidhet me çdo aplikacion React Native që po funksionon në nivel lokal.

> Provoni të ringarkoni aplikacionin nëse *Developer Tools* nuk lidhen pas disa sekondash.

[Mësoni më shumë rreth të bërit *debug*  React Native.](https://reactnative.dev/docs/debugging)
