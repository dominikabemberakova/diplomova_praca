# # Užívateľská príručka k diplomovej práci na detekciu a segmentáciu glaukómu

## Úvod
V tejto diplomovej práci sme sa zaoberali segmentáciou obrazov očí na identifikáciu a izoláciu oblastí postihnutých glaukómom pomocou modelu U-Net. Po úspešnej segmentácii sme z vysegmentovaných masiek vykonali klasifikáciu, aby sme rozlíšili obrázky s prítomnosťou glaukómu od normálnych. Na klasifikáciu sme použili modely ResNet, VGG16 a MobileNet. Cieľom bolo vyvinúť presný a efektívny model na pomoc v diagnostike glaukómu.

## Predpoklady
Pred začatím sa uistite, že máte prístup k Google Colab a účet na Kaggle, odkiaľ si môžete stiahnuť potrebné dáta.

## Dáta
Dátové sady je možné stiahnuť z nasledujúceho linku: [Kaggle Glaucoma Datasets](https://www.kaggle.com/datasets/arnavjain1/glaucoma-datasets).

## Príprava dát
Na začiatok projektu som získala `.xlsx` súbory pre každý dataset (`origu` a `g1020`), kde som načítala názvy a označenia (labely 0 alebo 1). V prípade datasetu `refuge` som použila `index.json` súbor, avšak musela som odstrániť 400 obrázkov, ktoré nemali label. Následne som tieto dve tabuľky spojila, čo mi poskytlo 2470 obrázkov.

## Rozdelenie dát
Získané obrázky som rozdelila na vyvážený dataset obsahujúci 544 obrázkov s glaukómom a 544 normálnych obrázkov. Z tejto množiny som vyčlenila 10% na validačnú a 10% na testovaciu súpravu. Celkovo bolo na segmentáciu použitých 2470 obrázkov, z ktorých sme vyčlenili 110 testovacích a rozdelili zvyšok na 2124 tréningových a 236 validačných obrázkov.

Na klasifikáciu sme použili 1088 obrázkov, z ktorých sme odrátali 110 testovacích, čím vznikla množina 868 tréningových obrázkov a 110 validačných obrázkov.

## Práca v Google Colab
1. **Nahratie súborov:** Načítajte súbory do prostredia Google Colab.
2. **Inštalácia potrebných knižníc:** Uistite sa, že máte nainštalované všetky potrebné knižnice pomocou príkazu `!pip install <názov_knižnice>`.
3. **Spustenie skriptov:** Po načítaní dát môžete spustiť jednotlivé notebooky (`segmentation.ipynb`, `classification.ipynb`).

## Segmentácia
Pri segmentácii sme použili model U-Net. Predikované masky sme ukladali priamo do priečinku na Google Drive pod pôvodným názvom s príponou `.png`. Súčasne sme vytvorili Excel súbor, ktorý obsahoval informácie o všetkých vysegmentovaných maskách.

## Klasifikácia
V klasifikačnom kroku sme k týmto predikovaným obrázkom pridali label 0 alebo 1 a použili modely ResNet, VGG16 a MobileNet. Rozdelili sme dáta do priečinkov na glaukóm a normálne, aby sme mohli ďalej efektívne pracovať s obrázkami. Klasifikácia zahŕňa tréning, validáciu a testovanie modelu na rozlíšenie medzi glaukómovými a normálnymi obrázkami.
