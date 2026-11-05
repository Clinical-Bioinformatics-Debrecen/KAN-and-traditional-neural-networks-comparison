# KAN-and-traditional-neural-networks-comparison

**Projekt címe:** Kolmogorov–Arnold hálózatok és tradicionális neurális hálók teljesítményének összehasonlítása genomikai szekvenciaosztályozásban

**Projekt Célja:**
Kolmogorov–Arnold Networkök (KAN-ok) és tradicionális neurális hálózatok (pl. multilayer perceptronok, MLP-k) teljesítőképességének összehasonlítása DNS-szekvenciák genomikai eredet szerinti osztályozásában. Cél a két neurális hálózati megközelítés milyen pontossággal képes rövid DNS-szekvenciák alapján megkülönböztetni különböző eredetű szekvenciákat. A cél egy háromosztályú osztályozási modell kidolgozása, amely képes azonosítani a genomszekvencia-töredékek eredetét.

**Három vizsgált osztály:**
- Plazmidok
- Baktériumkromoszómák
- Bakteriofágok

**Tervezett adatforrások:**
- PLSDB2 – plazmidok https://ccb-microbe.cs.uni-saarland.de/plsdb2025/
- RefSeq – baktériumkromoszómák https://www.ncbi.nlm.nih.gov/refseq/
- PhageScope – bakteriofágok https://phagescope.deepomics.org/


A projektet Python nyelven, objektumorientált programozási megközelítés alkalmazásával fogjuk megvalósítani.

**Projekt leírása:**

A DNS szekvenciák eredet szerinti osztályozása fontos feladat például metagenomikai adatok elemzésében, ahol gyakran szükséges meghatározni, hogy egy DNS-szekvencia baktériumkromoszómából, mobil genetikai elemből (pl. plazmidból), vagy bakteriofág genomból származik. A projekt során a DNS-szekvenciákat k-mer alapú reprezentációval alakítjuk gépi tanulási modellek számára feldolgozható bemenetté, majd azonos adathalmazon és azonos tanítási/tesztelési protokoll mellett hasonlítjuk össze a KAN-ok és a tradicionális neurális hálózatok teljesítményét.

**Projekthez tartozó információk összegzése:**

A többrétegű perceptronok (MLP-k) a mélytanulási architektúrák alapvető építőelemei, és több neuronszintből állnak. 

<img width="1144" height="1020" alt="image" src="https://github.com/user-attachments/assets/0031e59f-b1b5-4def-9b55-8f7d50b24652" />

Három fő részből állnak:
1.	Input layer (bemeneti réteg): ide kerülnek a feldolgozandó adatok.
2.	Hidden layers (rejtett rétegek): itt történik a mintázatok és összefüggések felismerése.
3.	Output layer (kimeneti réteg): itt születik meg a modell előrejelzése.

A KAN ezeknek az MLP-knek az alternatívája, amely jobb értelmezhetőséget és nagyobb pontosságot kínál. A legfontosabb különbség, hogy a hagyományos hálózatok tanulható súlyokkal dolgoznak, míg a KAN a neuronok közötti kapcsolatokon tanulható matematikai függvényeket alkalmaz. Ezeket a függvényeket B-spline görbékkel reprezentálja, ami lehetővé teszi az összetett összefüggések modellezését és potenciálisan a hálózat működésének jobb értelmezhetőségét.

Legfontosabb előnyeik közé tartozik a nemlineáris összefüggések rugalmas modellezése és a tanult kapcsolatok értelmezhetőségének lehetősége.

**Szakirodalmi összefoglaló:**

### 1. A Comprehensive Survey on Kolmogorov Arnold Networks (KAN)
Ji, T., Hou, Y., Zhang, D. (2025).

A tanulmány átfogó áttekintést nyújt a KAN matematikai hátteréről, felépítéséről, tanítási módszereiről és alkalmazási lehetőségeiről. Bemutatja a hagyományos többrétegű perceptronok (MLP) és a KAN közötti legfontosabb különbségeket. Például: MLP pontosabb lehet KAN-nál ha a betanítás korlátozott, de KAN jobban tudja kezelni azokat az adatokat ahol zaj van. Bizonyos paraméterek finomhangolása után a KAN jobb teljesítményt nyújt, mint az MLP, azonban több időt és számítási kapacitást igényelhet. Komplex adatok feldolgozásában megbízhatóbbnak tűnt a KAN (magasabb F1-pontszám és accuracy).
A KAN a hagyományos, rögzített súlyozott kapcsolatok helyett tanulható egyváltozós függvényeket alkalmaz, amelyeket jellemzően B-spline függvényekkel reprezentálnak. A szerzők ismertetik a KAN előnyeit, például a nemlineáris összefüggések modellezését és az értelmezhetőséget, valamint a számítási igényből és a tanítási időből adódó korlátokat.


### 2. CoxKAN: Kolmogorov-Arnold Networks for Interpretable, High-Performance Survival Analysis
Knottenbelt, W. et al. (2025).

A kutatás egy új, CoxKAN nevű modellt mutat be, amely a KAN architektúrát a túlélésanalízisben alkalmazza. A szerzők szintetikus, klinikai és genomikai adatokon (CNV + génexpresszió + mutációs státusz) vizsgálták a modell teljesítményét, és összehasonlították többek között a hagyományos Cox-regresszióval és a DeepSurv neurális hálózattal. A modell képes nemlineáris összefüggések és változók közötti interakciók felismerésére. A tanulmány bemutatja, hogy a KAN-alapú módszerek a predikciós teljesítmény mellett az eredmények értelmezhetőségében is előnyös lehet.


### 3. Kolmogorov-Arnold Networks for Genomic Tasks
Cherednichenko, O., Poptsova, M. (2025).

A tanulmány a KAN genomikai alkalmazási lehetőségeit vizsgálja. A szerzők lineáris KAN (LKAN) és konvolúciós KAN (CKAN) rétegeket építettek be meglévő mélytanulási architektúrákba, majd ezeket hagyományos neurális hálózatokkal hasonlították össze. A vizsgálatok során a DNS szekvencia osztályokat és generálási feladatokat használták (ide tartoznak a promóterek, enhancere, transzkfipciós faktorok kötőhelyei és a nem-B DNS-struktúrák felismerése). Az LKAN a vizsgált osztályozási feladatok többségében jobb eredményt ért el a hagyományos modellnél. A CKAN esetében számítási és memória igény korlát volt. 

### 4. Interpretable Graph Kolmogorov-Arnold Networks for Multi-Cancer Classification and Biomarker Identification Using Multi-Omics Data 
Alharbi, F. et al. (2025).

A tanulmány egy MOGKAN nevű, gráfalapú KAN-architektúrát mutat be, amely többféle omikai adat integrálásával végez daganatos betegségek osztályozását. A modell mRNS-, mikroRNS- és DNS-metilációs adatokat, valamint fehérje-fehérje interakciós hálózatokat használ. A szerzők 31 különböző daganattípus osztályozásán vizsgálták a módszert, amely 96,28%-os pontosságot ért el. A modell emellett lehetővé tette a fontos biomarkerek azonosítását és biológiai értelmezését.

### 5. SimpleKANSleepNet: A Kolmogorov-Arnold Network Based Sleep Stage Classification Method
Ji, X., Wang, L., Zhou, Y. (2026).

A kutatás egy "SimpleKANSleepNet" nevű, KAN-alapú modellt mutat be az alvási fázisok automatikus osztályozására. A rendszer konvolúciós neurális hálózatot (CNN) alkalmaz a fiziológiai jelek jellemzőinek kinyerésére. A modell EEG-, EMG-, EOG- és ECG-jelekből származó jellemzőket használ. Az eredmények alapján a KAN hasonlóan jó eredményeket mutatott a vizsgált alvásfázis osztályozási feladatokban.

### 6. Protein-Nucleic Acid Binding Site Prediction Using Interpretable Kolmogorov-Arnold Networks with Hypergraph Representation Learning
Zhu, Y. et al. (2026).

A tanulmány az IKANbind nevű modellt mutatja be, amely KAN-t, fehérje nyelvi modelleket és hipergráf-alapú reprezentációtanulást kombinál az aminosavak azonosítására. A megközelítés a DNS- és RNS-kötő fehérjékben található kötőhelyek felismerését célozza. Az eredmények szerint többek között az aminosavak töltése és polaritása fontos szerepet játszik a nukleinsavkötő helyek felismerésében. 


