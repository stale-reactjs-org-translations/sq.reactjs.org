---
title: Konfigurimi i redaktorit
---

<Intro>

Një redaktor i konfiguruar siç duhet mund ta bëjë kodin më të qartë për t'u lexuar dhe më të shpejtë për të shkruar. Madje mund t'ju ndihmojë të kapni *bugs* ndërsa i shkruani ato! Nëse kjo është hera e parë që konfiguroni një redaktor ose po kërkoni të rregulloni redaktorin tuaj aktual, ne kemi disa rekomandime.

</Intro>

<YouWillLearn>

* Cilët janë redaktorët më të njohur
* Si të formatoni automatikisht kodin tuaj

</YouWillLearn>

## Reaktori juaj {/*your-editor*/}

[VS Code](https://code.visualstudio.com/) është një nga redaktorët më të njohur në përdorim sot. Ka një *marketplace* të madh me *extensions* dhe integrohet mirë me shërbimet e njohura si GitHub. Shumica e veçorive të listuara më poshtë mund t'i shtohen VS Code si *extensions* gjithashtu, duke e bërë atë shumë të konfigurueshëm!

Redaktorë të tjerë të njohur të tekstit të përdorur në komunitetin React përfshijnë:

* [WebStorm](https://www.jetbrains.com/webstorm/) është një mjedis zhvillimi i integruar i krijuar posaçërisht për JavaScript.
* [Sublime Text](https://www.sublimetext.com/) ka mbështetje për JSX dhe TypeScript, [sintaks me theks](https://stackoverflow.com/a/70960574/458193) dhe auto-kompletim të integruar.
* [Vim](https://www.vim.org/) është një redaktues teksti shumë i konfigurueshëm i krijuar për ta bërë krijimin dhe ndryshimin e çdo lloj teksti shumë efikas. Përfshihet si "vi" me shumicën e sistemeve UNIX dhe me Apple OS X.

## Karakteristikat e rekomanduara të redaktuesit të tekstit {/*recommended-text-editor-features*/}

Disa redaktorë vijnë me këto veçori të integruara, por të tjerë mund të kërkojnë shtimin e një *extension*. Kontrolloni për t'u siguruar, se çfarë mbështetje ofron redaktori që keni zgjedhur!

### Linting {/*linting*/}

*Code linters* gjejnë probleme në kodin tuaj ndërsa shkruani, duke ju ndihmuar t'i rregulloni ato direkt. [ESLint](https://eslint.org/) është një linter open source popullor për JavaScript.

* [Instaloni ESLint me konfigurimin e rekomanduar për React](https://www.npmjs.com/package/eslint-config-react-app) (sigurohuni që keni [Node të instaluar!](https://nodejs.org/en/download/current/))
* [Integroni ESLint në VSCode me *extension* zyrtare](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

### Formatimi {/*formatting*/}

Gjëja e fundit që do të dëshironit të bënit kur ndani kodin tuaj me një kontribues tjetër është të futeni në një diskutim rreth [tabs vs spaces](https://www.google.com/search?q=tabs+vs+spaces)! Për fat të mirë, [Prettier](https://prettier.io/) do të pastrojë kodin tuaj duke e riformatuar atë në përputhje me rregullat e paracaktuara dhe të konfigurueshme. Ekzekutoni Prettier dhe të gjitha *tabs* (tasti tab në pc)  do të konvertohen në *spaces* (hapësira) — dhe *indentation* (nxjerrja në kryeradhë e tekstit), thonjëzat, etj do të ndryshohen gjithashtu për t'iu përshtatur konfigurimit. Në konfigurimin ideal, Prettier do të funksionojë kur ruani skedarin tuaj, duke i bërë shpejt këto modifikime për ju.

Mund të instaloni [Prettier extension in VSCode](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) duke ndjekur këto hapa:

1. Hapni VS Code
2. Përdorni *Quick Open* (press Ctrl/Cmd+P)
3. Ngjit `ext install esbenp.prettier-vscode`
4. Shtyp Enter

#### Formatimi në ruajtje {/*formatting-on-save*/}

Në mënyrë ideale, ju duhet të formatoni kodin tuaj në çdo ruajtje. VS Code ka *settings* (cilësime) për këtë!

1. Në VS Code, shtypni `CTRL/CMD + SHIFT + P`.
2. Shkruani "settings"
3. Shtypni Enter
4. Në *search bar*, shkruani "format on save"
5. Sigurohuni që opsioni "format on save" të jetë shënuar (*tick*)!

> Nëse paracaktimi i ESLint ka rregulla formatimi, ato mund të bien ndesh me Prettier. Ne rekomandojmë të çaktivizoni të gjitha rregullat e formatimit në paracaktimin tuaj ESLint duke përdorur [`eslint-config-prettier`](https://github.com/prettier/eslint-config-prettier) kështu që ESLint përdoret *vetëm* për kapjen e gabimeve logjike. Nëse dëshironi të detyroni që skedarët të formatohen përpara se një *pull request* është bërë *merge*, përdorni [`prettier --check`](https://prettier.io/docs/en/cli.html#--check) për *continuous integration*.
