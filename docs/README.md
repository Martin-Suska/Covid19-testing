# Covid19 efektívnejšie testovanie

## Nápad

Nápad nie je môj, poznám ho z článkov napr. [tu](https://www.timesofisrael.com/to-ease-global-virus-test-bottleneck-israeli-scientists-suggest-pooling-samples/). Mňa to iba zaujal natoľko, aby som to skúsil preveriť.

## Princíp

Za predpokladu, že infikovaných osôb je v spoločnosti relatívne málo, tak sa najprv otestuje mix `K` vzoriek a keď sa tento mix vyhodnotí ako pozitívny až potom sa testujú jednotlivé vzorky.

Táto metóda nie je nič nové, používa sa napr. aj na test HIV pri darovaní krvi.

## Preverenie

Bude nasledovať trochu počítania, ale ide iba o stredoškolské cvičenie z pravdepodobnosti.

Povedzme, že vieme (po dňoch testovania máme skúsenosť) koľko testov vychádza __negatívne__ (poroz, pri testovaní nás asi viac zaujímajú pozitívne nálezy = nakazení). Označme tento pomer P<sub>n</sub> (prevdepodobnosť, že test vyšiel negatívne).

Keď budeme testovať mix vytvorený z K vzoriek, tak pravdepodobnoť, že mix je negatívny je P<sub>kn</sub> = P<sub>n</sub><sup>K</sup>.

Pravdepodobnost opačného javu, že mix je pozitívny je P<sub>kp</sub> = 1 - P<sub>kn</sub>.

Keď to poskladáme dohromady:
- urobíme mix a otestujeme mix (tj. jeden test)
- s pravdepodobnosťou P<sub>kp</sub> potrebujeme urobiť ďalších K testov (inak sme hotový)

Štatisticky očakávaný počet testov na vyhodnotenie K vzoriekje teda 1 + P<sub>kp</sub> * K, ked chceme vedieť koľko testov sa ušetrí, stačí to vydeliť počtom vzoriek (K).

![expected test count](/images/expected_test_count.png)

Keď zafixujeme v tejto rovnici P<sub>n</sub> (použijeme namerané hodnoty), potom vypočítame z toho ideálne K do mixu:

![expected test count table](/images/expected_test_count_table.png)

V tabuľke vyššie je vidieť pre aké K dostaneme najväčšie ušetrenie. Napr. do hodnoty 87.5% pre P<sub>n</sub> je optimálne K 3, od 88% po 93.5% je to 4. Hodnota pre K=4 a P<sub>n</sub>=90% je 0.59390, čo znamená, že sa ušetrí 40% testov (čiže na 100 otestovaných stačí 60 testov).
