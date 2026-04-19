![Borítókép](../Cloud%20Programming_MSc_Juhasz_IId-1_1.jpg)

![EFOP logó](../Cloud%20Programming_MSc_Juhasz_IId-1_2.png)

# Felhőprogramozás

**Szerző:** Juhász Zoltán
**Kiadó:** Pannon Egyetem, 2020
**Támogatás:** EFOP-3.4.3-16-2016-00009

*A felsőfokú oktatás minőségének és hozzáférhetőségének együttes javítása a Pannon Egyetemen*

---

## Tartalomjegyzék

- Előszó
- 1 Bevezetés
- 2 A múlt technológiai fejlődése: út a felhőalapú számítástechnikához
  - 2.1 Számítási erőforrásokhoz való hozzáférés és megosztás
    - 2.1.1 Korlátozott erőforrású rendszerek – nagyszámítógépek (mainframe-ek)
    - 2.1.2 Személyi számítógépek, hálózatok és kliens-szerver rendszerek
    - 2.1.3 Szuperszámítógépek
  - 2.2 Kliens-szerver rendszerek programozása
    - 2.2.1 Távoli eljáráshívás (Remote Procedure Call)
    - 2.2.2 Távoli metódushívás (Remote Method Invocation)
    - 2.2.3 Érvek a lazán csatolt rendszerek mellett
  - 2.3 Szolgáltatás-orientált rendszerek
    - 2.3.1 XML alapú szolgáltatások – webszolgáltatások
    - 2.3.2 RESTful szolgáltatások
  - 2.4 Grid számítástechnika
  - 2.5 Önkéntes erőforrás-megosztás
  - 2.6 Hoszting és a kialakuló közműszerű számítástechnika
  - 2.7 Virtualizáció
- 3 A felhőtechnológia alapjai
  - 3.1 Alapfogalmak
  - 3.2 A felhő gazdaságtana
  - 3.3 Felhasználói és használati támogatás a felhőben
  - 3.4 Egy kis felhőtörténet
    - 3.4.1 Az Amazon felhőszolgáltatás eredete
    - 3.4.2 A Microsoft és a felhő
    - 3.4.3 Google Cloud
    - 3.4.4 IBM és Oracle
  - 3.5 Árképzés
  - 3.6 Programozás
- 4 Amazon Web Services (AWS)
  - 4.1 IaaS-rétegbeli szolgáltatások
    - 4.1.1 Számítási (Compute) szolgáltatások
    - 4.1.2 Tárolási (Storage) szolgáltatások
    - 4.1.3 Hálózati szolgáltatások
  - 4.2 PaaS-rétegbeli szolgáltatások
    - 4.2.1 AWS Elastic Beanstalk
  - 4.3 SaaS-rétegbeli szolgáltatások
  - 4.4 Szolgáltatáskezelés és API-k
- 5 Google Cloud Platform
  - 5.1 GCP-szolgáltatások az IaaS-rétegben
  - 5.2 PaaS-rétegbeli szolgáltatások
  - 5.3 SaaS-rétegbeli szolgáltatások
- 6 A Google Cloud Platform használata
  - 6.1 A GCP projekt
  - 6.2 GCP erőforrások elérésének módjai
  - 6.3 A Compute Engine használata
  - 6.4 A Cloud Storage használata
- 7 Nagyléptékű feladat-végrehajtás a felhőben
  - 7.1 A Big Data megjelenése
  - 7.2 Adatfeldolgozó szoftverkeretrendszerek
    - 7.2.1 Batch és stream adatfeldolgozás
    - 7.2.2 Apache Hadoop/MapReduce
    - 7.2.3 Apache Spark
  - 7.3 MapReduce és Spark feladatok futtatása GCP-n
- 8 Adatfolyam-feldolgozás
  - 8.1 Stream algoritmusok
  - 8.2 Népszerű stream adatfeldolgozó keretrendszerek
    - 8.2.1 Spark Streaming
    - 8.2.2 Apache Flink
    - 8.2.3 Apache Storm és Trident
    - 8.2.4 Apache Kafka és Kafka Streams
    - 8.2.5 Apache Beam és GCP Dataflow
  - 8.3 Apache Beam és a GCP Dataflow
- 9 Felhőfüggvények (Cloud Functions)
- 10 Szolgáltatáskommunikáció: Pub/Sub
  - 10.1 Google Pub/Sub áttekintés
  - 10.2 Pub/Sub üzenetfolyam
  - 10.3 Üzenetkézbesítési példa
  - 10.4 Üzenetek közzététele és fogadása kódban
- 11 GCP szolgáltatáspéldák
  - 11.1 Vision AI
  - 11.2 Cloud Translation
  - 11.3 Text-to-Speech
- 12 Felhőszolgáltatás-orkesztráció
  - 12.1 Komplex optikai karakterfelismerő (OCR) alkalmazás példája
- 13 Következtetések
- Irodalomjegyzék

---

## Előszó

A felhőtechnológia a számítástechnika egy viszonylag új, ugyanakkor rendkívül izgalmas területe. Az elosztott rendszerek, a hálózatok, a virtualizáció és a szolgáltatásorientált számítástechnika (SOA) területén végzett több évtizedes akadémiai és ipari kutatás-fejlesztési munka mára gyakorlati valósággá érett. Ennek eredményeként szinte korlátlan számítási és tárolási kapacitás áll rendelkezésre, amelyre építve új típusú alkalmazások és szolgáltatások jöhetnek létre, felhasználók millióit kiszolgálva.

A könyv célja, hogy bevezetést nyújtson a felhőrendszerek programozásába. Mivel a felhőinfrastruktúrákat egyre inkább a nagy technológiai vállalatok magasan specializált adatközpontjai üzemeltetik, az egyéni fejlesztők és a kisebb cégek számára a valódi lehetőségek a szoftveres oldalon rejlenek. A témakörhöz kapcsolódó tananyag mennyisége hatalmas; ezért elsősorban a legalapvetőbb fogalmak, módszerek és programozási technikák bemutatására koncentrálunk, ami megfelelő alapot biztosít a hallgatóknak a speciális területek későbbi, mélyebb szintű tanulmányozásához.

A könyv tartalma szorosan kapcsolódik a veszprémi Pannon Egyetem Műszaki Informatikai Karán oktatott *Felhőprogramozás* című MSc kurzus struktúrájához és tartalmához. Bár a mű bevezető jellegű, a kurzus elvégzésének előfeltétele a Java programozási nyelv ismerete, valamint a számítógép-architektúrák, az operációs rendszerek és az elosztott rendszerek alapfogalmainak megértése. A fejezeteket nem feltétlenül kell a könyvben szereplő sorrendben olvasni, de a témával még csak most ismerkedő olvasók számára ez a leginkább célravezető megközelítés.

Bár a kézirat összeállítása során a legnagyobb gondossággal jártunk el, hibák és hiányosságok előfordulhatnak. Ezekért kizárólag a szerző felelős. A könyv jövőbeli javítása és bővítése érdekében az olvasók visszajelzéseit és építő jellegű megjegyzéseit örömmel fogadjuk.

Hálásan köszönjük az Európai Unió és a Magyar Kormány támogatását az EFOP-3.4.3-A.2.3 számú támogatási szerződés keretében.

*Dr. Juhász Zoltán*

---

## 1. Bevezetés

Az elmúlt évtized során a „felhő” (cloud) közismert fogalommá vált. Adatainkat a felhőben tároljuk, és nap mint nap olyan szolgáltatásokat használunk, mint a Gmail, az Amazon, a Netflix, a Spotify, illetve különböző webáruházak és online hírszolgáltatások, anélkül, hogy belegondolnánk, fizikailag pontosan hol is találhatók, hogyan implementálták, vagy éppen miként üzemeltetik őket. Létezésüket és rendelkezésre állásukat (availability) magától értetődőnek vesszük.

A számítástechnikai és IT-iparnak több évtizedes kutatás-fejlesztésre, valamint több ezer emberévnyi munkára volt szüksége ahhoz, hogy ezeket a rendszereket – és mindenekelőtt magát a felhőt – létrehozza. Mindannyian ismerjük a felhővel kapcsolatos divatos kifejezéseket: korlátlan tárhely és számítási kapacitás, igény szerinti használat, alacsony költségek, skálázhatóság, magas rendelkezésre állás, rugalmasság és szolgáltatásintegráció. Azt is tudjuk, hogy valahol a világban hatalmas adatközpontok működnek, amelyek a felhőinfrastruktúra gerincét adják. Ezeket a központokat túlnyomórészt globális technológiai óriásvállalatok üzemeltetik, hiszen elképesztően magas kezdeti befektetésre van szükség ahhoz, hogy valaki felhőszolgáltatóvá váljon, és valóban globális léptékben tudjon szolgáltatásokat nyújtani.

Ez a könyv a felhőről szól, kifejezetten egy szoftverfejlesztő szemszögéből. Nem az üzemeltetési vagy a napi szintű menedzsmentkérdésekre fókuszálunk. Ehelyett azt vizsgáljuk meg, hogy ez az új „közeg” hogyan befolyásolja a szoftverfejlesztést, valamint az alkalmazások létrehozásának és üzembe helyezésének módját. A felhővel kapcsolatos leggyakoribb kifejezések – *felhőalapú számítástechnika* (*Cloud Computing*), *felhőarchitektúra* (*Cloud Architecture*) és *felhőprogramozás* (*Cloud Programming*) – közül mi ez utóbbit fogjuk részletesen körüljárni.

A könyv – és a hozzá kapcsolódó kurzus – célja nem csupán gyakorlati programozási tippek átadása. Bízom benne, hogy a kurzus végére a hallgatók szélesebb perspektívát és mélyebb megértést szereznek azokról az elméleti és technológiai hajtóerőkről, amelyek az IT-ipart a felhő irányába mozdították. A modern számítástechnika és szoftverfejlesztés főbb kihívásainak megértése érdekében a 2. fejezet rövid áttekintést nyújt azokról a kulcsfontosságú történelmi fejleményekről, amelyek a felhőtechnológia megszületésének előfutárai és előfeltételei voltak. Olyan témákat érintünk, mint az erőforrás-megosztás, a hálózatok evolúciója, a különféle nagy teljesítményű számítási rendszerek, valamint az elosztott rendszerek programozási kihívásai. Ezen technológiai területek érettsége biztosította azt az alapot, amelyre a modern felhő felépülhetett.

A könyv következő része általánosságban tárgyalja a felhőt. Megvitatjuk a főbb jellemzőit, valamint architekturális, üzemeltetési és szoftveres vonatkozásait. Ezt követően áttekintést adunk a legfontosabb felhőszolgáltatókról, bemutatva rövid történetüket, piaci részesedésüket, relevanciájukat és szolgáltatáskínálatukat.

Ezután rátérünk a programozási aspektusokra. Az infrastrukturális összetevőkkel kezdjük: adattárolás (storage), számítás (compute) és hálózat (network), mivel ezek bármely felhőrendszer alapvető építőkövei. Ezt követik azok a magasabb szintű szolgáltatások, amelyek jelentősen megkönnyítik a fejlesztők munkáját: például a különféle alkalmazásszolgáltatások és speciális platformok, amelyeket jellemzően a webalapú rendszerek fejlesztése során használnak.

A skálázhatóság fogalmára építve megvizsgáljuk, hogyan hajthatók végre nagyléptékű számítási feladatok több, párhuzamosan futó szolgáltatáspéldány segítségével. Olyan népszerű elosztott végrehajtási mintákat veszünk górcső alá, mint a MapReduce. A végrehajtási példákat, és úgy általában a könyv gyakorlati feladatait a Google Cloud Platform (GCP) környezetében mutatjuk be. Ennek oka a Google nagylelkű támogatása, amely évek óta ingyenes hozzáférést biztosít hallgatóink számára a felhőrendszeréhez, valamint az érdeklődők számára elérhető kiváló dokumentáció. A könyv utolsó fejezeteiben az adatfolyam-feldolgozás (stream processing), a Cloud Functions (szerver nélküli függvények), a Publish/Subscribe (közzétevő-feliratkozó) kommunikáció, az AI-szolgáltatások, végezetül pedig a szolgáltatás-orkesztráció (service orchestration) témaköreit tárgyaljuk.

A könyv végső célja, hogy elmélyítse a felhőalapú számítástechnika általános megértését, és olyan szintű technológiai, illetve szoftvermérnöki tudással vértezze fel a hallgatókat, amelyre biztosan építhetnek jövőbeli karrierjük során.

MSc kurzusunkon az elméleti anyagot gyakorlati programozási laborok kísérik, amelyek során a hallgatók meglévő példaalkalmazásokat futtathatnak és módosíthatnak, valamint tapasztalatot szerezhetnek a saját felhőalkalmazásaik nulláról történő felépítésében is. Az anyagot önállóan feldolgozó olvasóknak mindenképpen érdemes az adott fejezetekhez kapcsolódó gyakorlati kódpéldákat is kipróbálniuk.

---

## 2. A múlt technológiai fejlődése: út a felhőalapú számítástechnikához

A számítástechnika Szent Grálja egy olyan rendszer, amely kivételesen nagy teljesítményű, ingyenes vagy nagyon olcsó a használata, bárki számára hozzáférhető, megbízható és mindenütt jelenlévő, gyors, hatékony és egyszerű módot biztosít az alkalmazásfejlesztésre és -telepítésre, és ugyanakkor maximális felhasználói élményt és használhatóságot nyújt a végfelhasználók számára. Ezt a varázslatos rendszert még nem találtuk meg, de a felhő valószínűleg a létező jelöltek közül a legközelebb áll hozzá.

Ennek a fejezetnek a célja, hogy bemutassa a nagy számítási rendszerekben jellemzően fellelhető problémákat, és áttekintse az elmúlt évtizedekben megoldásukra kitalált különféle technológiai megoldásokat. Célunk az is, hogy illusztráljuk: a felhőalapú számítástechnika nem egy teljesen új, egyedi koncepció, hanem évtizedek szisztematikus kutatási és fejlesztési munkájának eredménye az elosztott számítási rendszerek területén.

Ennek a fejezetnek a technológiai fejleményekről szóló áttekintése nem annyira az egyes konkrét technológiák technikai részleteire összpontosít (feltételezzük, hogy az olvasók már ismerik ezeket az alapvető témákat), hanem azokra a problémákra, amelyeket megoldani igyekeztek, arra, ahogyan ezt tették, valamint egy fogalmi út megrajzolására ("a pontok összekötése" révén), amely a felhőalapú számítástechnika megjelenéséhez vezet. Minden alfejezet végén hangsúlyozzuk, hogyan találja meg helyét egy adott technológia vagy annak alapvető fogalmai a modern felhőalapú számítási rendszerekben.

### 2.1 Számítási erőforrásokhoz való hozzáférés és megosztás

Az első központi problémakör, amelyet megvizsgálunk, az úgynevezett *erőforrás-megosztás problémája*. Egy számítógépes rendszert úgy érdemes kialakítani és üzemeltetni, hogy költségei minimálisak legyenek, miközben maximalizálja a kihasználtságot és a felhasználók által érzékelt teljesítményt. Sajnos ezek egymással ütköző igények, amelyeket nehéz egyszerre kielégíteni. Nézzünk vissza a számítástechnika történetére, és lássuk, milyen formában és szinten jelent meg az erőforrás-megosztás kérdése különféle számítási rendszerekben.

#### 2.1.1 Korlátozott erőforrású rendszerek – nagyszámítógépek (mainframe-ek)

A számítástechnika hőskorában a számítógépek nagyok, drágák és ritkák voltak, jellemzően speciális számítási létesítményekben helyezkedtek el. Ezek a *mainframe számítógépek* (lásd 2-1. ábra) speciálisan képzett műszaki személyzetet igényeltek a gépek üzemeltetéséhez és programozásához. A számítógépek korlátozott számú speciális célú programot hajtottak végre, amelyek meghatározott kutatási vagy üzleti problémákra irányultak. A legtöbb rendszer egyszerre csak egy programot tudott futtatni, ezért *gépidőt* (számítási időt) előre le kellett foglalni. Mivel a számítógépeket központilag telepítették és kezelték, a rendszergazdák optimális programvégrehajtási ütemezéseket tudtak létrehozni, amelyek magasan tartották a számítógép kihasználtsági arányát (következésképpen alacsony tényleges költséggel). Megjegyzendő, hogy a számítógépes rendszer *egységnyi üzemeltetési költsége* a kihasználtsági arányától függ. Ha egy rendszer, amelynek kezdeti költsége például 10 000 USD, 100 000 órán keresztül működik (kb. 11 év) 100%-os kihasználtsággal, akkor egy órányi programfuttatás költsége 0,1 dollár. Ha ugyanaz a rendszer az idő 90%-ában tétlen, a tényleges programfuttatási költség 1 USD/órára nő. Ezért a magas kihasználtsági arány fenntartása fontos cél a rendszer üzemeltetésében.

A későbbi technológiai fejlesztések időosztásos vagy időszeletelt működési módokat eredményeztek, amelyekben a felhasználók egyszerre használhatták a számítógépet *terminálokon* keresztül. A folyamatos fejlesztések ellenére ezeknek a központosított mainframe rendszereknek számos hátránya volt a végfelhasználók számára:

- A számítógépek megosztott használata miatt a felhasználóknak várniuk kellett egymásra; a programokat nem lehetett futtatni addig, amíg az előző futó példány be nem fejeződött.
- Időosztásos, multiplexelt módban minden felhasználói program csökkentett sebességgel futott. A teljesítménycsökkenés arányos volt az egyidejűleg csatlakoztatott felhasználók számával.
- A központi adminisztráció szigorú szabályokat eredményezett, amelyeket be kellett tartani, és amelyek befolyásolták, hogyan és mikor lehet a rendszerhez hozzáférni, és milyen programokat lehet futtatni.

*2-1. ábra: Tipikus nagyszámítógép-rendszer az 1960-as években.*

![2-1. ábra](<../Cloud Programming_MSc_Juhasz_IId-9_1.jpg>)

Figyelje meg a rendszer architektúra diagramját (2-2. ábra), amely bemutatja, hogyan csatlakoztak a terminálok a központi szerverhez. Ez hasonlít egy modern hálózati számítógépes rendszerhez. A különbség az, hogy a terminálok nem valódi számítógépek; csak bemeneti és kimeneti képességekkel rendelkező eszközök, amelyek a központi számítógépes létesítményhez csatlakoznak.

*2-2. ábra: Nagyszámítógép-rendszer architektúrája több terminállal.*

![2-2. ábra](<../Cloud Programming_MSc_Juhasz_IId-10_1.png>)

#### 2.1.2 Személyi számítógépek, hálózatok és kliens-szerver rendszerek

Az 1980-as években induló Személyi Számítógép (PC) forradalom radikális szemléletváltást hozott a megosztott számítógépes rendszerekkel kapcsolatban. A miniatürizálás (integrált áramkörök tömeggyártása) eredményeként a számítógépek költsége olyan szintre csökkent, amely először a kisvállalkozásoknak, majd magánszemélyeknek is lehetővé tette, hogy saját számítógépük legyen. A PC melletti egyik fő érv az volt, hogy a felhasználóknak többé nem kellett másokkal megosztaniuk számítógépüket; bármikor és bármire használhatták. Azt a tényt, hogy a felhasználóknak ki kellett képezniük magukat ahhoz, hogy képesek legyenek üzemeltetni, adminisztrálni és kezelni a számítógépeket, nem verték nagydobra…

A számítógépekkel együtt szükség volt perifériákra is. A felhasználók kis nyomtatókat, szalagos adatmentő (tape backup) eszközöket stb. vásároltak. Ezeket az eszközöket jellemzően viszonylag ritkán használták. Üzleti környezetben az alkalmazottak privát nyomtatóhasználatának többletköltsége összekapcsolódott az adatmegosztás problémáival. Az egyes PC-k az adataikat a helyi merevlemezen tárolták. A nagyobb projektek különböző szakaszain dolgozó emberek kollégáik által bemenetként igényelt fájlokat másoltak és hordoztak maguknál. Nem sok változott a technológia fejlődésével, az adatátvitel a floppy lemezekről CD-re került.

Szerencsére a PC-forradalommal együtt a számítógép-hálózati technológia is megfizethetővé vált. A helyi hálózatok (LAN) lehetővé tették a PC-k egymás közötti kommunikációját, ami elősegítette a köztesréteg-szoftverek (*middleware*) fejlesztését, amelyek megkönnyítették az adatok és perifériás eszközök megosztását. Egy ilyen sikeres termék volt a Novell NetWare, amely lehetővé tette a kisvállalkozások számára nyomtatószerverek létrehozását (kevesebb számú nyomtató használata sokkal magasabb kihasználtsági aránnyal) és megosztott könyvtárakat, amelyeken a felhasználók másokkal megoszthatták az adatokat.

Az 1980-as évek óta a hálózati technológia fenomenális sebességgel fejlődött. Az Ethernet hálózatok általánossá váltak, néhány évente jelentős sávszélesség-növekedéssel, amint az a 2-3. ábrán látható. A helyi hálózatok után hamarosan földrajzilag távoli számítógépeket is össze lehetett kötni Wide Area Network (WAN) hálózatok segítségével. Különféle szegregált, szigetszerű számítógép-hálózatokra épülve, valamint a TCP/IP és Domain Name System technológiák alkalmazásával létrejött a globális Internet hálózat, amelyhez a legtöbb ország az 1990-es évek végére csatlakozott.

A nem megosztott számítógépek elterjedése után a legtöbb intézet felismerte a megosztás szükségességét, mind pénzügyi, mind üzleti hatékonysági okokból. A hálózatok biztosították az alapvető összekapcsolási szövetet az elosztott számítási rendszerek létrehozásához. Az elosztott rendszer legegyszerűbb formája a kliens-szerver architektúra (2-4. ábra illusztrálja), amelyben egy központosított szerver valamilyen jól definiált funkcionalitást biztosít, amelyhez több kliens is hozzáférhet. A szerverek a kliens kéréseit az implementált funkcionalitásuknak megfelelően szolgálják ki. A szervertípusok gyakori példái közé tartoznak az FTP, e-mail, idő, adatbázis és webszerverek. Hangsúlyozni kell, hogy a szerverek egy adott funkcionalitásra vagy alkalmazástípusra vonatkozó kérések végrehajtására *specializálódnak*. A klienseknek ismerniük kell a szerver hozzáférési részleteit és használati specifikumait ahhoz, hogy egy adott szervert használni tudjanak. A kliens-szerver rendszerek érdekes programozási kihívásokat jelentenek, amelyeket a következő fejezetben vizsgálunk meg.

*2-3. ábra: A hálózati sávszélesség növekedése az évek során.*

![2-3. ábra](<../Cloud Programming_MSc_Juhasz_IId-11_1.png>)

*2-4. ábra: Általános kliens-szerver architektúra*

![2-4. ábra](<../Cloud Programming_MSc_Juhasz_IId-11_2.png>)

#### 2.1.3 Szuperszámítógépek

Bár a személyi számítógépek minden bizonnyal tönkretették a mainframe számítógépipart, az tény maradt, hogy nem minden számítási feladatot lehet személyi számítógépekkel megoldani. A számítási szempontból kivételesen igényes problémákhoz speciális, sokkal nagyobb teljesítményű számítógépeket hoztak létre. Ezek a *szuperszámítógépek* vették át a korábbi mainframe számítógépek szerepét. A szuperszámítógépek, definíció szerint, egy adott időpontban a világ legnagyobb teljesítményű számítógépei. Nagyon drágák, ezért központosított szuperszámítógép-központokban helyezik el őket. A nagy országokban több szuperszámítógép-központ is található, a kisebbeknek lehet egy vagy egy sem. A szuperszámítógépekhez való hozzáférés korlátozott, csak kiválasztott és jóváhagyott felhasználók futtathatnak programokat rajtuk. A programfutás általában *batch végrehajtási módot* követ, azaz egy program beolvassa a bemenetét fájlokból, végrehajtódik, majd az eredményeket kimeneti fájlokba menti. Az interaktív programfutás általában nem támogatott. A felhasználói programok (úgynevezett *jobok*) akkor futnak le, ha a feladathoz szükséges összes erőforrás (processzorok, memória, tároló) rendelkezésre áll. Következésképpen a szuperszámítógépes rendszerek sorbaállító (queuing) rendszereket alkalmaznak a feladat-végrehajtáshoz. A felhasználók egy vagy több végrehajtási várólistához beküldik feladataikat, és várják, hogy a program lefusson és eredményeket produkáljon. Figyelemre méltó a hasonlóság a korai mainframe rendszerekkel, ahol a felhasználóknak számítógép-időt kellett lefoglalniuk programjaik futtatásához. A szuperszámítógépek megosztása szükségszerű ahhoz, hogy elérjük a magas kihasználtsági arányt, amely minimálisan tartja az üzemeltetési költségeket.

A szuperszámítógépek teljesítményét az egy másodperc alatt végrehajtott lebegőpontos műveletek (*flop*) számával mérik (*flop/s*). A teljesítményt általában ezer flop többszöröseiben mérik, például Mflop/s (10⁶), Gflop/s (10⁹), Tflop/s (10¹²), Pflop/s (10¹⁵) stb. Az első számítógép, amelyet szuperszámítógépnek tartottak, a Control data Corporation által gyártott CDC 6600 volt, amelyet a Cray Research Cray-1-je követett. Az első rendszer, amely elérte az 1 Gflop/s szintet, a Cray Y-MP volt. A következő mérföldkövet, az 1 Tflop/s-t az ASCI Red rendszer érte el. A Petaflop teljesítményt először az IBM Roadrunner számítógép érte el. A jelentős szuperszámítógépek legfontosabb hardver tulajdonságai az 1. táblázatban találhatók. A jelen sorok írásakor folyamatban van az első Exaflop/s szuperszámítógép létrehozása.

**1. táblázat: Jelentős szuperszámítógép-rendszerek és rendszerspecifikációik**

| Szuperszámítógép | Főbb specifikációk |
|---|---|
| CDC 6600 (1964) | CPU: 60-bites processzor @ 10 MHz; Memória: max. 982 kB (131000 x 60 bit); Teljesítmény: 2 MIPS |
| Cray-1 (1976) | CPU: 64-bites processzor @ 80 MHz; Memória: 8,39 MB (max. 1 048 576 szó); Teljesítmény: 160 MFlop/s |
| Cray Y-MP (1988) | Processzorok: 8 vektorprocesszor @ 167 MHz; Memória: 512 MB; Teljesítmény: 2,144 GFlop/s |
| ASCI Red (1997) | Processzorok: 9298 x Pentium II Xeon Core; Memória: 1,212 terabyte; Teljesítmény: 1,3 TFlop/s |
| IBM Roadrunner (2008) | Processzorok: 12 960 IBM PowerXCell 8i és 6 480 AMD Opteron dual-core; Memória: 103,6 terabyte; Teljesítmény: 1,042 PFlop/s |
| Tianhe-2 (2013) | Processzorok: 32 000 Intel Xeon E5-2692 12C @ 2,200 GHz és 48 000 Xeon Phi 31S1P; Memória: 1345 terabyte; Teljesítmény: 33,86 PFlop/s |
| Summit (2018) | Processzorok: 9 216 POWER9 22-magos CPU és 27 648 NVIDIA Tesla V100 GPU; Memória: 4 608 x 600 GB; Teljesítmény: 200 PFlop/s |
| Fugaku (2020) | Processzorok: 158 976 Fujitsu A64FX CPU (48 mag); Memória: 4 866 048 GB; Teljesítmény: 415 PFlop/s |

A korai szuperszámítógép-rendszerek szekvenciális számítógépek voltak, amelyek egyetlen utasításfolyamot hajtottak végre. Gyorsaságuk a speciális tervezésből, a gyorsabb félvezető technológiából és a hagyományos számítógépekben elérhető magasabb órajel sebességből adódott. Később speciális hardveres gyorsítási technikákat alkalmaztak, mint például vektorműveletek és belső pipelining. A modern szuperszámítógépek ezzel szemben párhuzamos számítógépek, amelyek gyakran több százezer processzormagot tartalmaznak. A párhuzamos szuperszámítógépek csak akkor tudnak nagy teljesítményt elérni, ha gondosan megírt és optimalizált párhuzamos programot futtatnak rajtuk. Ezekhez a programokhoz jellemzően Fortran, C, C++ nyelveket használnak megfelelő párhuzamos programozási kiterjesztésekkel, például OpenMP [1] vagy MPI (Message Passing Interface) [2][3], CUDA [4].

*2-5. ábra: A Cray-1 szuperszámítógép*

![2-5. ábra](<../Cloud Programming_MSc_Juhasz_IId-13_1.png>)

*2-6. ábra: A Tianhe-2 szuperszámítógép*

![2-6. ábra](<../Cloud Programming_MSc_Juhasz_IId-13_2.png>)

*2-7. ábra: A Summit szuperszámítógép*

![2-7. ábra](<../Cloud Programming_MSc_Juhasz_IId-13_3.png>)

*2-8. ábra: A Fugaku szuperszámítógép*

![2-8. ábra](<../Cloud Programming_MSc_Juhasz_IId-13_4.png>)

### 2.2 Kliens-szerver rendszerek programozása

Ahogy korábban említettük, az elosztott rendszerek legegyszerűbb formája a kliens-szerver architektúra. Ebben a fejezetben ezen rendszerek programozási aspektusait vizsgáljuk meg. Az itt áttekintett technológiákat azzal a szándékkal hozták létre, hogy emeljék a programozás absztrakciós szintjét, növeljék a programozói termelékenységet és – ugyanakkor – növeljék a létrehozott kód minőségét és karbantarthatóságát. Emlékeztetőül a 2-9. ábra egy általánosított kliens-szerver rendszer architektúráját mutatja. A kliens szerepe, hogy különféle kéréseket küld a szervernek és várja a válaszát. A szerver folyamatosan figyeli a beérkező kéréseket, értelmezi őket, majd kiszolgálja a kérést, generálja és elküldi a választ a kliensnek.

*2-9. ábra: Kérés-válasz üzenetcsere egy kliens-szerver rendszerben*

*(Megjegyzés: a 2-9. ábra az eredeti PDF-ben vektorgrafikusan került beágyazásra, ezért külön képfájlként nem elérhető.)*

Egy ilyen rendszer programozásának prototipikus megközelítése az üzenetküldés (message passing) a hálózati kapcsolatot létrehozó operációs rendszer függvények segítségével, majd az összeállított üzenet elküldése és a válasz fogadása. Ennek egy szemléltetése, C-ben programozva, a következő kódrészletben látható.

```c
/***************** CLIENT CODE ****************/

#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <string.h>

int main(){
  int clientSocket;
  char buffer[1024];
  struct sockaddr_in serverAddr;
  socklen_t addr_size;

  /*---- Create the socket ----*/
  clientSocket = socket(PF_INET, SOCK_STREAM, 0);

  /*---- Configure settings of the server address struct ----*/
  serverAddr.sin_family = AF_INET;
  serverAddr.sin_port = htons(7891);
  serverAddr.sin_addr.s_addr = inet_addr("127.0.0.1");
  memset(serverAddr.sin_zero, '\0', sizeof serverAddr.sin_zero);

  /*---- Connect to the server ----*/
  addr_size = sizeof serverAddr;
  connect(clientSocket, (struct sockaddr *) &serverAddr, addr_size);

  /*---- Read the message from the server into the buffer ----*/
  recv(clientSocket, buffer, 1024, 0);

  /*---- Print the received message ----*/
  printf("Data received: %s",buffer);

  return 0;
}
```

Ugyanaz a funkcionalitás Java-ban megvalósítva így néz ki:

```java
import java.io.*;
import java.net.*;
import java.util.logging.Level;
import java.util.logging.Logger;

public class MyClient {
    private final int PORT = 10000;
    private Socket server;
    private BufferedReader in;
    private PrintWriter out;

    public static void main(String[] args) {
        new MyClient().start();
    }

    public void start(){
        try {
            System.out.println("Client is started...");
            // 1. establish connection with server
            server = new Socket("localhost", PORT);
            // 2. create stream instances for communication
            in = new BufferedReader(new InputStreamReader(server.getInputStream()));
            out = new PrintWriter(server.getOutputStream(), true);
            // 3. send request
            out.println("HELLO");
            // 4. receive response
            String response = in.readLine();
            System.out.println("Response from server: " + response);
        } catch (IOException ex) {
            Logger.getLogger(MyClient.class.getName()).log(Level.SEVERE, null, ex);
        } finally{
            // 5. close communication channels
            try{
                if (in != null) in.close();
                if (out != null) out.close();
                if (server != null) server.close();
            }catch(IOException e){
                e.printStackTrace();
            }
        }
    }
}
```

Mivel az üzenetcsere a kliens-szerver rendszerek ilyen alapvető művelete, ezt az utasítássorozatot nagy alkalmazásokban sokszor meg kell ismételni. Ez közel azonos kódrészletek többszöri ismétlődéséhez vezet az alkalmazás forráskódjában. A fejlesztők ezeket gyorsan az üzenetcserét kezelő egyedi függvényekkel helyettesítenék. Szabványosítás nélkül azonban minden rendszer függvények, paraméterátadás és hibakezelési konvenciók eseti halmazát használná, ami a hosszú távú kódkarbantartást és az együttműködést nagyon bonyolulttá tenné.

#### 2.2.1 Távoli eljáráshívás (Remote Procedure Call)

Nem meglepő, hogy ezt a problémát az elosztott rendszerek programozói közössége nagyon korán felfedezte, és megkezdődött a szabványosítási munka. Az első javaslat, amely befolyásossá vált, a Sun Microsystems *Remote Procedure Call* (RPC) volt [5]. Az RPC kulcsfilozófiája, hogy olyan programozási felületet biztosítson egy távoli szerver eléréséhez és használatához, amelyet a fejlesztők már ismernek. Ez a természetes közös absztrakció az eljárás- vagy függvényhívás, amely minden programozó számára jól ismert. Ha el tudjuk rejteni a kapcsolatfelépítés, üzenetcsomagolás és -átvitel részleteit és bonyolultságait, a programozók jobban a programlogikára tudnak koncentrálni, és ezzel egyidejűleg a programok minősége is növekszik. Egy ilyen szabványosított rendszer csak akkor tud működni, ha létezik egy speciális futtatókörnyezet, amely ezeket a háttérfeladatokat a programozó nevében elvégzi. Az elosztott rendszerek terminológiájában ezt a futtatókörnyezetet köztesrétegnek (*middleware*) nevezzük, amely egy szoftverréteg az elosztott alkalmazás és az operációs rendszer között. A köztesréteg szerepe egy közös absztrakciós réteg létrehozása, amelyet az elosztott rendszerben együttműködő összes fél ismer.

Ahhoz, hogy elérjük ezt a köztesréteget, vagyis az RPC futtatókörnyezetét, speciális kódrészleteket kell létrehozni, úgynevezett csonkokat (*stubokat*), amelyek a kliens- és szerverkódot a köztesréteghez kapcsolják [6]. A 2-10. ábra illusztrálja az RPC-hívás működését a csonkokon keresztül. A csonkokat egy RPC-fordító generálja.

*2-10. ábra: Az RPC mechanizmus megvalósítása*

![2-10. ábra](<../Cloud Programming_MSc_Juhasz_IId-16_1.png>)

Itt eltekintünk a megvalósítás és fordítási folyamat részleteitől, és csak egy egyszerűsített kódrészletet mutatunk be a kliens-szerver interakció szemléltetésére. A kliens a `clnt_create()` függvénnyel csatlakozik a szerverhez, és sikeres csatlakozás esetén a `print_list_1()` függvény hívásával hajt végre egy távoli műveletet (egy elemlista nyomtatása). Ha összehasonlítjuk a korábbi socket-szintű implementációt ezzel az RPC verzióval, az egyszerűsítés elkerülhetetlen.

```c
    CLIENT *cl;
    int *result;
    ...
    cl = clnt_create(argv[1], PRINTER, PRINTER_V1, "tcp");
    if (cl == NULL) {
        printf("error: could not connect to server.\n");
        return 1;
    }
    result = print_list_1(l, cl);
    if (result == NULL) {
        printf("error: RPC failed!\n");
        return 1;
    }
```

#### 2.2.2 Távoli metódushívás (Remote Method Invocation)

A Java különleges helyet foglal el az elosztott rendszerekben platformfüggetlensége miatt. A Java virtuális gép egységes futtatási környezetet biztosít a Java alkalmazásoknak, függetlenül attól, hogy milyen hardvert és operációs rendszert használnak egy adott számítógépen. Mivel a Java támogatja az objektumok szerializációját (állapotuk bájtsorozattá alakítását), nemcsak adatokat, hanem Java-osztályokat is lehet küldeni az egyik virtuális gépből (VM) a másikba. Ez a Java-változatú, illetve Java-alapú újraimplementációja az RPC-nek: a *Remote Method Invocation* (RMI) technológia [7].

Az RMI célja, hogy távoli metódushívási mechanizmust biztosítson Java programok számára. Mivel egy Java program a JVM-ben fut és elszigetelt a hardvertől, a standard Java metódushívási mechanizmus nem alkalmas távoli számítógépek elérésére. Az RMI tervezői bevezettek egy middleware réteget, amely az alapul szolgáló operációs rendszerrel együttműködve kapcsolatokat épít ki és adatokat továbbít egy távoli félhez. Ezen túlmenően, mivel a Java 100%-os objektumorientált nyelv, egy speciális absztrakciót – egy csonk (stub) osztályt – vezettek be, amely a távoli szervert a kliens számára normál Java objektumként reprezentálja a működés során.

Az RMI működéséhez némi további infrastruktúrára van szükség. Mivel az objektum-perzisztencia mechanizmus csak az objektum állapotát továbbítja, egy további módot kell biztosítani a lefordított Java osztályok továbbítására a másik félnek, hogy a távoli VM osztálybetöltője megtalálja az osztályt betöltéskor. Az RMI HTTP szervereket használ az osztályfájlok exportálásához. Az utolsó gépezet az, ahogy a kliensek és a szerver megtalálják egymást az RMI-ben. Az IP-cím és portszám alapján történő egyszerű címzési módszerrel szemben az RMI egy interfész-alapú lookup mechanizmust használ. A távoli szervereket az interfészük írja le, amely a szerver funkcionalitását rögzíti. Ez azt jelenti, hogy a klienseknek ismerniük kell a használni kívánt interfészt, mivel ez az interfész fogja biztosítani azokat a nyilvános metódusokat, amelyeket a kliens meghívhat. Az interfészek használata jobb leírást nyújt a távoli funkcionalitásról, mint a portszámokkal lehetséges. Most egy távoli rendszernek tetszőleges számú funkcionalitása lehet a kliensek számára, amennyiben azokat metódus-szignatúrákkal le lehet írni. A Java erős típusossága biztosítja, hogy a kliensek csak azokat a szolgáltatásokat érhetik el és használhatják, amelyekhez fejlesztették őket. Ezen komponensek kölcsönhatása a 2-11. ábrán látható.

*2-11. ábra: A Java RMI rendszer összetevői és architektúrája.*

![2-11. ábra](<../Cloud Programming_MSc_Juhasz_IId-18_1.png>)

A következő fejezet egy RMI kliens-szerver alkalmazás fejlesztésének kulcsfontosságú lépéseit mutatja be. Csak a legfontosabb kódrészleteket fogjuk bemutatni. Egy hipotetikus távoli bank példáját használjuk, amely lehetővé teszi a kliens számára, hogy pénzt helyezzen el, vonjon ki és utaljon át egy bankszámláról. A szerver funkcionalitását egy Java interfész írja le. Specifikáció szerint a távoli szerver interfésznek a `Remote` interfészből kell leszármaznia, és minden metódusnak tartalmaznia kell egy `throws RemoteException`-t a deklarációban.

```java
import java.rmi.Remote;
import java.rmi.RemoteException;

public interface BankInterface extends Remote {
    int deposit(int amount) throws RemoteException;
    int withdraw(int amount) throws RemoteException;
    int getBalance() throws RemoteException;
}
```

A szerver ezt az interfészt egy olyan Java osztállyal implementálja, amely a `UnicastRemoteObject`-ből származik, és indításkor regisztrálja magát az `RMIregistry`-be.

```java
public class BankServer extends UnicastRemoteObject implements BankInterface {
    static int balance = 0;

    public BankServer() throws RemoteException {
        super();
    }

    public int getBalance() throws RemoteException {
        return balance;
    }

    // other methods are omitted

    public static void main(String[] args) {
        if (System.getSecurityManager() == null) {
            System.setSecurityManager(new RMISecurityManager());
        }
        String name = "BankServer";
        try {
            BankServer server = new BankServer();
            Naming.rebind(name, server);
            System.out.println("BankServer bound");
        } catch (Exception e) {
            System.err.println("BankServer exception: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

A kliens két fő lépést hajt végre a programban. Az első a távoli szerver megkeresése az `RMIRegistry` használatával, a második pedig a távoli funkcionalitások végrehajtása a szervert reprezentáló csonk/proxy (stub/proxy) objektumon lokális metódushívásokkal. A kliens kód szépen illusztrálja az RMI magas absztrakciós szintjét és eleganciáját a kliens-szerver rendszerek implementálásában.

```java
public class ATMClient{
    public static void main(String args[]) {
        if (System.getSecurityManager() == null) {
            System.setSecurityManager(new RMISecurityManager());
        }
        BufferedReader stdIn = new BufferedReader(new InputStreamReader(System.in));
        try {
            String name = "//" + args[0] + "/BankServer";
            BankInterface server = (BankInterface) Naming.lookup(name);
            ...
            boolean finished = false;
            while (!finished){
                ...
                balance = server.getBalance();
                ...
            }
        }catch(RemoteException ex){
            ex.printStackTrace();
        }
        ...
    }
}
```

#### 2.2.3 Érvek a lazán csatolt rendszerek mellett

Az RPC/RMI programozási absztrakció nagy segítség a bonyolultság és a programhibák csökkentésében az elosztott szoftverfejlesztésben. Természetes kiterjesztését nyújtja a jól ismert függvény/eljárás/metódushívási technikának. Kiderül azonban, hogy hibák jelenlétében kissé törékeny. A low-level kommunikáció részleteinek elrejtése, valamint annak "színlelése", hogy a szerver csak egy közönséges funkciója egy objektumnak, sok programozónak azt sugallja, hogy a rendszer, amelyen dolgoznak, pontosan ugyanúgy viselkedik, mint egy hagyományos, lokálisan futó program. Semmi sem lehetne távolabb az igazságtól! Az elosztott szerverek különféle hibákat produkálhatnak, amelyek szekvenciális programokban nem léteznek. A hálózati kapcsolat megszakadhat, a szerver tranziens vagy végzetes hibát produkálhat, helytelen eredményeket vagy egyáltalán nem produkál eredményt. Ezeket a helyzeteket nehéz függvényhívásokkal monitorozni és kontrollálni. Az RMI speciális Java kivételeket (RemoteException) használ, amelyek jelzik a hívónak, ha valami rosszul ment.

A valódi nehézség a hosszú metódushívási láncokban jelentkezik; amikor több elosztott rendszerkomponens hívja egymást egy összetett feladat végrehajtásához. Nézzünk egy példát, amelyben egy C kliens meghívja az A szervert. Az A szerver viszont meghívja a B szervert segítségért, amely aztán meghívja a D szervert. A kliens lehet, hogy nincs tudatában ennek a megvalósítási részletnek, mivel csak az A szerverhez csatlakozott. Ha nincs hiba, a rendszer tökéletesen működik, de ha hiba történik, az egész rendszer állapota könnyen megromolhat. Gondoljunk egy tranzakciós integritást igénylő feladatra. Hogyan tudjuk garantálni, hogy egy feladat csak akkor hajtódik végre, ha az összes alfeladat helyesen fut le? Ha a hívási lánc bármelyik tagja hibát generál, dominó-effektus indul el, és kivételek (vagy hibakódok) terjednek végig a rendszerben visszafelé irányban. Továbbá, ha egy metódushívás határozatlan ideig lóg (várakozás vagy holtpont (deadlock) miatt), minden hívó metódus is blokkolódik. Ezt a működési módot *erős csatolásnak* (*strong coupling*) nevezik elosztott rendszerekben. Más szavakkal, az egyik komponens hibája közvetlenül befolyásolja egy másik komponens működését. Egy szerver teljes meghibásodása blokkolja az egész rendszert, és a feladatok már nem hajthatók végre. Ahogy a 2-12. ábrán látható, egy elosztott metódushívási láncban számos lehetséges hibahely van. Meglehetősen nehéz a pontos hibaokot egyetlen visszaadott RemoteException példányból megtalálni; ráadásul még nehezebb garantálni a rendszer állapotának integritását egy ilyen helyzetben.

*2-12. ábra: Lehetséges hibahelyek egy RPC/RMI hívásban*

*(Megjegyzés: a 2-12. ábra az eredeti PDF-ben vektorgrafikusan került beágyazásra, ezért külön képfájlként nem elérhető.)*

Ahogy a fejlesztők egyre nagyobb elosztott rendszerek létrehozására tettek kísérletet, az erősen csatolt metódusláncolási absztrakcióban rejlő skálázhatósági problémák nyilvánvalóvá váltak. Az ipar a lazán csatolt kommunikáló rendszerek felé fordult, amelyek az üzenetküldéses típusú kommunikációra és az aszinkron végrehajtásra támaszkodnak. Ezekkel részletesebben később foglalkozunk.

### 2.3 Szolgáltatás-orientált rendszerek

A szolgáltatásorientáció koncepciója a kliens-szerver rendszerekből és az interfészek használatából nőtt ki a szerver funkcionalitás leírására. Annak érdekében, hogy az elosztott rendszerek rugalmasabbak, kevésbé kötöttek legyenek a hardverhez, a kutatók olyan módokat kerestek, amelyekkel szétválaszthatók a szerverkódot futtató rendszer és a funkcionalitás, amelyet a szerver képvisel. A *szolgáltatás* koncepciója megfelelő általánosításként jelent meg. Egy *szolgáltatás* egy funkcionalitás-darab, amelyet hardverben vagy szoftverben implementálnak, és hasznos funkciót biztosít a kliens számára. Egy szolgáltatást a szolgáltató és a szolgáltatás fogyasztója közötti szerződés képvisel. A szolgáltatásorientált szoftverrendszerekben a kulcsfontosságú újdonság az a képesség, hogy a szolgáltatókat a szolgáltatásuk alapján találjuk meg a szerver fizikai végrehajtását lehetővé tevő címe helyett. Például, ha egy dokumentumot akarok lefordítani mondjuk németről angolra, akkor csak olyan online szolgáltatások érdekelnek, amelyek ezt a fordítást biztosítani tudják. Nem érdekel, hol futnak (IP-cím), csak az, hogy a fordítás megvalósuljon. Hogyan érhető el ez? Ezt a fejezet további részében látni fogjuk.

A szolgáltatásorientált rendszerek a következő alapelveken nyugszanak: (i) a szolgáltatást egy interfész írja le; (ii) van egy címtár, amely közvetít a kliensek és a szolgáltatások között (a szolgáltatások regisztrálnak, a kliensek a címtárban keresnek); (iii) a kliensek és a szolgáltatások csak a szolgáltatás végrehajtásának időtartama alatt lépnek kapcsolatba; (iv) a kliensek és a szolgáltatások nyílt, szabványos technológiákat és protokollokat használnak.

*2-13. ábra: Egy szolgáltatásorientált rendszer általános architektúrája és működése*

![2-13. ábra](<../Cloud Programming_MSc_Juhasz_IId-21_1.png>)

A szolgáltatásorientáció 2000-től kezdett népszerűvé válni. Mint minden heterogén elosztott rendszernél, az első kulcsprobléma egy platformfüggetlen kommunikációs és protokoll keretrendszer létrehozása volt. Ezután megkezdődhetett a szolgáltatásorientált rendszerek tervezése és megvalósítása. A szolgáltatásorientált számítástechnika ígérete az volt, hogy jól definiált funkcionalitással rendelkező, Internet-képes „komponenseket" hoz létre, amelyekből viszonylag egyszerű integrációs folyamatokkal nagyobb, komplexebb alkalmazások hozhatók létre.

A middleware technológia első jelöltje az XML volt. Érdekes módon ez nem egy programozási nyelv, hanem egy jelölőnyelv. Az XML-t azonban mindig is számítógépek számára tervezték, nem embereknek, és szigorú, szabályalapú megközelítést hordoz az adatok és műveletek leírásához. Az ötlet az volt, hogy az XML-t használják a szolgáltatás funkcionalitásának leírására, valamint az adatkommunikációban és a szolgáltatáshívásokban is. Ez utóbbihoz további eszközöket kellett fejleszteni, amelyek a szolgáltatás interfészekből „stub"-okat generáltak a célprogramozási nyelvekhez. Nem meglepő módon az első XML-alapú szolgáltatási rendszerek RPC-stílusú szolgáltatáshívást használtak.

#### 2.3.1 XML alapú szolgáltatások – webszolgáltatások

Amikor az XML-t és a szolgáltatásorientációt a HTTP protokoll fölött használjuk, akkor Web Service (webszolgáltatás) technológiáról beszélünk. A webszolgáltatások olyan szolgáltatások, amelyeket az Interneten keresztül, webprotokollok használatával történő meghívásra terveztek. Céljuk az volt, hogy gerincét képezzék a vállalatok közötti (business-to-business, B2B) alkalmazások új generációjának, amely leegyszerűsíti az online üzletelést, és olyan rendszereket hoz létre, amelyek a jövőben könnyen karbantarthatók és módosíthatók. A 2-14. ábra szemlélteti egy webszolgáltatás-alapú szolgáltatásorientált rendszer általános architektúráját.

A szolgáltatásokat egy XML-alapú WSDL (Web Service Description Language) interfész-leíró írja le, amely információkat hordoz a szolgáltatás helyéről, az általa kínált funkcionalitásról és az elérés módjáról. Ez a leírás egy nyilvános címtárban, az UDDI-ban (Universal Description, Discovery, and Integration) van tárolva. A címtár szintén XML-alapú. A kliensek az UDDI címtárat használják megfelelő szolgáltatások kereséséhez, kinyerik a szolgáltatás eléréséhez szükséges információkat, majd XML-alapú SOAP (Simple Object Access Protocol) üzenetek használatával csatlakoznak a szolgáltatáshoz, és végrehajtják a választott funkciókat.

*2-14. ábra: A Web Service architektúra*

![2-14. ábra](<../Cloud Programming_MSc_Juhasz_IId-22_1.png>)

A webszerverekhez hasonlóan a webszolgáltatásoknál is az az ajánlás, hogy állapot nélküli (stateless) szolgáltatásokat valósítsunk meg. Az állapot nélküli szolgáltatások nem függenek a hívások sorrendjétől, nem változtatják saját állapotukat, és minden beérkező kérésre mindig ugyanazt a műveletet hajtják végre, ami sokféle, nagy elosztott rendszerekben fellépő hibával szemben toleránssá teszi őket. Sajnos sok szolgáltatás, különösen a kliensfüggő üzleti szolgáltatások állapotfüggőek (stateful), ami a szolgáltatásokban az állapottámogatás bevezetéséhez vezetett. A növekvő komplexitás szükségessé tette az egyszerű WSDL-SOAP alapú kliens-szolgáltatás interakciós technológia kiterjesztését. A Web Service technológiai stackben (a 2-15. ábrán szemléltetve) számos új réteg és komponens jelent meg, amelyek különböző további működési funkciókért voltak felelősek (pl. elosztott tranzakciók kezelése, kontextus biztosítása, szolgáltatások orkesztrációja, üzleti munkafolyamatok leírása stb.). Ez sajnos egy olyan komplex és nagy technológiai rendszert eredményezett, amelyet szinte lehetetlen megérteni. A Web Service specifikációk halmaza, amelyet köznyelven „WS-* stack"-nek neveznek, több mint 70 specifikációt tartalmaz.

*2-15. ábra: A Web Service technológiai stack*

![2-15. ábra](<../Cloud Programming_MSc_Juhasz_IId-22_2.png>)

#### 2.3.2 RESTful szolgáltatások

A Representational State Transfer (röviden REST) Roy Fielding 2000-es PhD munkájának eredménye, és egy alternatív megközelítés alapja nagy elosztott szolgáltatási rendszerek létrehozásához. A mainstream szolgáltatásorientált megközelítések komplexitásával elégedetlen Fielding egy egyszerű, erőforrás-orientált módot javasolt a szolgáltatások leírására. Míg a hagyományos megközelítések a számítás fogalma köré összpontosultak (valami végrehajtása a kliens nevében), a REST a problémát az adat szempontjából vizsgálta. Fielding azt javasolta, hogy minden entitásnak (akár egyetlen memóriabájtnak is) lehessen egy URL-je, amelyen keresztül az állapota lekérdezhető és módosítható. Ezekhez csak egy GET és POST HTTP parancs szükséges, az erőforrásra mutató URL-lel együtt. Kidolgozott egy módszert a szolgáltatási interfészek URL-ekkel történő leírására, beleértve a GET és POST parancsokat.

A REST-alapú vagy RESTful szolgáltatások egyszerűsége miatt ez a megközelítés nagyon gyorsan népszerűvé vált, valódi véleménykülönbséget okozva a webszolgáltatás közösségben. Mindazonáltal mára úgy tűnik, a REST a tiszta győztes, az XML-alapú Web Service-eket már csak kivételes körülmények között használják új rendszerfejlesztéshez. A REST részletei megtalálhatók Fielding disszertációjában⁷ vagy a következő Wikipédia bejegyzésben: https://en.wikipedia.org/wiki/Representational_state_transfer.

### 2.4 Grid számítástechnika

A Grid Computing az 1990-es évek végén jelent meg két független, egyidejű mozgalom eredményeként. Az Egyesült Államokbeli szuperszámítógépek elszigetelten működtek, ami nagy regionális különbségeket eredményezett a szuperszámítógépek terhelésében. Egy szuperszámítógép-központ túl lehetett terhelve, így a felhasználói feladatok munkasorokban várakoztak, miközben más központok ugyanabban az időben kihasználatlanok (idle) maradtak, mivel nem kaptak elég feladatot a rendszer megfelelő terhelésének fenntartásához. A kutatók azt javasolták, hogy ezen központok egy nagyobb rendszerbe való összekapcsolásával, amely automatikusan a legmegfelelőbb központba küldi a feladatokat, növelni lehet a szuperszámítógép-központok általános hatékonyságát és kihasználtságát, valamint csökkenteni lehet a felhasználók várakozási idejét. Körülbelül ugyanebben az időben a hálózati és az elosztott számítási rendszerek elértek egy olyan érettségi szintet, amely lehetővé tette nagy számítási klaszterek létrehozását helyi hálózaton keresztül összekapcsolt számítógépekből. A kutatók azt javasolták, hogy ezt a koncepciót terjesszék ki nagy kiterjedésű hálózatokra, azaz távoli számítógépeket kapcsoljanak össze nagy virtuális párhuzamos számítógépek létrehozásához. Az első törekvés szuperszámítógépek összekapcsolását javasolta, míg a második ugyanezt tervezte számítógépklaszterekkel. Mindkettő célja a meglévő számítási erőforrások hatékonyságának és kihasználtságának növelése volt egy hatékony terheléselosztó szoftverréteg biztosításával.

A Grid Computing kifejezést azzal a céllal vezették be, hogy a számítástechnikához való hozzáférést az elektromos áramhoz való hozzáféréssel hasonlítsák össze. Az Egyesült Államokban az elektromos energiaelosztó rendszert Power Grid-nek nevezik. Az ötlet az volt, hogy a kutatók számára földrajzi elhelyezkedésüktől függetlenül számítási és tárolási lehetőségeket biztosítsanak. Ha egy számítógép a Grid-hez van csatlakoztatva, hozzáférhet az erőforrásokhoz, ugyanúgy ahogy áramot kapunk, amikor eszközünket a konnektorba dugjuk. A korai törekvések különböző szoftverrendszereket eredményeztek, amelyek célja magas szintű programozási interfész biztosítása volt párhuzamos programok elosztott klasztereken való létrehozásához és futtatásához. Jelentős rendszerek közé tartozik a Parallel Virtual Machine (PVM) [8], a Legion [9] és a Globus Toolkit [10]. Ezek a korai rendszerek kezdetben kis klaszteralapú rendszerek létrehozására összpontosítottak, módokat keresve az egyetemi klaszterekben lévő kihasználatlan (idle) számítógépek hatékony használatára, de ahogy tapasztalat gyűlt össze, egyre nagyobb kiterjedésű rendszereket próbáltak létrehozni. 2005-re szinte minden fejlett ország épített nemzeti grid rendszert. Európában a CERN által vezetett DataGrid projekt [10] (több

---

⁷ https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm

európai ország részvételével) ennek a koncepciónak sikeres demonstrálása volt, bár ez egy csak egy konkrét feladatra, a Nagy Hadronütköztető által generált adatok feldolgozására létrehozott rendszer volt.

A legsikeresebb middleware szoftverfejlesztési projekt a Globus toolkit volt, amely arra összpontosított, hogy meglévő rendszereket, szoftverkomponenseket és szabványos protokollokat (mint például az FTP) használjon, új programozási absztrakciók (mint a PVM vagy a Legion) létrehozása helyett. Egy Globus publikációból [11] vett példát fogunk használni, amely segít megérteni a Grid Computing mögötti gondolatokat.

Tegyük fel, hogy egy kutató szeretne futtatni egy szimulációs programot. Ez a konkrét program egy elosztott szimuláció, és interaktív módban működik. Az interaktív mód köztudottan nehezen kivitelezhető batch végrehajtási környezetekben, és még problematikusabb több helyszínes esetben. Minden helynek elegendő erőforrást kell biztosítania a program futtatásához, és ezt egyidejűleg a többivel. Jó lenne, ha ezt a felhasználó helyett maga a rendszer végezné el. Amint a 2-16. ábra szemlélteti, egy grid erőforrás-menedzsment rendszerben elvárnánk egy elosztott szimuláció specifikus brokert, amely átveszi a konfigurációs feladatot a felhasználótól. Ez lefordítja a felhasználó kérését számítógép-specifikus fogalmakra, és elkezdi keresni a kérés kiszolgálására kész szuperszámítógép-helyszíneket. Valós idejű információt gyűjt egy másodszintű brokertől, a szuperszámítógép erőforrás-brokertől, és annak segítségével több helyszínen is erőforrásokat együttesen lefoglal erőforrásokat a szimuláció végrehajtásához. Amint a közös erőforrás-allokáció befejeződött, a szimuláció elindul. A felhasználó csak a kezdeti kérést és a futó szimulációs programot látja. Minden technikai részlet el van rejtve.

*2-16. ábra: Felhasználó által generált erőforrás-lekérdezés végrehajtásának magas szintű nézete*

![2-16. ábra](<../Cloud Programming_MSc_Juhasz_IId-24_1.png>)

Ahogy mondani szokták, „az ördög a részletekben rejlik". Hogyan érhető ez el? Milyen szoftverkomponensek szükségesek a program végrehajtásának menedzseléséhez? A 2-17. ábra részletesebben mutatja ennek az erőforrás-menedzsment rendszernek a működését. A rendszer egy Resource Specification Language segítségével leírt specifikációkat használ az erőforrás- és ütemezési követelmények kifejezésére. Minden helyszínen egy helyi Globus Resource Allocation Manager (GRAM) fut, amely

begyűjti és továbbítja az erőforrás-információkat az Information Service-nek, feldolgozza az RSL-kéréseket, elfogadva vagy elutasítva őket, és felelős egy végrehajtás alatt álló feladat monitorozásáért és kezeléséért.

Az erőforrás-brokerek a grid információit az Information Service-ből olvassák, és egy kliens kérésének feldolgozása során specializált lekérdezéseket generálnak, és esetleg kapcsolatba léphetnek más, specifikusabb brokerekkel specializált lekérdezésekkel. Amikor a szükséges erőforrás-követelmény teljesül, a Broker együtt dolgozik a co-allocatorral a szükséges szoftverkomponensek lefoglalásához, allokációjához és végrehajtásához.

*2-17. ábra: A Globus erőforrás-menedzsment rendszerének architektúrája*

![2-17. ábra](<../Cloud Programming_MSc_Juhasz_IId-25_1.png>)

Ahogy a Grid Computing fejlődött, a szolgáltatásorientáció fogalma hasznos absztrakcióként jelent meg a Gridben. Ennek eredményeként a Globus Toolkit jelentős átalakításon ment keresztül, és szolgáltatásorientált változattá alakult, amely a Web Service-eket használja mögöttes technológiaként. Az új rendszert Open Grid Service Architecture-nek (OGSA) nevezték. Ezt a kezdeményezést egy nemzetközi bizottság irányította, amelyben az akadémiai és üzleti közösség képviselői vettek részt.

### 2.5 Önkéntes erőforrás-megosztás

A push-stílusú Grid rendszerek alternatívája, amelyekben a felhasználók távoli helyszínekre küldik programjukat végrehajtásra, az önkéntes számítástechnika; amelyben a számítógépek tulajdonosai felajánlják számítógépüket programok végrehajtására. A programok pull-stílusban kerülnek telepítésre, egy központi feladat-adatbázishoz való csatlakozás útján.

Az első és leghíresebb példa egy ilyen számítási rendszerre a SETI@home projekt. A projekt 1999-ben indult a Berkeley Egyetemen azzal az ötlettel, hogy a kihasználatlan (idle) számítógépes erőforrásokat rádióteleszkóp-adatok elemzésével földönkívüli élet jeleinek keresésére használják. Ebben a rendszerben⁸ a felhasználók telepítettek egy programot, amely képernyővédőként futott, de véletlenszerű grafikák rajzolása helyett a SETI szerverhez csatlakozott, letöltött egy teleszkóp-adatszegmenst, és elemezte azt. A rendszer egyszerűsített architektúráját a 2-18. ábra mutatja. Érdekes megjegyezni, hogy ebben a rendszerben az elemzési programokat futtatni kívánó kliens a szerver, a számítási erőforrásokat biztosító felhasználók pedig a kliensek. A rendszer másik fontos jellemzője, hogy a munkaelosztás teljesen automatikus, és a működés hibatűrő; a működés folyamatos

---

⁸ https://setiathome.berkeley.edu/sah_papers/cacm.php

még kliens-meghibásodások vagy leválások esetén is. A projekt nagy siker volt; milliók adományozták számítógép-idejüket, és a projekt összesített számítási teljesítménye meghaladta a legjobb szuperszámítógépekét. A projekt technikai részleteit [12] tárgyalja.

*2-18. ábra: A SETI@home rendszer architektúrája*

![2-18. ábra](<../Cloud Programming_MSc_Juhasz_IId-26_1.png>)

A projekt sikere egy új alprojektet eredményezett, a futtató infrastruktúra fejlesztését és támogatását. Egy általánosított szoftverrendszer, a Berkeley Open Infrastructure for Network Computing (BOINC)⁹ jött létre, amely hasonló elosztott számítási erőforrásokat kereső projektek számára vált elérhetővé. Több mint 30 tudományos projekt használja a BOINC infrastruktúrát, közel 800 000 aktív résztvevő számítógéppel és több mint 40 petaFlop/s összesített számítási teljesítménnyel.

Egy hasonló projekt, amely a BOINC projekt ernyőjén kívül fut, a Folding@home, amely fehérje-szerkezet kutatási platform. Az írás idején a projekt fő fókusza olyan molekulák megtalálása, amelyek a COVID-19 vírus elleni potenciális gyógyszerekként használhatók.

### 2.6 Hoszting és a kialakuló közműszerű számítástechnika

Az 1990-es évek végére, a 2000-es évek elejére a számítógépek nélkülözhetetlenné váltak a vállalatok napi működésében. Egyre több számítógépet telepítettek a vállalatoknál, és nyilvánvalóvá vált, hogy ezek a rendszerek professzionális támogatást és karbantartást igényelnek. Kezdetben a vállalatok IT-szakembereket kezdtek alkalmazni erre a feladatra, de ez valódi problémát jelentett a kis- és középvállalkozások számára, amelyek elsődleges tevékenysége nem az informatika. A kereskedelmi, gyártási stb. területen működő kis cégek számára nem volt életképes és hatékony teljes munkaidős IT-személyzetet fizetni a cég weboldalának vagy belső számítógépeinek felügyeletére. Néhány éven belül új iparág jött létre, a kiszervezett webhoszting. Gazdaságosabb volt egy nagysebességű összeköttetésekkel rendelkező szerverfarmot egy helyszínen üzemeltetni, és több kisvállalat weboldalát ott futtatni. A méretgazdaságosság alacsonyabb árakat eredményezett, a vállalatok elfelejthették a weboldal üzemeltetésének részleteit, és elsődleges szerepükre összpontosíthattak. A webhosztingot hamar követte az általános hoszting, ahol teljes számítógépeket menedzseltek és üzemeltettek egy ügyfél számára, tetszőleges

---

⁹ https://boinc.berkeley.edu/

alkalmazásokat futtatva. A vállalatok szerették ezt a megközelítést, mivel fix havi díjat tudtak fizetni a szolgáltatásokért, amelyeket könnyen lehetett tervezni az éves költségvetésben. Ez volt a kezdete annak, amit ma közműszerű számítástechnikának nevezünk.

A SUN Microsystems volt az első jelentős IT-vállalat, amely üzleti potenciált látott az ilyen típusú számítástechnikában. Tökéletesen illeszkedve mottójukhoz, „The Network Is The Computer”, létrehozták a Sun Containert, egy hordozható szerverkonténert (lásd 2-19. ábra), amelyet eredetileg olyan nagy ügyfelek számára terveztek, akiknek extra számítási teljesítményre volt szükségük. 2005-ben a SUN elkezdte saját maga üzemeltetni ezeket a rendszereket, és rögzített használatalapú díjon kínált hozzáférést az erőforrásokhoz. A Sun Grid Compute Utility esetén az ár 1 dollár volt CPU-óránként; a Sun Grid Storage Utility esetén az ár 1 dollár volt gigabájtonként havonta. A rendszer valódi siker volt, de a szerencsétlen 2008-as pénzügyi válság csődbe juttatta a SUN-t, és ezzel véget vetett a vállalat önálló működésének.

*2-19. ábra: A SUN Grid konténer*

![2-19. ábra](<../Cloud Programming_MSc_Juhasz_IId-27_1.png>)

### 2.7 Virtualizáció

A virtualizáció mint technológia régóta ismert, és rendszeresen használták mainframe számítógépeken. A virtualizáció célja egy szoftverrendszer absztrahálása vagy leválasztása a hardverkörnyezetéről, egy virtuális környezet létrehozásával, legtöbbször virtuális gép formájában. A virtualizáció a hosting szolgáltatók és adatközpontok megjelenésével kapott figyelmet és népszerűséget.

A múltban egy szoftver csak azon a hardveren tudott futni, amelyre lefordították. Ez törékeny infrastruktúrát és szállítói függőséget (vendor lock-in) eredményezett. Például, ha egy számítógép elavulttá vált, egyre nehezebb volt a szükséges hardverinfrastruktúrát karbantartani és a szoftvert működőképesen tartani. Továbbá egy konkrét operációs rendszerre fejlesztett rendszer „élethosszig tartó" választássá vált, mivel az alkalmazás fejlesztése után lehetetlen volt más platformra áttérni.

A virtuális gépek használata lehetővé teszi egy rugalmasabb és hatékonyabb számítástechnikai infrastruktúra létrehozását. A virtualizációval lehetővé válik egy hardvererőforrás virtualizálása és bármilyen operációs rendszer futtatása rajta (2-20. ábra). Hasonlóképpen lehetséges egy operációs rendszer virtualizálása és alkalmazások futtatása rajta, annak ellenére, hogy az alatta lévő platform inkompatibilis operációs rendszert futtat.

Ahogy a 2-21. ábra mutatja, a virtualizációnak különböző területei vannak (hardver, hálózat, tárolás, memória stb.). *Hardver-virtualizáció* esetén egy Virtual Machine Monitor (VMM) nevű virtualizációs réteget használnak, amely felelős a hardver emulálásáért az operációs rendszer felé. A hardver-virtualizáció célja, hogy bármilyen hardveren futtathatóak legyenek teljes operációs rendszerek módosítás

nélkül. A virtualizációs réteg utasításkészlet-architektúrát és hardver-nézetet emulál, amelyet a vendég operációs rendszer igényel.

*2-20. ábra: A virtualizáció lehetővé teszi különböző operációs rendszerek futtatását ugyanazon a hardveren*

![2-20. ábra](<../Cloud Programming_MSc_Juhasz_IId-28_1.png>)

*Teljes virtualizáció* (*Full Virtualization*) esetén a tényleges hardver teljes szimulációja történik, hogy egy módosítatlan vendég operációs rendszer futtatható legyen.

A *paravirtualizáció* érdekes megközelítést jelent a hardvervirtualizációhoz. Ebben a virtualizációtípusban a virtualizációs réteg egy speciális API-t kínál az operációs rendszernek, amely lehetővé teszi, hogy az operációs rendszer egyes funkciói a gazdagép hardverén hajtódjanak végre az emulált réteg helyett. Ez növeli a teljesítményt és a végrehajtási hatékonyságot. Sajnos ez módosítást igényel az operációs rendszer kódjában. Néhány operációs rendszernek van paravirtualizált változata.

*2-21. ábra: Az erőforrás-virtualizáció különböző formái¹⁰*

![2-21. ábra](<../Cloud Programming_MSc_Juhasz_IId-28_2.png>)

A teljes és paravirtualizációs módszerek szoftveralapú megközelítések. Az utasításokat binárisan lefordítják a vendégváltozatról a gazdagépen futó változatra, ami jelentős teljesítményveszteséget okoz. A hardvervirtualizáció legelterjedtebb stratégiája ma a *hardveresen támogatott virtualizáció* (*hardware-assisted virtualisation*), amely a CPU-gyártók speciális hardvertámogatására támaszkodik. Ebben a módban az operációs rendszer vagy alkalmazás számos funkciója felhasználhatja a gazdagép számítógép (főleg a

---

¹⁰ A virtualizációs ábrák forrása: https://www.znetlive.com/blog/virtualization-in-cloud-computing/

CPU-jának) fizikai hardver-erőforrásait, ami sokkal magasabb teljesítményt eredményez, mint a teljes szoftver-emuláció alapú virtualizációs technikák.

Összefoglalva, a virtualizáció fő előnyei a következők.

- A virtualizáció lehetőséget biztosít az erőforrások hatékony kezelésére. Az alkalmazásokat, rendszereket tetszés szerint el lehet indítani és leállítani pillanatképek (snapshotok) segítségével, szükség esetén új hardverre migrálhatók.
- A virtualizáció növeli az IT-műveletek hatékonyságát. Lehetséges több virtuális gépet futtatni egy számítógépen, és maximalizálni a processzorok kihasználtságát a hagyományos egy alkalmazás egy szerveren konfiguráció helyett, amely sok üresjáratú CPU-ciklust eredményez.
- A virtualizáció könnyebbé teszi a biztonsági mentést és a katasztrófa utáni helyreállítást. A virtuális gép-képek és állapot-pillanatképek (snapshotok) könnyen létrehozhatók és tárolhatók/archiválhatók.
- A virtualizáció növeli a költségmegtakarítást a csökkentett hardverkiadások révén. Ez az erőforrások jobb kihasználásának eredménye.

Vannak hátrányai is a virtualizációnak, amelyeket érdemes megemlíteni.

- A virtualizációnak van némi teljesítmény-büntetése az extra rétegek miatt. Ez kissé alacsonyabb végrehajtási sebességet eredményezhet az alkalmazások számára.
- Kereskedelmi szoftvercsomagok esetén a virtualizált végrehajtás kifejezetten tiltott lehet, vagy megnövekedett licencköltségeket eredményezhet.
- Egy virtualizációt alkalmazó szervezetnek ki kell képeznie az IT-személyzetét virtualizációban.

## 3. Felhőtechnológiai alapok

A felhőtechnológia a modern, mindennapi életünk szerves része. Laikus megfogalmazásban egy olyan hatalmas, virtuális és skálázható számítási és tárolási infrastruktúraként definiálhatjuk, amelyet felhőszolgáltatók üzemeltetnek, és amelyet vállalatok vagy magánszemélyek igény szerint vehetnek igénybe különféle célokra. A felhő legfőbb előnye, hogy mentesíti az IT-felhasználókat a hardver- és szoftverkomponensek üzemeltetésének és adminisztrációjának terhe alól. Legfigyelemreméltóbb jellemzője pedig az egyszerű használhatóság és az igény szerinti skálázhatóság. Erre az utóbbi tulajdonságra a későbbiekben még részletesebben is kitérünk.

Egy modern, a mindennapi működésében számítógépekre támaszkodó vállalat IT-infrastruktúrájának üzemeltetése során két, egymással ellentétes cél fogalmazódik meg. Az első cél az infrastruktúra méretének minimalizálása, a kezdeti és a működési költségek alacsonyan tartása érdekében. A második cél pedig az, hogy mindig elegendő erőforrás álljon rendelkezésre a jövedelmező működéshez szükséges feladatok elvégzéséhez. Ha az üzletmenetet állandó és egyenletes számítási igény jellemzi (például fix számú alkalmazás 24/7-es futtatása), a szükséges kapacitás könnyen tervezhető. Ingadozó terhelés esetén azonban a helyzet jóval bonyolultabb. A legproblémásabb esetet a kiszámíthatatlan, hirtelen megugró, lökésszerű terhelések jelentik.

Mivel a vállalatoknak szélsőséges terhelés mellett is működőképesnek kell maradniuk, a technológiai vezetők általában túlméretezik a rendszereiket; vagyis a maximálisan elképzelhető rendszerterhelésre terveznek. Ingadozó vagy lökésszerű használat esetén ez a stratégia az esetek többségében a rendszer alulkihasználtságát (underutilization) eredményezi (lásd 3-1. ábra). Az alulkihasználtság pedig egyet jelent az erőforrások és a működési költségek elpazarlásával. Sokkal gazdaságosabb lenne az átlagos rendszerterhelés szintjére tervezni, ez azonban az infrastruktúrát és magát a vállalatot is sebezhetővé tenné, hiszen a legkritikusabb esetekben – azaz a csúcsidőszakokban – a rendszer képtelen lenne kiszolgálni az igényeket.

*3-1. ábra: Változó számítási terhelés és annak hatása a kapacitástervezésre. (Az eredeti PDF-ben a grafika nem kinyerhető összefüggő képként.)*



Éppen ezért minden olyan megbízható külső infrastruktúra, amely csúcsterhelés esetén extra erőforrásokat képes biztosítani a vállalatok számára, rendkívül vonzó lehetőség. Ez lehetővé teszi a cégek számára, hogy csökkentsék a saját IT-infrastruktúrájuk költségeit: a normál terhelésű időszakokat saját, belső erőforrásokkal szolgálják ki, a csúcsidőszakokban pedig külső erőforrásokra támaszkodnak. A felhőtechnológia az első olyan technológia, amely ezt globális méretekben és üzleti (enterprise) minőségben képes nyújtani.

A felhő ezen jellemzője önmagában is elegendő lenne ahhoz, hogy vonzó és sikeres szolgáltatássá tegye az üzleti világ számára. Ami azonban igazán különlegessé teszi, az az, hogy nemcsak gazdaságilag racionális, hanem egy olyan infrastruktúrát is képvisel, amely platformként szolgál rengeteg további, még izgalmasabb lehetőség számára.

### 3.1 Alapfogalmak

A felhőszolgáltatók hatalmas adatközpontokat üzemeltetnek, amelyek több ezer szerverből állnak. Ez a szerverpark alkotja a felhő gerincét. A virtualizációs technológiának köszönhetően ezeken a rendszereken különböző operációs rendszerek futhatnak elszigetelten és hatékonyan, miközben könnyen monitorozhatók, menedzselhetők és migrálhatók.

Ha szükséges, ezek az alacsony szintű erőforrások (szerverek, tárolók és hálózatok) a szervezetek vagy magánszemélyek számára saját „rendszerként” használhatók, mintha csak egy hagyományos szerverhoszting cég biztosítaná őket. Ezt a szolgáltatási modellt **Infrastruktúra mint Szolgáltatásnak (Infrastructure-as-a-Service – IaaS)** nevezzük, és a 3-2. ábra szolgáltatási piramisának legalsó rétegeként jelenik meg. Ez a típus maximális rugalmasságot biztosít a felhasználónak abban, hogy mit és hogyan futtat a rendszeren, cserébe viszont az erőforrások kezelésének (például az operációs rendszer frissítésének) felelőssége is a felhasználót terheli.

![3-2. ábra](<../Cloud Programming_MSc_Juhasz_IId-31_1.png>)

*3-2. ábra: A felhő különböző szolgáltatási rétegei*



Azonban nem minden ügyfélnek van szüksége ilyen szintű rugalmasságra. Sokaknak csupán egy beépített funkcionalitásokkal rendelkező weboldalra van szükségük (pl. webáruházak, közműszolgáltatók portáljai stb.). Ezek az alkalmazások szabványos szoftverkeretrendszerekre épülnek, és az üzemeltetésük nagymértékben leegyszerűsíthető, ha a felhőszolgáltató biztosítja és kezeli a futtatókörnyezetet. Ilyen lehet például egy ASP.Net, Spring vagy Node.js webalkalmazás, a hozzá tartozó háttér-adatbázissal együtt. Ebben az esetben a szolgáltató egy kész platformot biztosít és üzemeltet a felhasználó számára. Ezt **Platform mint Szolgáltatásnak (Platform-as-a-Service – PaaS)** hívjuk. A felhasználónak csupán a saját alkalmazáskódját kell biztosítania, amelyet erre a platformra telepít.

Még magasabb absztrakciós szinten komplett szoftverrendszerek is elérhetővé tehetők a felhőben. Ennek legkézenfekvőbb példája egy felhőalapú e-mail szolgáltatás. A felhasználókat egyáltalán nem érdeklik a szolgáltatás működési vagy technikai részletei, nem érdekli őket, hol vannak a szerverek, vagy hogyan frissítik a szoftvert; ők csak elektronikus leveleket akarnak küldeni és fogadni. A **Szoftver mint Szolgáltatás (Software-as-a-Service – SaaS)** gyönyörű példája annak, hogyan lehet egy hasznos funkcionalitást szolgáltatásként absztrahálni és milliók számára elérhetővé tenni.

Ahogy egyre feljebb haladunk a szolgáltatási piramisban, a felhasználóknak annál kevesebb felelősségük és tennivalójuk akad a rendszer üzemeltetésével és menedzsmentjével kapcsolatban. Ezt az összefüggést foglalja össze a 3-3. ábra.

![3-3. ábra](<../Cloud Programming_MSc_Juhasz_IId-32_1.png>)

*3-3. ábra: Menedzsmentfelelősségek változása a felhő különböző absztrakciós rétegeiben*



Újabban a hagyományos IaaS, PaaS és SaaS rétegeket kiegészítve további szolgáltatástípusok is megjelentek a piacon, nevezetesen a **Container-as-a-Service (CaaS)** és a **Function-as-a-Service (FaaS)**. Ezeket a programozással foglalkozó későbbi fejezetekben részletesen is tárgyaljuk.

### 3.2 A felhő gazdaságtana

A felhő legfőbb vonzereje a költséghatékonyság, a kimagasló teljesítmény és a megbízhatóság. Ezek mind a *méretgazdaságosságból (economies of scale)* fakadnak. A felhő-adatközpontok hatalmas, központosított szerverparkok, rendkívül magas szerver- és tárolósűrűséggel. A 3-4. és 3-5. ábrák egy-egy Google, illetve Amazon adatközpontot mutatnak be.

![3-4. ábra](<../Cloud Programming_MSc_Juhasz_IId-32_2.png>)

*3-4. ábra: A Google egyik felhő-adatközpontja*

![3-5. ábra](<../Cloud Programming_MSc_Juhasz_IId-33_1.png>)

*3-5. ábra: Az Amazon egyik felhő-adatközpontja*

![3-6. ábra](<../Cloud Programming_MSc_Juhasz_IId-33_2.png>)

*3-6. ábra: Egy Amazon adatközpont belseje*

![3-7. ábra](<../Cloud Programming_MSc_Juhasz_IId-33_3.png>)

*3-7. ábra: Egy Google adatközpont belseje*

![3-8. ábra](<../Cloud Programming_MSc_Juhasz_IId-34_1.png>)

*3-8. ábra: A Google adatközpont hűtőrendszerének gépháza*

 E gigantikus méretek miatt a szolgáltatók hatalmas kedvezménnyel tudják beszerezni a hardverkomponenseket, és gyakran az elektromos áramot is. A központosítás emellett megkönnyíti a legmagasabb szintű fizikai és informatikai biztonsági intézkedések bevezetését is. Mivel az adatközpontokban lévő rendszerek nagyon hasonlóak, a legtöbb adminisztratív feladat teljesen automatizálható, így az IT-személyzet költsége viszonylag alacsonyan tartható.

A központosított tervezés lehetővé teszi a szolgáltatók számára, hogy adatközpontjaikat rendkívül hatékonyan működtessék. Azt az üzemeltetési hatékonyságot és biztonsági szintet, amit ezek a szolgáltatók nyújtanak, egy hagyományos vállalati IT-infrastruktúrában szinte lehetetlen lenne elérni.

Természetesen a felhőszolgáltató felelőssége nem merül ki egy-egy IaaS-, PaaS- vagy SaaS-szolgáltatáspéldány elindításában. Egy szolgáltatónak számtalan egyéb működési tényezőre is figyelnie kell. Ahogy a 3-9. ábra mutatja, ezek egy része a belső menedzsmenthez és a jogszabályi megfelelőséghez kapcsolódik, míg mások a magasabb szintű szolgáltatások közvetítését teszik lehetővé.

![3-9. ábra](<../Cloud Programming_MSc_Juhasz_IId-34_2.png>)

*3-9. ábra: Általános felhőtechnológiai stack. Megjegyzendő, hogy a szolgáltatások (IaaS, PaaS, SaaS) a felhasználó felé fordított felületet képviselik.*



### 3.3 Felhasználói és használati támogatás a felhőben

Eddig a felhasználói támogatást a menedzsmenti és üzemeltetési felelősség szempontjából vizsgáltuk. A felhőszolgáltatásokat azonban a felhasználók funkcionális igényei alapján is csoportosíthatjuk. A felhőben dolgozó szoftverfejlesztőknek speciális, fejlesztést támogató komponensekre van szükségük (pl. forráskód-tárolókra (repositorykra), tesztkörnyezetekre). Az ipari végfelhasználóknak az adott ágazatukhoz kapcsolódó technológiákra lehet szükségük, mint például a Dolgok Internete (Internet-of-Things – IoT) támogatás. Az adatközpontú felhasználóknak pedig széles körű adattárolási és -elemzési eszközökre. Ezek közül mutat be néhányat a 3-10. ábra.

![3-10. ábra](<../Cloud Programming_MSc_Juhasz_IId-35_1.png>)

*3-10. ábra: Egy felhőplatform különböző felhasználói közösségeket célzó szolgáltatásai*



### 3.4 A felhő rövid története

Mielőtt részletesen is elmerülnénk a legjelentősebb felhőszolgáltatók és szolgáltatásaik, valamint a felhőprogramozás áttekintésében, érdemes röviden visszatekinteni az elmúlt két évtized fejleményeire. Ez segít megérteni, hogyan alakultak ki a mai modern felhőszolgáltatók, és milyen motivációk, okok, illetve lehetőségek vezettek a jelenlegi piaci erőviszonyokhoz.

Napjaink legnagyobb felhőszolgáltatói az Amazon, a Microsoft és a Google, akiket az Alibaba, az Oracle, az IBM és mások követnek. Ahogy a 3-11. ábrán látható elemzési diagram is mutatja (amely a piaci részesedést és az éves növekedési ütemet ábrázolja), az Amazon dominálja a globális piacot.

![3-11. ábra](<../Cloud Programming_MSc_Juhasz_IId-36_1.png>)

*3-11. ábra: A globális felhőszolgáltatók piaci részesedésének és éves növekedési rátájának pozíciója*

 A Microsoft és a Google dinamikusan növekszik, és bár lassan zárkóznak fel, piaci részesedésben egyelőre az Amazon mögött járnak. Az Oracle és az IBM kisebb szereplőknek számítanak, mérsékelt növekedési potenciállal.

Egy másik, a Gartner Group által készített elemzés a felhőszolgáltatókat egy négynegyedes (kvadráns) diagramon helyezi el a jövőképük (vision) és a megvalósítási képességük (ability to execute) alapján: Vezetők (Leaders), Kihívók (Challengers), Vizionáriusok (Visionaries) és Réspiaci szereplők (Niche Players). A 3-12. ábra négy pillanatképet mutat a 2015 és 2020 közötti eredményekről. Egyértelműen látszik, hogy az Amazon a globális vezető, ugyanakkor érdekes megfigyelni, ahogyan a Google egyre inkább növekszik, és lassan felzárkózik a Microsofthoz.

![3-12. ábra (a)](<../Cloud Programming_MSc_Juhasz_IId-37_1.png>)

![3-12. ábra (b)](<../Cloud Programming_MSc_Juhasz_IId-37_2.png>)

![3-12. ábra (c)](<../Cloud Programming_MSc_Juhasz_IId-37_3.png>)

![3-12. ábra (d)](<../Cloud Programming_MSc_Juhasz_IId-37_4.png>)

*3-12. ábra: A felhőszolgáltatók elhelyezkedésének alakulása a Gartner Group Challengers–Leaders–Niche Players–Visionaries mátrixában (2015–2020)*



#### 3.4.1 Az Amazon felhőszolgáltatás eredete

Az Amazont 1994-ben alapították, eredetileg könyvek, zenei kiadványok és elektronikai cikkek online értékesítésére. De hogyan jutott el egy online könyvesbolt a felhő világába, és hogyan vált ott piacvezetővé? A történet rendkívül tanulságos.

Az Amazon eredeti üzleti koncepciója az volt, hogy termékeket nagy mennyiségben, rendkívül alacsony áron értékesítsen az interneten. Az alacsony árak eléréséhez ki kellett iktatniuk a közvetítőket az értékesítési láncból (azaz közvetlenül a raktárból szállítottak a vásárlóknak), a rendeléseket pedig a legmodernebb számítógépes rendszerek segítségével, elképesztő sebességgel kellett feldolgozniuk. Az első években a vállalat belső szoftverfejlesztése meglehetősen ad-hoc módon zajlott, a hosszú távú működés és növekedés különösebb megtervezése nélkül. A kilencvenes évek végére a vállalat egyre nehezebben tudott hatékonyan új rendszereket fejleszteni. Ez akkor vált igazán komoly problémává, amikor elkezdték a Target és a Marks & Spencer online vásárlási platformjait fejleszteni. Kiderült, hogy hiába a hatalmas tapasztalat, a fejlesztési időt nem tudták csökkenteni, főként azért, mert a legtöbb infrastrukturális és backend komponenst a semmiből, újra és újra fel kellett építeniük.

Ezt a problémát felismerve a menedzsment 2000 körül bevezetett egy szigorú belső szabályt: minden belső fejlesztőcsapatnak át kellett állnia a szolgáltatásorientált (SOA) tervezési módszertanra, és jól definiált interfészeket (API-kat) kellett létrehozniuk a rendszereikhez. Egy másik szabály kötelezővé tette, hogy minden csapat a cégen belüli más csapatok által már kifejlesztett szolgáltatásokat használja, és azokra építkezzen. Új szolgáltatásokat csak akkor lehetett nulláról írni, ha a cégben még nem állt rendelkezésre hasonló.

Ez a szemléletváltás néhány éven belül egy igazi szolgáltató vállalattá alakította az Amazont. A szolgáltatásorientált megközelítés az infrastruktúra rétegben is megjelent: a virtuális gépek (VM-ek) bevezetése rugalmassá és könnyen kezelhetővé tette a szerverparkot. Ennek az erőfeszítésnek az első kézzelfogható eredménye a SOAP/XML API 2002-es kiadása volt, amely lehetővé tette a partnerek számára, hogy programozottan is hozzáférjenek az Amazon bolti katalógusához. 2003-ban a vezetőség felismerte, hogy az IT-hoszting terén felhalmozott szakértelmük és a kész szolgáltatáskomponenseik hatalmas értéket képviselnek. Úgy döntöttek, hogy a vállalaton belül létrehoznak egy új részleget, az Amazon Web Services-t (AWS), amely külső ügyfelek számára is kínálja ezeket a számítási erőforrásokat és szolgáltatásokat.

Három évnyi intenzív fejlesztés után az Amazon 2006-ban elindította az első alapvető szolgáltatásait: a Simple Storage Service-t (S3), az Elastic Compute Cloud-ot (EC2) és a Simple Queue Service-t (SQS). Akkoriban nagyon kevesen gondolták volna, hogy ez az első lépés a világ legnagyobb felhőszolgáltatójának megszületése felé. A siker és az azt követő növekedés robbanásszerű volt. A versenytársak csak több éves késéssel kezdtek el reagálni a piac átalakulására. Azóta az Amazon nemcsak felhőszolgáltatóvá vált, hanem a világ egyik legnagyobb és legértékesebb vállalatává is. A háttérben a cég az évek során hatalmas szakértelmet épített fel a gépi tanulás (Machine Learning) és a mesterséges intelligencia (AI) területén is, így ezen a piacon is kulcsszereplővé lépett elő.

#### 3.4.2 A Microsoft és a felhő

A Microsoft felhőplatformjának fejlesztése 2008-ban vette kezdetét. A rendszert – eredetileg Windows Azure néven – 2010-ben indították el, majd később átnevezték Microsoft Azure-ra. A Microsoft eredeti fókusza az üzleti partnerein volt: egy sokkal egyszerűbben üzemeltethető IT-infrastruktúra alternatívát kínáltak nekik, valamint lehetőséget arra, hogy meglévő (legacy) alkalmazásaikat kódmódosítás nélkül, több millió felhasználóra tudják felskálázni. Később ez a fókusz kiszélesedett, és egy olyan globális rendszert eredményezett, amely végfelhasználók és nagyvállalatok számára egyaránt széles körű szolgáltatásokat kínál. A Microsoft erőfeszítéseinek sikerességét mi sem jelzi jobban, minthogy stabilan a második helyet foglalják el a globális felhőpiacon.

#### 3.4.3 Google Cloud

A Google, mint webes keresőóriás, eleve hatalmas, percenként több millió keresési lekérdezést kiszolgáló szerverfarmokra támaszkodott. Ezzel jelentős szakértelmet építettek fel a szerverek hatékony üzemeltetése és menedzsmentje terén. Nem meglepő tehát, hogy egy idő után érdeklődni kezdtek a felhőszolgáltatások külső felhasználóknak történő értékesítése iránt is. A vállalat 2008-ban indította el első szolgáltatását, a Google App Engine-t, amely PaaS platformot biztosított webes alkalmazások számára. Ezt hamarosan más szolgáltatások is követték: a Google Cloud Storage és a BigQuery 2010-ben, a Google Cloud SQL 2011-ben, a Google Compute Engine (IaaS) pedig 2013-ban. A Google nagyon agresszív stratégiát követ a felhőfejlesztésben, így ma ők számítanak a leggyorsabban növekvő felhőszolgáltatónak. A Google-on belül a felhő divízió (Google Cloud) a vállalat leggyorsabban növekvő és legnyereségesebb ágává vált.

#### 3.4.4 IBM és Oracle

Két viszonylag későn érkezett szereplő a felhőpiacon az IBM és az Oracle. Az IBM 2013-ban kezdte saját felhőrendszerének fejlesztését, eleinte kifejezetten az IaaS (infrastruktúra) rétegre koncentrálva. 2016-ban bevezették a PaaS szolgáltatásaikat, és 2017-re már a szolgáltatási piramis valamennyi rétegét lefedték. Az Oracle 2016-ban indította el felhőszolgáltatását, és azóta is folyamatosan bővíti portfólióját, hogy az alkalmazási területek (use case-ek) minél szélesebb skáláját ki tudja szolgálni.

### 3.5 Árképzés

Emlékszünk még a közműszerű számítástechnika modelljére és a SUN Microsystems konténerére, amely egységes, 1 dollár/CPU-óra árazást alkalmazott? Ezt az árazási sémát **fix áras (igény szerinti)** vagy **használatalapú** árazásnak nevezzük. Az Amazon ezt az egyszerű, óradíjas sémát vezette be szolgáltatásaihoz 2006-ban. Az óránkénti díjszámítás azt jelentette, hogy még ha a felhasználó csak 5 percig is használta az erőforrást, a teljes órás díjat ki kellett fizetnie. Néhány évvel később a szolgáltatók finomítottak ezen a modellen: a legkisebb számlázási egységet először 5 percre, majd 1 percre, végül pedig másodpercre csökkentették. A perc- és másodperc-alapú számlázás különösen vonzóvá vált a rövid, de intenzív, lökésszerű számítási terhelések esetén. Ez az igény szerinti séma nagyon kedvező a vállalatok számára, mivel rendkívül egyszerűvé teszi az erőforrás-használat tervezését, költségvetését és könyvelését.

Az árazási stratégiák további fejlődése a kedvezményes és a dinamikus árazás megjelenéséhez vezetett. A **foglalásos árazás (reserved pricing)** megköveteli, hogy a felhasználó előre lekösse egy bizonyos mennyiségű erőforrás használatát (jellemzően 1 vagy 3 évre), cserébe aztán jóval alacsonyabb, kedvezményes áron veheti azt igénybe. Koncepcionálisan ez nagyon hasonlít a Grid rendszerek erőforrás-bróker mechanizmusaihoz.

Egy másik népszerű alternatíva a **spot árazás (spot pricing)**, amely egy dinamikus, aukcióalapú árazási mechanizmus. A spot árazást jellemzően a szolgáltatók az éppen kihasználatlan (idle) erőforrásaik értékesítésére használják. Az akár 80-90%-kal alacsonyabb ár bevonzza azokat a felhasználókat, akik olyan rugalmas, hibatűrő feladatokat futtatnak, amelyeknél nem probléma, ha a szervert a szolgáltató menet közben elveszi tőlük (ha egy jobban fizető on-demand ügyfélnek szüksége van a kapacitásra). Ennek a három alapvető árazási sémának számtalan finomított változata létezik a piacon, amelyeket a későbbi fejezetekben, az adott szolgáltatások tárgyalásakor részletesebben is megvizsgálunk.

### 3.6 Programozás

Mivel a felhőkörnyezetet elsősorban számítási feladatok végrehajtására hozták létre – legyenek azok webalapú alkalmazások, Big Data adatfeldolgozási folyamatok vagy éppen Machine Learning munkafolyamatok –, természetszerűleg felmerül a kérdés: Milyen programozási nyelv vagy nyelvek használhatók felhőalapú alkalmazások fejlesztésére?

Ezen a téren két, egymásnak feszülő követelmény jelentkezik. A felhasználók a lehető legszélesebb felhős erőforrás-környezetben szeretnék futtatni programjaikat. Ideális esetben ez teljes platformfüggetlenséget jelentene. Ugyanakkor szeretnék megtartani és újrahasznosítani a már meglévő (legacy) forráskódjaikat, szoftverkomponenseiket, és elvárják, hogy ezek akár kódmódosítás nélkül, azonnal futtathatók legyenek a felhőben.

Másrészről, a felhőszolgáltatók érdeke az lenne, hogy minél kevesebb, optimális esetben mindössze egy-két programozási nyelvet kelljen csak támogatniuk. Minden egyes újonnan támogatott nyelv megköveteli ugyanis a teljes felhőprogramozási API replikációját az adott nyelvre, ami drasztikusan növeli a saját kódbázisuk méretét, valamint a tesztelési, karbantartási és jövőbeli fejlesztési erőfeszítéseiket.

Ennek az ellentétnek jelenleg az a kompromisszumos feloldása, hogy a nagyobb felhőszolgáltatók igyekeznek a lehető legtöbb populáris nyelvet támogatni SDK-k (Software Development Kit-ek) formájában. A legelterjedtebb, hivatalosan is támogatott nyelvek ma a felhőben a **Java, a Python, a JavaScript (Node.js), a C# és a Go**, de bizonyos szolgáltatóknál számos egyéb nyelv (pl. Ruby, PHP, C++) is elérhető.

---

## 4. Amazon Web Services (AWS)
Az Amazon Web Services (AWS) a világ legnagyobb és piacvezető felhőszolgáltató rendszere. A szolgáltatások rendkívül széles választékát kínálja a felhasználók számára, a dedikált komponensszolgáltatásoktól kezdve a teljes alkalmazásokig, mindezt a legmagasabb szintű rendelkezésre állás (high availability) mellett. Az AWS által kínált szolgáltatáskategóriák teljes listája a hivatalos weboldalán található [13] (ennek egy pillanatképe a 4-1. ábrán látható). Minden egyes kategória számos további, specializált szolgáltatást foglal magában.

![4-1. ábra](<../Cloud Programming_MSc_Juhasz_IId-40_1.png>)

*4-1. ábra: Szolgáltatáskategóriák az Amazon Web Servicesnél*



Az AWS számos különböző iparág számára nyújt célzott megoldásokat (solutions), amelyek jelentősen megkönnyítik a felhőtechnológia bevezetését ezen szektorok szereplői számára. Az alábbi táblázat az egyes iparági szektorokat és az azokra jellemző, illusztratív felhőalapú megoldásokat foglalja össze:

Iparág	Megoldások
Reklám és marketing (Advertising & Marketing)	Megoldások adatanalitikához, személyre szabáshoz, üzenetküldéshez és integrált marketingkampányokhoz.
Autóipar (Automotive)	Megoldások hálózatba kapcsolt járművekhez (connected vehicles), önvezető technológiák fejlesztéséhez, gyártáshoz és ellátásilánc-menedzsmenthez.
Napi fogyasztási cikkek (Consumer Packaged Goods)	Megoldások intelligens gyárakhoz (smart factories), ellátási láncokhoz, adatvezérelt előrejelzéshez (smart forecasting), okosotthonokhoz és intelligens termékekhez.
Oktatás (Education)	Megoldások alap- és középfokú oktatási intézményeknek, egyetemeknek: online és távoktatáshoz, virtuális laborokhoz, videostreaminghez és hallgatói kapcsolatkezeléshez.
Energiaipar (Energy)	Megoldások szeizmikus adatgyűjtéshez, tároláshoz és elemzéshez, tározószimulációhoz, mezőfejlesztési tervezéshez és felszín alatti adatmenedzsmenthez.
Pénzügyi szolgáltatások (Financial Services)	Megoldások bankok, tőkepiaci és biztosítási intézmények számára, beleértve a skálázható tranzakciófeldolgozási infrastruktúrát, az adatanalitikát és a gépi tanulást.
Játékipar (Gaming)	Adatbázis-, számítási, analitikai és gépi tanulási erőforrások játékfejlesztők és online játékszolgáltatók számára.
Közigazgatás és kormányzat (Government)	Kereskedelmi felhőszolgáltatások a közigazgatás számára (a kormányzattól az önkormányzatokig), amelyek minden biztonsági besorolási szinten (Unclassified, Sensitive, Secret, Top Secret) megfelelnek az előírásoknak.
Egészségügy és élettudományok (Healthcare & Life Sciences)	Megoldások egészségügyi szolgáltatóknak és biztosítóknak, a gyógyszer- és biotechnológiai iparnak, valamint a genomikának (skálázható számítás, adattárolás, analitika és gépi tanulás).
Gyártás (Manufacturing)	Megoldások termék- és gyártástervezéshez (párhuzamos szimulációk és adatfeldolgozás), okosgyárakhoz, valamint intelligens termékekhez és szolgáltatásokhoz (IoT és Big Data technológiák).
Média és szórakoztatás (Media & Entertainment)	Megoldások digitális tartalom létrehozásához és terjesztéséhez (videóalkalmazások, „stúdió a felhőben”, biztonságos tartalom-streaming).
Nonprofit szektor (Nonprofit)	Megoldások weboldalakhoz, adománygyűjtő kampányokhoz, IoT-alapú környezeti monitorozáshoz.
Kiskereskedelem (Retail)	Megoldások webáruházakhoz, ügyfélkapcsolat-kezeléshez (CRM), adatanalitikához és gépi tanulással támogatott ajánlórendszerekhez.
Távközlés (Telecommunications)	Megoldások számlázáshoz (billing), tartalomterjesztéshez (CDN) és automatizált ügyfélszolgálathoz.
Utazás és vendéglátás (Travel & Hospitality)	Megoldások a vendégélmény személyre szabásához, az IT-költségek csökkentéséhez és az ügyfélszolgálat minőségének javításához.
Az Amazon ezen szolgáltatásokat a világ legnagyobb felhőinfrastruktúrájára építve nyújtja. Az AWS jelenleg több mint 245 országban érhető el, és 24 földrajzi régióval (Region) rendelkezik (lásd 4-2. ábra). Minden régió több rendelkezésre állási zónát (Availability Zone – AZ) foglal magában, amelyeket alacsony késleltetésű (low latency), nagy sávszélességű és redundáns hálózatok kötnek össze a magas rendelkezésre állás és a hibatűrés (failover) biztosítása érdekében. A zónák fizikailag is elkülönülő, egyedi meghibásodási tartománynak (fault domain) tekintendők.

![4-2. ábra](<../Cloud Programming_MSc_Juhasz_IId-41_1.png>)

*4-2. ábra: Meglévő és tervezett AWS globális régiók*



A következő alfejezetekben a legfontosabb AWS-szolgáltatásokat tekintjük át részletesebben.

### 4.1 IaaS-rétegbeli szolgáltatások
Az AWS infrastruktúrarétegének alapvető szolgáltatásai bármely modern számítógépes rendszer három kulcselemét absztrahálják: a számítási (compute), a tárolási (storage) és a hálózati (network) kapacitásokat.

#### 4.1.1 Számítási (Compute) szolgáltatások
Az Amazon Elastic Compute Cloud (Amazon EC2) az egyik legelsőként bevezetett Amazon-szolgáltatás, amely webalapú szolgáltatásként kínál rugalmasan skálázható virtuális gépeket. Ezek a virtuális gépek (VM) különböző hardvererőforrásokon futtathatók, és az alábbi példánytípus-családok (instance families) valamelyikébe tartoznak: general purpose (általános célú), compute optimized (számításra optimalizált), memory optimized (memóriára optimalizált), storage optimized (tárolásra optimalizált), valamint accelerated computing (hardveres gyorsítókkal, pl. GPU-val vagy FPGA-val szerelt) rendszerek.

Az általános célú (general purpose) példányokat üzletileg kritikus alkalmazásokhoz, kis- és közepes méretű adatbázisokhoz, valamint tipikus webes alkalmazásokhoz tervezték.

A számításra optimalizált (compute optimized) példányok ideálisak nagy teljesítményű számításokhoz (HPC), kötegelt (batch) feldolgozáshoz és videókódoláshoz.

A memóriára optimalizált (memory optimized) gépek nagy teljesítményű, memóriában futó (in-memory) adatbázisok, elosztott gyorsítótárak (cache-ek) és valós idejű Big Data analitika futtatására szolgálnak.

A tárolásra optimalizált (storage optimized) példányok kifejezetten NoSQL adatbázisokhoz, adattárházakhoz (data warehouse) és elosztott fájlrendszerekhez alkalmasak.

Végül az akcelerátor (accelerated computing) példányok a számításigényes gépi tanulási (Machine Learning) feladatok, a nagy grafikai igényű alkalmazások és a tudományos algoritmusok futtatására javasoltak.

Minden példánycsalád több alkategóriát tartalmaz, amelyek az alapul szolgáló hardverplatformot jelölik. Például az AWS általános célú családja olyan osztályokat foglal magában, mint az A1, M4, M5, M5a, M5n, M6g, T2, T3, T3a és T4g. Az A1 osztály az Amazon saját, ARM-alapú 64 bites Graviton processzorait használja; az M4 és M5 osztályok Intel Xeon CPU-kra épülnek; az M5a pedig AMD EPYC processzorokat használ (az M5n az M5-höz képest nagyobb hálózati sávszélességet biztosít).

A T-osztályok (T2–T4) az úgynevezett lökésszerűen terhelhető (burstable) példánytípusok, amelyek nagyon érdekes és költséghatékony használati modellt kínálnak. Ezek a gépek egy alapszintű CPU-teljesítményt nyújtanak, de lökésszerű (burst) terhelés esetén képesek megemelni a teljesítményüket. Amikor a példány kihasználatlan (idle), CPU-krediteket gyűjt (ezzel pénzt takarítva meg a felhasználónak), amelyeket később felhasználhat a kiugró terhelési igények fedezésére. A magok száma, a memória típusa és mérete, valamint a hálózati sávszélesség extrém széles tartományban skálázható: a magok száma 1-től 96 virtuális processzorig (vCPU) terjedhet, a rendszermemória 8 GB-tól egészen 24 TB-ig skálázható, a hálózati sávszélesség pedig 1 és 100 Gbps között mozoghat. A 2. táblázat az általános célú M4-es példánytípus elérhető konfigurációit foglalja össze.

2. táblázat: Általános célú (General Purpose) M4 példánytípus-konfigurációk

Példánytípus	vCPU	Memória (GiB)	Tároló (Storage)	Dedikált EBS sávszélesség (Mbps)	Hálózati teljesítmény
m4.large	2	8	Csak EBS	450	Közepes (Moderate)
m4.xlarge	4	16	Csak EBS	750	Magas (High)
m4.2xlarge	8	32	Csak EBS	1,000	Magas (High)
m4.4xlarge	16	64	Csak EBS	2,000	Magas (High)
m4.10xlarge	40	160	Csak EBS	4,000	10 Gigabit
m4.16xlarge	64	256	Csak EBS	10,000	25 Gigabit
Az EC2 számítási szolgáltatásnak több, specializált változata is létezik. Az Amazon EC2 Auto Scaling szolgáltatás a bejövő forgalom és a kereslet változásainak megfelelően automatikusan képes új számítási kapacitásokat hozzáadni, vagy a feleslegeseket leállítani. Az Amazon EC2 Spot Instances a spot árazási modellt alkalmazza, amellyel a rugalmas, hibatűrő (fault-tolerant) feladatok futtatása esetén akár 90%-os költségmegtakarítás is elérhető az on-demand árakhoz képest. Az AWS Batch szolgáltatás olyan esetekre nyújt megoldást, amikor nagyon sok, párhuzamos számítási feladatot (job) kell kötegelve végrehajtani. A Batch jelentősen leegyszerűsíti ezt a folyamatot, mivel a felhasználónak nem kell előre egy fix méretű klasztert felépítenie és feladatütemező (scheduler) szoftvert telepítenie. A szolgáltatás dinamikus skálázással automatikusan felügyeli és végrehajtja a feladatokat, pontosan annyi erőforrást allokálva, amennyire az aktuális jobnak szüksége van. Ez ideális tudományos számításokhoz (például molekuláris dinamikai szimulációkhoz, genetikai elemzésekhez), valamint a médiaiparban speciális vizuális effektek (VFX) és animációs filmek rendereléséhez.

#### 4.1.2 Tárolási (Storage) szolgáltatások
Az Amazon három fő kategóriában biztosít felhőalapú adattárolási lehetőségeket: ezek az objektum- (object), a fájl- (file) és a blokkalapú (block) tárolási szolgáltatások. A három modell közötti alapvető különbség a tervezett felhasználási módban és az adathozzáférési interfészekben rejlik.

Amazon Simple Storage Service (S3)
Az S3 tárolószolgáltatásban az adatokat objektumokként tárolják logikai tárolókban, az úgynevezett „vödrökben” (bucket). Egyetlen objektum mérete akár az 5 terabájtot is elérheti. A szolgáltatás a háttérben automatikusan skálázza a tárolási erőforrásokat a mindenkori igényeknek megfelelően. Az S3 kiemelkedő, 99,999999999%-os (11 kilences) tartósságra (durability) lett tervezve. Ennek elérése érdekében a rendszer automatikusan több geográfiai helyszínen, különböző eszközökön készít és tárol replikákat az összes S3 objektumról.

Az S3 lehetővé teszi metaadat-címkék (tagek) hozzárendelését az objektumokhoz, robusztus adathozzáférés-vezérlést (Access Control) biztosít a jogosulatlan felhasználókkal szemben, közvetlen Big Data elemzéseket tesz lehetővé, és részletes monitorozást biztosít. Az objektumok hozzáférhetők az S3 Access Pointokon vagy közvetlenül a bucket egyedi hosztnevén keresztül. A szolgáltatás többféle tárolási osztályt (Storage Class) kínál, amelyek eltérnek a hozzáférési idő, a redundancia és az árképzés tekintetében. Ezek az osztályok: S3 Standard, S3 Intelligent-Tiering, S3 Standard-Infrequent Access, S3 One Zone-Infrequent Access, Amazon S3 Glacier, Amazon S3 Glacier Deep Archive és az S3 Outposts. Az S3 egyik leginnovatívabb funkciója az intelligens rétegezés (Intelligent-Tiering), amely a felhasználó beavatkozása nélkül, a hozzáférési mintázatok elemzése alapján automatikusan mozgatja az adatobjektumokat a különböző árkategóriájú tárolási osztályok között (ahogy azt a 4-3. ábra is szemlélteti), így drasztikus költségmegtakarítást eredményezve.

![4-3. ábra](<../Cloud Programming_MSc_Juhasz_IId-43_1.png>)

*4-3. ábra: Intelligens adatrétegezés az AWS S3 szolgáltatásban*



Amazon Elastic File System (EFS)
Az Amazon Elastic File System (EFS) egy hagyományosabb, fájlszintű adattárolási szolgáltatás. Egy rendkívül egyszerű, skálázható, teljes mértékben menedzselt elasztikus NFS (Network File System) fájlrendszert biztosít, amely az AWS felhőszolgáltatásokkal és a helyi (on-premises) vállalati erőforrásokkal egyaránt transzparens módon használható. Az EFS legfőbb erőssége, hogy az alkalmazások futásának megszakítása nélkül képes automatikusan, akár petabájtos méretűre skálázódni. Két tárolási osztály érhető el benne: a Standard és a ritkábban használt adatokhoz optimalizált Infrequent Access (EFS IA). Az életciklus-kezelés (Lifecycle Management) bekapcsolásával a rendszer a ritkábban megnyitott fájlokat automatikusan és észrevétlenül áthelyezi a költséghatékonyabb EFS IA osztályba.

Amazon Elastic Block Store (EBS)
Az Amazon Elastic Block Store (EBS) a nagy sávszélességet (throughput) és intenzív tranzakciókezelést igénylő feladatokhoz készült, mint például a relációs és NoSQL adatbázisok, az ERP (vállalatirányítási) rendszerek, a konténerizált alkalmazások és a Big Data analitikai motorok. Ez egy könnyen használható, nagy teljesítményű blokkalapú tárolószolgáltatás, amelyet kifejezetten az EC2 virtuális gépek operációsrendszer- és adatlemezeként történő felhasználásra terveztek. Az optimális ár-érték arány és a teljesítmény egyensúlyozása érdekében a felhasználók öt különböző kötet-típus (volume type) közül választhatnak: a nagy teljesítményű adatbázisokhoz egyszámjegyű milliszekundumos késleltetést (latency) nyújtó SSD kötetektől egészen a hatalmas, szekvenciális adatmozgatást (pl. Hadoop) igénylő gigabájt/másodperc sávszélességű HDD kötetekig. A kötetek mérete és I/O teljesítménye működés közben, az alkalmazások leállítása nélkül is módosítható (tunable). A kritikus rendszerek támogatása érdekében minden EBS-kötet automatikusan replikálódik az adott Rendelkezésre állási zónán (AZ) belül.

Adatbiztonság
A felhőbe történő migráció során az egyik leggyakoribb aggodalom az adatbiztonság kérdése: Mennyire vannak biztonságban az adataink? Számos szervezet hiába húzna hatalmas hasznot a felhőtechnológiából, a vélt biztonsági kockázatok miatt mégis elzárkózik tőle. (Természetesen léteznek kivételes esetek, például a pénzügyi vagy állami egészségügyi szektorban, ahol a szigorú jogszabályi megfelelőség tiltja az adatok külső szerveren történő tárolását.) Minden más esetben azonban az adatvesztéstől vagy adatszivárgástól való félelem nagyrészt alaptalan.

A modern felhőrendszerekben az adatok alapértelmezés szerint mindig titkosítva vannak. Titkosítás védi őket adatátvitel közben (encryption in transit) és a fizikai tárolóeszközökön egyaránt (encryption at rest). Az Amazon S3 támogatja mind a szerveroldali (három különböző kulcskezelési lehetőséggel), mind a kliensoldali titkosítást. Ez azt jelenti, hogy még egy esetleges adatvédelmi incidens során is csak titkosított, a támadók számára olvashatatlan és használhatatlan adathalmaz kerülne ki. A legtöbb ismert „felhős” adatszivárgás hátterében valójában a felhasználó (az ügyfél) emberi hibája, például egy rosszul konfigurált hozzáférési jogosultság állt. A nagy szolgáltatók (Amazon, Microsoft, Google) a világ legjobb kiberbiztonsági szakértőit foglalkoztatják, és olyan szigorú biztonsági protokollokat alkalmaznak, amelyeket egy hagyományos vállalati (on-premises) infrastruktúrában szinte lehetetlen lenne reprodukálni. A titkosítás mellett az Amazon IAM (Identity and Access Management) rendszere granuláris hozzáférés-vezérlést tesz lehetővé: egy feltöltött adat alapértelmezés szerint csak a létrehozója számára hozzáférhető, a megosztás pedig kizárólag explicit jogosultságadással történhet. Azokhoz a rendszerekhez, amelyek további hálózati izolációt igényelnek, dedikált virtuális magánhálózatok (Virtual Private Cloud – VPC) hozhatók létre.

#### 4.1.3 Hálózati szolgáltatások
A számítási és tárolási szolgáltatások után a harmadik elengedhetetlen infrastrukturális alappillér a hálózat. Felmerülhet a kérdés: Mi olyan különleges a hálózatépítésben, hogy dedikált szolgáltatásként kell megjelennie? Nem csupán egy automatikus összeköttetés a szerverek között?

Meglepő, hogy a modern felhőalkalmazások milyen sokrétű és extrém hálózati követelményeket támasztanak. A felhasználók skálája a családi fotókat mentő magánszemélyektől egészen a teljes globális IT-működésüket a felhőre bízó multinacionális óriásvállalatokig terjed. Ezen komplex igények kiszolgálása érdekében az AWS hálózati szolgáltatások egész arzenálját biztosítja. Ezek a szolgáltatások funkciójuk szerint három fő csoportra bonthatók: hálózatok építését, skálázását, illetve biztonságát támogató eszközökre.

Az Amazon VPC (Virtual Private Cloud) segítségével a felhasználók logikailag elszigetelt, egyedi IP-címtartománnyal és útválasztási (routing) szabályokkal rendelkező privát hálózatokat hozhatnak létre a felhőben. Az AWS Transit Gateway központi elosztóként (hub) szolgál a különböző VPC-k és a vállalat helyi (on-premises) hálózatai közötti forgalom irányításához. Ha az internet teljes megkerülésével, privát – dedikált – fizikai kapcsolatra van szükség a vállalati iroda és a felhő között, az AWS Direct Connect és az AWS PrivateLink nyújt megoldást. Az Amazon Route 53 egy rendkívül megbízható, menedzselt globális DNS-szolgáltatás, amely a végfelhasználókat a leggyorsabb válaszidőt biztosító szerverekhez irányítja. Vállalati szintű, titkosított alagutak kialakítására az AWS Virtual Private Network (VPN) használható.

A hálózatok forgalmi skálázását az Elastic Load Balancing (ELB) végzi, amely a bejövő hálózati terhelést automatikusan és egyenletesen elosztja a rendelkezésre álló EC2 virtuális gépek, konténerek vagy Lambda függvények között. A hálózat védelmét és biztonságát olyan szolgáltatások garantálják, mint az AWS Shield (amely az elosztott túlterheléses, azaz DDoS támadások ellen véd), az AWS WAF (Web Application Firewall, amely a tipikus webalapú alkalmazásszintű sebezhetőségeket szűri), valamint az AWS Firewall Manager, amely lehetővé teszi a tűzfalszabályok központosított kezelését. Ezeknek a szolgáltatásoknak a gyakorlati kombinációját mutatja be a 4-4. ábra.

![4-4. ábra](<../Cloud Programming_MSc_Juhasz_IId-45_1.png>)

*4-4. ábra: Privát és publikus alhálózatok, terheléselosztás és biztonsági szolgáltatások kombinációja*



### 4.2 PaaS-rétegbeli szolgáltatások
Bár az előzőekben bemutatott IaaS infrastrukturális szolgáltatások maximális rugalmasságot nyújtanak a szoftverfejlesztőknek, ennek ára van: ahogy az alkalmazás és annak felhasználói bázisa növekszik, egyre több szolgáltatást kell manuálisan konfigurálni és felügyelni, ami drasztikusan megnöveli a rendszer komplexitását.

A Platform mint Szolgáltatás (PaaS) réteget pontosan ennek a problémának a kiküszöbölésére hozták létre. Itt a mélyebb, infrastrukturális részletek (operációs rendszer foltozása, webszerver-konfiguráció stb.) el vannak rejtve a fejlesztő elől, aki így kizárólag az alkalmazás kódjára koncentrálhat. Az Amazon univerzális PaaS megoldása a felhőalkalmazások futtatására az AWS Elastic Beanstalk.

#### 4.2.1 AWS Elastic Beanstalk
Az AWS Elastic Beanstalk egy rendkívül könnyen használható szolgáltatás webalkalmazások gyors üzembe helyezésére és automatikus skálázására. A platform natívan támogatja a Java, .NET, PHP, Node.js, Python, Ruby, Go és a Docker környezetben fejlesztett alkalmazásokat. Amikor egy fejlesztő feltölt egy alkalmazást (például egy Java `.war` fájlt) az Elastic Beanstalkba, a rendszer automatikusan felépíti a megfelelő futtatókörnyezetet, és lefoglalja a futtatáshoz szükséges AWS-erőforrásokat, például az EC2-példányokat. Az Elastic Beanstalk transzparens módon, a háttérben kezeli a kapacitáselosztás, a terheléselosztás, az automatikus skálázás és az alkalmazásállapot figyelésének minden apró részletét.

Az alkalmazás elindítását követően a felhasználó könnyedén felügyelheti a működést egy átlátható műszerfalon (dashboard). A telepítési és indítási munkafolyamatot a 4-5. ábra szemlélteti (Java alkalmazás esetén például a futtatási környezet egy Apache Tomcat webszerver, amely beépítve támogatja a Java Servleteket).

![4-5. ábra](<../Cloud Programming_MSc_Juhasz_IId-46_1.png>)

*4-5. ábra: Alkalmazás-menedzsment munkafolyamata*



### 4.3 SaaS-rétegbeli szolgáltatások
Bizonyos esetekben egy komplett szoftveres funkcionalitást érdemes kulcsrakész szolgáltatásként kínálni. Ezen a szinten a felhasználóknak egyáltalán nem kell ismerniük sem a rendszer implementációs, sem az üzemeltetési vagy szerverkezelési részleteit; csupán magát a funkciót használják (pl. fájlok feltöltése, e-mailek küldése, videóhívások indítása). Ez a felhő legmagasabb absztrakciós szintje, a Szoftver mint Szolgáltatás (Software-as-a-Service – SaaS).

Az AWS SaaS kínálata a harmadik feles (third-party), AWS-en futó alkalmazások mellett az Amazon saját, vállalati megoldásait is magában foglalja. Ilyen például a dokumentumkezelő WorkDocs, a vállalati levelező WorkMail, az online megbeszéléseket támogató Chime, vagy az adatelemzést vizualizáló QuickSight. Ezeken felül az AWS számos, API-n keresztül hívható SaaS „okoskomponenst” is kínál, amelyekkel a fejlesztők pillanatok alatt mesterséges intelligenciával ruházhatják fel meglévő alkalmazásaikat (pl. a Comprehend a szövegelemzéshez, a Translate a gépi fordításhoz, a Rekognition a kép- és videóelemzéshez, a Polly a beszédszintézishez (Text-to-Speech), a Transcribe pedig a beszédfelismeréshez).

### 4.4 Szolgáltatásvezérlés és API-k
Az AWS szolgáltatásai és alkalmazásai szinte bármilyen modern programozási nyelvből vezérelhetők és programozhatók. Ehhez a szolgáltató hivatalos SDK-kat (Software Development Kit) biztosít. Az AWS jelenleg natív SDK-t kínál többek között a Java, Python, JavaScript (Node.js és böngészős), C#, PHP, Ruby, Go és C++ nyelvekhez.

A legtöbb szolgáltatás emellett a parancssori felületről (Command Line Interface – CLI) is vezérelhető. Az AWS CLI egy egységes, parancssori eszköz, amelyből szinte az összes AWS erőforrás hozzáférhető. A CLI parancsok szkriptesítésével (shell scriptek) a DevOps mérnökök könnyen automatizálhatják a napi rutin- vagy üzemeltetési feladatokat. Néhány alapvető CLI példa az EC2 példányok lekérdezésére, indítására, valamint üzenetek közzétételére:

```bash
$ aws ec2 describe-instances
$ aws ec2 start-instances --instance-ids i-1348636c
$ aws sns publish --topic-arn arn:aws:sns:us-east-1:546419318123:OperationsError --message "Script Failure"
$ aws sqs receive-message --queue-url https://queue.amazonaws.com/546419318123/Test
$ aws help
```

Java SDK
Az AWS Java SDK egy robusztus, átfogó osztálykönyvtárat biztosít az AWS szolgáltatások programozott vezérléséhez (a hivatalos API dokumentáció a https://sdk.amazonaws.com/java/api/latest/ címen érhető el). Érdemes megjegyezni, hogy az AWS Java SDK jelenleg több mint 73 000 Java osztályt és interfészt tartalmaz – ez nagyjából a tízszerese a standard Java SE platform beépített osztályainak! Ez a szám is jól illusztrálja az AWS infrastruktúrájának és szolgáltatási palettájának elképesztő méretét.

A Java SDK hivatalos dokumentációja számtalan kódpéldát tartalmaz, amelyek különböző felhasználási eseteken (use cases) keresztül szemléltetik az integrációt. Az alábbiakban két reprezentatív példát mutatunk be.

Az első kódrészlet bemutatja, hogyan hozható létre és indítható el programozottan egy új Elastic Compute (EC2) virtuális gép példány, és hogyan rendelhetünk hozzá egy metaadat-címkét (Tag):

```java
String name = args[0];       // A példány (instance) neve
String amiId = args[1];      // Az operációs rendszer lemezképének ID-ja (AMI ID)

Region region = Region.US_WEST_2;
Ec2Client ec2 = Ec2Client.builder()
        .region(region)
        .build();

// A futtatási kérés összeállítása
RunInstancesRequest runRequest = RunInstancesRequest.builder()
        .imageId(amiId)
        .instanceType(InstanceType.T1_MICRO)
        .maxCount(1)
        .minCount(1)
        .build();

// A példány létrehozása és indítása
RunInstancesResponse response = ec2.runInstances(runRequest);
String instanceId = response.instances().get(0).instanceId();

// Címke (Tag) létrehozása a példány elnevezéséhez
Tag tag = Tag.builder()
        .key("Name")
        .value(name)
        .build();

CreateTagsRequest tagRequest = CreateTagsRequest.builder()
        .resources(instanceId)
        .tags(tag)
        .build();

try {
    ec2.createTags(tagRequest);
    System.out.printf(
           "Successfully started EC2 Instance %s based on AMI %s\n",
           instanceId, amiId);
} catch (Ec2Exception e) {
    System.err.println(e.awsErrorDetails().errorMessage());
    System.exit(1);
}
```

A második példa azt szemlélteti, hogyan férhetünk hozzá egy már futó EC2 példányhoz (az instanceID ismeretében), és hogyan engedélyezhetjük rajta a részletes teljesítménymonitorozást (CloudWatch Detailed Monitoring):

```java
String instanceId = args[0];

Region region = Region.US_WEST_2;
Ec2Client ec2 = Ec2Client.builder()
        .region(region)
        .build();

MonitorInstancesRequest request = MonitorInstancesRequest.builder()
        .instanceIds(instanceId)
        .build();

ec2.monitorInstances(request);

System.out.printf("Successfully enabled monitoring for instance %s\n",
                    instanceId);
```


---

## 5. Google Cloud Platform
A Google valószínűleg a világ leggyorsabban növekvő felhőszolgáltatója. A Google Cloud Platform (GCP) a szolgáltatások rendkívül széles választékát kínálja: a legalacsonyabb szintű infrastrukturális építőelemektől (IaaS) egészen a legmagasabb absztrakciós szintű, szerver nélküli (serverless) szoftverszolgáltatásokig. A Google Cloud Platform több mint 200 országban elérhető, és a vállalat a világ számos pontján üzemeltet hatalmas adatközpontokat (lásd 5-1. ábra).

![5-1. ábra](<../Cloud Programming_MSc_Juhasz_IId-49_1.png>)

*5-1. ábra: A GCP adatközpontok elhelyezkedése*



A GCP erőforrásai régiókba (Regions) vannak szervezve, amelyek több rendelkezésre állási zónából (Zones) állnak. E könyv írásakor a GCP 24 régióban működik, összesen 73 zónával. A fizikai és virtuális GCP erőforrások hatóköre alapján három típust különböztetünk meg: globális, regionális és zónális erőforrásokat.

A globális hatókörű erőforrások (amelyek bárhonnan elérhetők) közé tartoznak például az előre konfigurált operációsrendszer-lemezképek (images), a lemez-pillanatképek (snapshotok) és a globális hálózatok.

A regionális erőforrások (pl. Central US, Western Europe, East Asia) általában statikus külső IP-címeket tartalmaznak.

A legtöbb erőforrás – például a virtuális gép (VM) példányok és a hozzájuk csatolt lemezek – zónális hatókörű.

A zónák egyedülálló meghibásodási tartományt (fault domain) képviselnek. A zónarendszer használatának számos előnye van. Egyrészt lokalitást biztosít az alkalmazás erőforrásai számára (a szükséges erőforrások sokkal gyorsabban kommunikálnak, ha ugyanabban a zónában vannak, jellemzően <1 ms hálózati késleltetéssel, azaz RTT-vel). Másrészt elszigeteli az erőforrásokat más zónákban fellépő esetleges hardverhibáktól (fokozott megbízhatóság). Több zóna együttes használatával és az alkalmazások replikálásával robusztus redundancia építhető ki, ami jelentősen javítja a szolgáltatás rendelkezésre állását (a felhasználókat a hozzájuk legközelebbi zóna szolgálhatja ki), valamint garantálja a zökkenőmentes katasztrófa utáni helyreállítást (disaster recovery). A zónarendszer és a hozzá tartozó erőforrások grafikus illusztrációja az 5-2. ábrán látható.



![5-2. ábra](<../Cloud Programming_MSc_Juhasz_IId-50_1.png>)

*5-2. ábra: A globális, regionális és zónaszintű erőforrás-koncepció szemléltetése*

A GCP ma már több mint 100 terméket foglal magában; ezek egy reprezentatív részhalmazát az 5-3. ábra mutatja be.

![5-3. ábra](<../Cloud Programming_MSc_Juhasz_IId-50_2.png>)

*5-3. ábra: A Google Cloud Platform termékeinek reprezentatív részhalmaza*

 A kínálatban megtalálhatók az IaaS, PaaS, SaaS szolgáltatások, a Konténer mint Szolgáltatás (CaaS) és a Függvény mint Szolgáltatás (FaaS) megoldások, valamint a fejlesztést, a biztonságot és az üzemeltetést támogató termékek. A fejezet további részében a különböző szolgáltatáskategóriák legfontosabb technológiáit tekintjük át.

### 5.1 GCP szolgáltatások az IaaS rétegben
Az infrastruktúra-szolgáltatások a számítási (compute), az adattárolási (storage) és a hálózati (network) komponenseket foglalják magukban. Az IaaS réteg alapvető szolgáltatása a Compute Engine, amely egy adott hardver- és operációsrendszer-platformon futó virtuális gépet (VM) reprezentál. Ahogy más felhőszolgáltatóknál is, a mögöttes fizikai hardvereket a tervezett felhasználásuk alapján csoportosítják. A GCP esetében ezek a családok a következők: általános célú (General Purpose: E2, N1, N2, N2D), számításra optimalizált (Compute: C2), memóriára optimalizált (Memory: M2) és gyorsítókkal szerelt (Accelerator: A2) gépek.

Az általános célú gépeket elsősorban webszerverek és adatbázis-alkalmazások futtatására szánják, mivel kiváló egyensúlyt biztosítanak az ár és a teljesítmény között.

A nagy teljesítményt igénylő mérnöki szimulációkhoz és játékszerverekhez (gaming) a számításra optimalizált példányokat érdemes választani.

A memóriára optimalizált gépek hatalmas operatív tárral rendelkeznek, így ideálisak Big Data adatelemzéshez és memóriában futó (in-memory) adatbázisokhoz.

Ha pedig olyan mesterséges intelligencia modelleket szeretnénk tanítani, amelyek GPU-kat igényelnek, vagy tömegesen párhuzamosított (massively parallel) HPC feladatokat futtatnánk, a dedikált NVIDIA GPU-kkal kínált Accelerator gépek jelentik a legjobb megoldást.

A magok száma ezekben a virtuális gépekben 1-től egészen 96 vCPU-ig skálázható. A memóriaméret VM-enként akár az 1,4 TB-ot is elérheti. A VM hardveres konfigurációja természetesen közvetlenül befolyásolja az árat. A GCP Compute Engine példányok másodpercalapú, fix áras számlázást használnak a konfigurált vCPU-k és a RAM mérete alapján. A költségek csökkentésére azonban több beépített mechanizmus is létezik. A GCP automatikusan alkalmazza a tartós használati kedvezményt (sustained use discount): ha a rendszer észleli, hogy egy példány az adott hónap jelentős részében folyamatosan fut, a Google automatikusan árengedményt ad. Ha az alkalmazásunk terhelése egyenletes és jól előrejelezhető, élhetünk az elköteleződésen alapuló kedvezménnyel (committed use discount), amely (1 vagy 3 éves szerződés esetén) akár 50%-os megtakarítást is eredményezhet. Végül, ha a futtatott feladat rugalmas és elviseli a megszakításokat (pl. batch adatfeldolgozás), a megszakítható (preemptible) virtuális gépek választása a legjobb döntés, amely akár 80%-os árengedményt is kínál az azonnali (on-demand) árhoz képest.

A GCP Compute Engine további különleges funkciókkal is rendelkezik. Különösen szigorú megfelelőségi követelmények esetén a virtuális gépek egybérlős csomópontokon (sole-tenant nodes) is futtathatók. Ez azt jelenti, hogy az adott fizikai szervert kizárólag a mi VM-jeink használják, más ügyfelek példányaival nem osztozunk a hardveren (mintha csak egy dedikált szerverünk lenne a saját irodánkban). A biztonság fokozásának egy másik módja a Confidential VM-ek használata. Ezek a gépek a Confidential Computing technológiára épülnek, amely lehetővé teszi az adatok titkosítását még számítás (memóriában történő feldolgozás) közben is. A hagyományos felhőrendszerek biztosítják a nyugalmi állapotban lévő adatok titkosítását (encryption at rest) és a hálózati adatátvitel titkosítását (encryption in transit), azonban az adatok a memóriába betöltéskor eddig kénytelenek voltak visszafejtett formában létezni. A Confidential Computing révén ma már a CPU chipen belül, a hardverszintű titkosítás feltörése nélkül végezhetünk műveleteket az adatokon!

Az élő migráció (live migration) funkcióval a GCP képes garantálni, hogy a virtuális gépünk a hardveres rendszerkarbantartások idején is megszakítás nélkül fut tovább. A 24/7-es rendelkezésre állás ugyanis nem azt jelenti, hogy egy fizikai szerver sosem áll le. A rendszerszoftverek frissítéséhez vagy a hardverkomponensek cseréjéhez időről időre újra kell indítani az alapgépeket. Az élő migráció lehetővé teszi, hogy a felhőszolgáltató a futó VM-et a felhasználó beavatkozása (sőt, észlelése) nélkül és adatvesztés nélkül átmozgassa egy másik fizikai csomópontra, ugyanazon a zónán belül.

Az infrastrukturális réteg másik meghatározó pillére az adattárolás. Ezt a GCP-ben egyszerűen Cloud Storage-nak nevezik. A Cloud Storage egy objektumalapú tárolási szolgáltatás, amely korlátlan kapacitást kínál. Világszerte rendkívül alacsony késleltetéssel érhető el, és 99,999999999% (11 kilences) éves tartósságot (durability) garantál. Szigorúbb követelmények esetén bekapcsolható a geo-redundancia, amely révén az adatok két vagy több földrajzi régió között is automatikusan replikálódnak. A Cloud Storage a tervezett felhasználási mintázatok alapján különböző tárolási osztályokat kínál:

Standard Storage: a legjobb választás a gyakran (akár másodpercenként többször) olvasott adatokhoz, például weboldalakhoz, videostreaminghez és mobilalkalmazásokhoz.

Nearline Storage: költséghatékonyabb opció az olyan adatokhoz, amelyekhez várhatóan csak havonta egyszer férnek hozzá (pl. havi biztonsági mentések, ritkábban nézett multimédiás tartalmak).

Coldline Storage: rendkívül alacsony tárolási díjjal rendelkező osztály azokhoz az adatokhoz, amelyekhez évente legfeljebb egyszer férnek hozzá (pl. katasztrófa utáni helyreállításhoz (DR) fenntartott adatbázis-mentések).

Archive Storage: kizárólag a hosszú távú, passzív archiválást szolgálja. Ennek a legalacsonyabb a tárolási költsége, de az adatoknak legalább 365 napig érintetlenül kell maradniuk (pl. jogszabályi megfelelőség miatti kötelező adatmegőrzés).

A GCP hálózati szolgáltatásai lefedik azt a funkcionalitást, amelyet a korábbi, AWS-t bemutató fejezetben már részletesen tárgyaltunk. A Cloud Interconnect segítségével a helyi vállalati hálózatok dedikált fizikai vonalon köthetők össze a Google felhőjével. A Cloud VPN az interneten keresztül biztosít titkosított, virtuális magánhálózati kapcsolatot. A Virtual Private Cloud (VPC) segítségével regionális vagy globális logikai hálózatok hozhatók létre a felhőben. A Cloud Load Balancing gondoskodik a bejövő kérések globális, nagy teljesítményű elosztásáról az erőforrások között, míg a Cloud Armor fejlett védelmet nyújt ezen szolgáltatások számára a túlterheléses (DDoS) és webalapú támadások ellen.

![5-4. ábra](<../Cloud Programming_MSc_Juhasz_IId-52_1.png>)

*5-4. ábra: A Google Cloud Platform globális hálózati összeköttetései*

### 5.2 PaaS-rétegbeli szolgáltatások
A robusztus felhőalkalmazások gyors telepítése és futtatása érdekében – megkímélve a fejlesztőket a hálózat- és szervermenedzsment komplexitásától – a Google is kínál Platform mint Szolgáltatás (PaaS) megoldást, ez pedig a Google App Engine. Az App Engine szinte a teljes erőforrás-kezelést átvállalja a háttérben: gondoskodik az automatikus skálázásról, a biztonsági operációsrendszer-frissítésekről, a terheléselosztásról és a részletes alkalmazásmonitorozásról.

Az App Engine natívan támogatja a Java, Node.js, Python, Go, .NET, PHP és Ruby nyelveken fejlesztett alkalmazások futtatását. Amennyiben egy projekt ettől eltérő technológiát használ, úgynevezett egyedi futásidejű környezetek (például Docker-konténerek) alkalmazására is lehetőség van. Az App Engine alkalmazások zökkenőmentesen integrálódnak a GCP egyéb tárolási megoldásaival, mint a Cloud Storage, a Cloud SQL, a Firestore, de képesek külső, harmadik fél által üzemeltetett adatbázisokhoz is csatlakozni.

### 5.3 SaaS-rétegbeli szolgáltatások
A Google világszerte ismert a felhasználók milliárdjai számára elérhető innovatív szolgáltatásairól. A Gmail, a Google Naptár, a Google Dokumentumok és a Google Térkép maguk is kiváló példái a Szoftver mint Szolgáltatás (SaaS) modellnek. Emellett a Google Cloud Platform számos API-n keresztül elérhető „okoskomponenst” is kínál, amelyeket a fejlesztők építőkockaként építhetnek be saját alkalmazásaikba. Ezek közé tartoznak a gépi látást (Vision), a videóelemzést, a természetes nyelvfeldolgozást, a gépi fordítást és a komplex adatanalitikát biztosító modulok. Ezek közül a könyv későbbi fejezeteiben többet is részletesen megvizsgálunk és használunk majd.

---

## 6. A Google Cloud Platform használata
### 6.1 A GCP-projekt
A Google Cloud Platform szolgáltatásainak használatához a felhasználóknak először létre kell hozniuk egy GCP-fiókot, majd azon belül egy GCP-projektet. A projekt a GCP használatának legalapvetőbb logikai egysége: ez fogja össze egy adott alkalmazáshoz tartozó összes erőforrást, beállítást és hozzáférési jogosultságot, és ez képezi a számlázás (billing) alapját is.

Minden projektnek rendelkeznie kell (i) egy névvel (Project Name), (ii) egy azonosítóval (Project ID), valamint (iii) egy egyedi projektszámmal (Project Number). A projekt legegyszerűbben a GCP Console (a GCP webes alapú grafikus kezelőfelülete) segítségével hozható létre a https://console.cloud.google.com/ címen. A kezdőlap a 6-1. ábrán látható. A felhőkonzol letisztult és intuitív felületet biztosít a projektek és erőforrások kezeléséhez, a rendszer monitorozásához, valamint azonnali hozzáférést nyújt az egyes szolgáltatások részletes dokumentációjához.

![6-1. ábra](<../Cloud Programming_MSc_Juhasz_IId-53_1.png>)

*6-1. ábra: A Google Cloud Platform Console*



### 6.2 A GCP erőforrások elérésének módjai
A webes konzol (GCP Console) csupán az egyik, bár kétségkívül a leglátványosabb módja a szolgáltatások kezelésének. A szakértő DevOps mérnökök és felhőadminisztrátorok számára a legkényelmesebb és leggyorsabb eszköz a gcloud parancssori felület (Command Line Interface – CLI). A gcloud rendszerezett parancsok hierarchiáját biztosítja a különböző szolgáltatások eléréséhez és automatizálásához. Ez az eszköz a lokálisan telepíthető Google Cloud SDK részét képezi. Két egyszerű példa az alábbiakban szemlélteti a használatát:

Az első példa kilistázza a kiválasztott projektben található, az us-central1-a zónában futó összes Compute Engine virtuális gépet:

```bash
gcloud compute instances list --filter="zone:us-central1-a"
```

A parancsban a compute kulcsszó jelzi a hívott IaaS szolgáltatást, az instances list a kért műveletet, míg a --filter kapcsolóval szűkítjük a keresést a megadott zónára.

A következő parancs egy táblázatos formátumban listázza a felhasználóhoz tartozó összes projektet, megjelenítve a projekt nevét, azonosítóját és a létrehozás helyi időzónára (LOCAL) konvertált pontos idejét:

```bash
gcloud projects list \
    --format="table(name, project_id, createTime.date(tz=LOCAL))"
```

Aki nem szeretne lokálisan SDK-t telepíteni, annak a GCP Console egy beépített, azonnal használható parancssort kínál. A jobb felső sarokban található >_ (Aktiválás) ikonra kattintva a böngészőablak alján megnyílik a Google Cloud Shell (lásd 6-2. ábra).

![6-2. ábra](<../Cloud Programming_MSc_Juhasz_IId-54_1.png>)

*6-2. ábra: A Google Cloud Shell használata a GCP Console-ból*

 Ez a funkció a háttérben pillanatok alatt elindít egy ideiglenes Compute Engine virtuális gépet. Ez a VM 5 GB perzisztens tárolót, egy előre telepített és bekonfigurált Google Cloud SDK-t, egy beépített kódszerkesztőt, valamint a legnépszerűbb nyelvek (Java, Go, Python, Node.js, PHP, Ruby és .NET) futtatókörnyezeteit is tartalmazza. Ezenfelül a Cloud Shell automatikusan örökli a bejelentkezett felhasználó hitelesítő adatait, így azonnal hozzáfér a projekt erőforrásaihoz.

Az erőforrások kezelésének harmadik, legprofesszionálisabb módja a programozott hozzáférés (szoftverkódból történő vezérlés). Ezt a feladatot a Google a felhős klienskönyvtárak (Cloud Client Libraries) formájában támogatja. Ezek a fejlesztői csomagok (SDK-k) C#, C++, Java, Node.js, Go, Python, Ruby és PHP nyelvekhez érhetők el, és elegáns, objektumorientált API-t biztosítanak a felhőarchitektúrák automatizálásához.

### 6.3 A Compute Engine programozott használata
Ebben az alfejezetben bemutatjuk, hogyan lehet Compute Engine virtuális gépeket listázni, elindítani és leállítani Java kódból, a Cloud Client Library használatával. (Itt csak a lényeges kódrészleteket közöljük, a teljes, futtatható mintaprogram a hivatalos GitHub-tárolóban érhető el.)

Példányok listázása

```java
Page<Instance> instancePage;

// A Compute szolgáltatás kliensének inicializálása
Compute compute = ComputeOptions.getDefaultInstance().getService();

System.out.println("Listing VM instances ...");

// Virtuális gépek lekérése
instancePage = compute.listInstances();
System.out.printf("Instances:\n");

Iterator<Instance> iterator = instancePage.iterateAll();
while (iterator.hasNext()) {
    Instance instance = iterator.next();
    System.out.printf("Instance: %s\n", instance.getInstanceId().getInstance());
    System.out.printf("Data instance:\n%s\n\n", instance);
}
```

Példány indítása

```java
// Kliens inicializálása
Compute compute = ComputeOptions.getDefaultInstance().getService();
System.out.println("Starting VM instance ...");

// A kiválasztott példány elindítása
Operation operation = compute.start(instanceId);
if (operation == null) {
    System.out.printf("Error: Instance \"%s\" does NOT exist.\n", instanceId);
    return;
}

// Várakozás a művelet (operation) befejeződésére
try {
    operation = operation.waitFor();
} catch (InterruptedException e) {
    e.printStackTrace();
} catch (TimeoutException e) {
    e.printStackTrace();
}
```

Példány leállítása

```java
// Kliens inicializálása
Compute compute = ComputeOptions.getDefaultInstance().getService();
System.out.println("Stopping VM instance ...");

// A kiválasztott példány leállítása
Operation operation = compute.stop(instanceId);
if (operation == null) {
   System.out.printf("Error: Instance \"%s\" does NOT exist.\n", instanceId);
   return;
}

// Várakozás a leállítás befejeződésére
try {
    operation = operation.waitFor();
} catch (InterruptedException e) {
    e.printStackTrace();
} catch (TimeoutException e) {
    e.printStackTrace();
}
```

### 6.4 A Cloud Storage programozott használata
A Google Cloud Platform használatát bemutató fejezetet két olyan kódrészlettel zárjuk, amelyek a Google Cloud Storage objektumtároló API-szintű vezérlését szemléltetik. Az első példa egy új tárolóvödör létrehozását, míg a második az elérhető tárolóvödrök listázását mutatja be.

Új tárolóvödör létrehozása

```java
import com.google.cloud.storage.Bucket;
import com.google.cloud.storage.BucketInfo;
import com.google.cloud.storage.Storage;
import com.google.cloud.storage.StorageClass;
import com.google.cloud.storage.StorageOptions;

public class CreateBucketWithStorageClassAndLocation {
  public static void createBucketWithStorageClassAndLocation(
            String projectId, String bucketName) {
    
    // A GCP projektünk azonosítója (ID)
    // String projectId = "your-project-id";

    // A létrehozni kívánt globálisan egyedi GCS bucket név
    // String bucketName = "your-unique-bucket-name";

    Storage storage = StorageOptions.newBuilder().setProjectId(projectId)
            .build().getService();

    // A tárolási osztály (Storage Class) megadása
    StorageClass storageClass = StorageClass.COLDLINE;

    // A földrajzi elhelyezkedés (Location) megadása
    String location = "ASIA";

    Bucket bucket =
        storage.create(
            BucketInfo.newBuilder(bucketName)
                .setStorageClass(storageClass)
                .setLocation(location)
                .build());

    System.out.println(
        "Created bucket "
            + bucket.getName()
            + " in "
            + bucket.getLocation()
            + " with storage class "
            + bucket.getStorageClass());
  }
}
```

Létező tárolóvödrök listázása

```java
import com.google.api.gax.paging.Page;
import com.google.cloud.storage.Bucket;
import com.google.cloud.storage.Storage;
import com.google.cloud.storage.StorageOptions;

public class ListBuckets {
  public static void listBuckets(String projectId) {
    
    // A GCP projektünk azonosítója (ID)
    // String projectId = "your-project-id";

    Storage storage = StorageOptions.newBuilder().setProjectId(projectId)
            .build().getService();
    Page<Bucket> buckets = storage.list();

    for (Bucket bucket : buckets.iterateAll()) {
      System.out.println(bucket.getName());
    }
  }
}
```


---

## 7. Nagyléptékű feladat-végrehajtás a felhőben
Ahogy azt a korábbiakban már tárgyaltuk, a felhő a szervezetek skálázható és nagyléptékű adatfeldolgozási igényeire adott válaszként jelent meg. A központi kérdés az, hogy miként hajthatók végre ezek a nagyléptékű számítások a felhőben. Bár egyetlen virtuális gép (VM) példány létrehozása és elindítása viszonylag egyszerű feladat, hogyan birkózzunk meg több száz vagy ezer ilyen példány egyidejű kezelésével? Továbbá magukat a számítási feladatokat (jobokat) is menedzselni kell. A feladatokat hozzá kell rendelni a VM-példányokhoz, el kell indítani őket, folyamatosan monitorozni kell az esetleges hibákat, és meghibásodás esetén gondoskodni kell az újraindításukról. A megfelelő mögöttes számítási infrastruktúra kiépítésének és a nagyszámú feladat végrehajtásának teljes folyamata könnyen ijesztő, komplex kihívássá válhat. Nem meglepő, hogy ezen folyamatok egyszerűsítésére számos szoftverkeretrendszert (software frameworköt) fejlesztettek ki.

### 7.1 A Big Data megjelenése
A nagy számítási kapacitású létesítményeket eredetileg nagyléptékű (tudományos és mérnöki) számítási problémák megoldására használták. Az elmúlt évtizedben azonban globális társadalmunk teljes digitális transzformációjának lehettünk tanúi. Az analóg adattárolás (papíralapú dokumentumok, mágneses audio- és videoszalagok, bakelitlemezek stb.) korszaka véget ért. A digitális adatgenerálás és -tárolás mára uralkodóvá vált. Hatalmas mennyiségű vállalati és nyilvános adat keletkezik folyamatosan. A dokumentumokat már digitális formátumban hozzák létre és tárolják (lásd 7-1. ábra).

![7-1. ábra](<../Cloud Programming_MSc_Juhasz_IId-58_1.png>)

*7-1. ábra: Az adatelőállítás és -tárolás analóg-digitális átalakulása az elmúlt évtizedekben*

 A legkülönfélébb adatok – a gyártástól kezdve a közigazgatásig – minden percben arra várnak, hogy feldolgozzák őket.

A digitális adatforradalom egyik legfontosabb jellemzője, hogy az adatok általában nyers formátumban keletkeznek és tárolódnak. Információt kinyerni ebből az adathalmazból csak számítógépes adatfeldolgozással lehet; az információ mintegy „be van ágyazva” az adatokba. A feldolgozás skálája a hagyományos adatbázis-rendszerek egyszerű lekérdezéseitől a komplex jellemzőkinyerésig (feature extraction) és adatelemzésig terjedhet, ez utóbbi magában foglalja a mesterséges intelligencia (AI) által támogatott megközelítéseket is az adatokban rejlő új mintázatok és trendek felfedezésére. Ezt az új, nagyléptékű adatfeldolgozási technológiát nevezzük Big Data technológiának, illetve Big Data adatfeldolgozásnak.

Egy precízebb definíció szerint egy rendszert akkor tekintünk Big Data rendszernek, ha:

olyan hatalmas adathalmazokból (datasetekből) áll, amelyek kezelésére a tipikus, hagyományos rendszerek képtelenek, és

új feldolgozási módszereket igényel, hogy ekkora adatmennyiséggel időben meg tudjon birkózni.

A Big Data rendszereket gyakran a „3V” modellel is jellemezzük, amely a következő három kulcsszón alapul:

Mennyiség (Volume): az adatméret nagyságrendekkel nagyobb, mint a hagyományos rendszerekben.

Sebesség (Velocity): az információ mozgásának és feldolgozásának sebessége a rendszerben lényegesen magasabb.

Változatosság (Variety): az adatok rendkívül széles spektrumú forrásokból származnak, minőségük és típusuk is nagyon eltérő.

A Big Data rendszerek természetes következménye a nagyléptékű számítási platformok iránti igény, ami – a fent tárgyalt digitális adatrobbanás miatt – azt jelenti, hogy ezek a platformok elsősorban adatfeldolgozási, -transzformációs és -elemzési feladatokat hajtanak végre. Úgy tűnik, a nagyméretű rendszerek többé már nem kizárólag a numerikus szimulációkat futtató tudósok eszközei.

Fontos megjegyezni, hogy a Big Data adatfeldolgozás sok szempontból különbözik a hagyományos nagy teljesítményű számítástechnikától (HPC). A HPC területén az alkalmazások többsége egyedi, speciális algoritmusokon alapul, amelyeket egy konkrét tudományos probléma gyors megoldására optimalizáltak. A Big Data feldolgozás ettől eltér, mivel ott a folyamat egy meglehetősen standard lépéssorozatot követ. Nevezzük ezt a Big Data feldolgozás életciklusának:

Adatgyűjtés (Ingest / Collect): ez a szakasz magában foglalja az adatok kinyerését, rendezését, címkézését és transzformációját.

Adatok tartós tárolása (Persist): hosszú távú tárolás, amely elosztott fájlrendszert vagy adatbázist igényel.

Feldolgozás és elemzés (Process and analyse): kötegelt (batch) vagy valós idejű feldolgozás, beleértve a lekérdezéseket, valamint a statisztikai és adatelemző algoritmusokat.

Eredmények vizualizálása (Visualise results): trendek, változások észlelése, adatalapú betekintések (insights) nyújtása.

### 7.2 Adatfeldolgozó szoftverkeretrendszerek
A múltban a nagyléptékű adatfeldolgozó alkalmazásokat hatalmas számítási klasztereken (compute clusters) hajtották végre. A felhőtechnológia megjelenésével e rendszerek közül sok migrált a felhőbe olyan adatfeldolgozó keretrendszerek (frameworkök) formájában, amelyek leegyszerűsítik ezen alkalmazások komplex végrehajtási és erőforrás-menedzsment lépéseit.

Ebben a fejezetben áttekintjük és összehasonlítjuk a legnépszerűbb felhős adatfeldolgozó keretrendszereket funkcionalitásuk, képességeik és hatékonyságuk alapján. A következő szoftvercsomagokat vizsgáljuk meg: Apache Hadoop, Apache Spark, Storm, Kafka, Flink, Beam. Szándékosan a nyílt forráskódú (open-source) keretrendszerekre fókuszálunk, mivel a felhőben a szállítói függőség (vendor lock-in) különösen veszélyes. Ha egy felhasználó olyan szolgáltatásra vagy keretrendszerre támaszkodik, amely kizárólag egyetlen felhőszolgáltatónál érhető el, a szolgáltatóváltás lehetősége a jövőben gyakorlatilag lehetetlenné válik.

Mielőtt azonban belevágnánk a keretrendszerek áttekintésébe, tisztáznunk kell egy alapvető koncepciót, a kötegelt (batch) és az adatfolyam- (stream) orientált adatfeldolgozás közötti különbséget, mivel ez kulcsfontosságú lesz a keretrendszerek megértéséhez.



![7-2. ábra](<../Cloud Programming_MSc_Juhasz_IId-60_1.png>)

*7-2. ábra: A stream-feldolgozás koncepciója ismeretlen méretű adathalmazon*

#### 7.2.1 Kötegelt (batch) és adatfolyam- (stream) feldolgozás
A hagyományos adatfeldolgozás az alábbiak szerint zajlik. A bemeneti (input) adatok több fájlban vagy egy adatbázisrendszerben vannak tárolva. Elindul egy program, amely beolvassa a teljes adathalmazt a memóriába, elvégzi a szükséges számításokat, majd – az eredmények elkészültével – elmenti azokat egy kimeneti (output) fájlba vagy adatbázisba. Ennek a végrehajtási modellnek a legfőbb jellemzője, hogy a bemeneti adat véges (bounded), statikus és perzisztens; a program hozzáfér a teljes adathalmazhoz, és a végrehajtás szakaszos (adatbemenet -> adatfeldolgozás -> adatkimenet). Ezt a végrehajtási stílust kötegelt (batch) feldolgozásnak nevezzük.

Vannak azonban olyan helyzetek, amikor a batch modell nem alkalmazható vagy nem praktikus. Számos modern alkalmazásban az adatok valós időben keletkeznek. Ilyenek például az élő médiaközvetítések, az IoT-rendszerek (közlekedési adatok, gyártási naplók), vagy a biztonsági rendszerek adatai. Ezekben az alkalmazásokban nem várhatjuk meg, amíg a teljes bemeneti adathalmaz rendelkezésre áll. Egy folyamatos, valós idejű adatfolyam ugyanis sosem ér véget! Az alternatíva az, hogy kis adatdarabokat (chunkokat) vagy rekordokat dolgozunk fel abban a pillanatban, ahogy azok elérhetővé válnak.

Amellett, hogy így a rendszerünk képes megbirkózni az élő adatokkal, ennek más előnyei is vannak. Mivel egyszerre csak az adathalmaz egy nagyon kis része van a memóriában, ezen alkalmazások erőforrás-igénye sokkal alacsonyabb. Ha az adatokat rekordonként dolgozzuk fel, a rendszer válaszideje (latency) és reaktivitása drasztikusan javul. Következésképpen ez az adatfeldolgozási mód, amelyet adatfolyam- (stream) feldolgozásnak nevezünk, még akkor is előnyös a teljesítmény javítása érdekében, ha egyébként a teljes adathalmaz már rendelkezésre állna a batch feldolgozáshoz.

#### 7.2.2 Apache Hadoop / MapReduce
A Hadoop/MapReduce keretrendszer egy nyílt forráskódú Apache projekt, amelyet eredetileg a Yahoo fejlesztett ki nagyléptékű webes keresőadatok indexelésére a Google által közzétett Map-Reduce programozási modell alapján. A mögöttes infrastruktúra egy nagyméretű, kereskedelemben kapható szerverekből (commodity servers) álló klaszter. Ezen fut a Hadoop, egy Java nyelven írt szoftverrendszer, amely hibatűrő és platformfüggetlen futtatási környezetet biztosít.
A rendszer a következő főbb komponensekből áll:

HDFS (Hadoop Distributed File System): a Hadoop elosztott fájlrendszere.

YARN: egy klaszterkoordinátor és erőforrás-ütemező.

MapReduce: a batch feldolgozó motor.

Hadoop Common: közös segédprogramok (utilities) készlete.

A Hadoop/MapReduce filozófiája az, hogy a nagy adatfeldolgozási feladatokat párhuzamosan kell végrehajtani. A bemeneti adatokat kisebb darabokra osztják, amelyeket különböző szerverekhez rendelnek egyidejű végrehajtásra (ez a „Map” fázis), majd a részeredményeket összegyűjtik, hogy kialakítsák a végső eredményt (ez a „Reduce” fázis). A bemeneti adatokat egy nagy, hibatűrő elosztott fájlrendszerben tárolják.

A Hadoop abból a feltételezésből építkezik, hogy egy elosztott rendszerben a meghibásodás nem kivétel, hanem a norma. A rendszer biztosítja az alkalmazásszintű hibatűrést. Számítási (compute) és tárolási (storage) csomópontokból áll; ezek a csomópontok általában ugyanazok a fizikai gépek, ami lehetővé teszi a feladatok végrehajtását ott, ahol az adat fizikailag is található, minimalizálva a hálózati adatmozgatást.

A feladatokat a YARN motor irányítja, amely egyetlen központi vezérlőből (ResourceManager), klaszter-csomópontonként egy munkavégzőből (NodeManager), valamint alkalmazásonként egy MRAppMaster-ből áll.



![7-3. ábra](<../Cloud Programming_MSc_Juhasz_IId-62_1.png>)

*7-3. ábra: A Hadoop architektúrája és job-végrehajtási mechanizmusa*

Egy MapReduce alkalmazás szerkezete egyszerű. A végrehajtási modell a következő:

Adathalmaz beolvasása a fájlrendszerből.

Az adatok felosztása darabokra (kulcs-érték / key-value párokra).

A számítás alkalmazása a részhalmazokra különböző csomópontokon (Map fázis).

Az egyes kulcsokhoz tartozó értékek redukálása (összevonása) egyetlen értékké (Reduce fázis).

Az eredmény fájlrendszerbe mentése.

Ennek a megvalósításához a programozónak a Mapper és Reducer interfészeket kell implementálnia a program különböző szakaszaihoz:
(input) <k1,v1> -> map -> <k2,v2> -> combine -> <k2,v2> -> reduce -> <k3,v3> (output)

A végrehajtás könnyebb megértése érdekében egy egyszerű programmal illusztráljuk a működést. A példa egy egyszerű Word Count alkalmazás, amely egy adott bemeneti halmazban megszámolja az egyes szavak előfordulásainak számát. A példa két osztállyal valósítja meg a szükséges funkcionalitást: a `TokenizerMapper` osztály implementálja a Mapper interfészt, a bemeneti fájlt szavakra bontja, és minden szóra egy `<<word>, 1>` párt bocsát ki. Az `IntSumReducer` osztály a Reducer interfészt valósítja meg, és egy adott szöveges kulcshoz tartozó értékek összegét számítja ki; ezt az osztályt egyszerre használjuk lokális (csomópont-szintű) combinerként és globális (rendszerszintű) reducerként is. A program `main()` metódusa konfigurálja a jobot (job configuration, JAR fájl, mapper, combiner és reducer osztályok, valamint a kimeneti Key és Value osztályok és a be-/kimeneti útvonalak beállítása), majd a `waitForCompletion()` metódus hívásával indítja el a végrehajtást.

```java
import java.io.IOException;
import java.util.StringTokenizer;
import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.fs.Path;
import org.apache.hadoop.io.IntWritable;
import org.apache.hadoop.io.Text;
import org.apache.hadoop.mapreduce.Job;
import org.apache.hadoop.mapreduce.Mapper;
import org.apache.hadoop.mapreduce.Reducer;
import org.apache.hadoop.mapreduce.lib.input.FileInputFormat;
import org.apache.hadoop.mapreduce.lib.output.FileOutputFormat;

public class WordCount {

  public static class TokenizerMapper extends Mapper<Object, Text, Text, IntWritable>{

    private final static IntWritable one = new IntWritable(1);
    private Text word = new Text();

    public void map(Object key, Text value, Context context) throws IOException,
                          InterruptedException {
      StringTokenizer itr = new StringTokenizer(value.toString());
      while (itr.hasMoreTokens()) {
        word.set(itr.nextToken());
        context.write(word, one);
      }
    }
  }

  public static class IntSumReducer extends Reducer<Text,IntWritable,Text,IntWritable> {
    private IntWritable result = new IntWritable();

    public void reduce(Text key, Iterable<IntWritable> values, Context context) throws
                          IOException, InterruptedException {
      int sum = 0;
      for (IntWritable val : values) {
        sum += val.get();
      }
      result.set(sum);
      context.write(key, result);
    }
  }

  public static void main(String[] args) throws Exception {
    Configuration conf = new Configuration();
    Job job = Job.getInstance(conf, "word count");
    job.setJarByClass(WordCount.class);
    job.setMapperClass(TokenizerMapper.class);
    job.setCombinerClass(IntSumReducer.class);
    job.setReducerClass(IntSumReducer.class);
    job.setOutputKeyClass(Text.class);
    job.setOutputValueClass(IntWritable.class);
    FileInputFormat.addInputPath(job, new Path(args[0]));
    FileOutputFormat.setOutputPath(job, new Path(args[1]));
    System.exit(job.waitForCompletion(true) ? 0 : 1);
  }
}
```



![7-4. ábra](<../Cloud Programming_MSc_Juhasz_IId-63_1.png>)

*7-4. ábra: A WordCount példaprogram végrehajtásának fázisai*

#### 7.2.3 Apache Spark
Bár az Apache Hadoop nagyon sikeres lett és évtizedekig iparági szabványként uralta a piacot, számos területen hátrányokkal is küzd. A legfőbb hátránya a Hadoopnak a feldolgozási sebessége. Mint minden elosztott rendszerben, a teljesítmény legszűkebb keresztmetszete az I/O műveletekben (a lemezhez és a hálózathoz való hozzáférésben) rejlik. A Hadoop rendkívül megbízható a hibatűrési mechanizmusai miatt, ami viszont jelentős I/O terheléssel jár: minden köztes adatot, minden Map folyamat után perzisztensen lemezre (a fájlrendszerbe) ment. Ennek a túlzott lemezhasználatnak az eredményeként a komplex adatfeldolgozási feladatok futásideje a Hadoopon nagyon hosszú is lehet.

Egy alternatív nyílt forráskódú keretrendszer az Apache Spark [15], amely kifejezetten a MapReduce modell hibáinak kiküszöbölésére fókuszál. A Spark egy gyors, memóriában futó (in-memory) adatfeldolgozó motor. Amíg a memória elegendő méretű, minden köztes adat a memóriában marad. A Spark csak akkor nyúl a lassú lemezes I/O műveletekhez, ha a feldolgozott adatméret meghaladja a rendelkezésre álló memóriát. A tisztán memóriabeli adatfeldolgozás révén a Spark akár 100-szor is gyorsabb lehet, mint a Hadoop!



![7-5. ábra](<../Cloud Programming_MSc_Juhasz_IId-65_1.png>)

![7-5. ábra](<../Cloud Programming_MSc_Juhasz_IId-65_2.png>)

*7-5. ábra: A Spark gazdag támogatása harmadik féltől származó alkalmazásokhoz*

A sebesség mellett a Spark egyéb előnyökkel is rendelkezik. Több programozási nyelvhez (például Java, Scala, Python, R) biztosít API-kat, és gazdagabb funkcionalitást kínál a puszta „Map” és „Reduce” lépéseknél: támogatja az SQL lekérdezéseket, a gépi tanulást (Machine Learning) és a gráfelemzési (Graph Analytics) műveleteket, valamint az adatfolyam-feldolgozási (streaming) képességeket is.

A Spark a következő végrehajtási módokat kínálja:

Standalone (önálló) mód: független klaszteralapú környezetként fut.

Hadoop mód: a Hadoop YARN klaszterkezelő rendszerén fut.

Spark MapReduce módban: a Spark jobok Hadoop/MapReduce jobokként hajtódnak végre (a régebbi MapReduce programok integrációját segítve).

A Spark bevezette a Rugalmas Elosztott Adathalmaz (Resilient Distributed Dataset – RDD) fogalmát, amely a Spark belső adatábrázolási struktúrája. Ez az elosztott adatstruktúra teszi lehetővé a Spark számára, hogy a műveleteket párhuzamosan, nagy hatékonysággal hajtsa végre a különböző csomópontokon, a fájlrendszert pedig csak a program elején és legvégén érintse. Ezzel szemben, amint az a 7-7. ábrán látható, a Spark a köztes adatok kezelésére az elosztott memóriát (RDD) használja.



![7-6. ábra](<../Cloud Programming_MSc_Juhasz_IId-65_2.png>)

*7-6. ábra: Köztes adatkommunikáció Hadoop/MapReduce esetén*



![7-7. ábra](<../Cloud Programming_MSc_Juhasz_IId-66_1.png>)

*7-7. ábra: Köztes adatkommunikáció Sparkban*

Mint korábban, most is a Word Count példaprogramot mutatjuk be, ezúttal azonban Spark Java implementációban. A kód a program főbb lépéseit illusztrálja: először egy Spark session (SparkSession) jön létre, amelyen keresztül a bemenet elérhető és a program leállítható. A bemenetet a Spark belső adatábrázolási struktúrájává, Rugalmas Elosztott Adathalmazzá (Resilient Distributed Dataset, RDD) alakítja, amely lehetővé teszi a műveletek párhuzamos végrehajtását a különböző csomópontokon. A szavak listájának előállítása után a `map` lépés kulcs-érték párokat hoz létre az `ones` adatstruktúrában, majd a `reduceByKey` művelet elvégzi a redukciót, az eredmény pedig a `counts` adatstruktúrába kerül. Végül a `counts` egy listává alakul, és az eredmények a konzolra íródnak. A köztes adatok végig az elosztott memóriában (RDD) maradnak, a fájlrendszer csak a program elején és legvégén kerül elérésre.

```java
package org.apache.spark.examples;

import scala.Tuple2;
import org.apache.spark.api.java.JavaPairRDD;
import org.apache.spark.api.java.JavaRDD;
import org.apache.spark.sql.SparkSession;
import java.util.Arrays;
import java.util.List;
import java.util.regex.Pattern;

public final class JavaWordCount {
  private static final Pattern SPACE = Pattern.compile(" ");

  public static void main(String[] args) throws Exception {

    if (args.length < 1) {
      System.err.println("Usage: JavaWordCount <file>");
      System.exit(1);
    }

    SparkSession spark = SparkSession
      .builder()
      .appName("JavaWordCount")
      .getOrCreate();

    JavaRDD<String> lines = spark.read().textFile(args[0]).javaRDD();

    JavaRDD<String> words = lines.flatMap(s -> Arrays.asList(SPACE.split(s))
                                    .iterator() );

    JavaPairRDD<String, Integer> ones = words.mapToPair(s -> new Tuple2<>(s, 1));
    JavaPairRDD<String, Integer> counts = ones.reduceByKey((i1, i2) -> i1 + i2);

    List<Tuple2<String, Integer>> output = counts.collect();
    for (Tuple2<?,?> tuple : output) {
      System.out.println(tuple._1() + ": " + tuple._2());
    }
    spark.stop();
  }
}
```

### 7.3 MapReduce és Spark feladatok futtatása GCP-n
Ahhoz, hogy a korábban bemutatott adatfeldolgozó programok megfelelően működjenek, a fejlesztőknek gondoskodniuk kell egy előre telepített és bekonfigurált Hadoop vagy Spark keretrendszert futtató szerverklaszterről. Ezt megtehetik saját (on-premises) erőforrásokon, vagy bérelhetnek megfelelő számú IaaS virtuális gépet a felhőben.

A Google Cloud Platform azonban ennél egy sokkal elegánsabb és magasabb szintű megoldást kínál: a Cloud Dataproc szolgáltatást. A Dataproc egy teljesen felügyelt (managed) felhőszolgáltatás, amellyel Apache Hadoop, Spark, Flink, és egyéb nyílt forráskódú adatfeldolgozó keretrendszerek futtathatók. A felhasználóknak csupán a kívánt keretrendszert és a futtatáshoz szükséges gépek paramétereit kell megadniuk, és a Dataproc percek (sokszor másodpercek) alatt automatikusan létrehozza a klasztert, feltelepíti a megfelelő szoftvereket, és a job lefutása után – amennyiben be van állítva – automatikusan le is állítja az erőforrásokat, minimalizálva ezzel a költségeket.



![7-8. ábra](<../Cloud Programming_MSc_Juhasz_IId-67_1.png>)

*7-8. ábra: A Dataproc szolgáltatás és lehetséges kapcsolatai más szolgáltatásokhoz*

#### 7.3.1 MapReduce feladatok futtatása GCP-n
Egy Hadoop klaszter létrehozása és egy feladat elindítása a Google Cloud Shell-ből a következő pofonegyszerű gcloud parancsokkal végezhető el:

```bash
> gcloud dataproc clusters create hadoop-cluster --region europe-west4
> gcloud dataproc jobs submit hadoop --cluster hadoop-cluster \
    --jar gs://test-bucket22/WordCount.jar \
    wordcount.WordCount gs://test-bucket22/words.txt gs://test-bucket22/results
```

#### 7.3.2 Spark feladatok futtatása GCP-n
A folyamat a Spark esetében szinte teljesen megegyezik. Először létrehozunk egy Spark klasztert, majd beküldjük a Spark jobot:

```bash
> gcloud dataproc clusters create spark-cluster --region europe-west4
> gcloud dataproc jobs submit spark --cluster spark-cluster \
    --jar gs://test-bucket22/WordCountSpark.jar -- \
    wordcount.WordCount gs://test-bucket22/words.txt gs://test-bucket22/results
```

Mindkét esetben a program kimenete a megadott felhős tárolóvödörben (gs://test-bucket22/results) jelenik meg. A végrehajtási naplók (logok) és a klaszter metrikái pedig könnyedén nyomon követhetők a Cloud Console Dataproc és Stackdriver (Operations) felületein, amint azt a 7-9. ábra is mutatja.

![7-9. ábra](<../Cloud Programming_MSc_Juhasz_IId-69_1.png>)

*7-9. ábra: Példa a Hadoop-klaszter monitorozó ablakára*



---

## 8. Adatfolyam-feldolgozás (Data Stream Processing)
Ahogy a 7.2.1. alfejezetben már említettük, nem minden adatfeldolgozási feladat végezhető el a hagyományos kötegelt (batch) végrehajtási stílusban. A folyamatos adatfolyamok (data streams) – mint például a valós idejű mérési vagy monitorozási adatok – nem dolgozhatók fel a hagyományos bemenet–feldolgozás–kimenet (input-process-output) paradigmával. Ilyen esetekben az adatfolyam-feldolgozás (stream processing) és a stream-algoritmusok nyújtanak megoldást. Amellett, hogy végrehajtási mechanizmust biztosít az ilyen jellegű feladatokra, a stream-feldolgozás javíthatja a rendszer teljesítményét (csökkenti a késleltetést, azaz a latency-t), és mérsékli az erőforrás-fogyasztást (kevesebb memóriát igényel, mivel a feldolgozás során egyszerre csak az adatok egy nagyon kis része van a memóriában).

Ebben a fejezetben röviden áttekintjük az adatfolyam-feldolgozás legfőbb jellemzőit, majd bemutatjuk és összehasonlítjuk a legnépszerűbb stream-adatfeldolgozó szoftverkeretrendszereket. A fejezetet a Beam keretrendszer és annak Google Cloud Platformon (GCP Dataflow) történő használatának bemutatásával zárjuk.

*8-1. ábra: Egy négy fázisból álló általános stream-feldolgozó rendszer. (Az ábra az eredeti PDF-ben vektorgrafikusan került beágyazásra, ezért külön képfájlként nem elérhető.)*


### 8.1 Stream algoritmusok

Az adatfolyam-feldolgozás legfontosabb megkülönböztető jegye a hagyományos, kötegelt (batch) feldolgozáshoz képest a folyamatos, korlátlan (unbound) bejövő adatfolyam. Az algoritmusoknak úgy kell feldolgozniuk az elemeket, ahogy azok érkeznek – anélkül, hogy a teljes, lezárt bemeneti adathalmaz rendelkezésre állna.

Egy egyszerű statisztikai számítási feladat jól megvilágítja ezt a különbséget. Tegyük fel, hogy $N$ darab $x_i,\ i = 1, \ldots, N$ mintának kívánjuk kiszámítani a varianciáját. A variancia a közismert képlettel definiált:

$$Var(X) = \frac{1}{n}\sum_{i=1}^{n} (x_i - \mu)^2$$

ahol $\mu$ az $x_i$ minták számtani átlaga (várható értéke):

$$\mu = \frac{1}{n}\sum_{i=1}^{n} x_i$$

Ha a teljes adathalmaz a rendelkezésünkre áll – tehát mind az $N$ elem memóriában vagy egy bemeneti fájlban elérhető –, a megvalósítás egyik kézenfekvő módja a kétmenetes (two-pass) algoritmus. Az első menetben kiszámítjuk az átlagot, a másodikban pedig a kapott átlag felhasználásával a varianciát. A Java-beli megvalósítás a következő:

```java
double varianceTwoPass(double[] data){

    // first pass: calculate mean
    double mean = 0;
    for (int i = 0; i < data.length; i++) {
        mean += data[i];
    }
    mean /= data.length;

    // second pass: calculate sample variance
    double variance = 0.0;
    for (int i = 0; i < data.length; i++) {
        variance += (data[i]-mean)*(data[i]-mean);
    }
    return variance/data.length;
}
```

Csábító lehet a két menetet egyetlen ciklusba összevonni az alábbi, algebrailag átalakított alakot használva:

$$Var(X) = \frac{1}{n}\sum_{1}^{n}(x_i - \mu)^2 = \frac{1}{n}\sum_{1}^{n} x_i^2 - \mu^2 = \frac{1}{n}\left[\sum_{1}^{n} x_i^2 - \frac{1}{n}\left(\sum_{1}^{n} x_i\right)^2\right]$$

A végső képlet első tagja a négyzetek összege, a második tag pedig az elemek összegének négyzete osztva az elemszámmal. Ez Java-ban az alábbi módon valósítható meg:

```java
double varianceSinglePass(double[] data){

    double sum = 0;
    double sumOfSquares = 0;
    double mean = 0;

    double variance = 0.0;
    for (int i = 0; i < data.length; i++) {
        sum += data[i];
        sumOfSquares += data[i] * data[i];
    }
    return (sumOfSquares - (sum * sum)/data.length) / data.length;
}
```

Ennek a megvalósításnak azonban komoly numerikus buktatója van: a `sumOfSquares` és a `(sum * sum)/data.length` értékei nagyon közel eshetnek egymáshoz, és különbségük olyan kicsivé válhat, hogy az a lebegőpontos aritmetika véges pontosságával már nem ábrázolható. Ezt a jelenséget katasztrofális kiejtésnek (catastrophic cancellation) nevezzük, és hibás eredményhez vezet. Következésképpen ez az egymenetes (one-pass) változat a gyakorlatban nem használható.

Egy numerikusan stabil, a katasztrofális kiejtéstől mentes egymenetes algoritmust Welford [17] közölt. Ez egy egymenetes – más néven online – algoritmus, amely az átlagot és a varianciát minden új minta feldolgozásakor inkrementálisan frissíti. Tekintsük először az átlag kiszámítását. Legyenek az $m_k,\ k = 1, \ldots, N$ részátlagok a következők: $m_1 = x_1/1$, $m_2 = (x_1 + x_2)/2$, $m_3 = (x_1 + x_2 + x_3)/3$, és így tovább. Belátható, hogy $m_k$ kifejezhető $m_{k-1}$ segítségével:

$$m_k = \frac{(n-1)m_{k-1} + x_n}{n}$$

ami tovább egyszerűsítve a következő rekurrens formára hozható:

$$m_k = m_{k-1} + \frac{x_n - m_{k-1}}{n}$$

Ez azt mutatja, hogy az átlag tetszőleges elemszámra iteratívan számolható pusztán az aktuális elem és az előző iteráció átlagának felhasználásával.

A lényegi kérdés az, hogy a variancia kifejezhető-e hasonló rekurzióval. Vezessük be $S_n = \sum_{1}^{n}(x_i - m_n)^2$ jelölést a varianciaképletben szereplő összegtagra; így a variancia egyszerűen:

$$Var(X) = \frac{1}{n}S_n$$

Az átlagnál megszokotthoz hasonló, $S_n = S_{n-1} + M_n$ alakú rekurrens formulát keresünk. Az $M_n$ tagot a $S_n - S_{n-1}$ különbség képzésével vezetjük le. Az összeg szétbontása, az $(a^2 - b^2) = (a+b)(a-b)$ azonosság alkalmazása, valamint a $\sum_{i=1}^{n}(x_i - m_n) = 0$ azonosság – amely közvetlenül következik $n \cdot m_n = \sum_{i=1}^{n} x_i$ definíciójából – több lépéses felhasználása után eljutunk a kompakt zárt alakhoz:

$$M_n = (x_n - m_n)(x_n - m_{n-1})$$

Ezzel megkapjuk az $S_n$-re vonatkozó végleges rekurzív képletet:

$$S_n = S_{n-1} + M_n = S_{n-1} + (x_n - m_n)(x_n - m_{n-1})$$

amelyből a variancia menet közben a $Var(X) = S_n/n$ összefüggéssel számítható.

A Welford-algoritmus jelentősége abban áll, hogy nemcsak egy numerikusan stabil, egymenetes módszert ad az átlag és a variancia kiszámítására, hanem mindezt anélkül, hogy a teljes adathalmaznak ismertnek kellene lennie. Így tetszőleges – akár ismeretlen vagy végtelen – hosszúságú adatsorozatra is alkalmazható. Egyben jól szemlélteti azt az általános tanulságot is, hogy a stream-algoritmusok gyakran algoritmikus – néha egészen a matematikai alapokig visszanyúló – átstrukturálást igényelnek ahhoz, hogy a probléma adatfolyam-környezetben egyáltalán megoldható legyen.

Képzeljünk el egy termelő-fogyasztó (producer-consumer) rendszert, amelyben a termelő adatelemek sorozatát állítja elő, és továbbítja a fogyasztónak, akinek feladata az átlag és a variancia folyamatos számítása. A Welford-algoritmus éppen erre alkalmas: a fogyasztó az adatfolyamot anélkül képes feldolgozni, hogy az elemeket a memóriában tárolnia kellene. A fogyasztó Java-implementációja az alábbiakban látható; feltételezzük, hogy a termelő és a fogyasztó egy `ArrayBlockingQueue` példányon keresztül kommunikálnak.

```java
private class Consumer extends Thread{
    private ArrayBlockingQueue data;
    private long n;
    private double mean;
    private double sn;
    private double variance;

    public Consumer(ArrayBlockingQueue data) {
        this.data = data;
    }

    public void run(){
        while (true) {
            try {
                int x = data.take();
                n++;
                double oldMean = mean;
                mean = mean + (x - mean)/n;
                sn = sn + (x - mean)* (x - oldMean);
                variance = sn/n;
            } catch (InterruptedException ex) {
                ex.printStackTrace();
            }
        }

    }
}
```

A variancia kiszámításának példája szépen illusztrálja, hogy a stream-algoritmusok megtervezése sokszor nem merül ki az ismert batch-algoritmusok mechanikus átültetésében: a helyes, numerikusan stabil és memóriahatékony megoldás eléréséhez gyakran magát a matematikai megfogalmazást kell újragondolni, hogy az adatfolyam-jellegű végrehajtásra alkalmassá váljon.

### 8.2 Népszerű stream-adatfeldolgozó keretrendszerek
Az alkalmazások „24/7” stílusú, folyamatos rendelkezésre állása és felhős működése magával hozta az adatfolyam-alkalmazások térnyerését. Ha a felhőben amúgy is folyamatosan számításokat végzünk, miért ne használnánk ezt a képességet a folyamatos adatáradat valós idejű feldolgozására is? Ezen alkalmazások elterjedése természetes módon vezetett a specifikus stream-feldolgozó keretrendszerek (frameworkök) kifejlesztéséhez.

A következőkben először a Sparkot vizsgáljuk meg, amely az adatfolyam-feldolgozást úgynevezett mikro-kötegek (microbatches) formájában támogatja. Mivel sok felhasználó úgy találta, hogy ez a fajta absztrakció és az általa elért teljesítmény bizonyos felhasználási esetekben nem felel meg az igényeiknek, az elmúlt évtizedben számos új, dedikált adatfolyam-keretrendszer is megjelent a piacon.

#### 8.2.1 Spark Streaming
A Spark Streaming a rendkívül népszerű Apache Spark kiterjesztése, amely lehetővé teszi az élő adatfolyamok (live data streams) feldolgozását. Számos különböző adatforrásból képes adatokat fogadni, és a feldolgozás után az eredményeket fájlrendszerekbe vagy adatbázisokba menteni (lásd 8-2. ábra).

![8-2. ábra](<../Cloud Programming_MSc_Juhasz_IId-76_1.png>)

*8-2. ábra: A Spark Streaming adatkapcsolatai harmadik féltől származó forrásokhoz és nyelőkhöz*



A megvalósítás a mikro-kötegek (microbatches) koncepcióján alapul. Ahogy a 8-3. ábra mutatja, a Spark Streaming fogadja a folyamatos bemeneti adatokat, majd azokat időalapon apró adatkötetekre (mikro-kötegekre) bontja. Ezeket a kötegeket aztán elküldi a normál Spark feldolgozó motornak (engine), ahol hagyományos, egyedi batch jobok sorozataként hajtódnak végre. Ezeket a mikro-kötegeket a rendszer belsőleg diszkretizált adatfolyamokként (discretised streams), röviden DStream-ekként absztrahálja. A Spark Streamingben a DStream adatstruktúra valójában nem más, mint a már megismert RDD-k folyamatos sorozata.

![8-3. ábra](<../Cloud Programming_MSc_Juhasz_IId-76_2.png>)

*8-3. ábra: Stream-végrehajtás megvalósítása a Spark batch-motor tetején*



A kötegelt WordCount példa implementációját a stream-műveletek támogatásához át kell alakítani. A stream-változat egy socket-alapú streamet használ arra, hogy folyamatosan szavakat fogadjon: minden egység egy-egy szövegsor, amelyet a rendszer `JavaReceiverInputDStream` típusú változóban tárol. Ezen a változón végezzük el a már jól ismert `map` műveletet a szavak (`JavaDStream`) előállításához, majd a `reduce` lépést, amelynek eredménye kulcs-érték párok sorozata (`JavaPairDStream`). Fontos megjegyezni, hogy ezek pusztán konfigurációs lépések: a tényleges stream-feldolgozás csak akkor indul el, amikor a `ssc` streaming kontextuson meghívjuk a `start()` metódust.

```java
...
// Create the context with a 1 second batch size
SparkConf sparkConf = new SparkConf().setAppName("JavaNetworkWordCount");
JavaStreamingContext ssc = new JavaStreamingContext(sparkConf, Durations.seconds(1));

// Create a JavaReceiverInputDStream on target ip:port and count the
// words in input stream of \n delimited text (eg. generated by 'nc')
// Note that no duplication in storage level only for running locally.
// Replication necessary in distributed scenario for fault tolerance.
JavaReceiverInputDStream<String> lines = ssc.socketTextStream(
        args[0], Integer.parseInt(args[1]), StorageLevels.MEMORY_AND_DISK_SER);

JavaDStream<String> words = lines.flatMap(x ->
                                Arrays.asList(SPACE.split(x)).iterator());
JavaPairDStream<String, Integer> wordCounts =
        words.mapToPair(s -> new Tuple2<>(s, 1)).reduceByKey((i1, i2) -> i1 + i2);

wordCounts.print();
ssc.start();
ssc.awaitTermination();
...
``` és redukálására (reduce). A stream feldolgozása ténylegesen az ssc.start() metódus meghívásakor veszi kezdetét.)

#### 8.2.2 Apache Flink
A kötegelt (batch) és a stream-adatfeldolgozás párhuzamos létezésének egyik legnagyobb problémája, hogy az élő adatfeldolgozás új implementációkat követel meg a már meglévő, jól bevált batch algoritmusainkhoz. Más szóval, ez egy diszruptív (felforgató) technológia: ha valaki áttér az élő adatfeldolgozásra, újra kell írnia a programjait. Ez azt eredményezi, hogy a fejlesztőknek két külön kódbázist kell fenntartaniuk ugyanarra a logikára: egyet a batch, egyet pedig a stream feldolgozáshoz. Ez szoftvermérnöki szempontból kifejezetten nem kívánatos helyzet.

Itt lép be a képbe az Apache Flink. A Flink fejlesztői azt a célt tűzték ki maguk elé, hogy egyetlen közös programozási modellben egyesítsék a stream és a batch világát. A Flink kulcsfogalma a data stream (adatfolyam), amelyen belül két alaptípust különböztet meg (lásd 8-4. ábra):

![8-4. ábra](<../Cloud Programming_MSc_Juhasz_IId-77_1.png>)

*8-4. ábra: Korlátos és korlátlan streamek egységes kezelése Flinkben*



A korlátlan adatfolyamok (unbounded streams) – amelyeknek van elejük, de nincs végük – a folyamatos, élő adatokat (live streaming data) reprezentálják.

A korlátos adatfolyamok (bounded streams) – amelyeknek pontosan definiált elejük és végük van – pedig a hagyományos batch feldolgozásra szánt adatokat írják le.

Azáltal, hogy a hagyományos batch bemeneti adatokat egyszerűen a korlátos adatfolyam egy speciális eseteként kezeli, a Flink feleslegessé teszi a duplikált kódbázisok fenntartását. Ugyanaz az algoritmus immár transzparens módon képes működni mindkét típusú adatfolyamon!

A Flink egy rendkívül funkció-gazdag adatfolyam-feldolgozó motor (lásd 8-5. ábra). Számos forrásból képes adatokat fogadni, tökéletesen integrálható különböző végrehajtási és tárolási rendszerekkel, az eredményeket pedig különféle adatfogyasztók (fájlrendszerek, adatbázisok, alkalmazások, eseménysorok) felé képes továbbítani.

![8-5. ábra](<../Cloud Programming_MSc_Juhasz_IId-77_2.png>)

*8-5. ábra: Gazdag integrációs funkciók gyors fejlesztést biztosítanak Flinkben*



Állapotkezelés (Handling state)
A nagy elosztott rendszerek egyik legkritikusabb problémája az állapot (state). Meghibásodások és hálózati hibák esetén nagyon nehéz fenntartani az alkalmazás konzisztens állapotát. Ennek eredményeként számos nagy elosztott rendszer az állapot nélküli (stateless) dizájnt részesíti előnyben, vagy egyenesen meg is követeli azt.

Nyilvánvaló azonban, hogy nem minden alkalmazás lehet állapot nélküli. A legtöbb, valódi üzleti értéket képviselő (non-trivial) alkalmazás igenis megköveteli az állapotok nyilvántartását. A Flink egyik legfőbb megkülönböztető jellemzője az állapottal rendelkező (stateful) műveletek kiemelkedő támogatása. A Flinkben az állapot első osztályú (first-class) entitásként jelenik meg, és a megvalósítása rendkívül hatékony, mivel memóriában lévő (in-memory) állapotreprezentációra épül. Szükség esetén – amikor az állapot mérete meghaladja a memória korlátait – az állapotkezelést és az állapot-pillanatképek (checkpointok) biztonságos perzisztálását egy csatlakoztatható állapot-háttérrendszer (pluggable state backend) veszi át. Ennek az okos és hatékony architektúrának köszönhetően a Flink könnyedén képes kezelni az akár terabájtos nagyságrendű alkalmazásállapotokat is (lásd 8-6. ábra).

![8-6. ábra](<../Cloud Programming_MSc_Juhasz_IId-78_1.png>)

*8-6. ábra: Állapottartó feldolgozás memóriabeli vagy lemezes állapotperzisztenciával*



Idő (Time)
Az idő egy másik kardinális tényezője az adatfolyam-alkalmazásoknak. A valós életben az eseményeknek oksági (kauzális) kapcsolatuk van: az egyik esemény nem történhet meg a másik előtt (például nem hallhatjuk a puskalövést azelőtt, hogy meghúznák a ravaszt). Következésképpen a stream-adatok legtöbbször időbélyegeket (timestamps) is tartalmaznak, amelyek az események sorrendiségének és okságának garantálására használhatók. Ennek megfelelően az adatfolyam-orientált rendszerek különbséget tesznek az eseményidő (event-time) és a feldolgozási idő (processing-time) alapú feldolgozás között.

Eseményidő (event-time) módban az alkalmazások az eseményeket a saját, eredeti időbélyegük alapján dolgozzák fel. Ez garantálja a konzisztens és reprodukálható eredményeket, függetlenül attól, hogy ténylegesen mennyi ideig tart a feldolgozás a rendszerben.

Feldolgozási idő (processing-time) módban az alkalmazások a szerver helyi rendszerideje (a feldolgozás pillanatának ideje) alapján operálnak. Ez tipikusan olyan valós idejű alkalmazásoknál használatos, ahol szigorú késleltetési (latency) követelmények vannak. Ilyenkor a rendszer csak a feldolgozási határidőig beérkezett eseményeket veszi figyelembe, ami azt jelenti, hogy bizonyos (a hálózatban késve érkező) események kimaradhatnak.

A Flink mindkét időmodellt teljeskörűen támogatja. Az alkalmazások a konkrét üzleti követelményektől függően választhatnak az eseményidő vagy a feldolgozási idő szemantikája közül. Eseményidő módban további finomítások – például a vízjelek (watermarks) támogatása és a későn érkező események (late events) intelligens kezelése – segítik a fejlesztőket abban, hogy pontosan a kívánt feldolgozási logikát valósíthassák meg. Mivel az adatfolyamok jellemzően időalapú számításokat (pl. csúszóablakos aggregációk, munkamenetek (session) felismerése, mintázatfelismerés) igényelnek, kiemelten fontos, hogy a rendszer hogyan kezeli és méri az időt.

---

#### 8.2.3 Apache Storm és Trident
A Spark Streaming mikro-kötegelt (micro-batch) megközelítésével szemben az Apache Storm egy valódi, eseményenkénti (event-by-event) valós idejű feldolgozó keretrendszer. Eredetileg a Twitter fejlesztette ki, majd később nyílt forráskódúvá tették. A Storm rendkívül alacsony késleltetést (sub-millisecond latency) biztosít, így ideális az olyan alkalmazásokhoz, ahol a feldolgozási sebesség kritikus tényező.

A Storm alkalmazásokat topológiáknak (topologies) nevezzük, amelyek irányított aciklikus gráfokként (DAG) épülnek fel. A gráf csomópontjai a feldolgozási logikát, míg az élek az adatfolyamokat képviselik. A rendszer két alapvető építőelemből áll:

Spout (Kibocsátó): Az adatforrás, amely egy külső rendszerből (például egy üzenetsorból vagy egy Twitter API-ból) olvassa be az adatokat, és folyamatos adatfolyamként (streamként) bocsátja ki azokat a topológiába.

Bolt (Feldolgozó): A tényleges számítási egység. A boltok fogadják a streameket, elvégzik a szükséges transzformációkat (szűrés, aggregáció, adatbázis-műveletek), majd az eredményt új streamként továbbíthatják más boltoknak, vagy elmenthetik egy külső tárolóba.

Bár a Storm rendkívül gyors, az alapértelmezett, eseményenkénti feldolgozása megnehezíti a komplex állapotkezelést (state management) és az úgynevezett pontosan egyszeri (exactly-once) feldolgozási szemantika garantálását hibák esetén. Ezen problémák áthidalására hozták létre a Trident kiegészítést. A Trident egy magasabb szintű absztrakció a Storm felett, amely a Spark Streaminghez hasonlóan mikro-kötegeket (micro-batches) használ. A Trident lehetővé teszi a fejlesztők számára, hogy állapotot (state) tartsanak fenn az adatfolyamok között, és garantálja, hogy minden rekord pontosan egyszer kerüljön feldolgozásra, még hardveres meghibásodások esetén is.



![8-7. ábra](<../Cloud Programming_MSc_Juhasz_IId-79_1.png>)

*8-7. ábra: Spoutokból és Boltokból álló Storm-topológia*



![8-8. ábra](<../Cloud Programming_MSc_Juhasz_IId-79_2.png>)

*8-8. ábra: A Storm klaszter-architektúra*



![8-9. ábra](<../Cloud Programming_MSc_Juhasz_IId-80_1.png>)

*8-9. ábra: Feldolgozási topológia a Storm Word Count példához*

#### 8.2.4 Apache Kafka és Kafka Streams
Az Apache Kafka egy elosztott eseménystreaming (event streaming) platform és üzenetközvetítő (message broker) rendszer, amelyet eredetileg a LinkedIn fejlesztett ki. Bár gyakran a stream-feldolgozó keretrendszerek (mint a Flink vagy a Spark) bemeneti forrásaként használják, a Kafka ma már önmagában is egy robusztus adatfeldolgozási ökoszisztémát alkot.

A Kafka architektúrájának alapjai:

Témakörök (Topics): Az üzenetek (események) logikai csatornái, amelyekbe az adatokat publikálják.

Termelők (Producers): Azok a folyamatok, amelyek adatokat generálnak és küldenek a témakörökbe.

Fogyasztók (Consumers): Azok a folyamatok, amelyek feliratkoznak a témakörökre, és feldolgozzák az onnan érkező eseményeket.

Brókerek (Brokers): A Kafka klaszter csomópontjai, amelyek a témakörök tárolásáért, particionálásáért és replikációjáért felelnek, biztosítva a magas rendelkezésre állást és a hibatűrést.

A Kafka a hagyományos üzenetsorokkal ellentétben az adatokat hosszú távon (akár napokig vagy hetekig) is képes tartósan (persistently) tárolni a lemezen, ami lehetővé teszi a fogyasztók számára, hogy a saját tempójukban dolgozzák fel az eseményeket, vagy akár „visszatekerjék” az időt és újra feldolgozzák a múltbeli adatokat.

A feldolgozási képességek bővítése érdekében jelent meg a Kafka Streams API. Ez egy könnyűsúlyú (lightweight) Java/Scala könyvtár, amellyel a fejlesztők dedikált klaszterek felépítése nélkül hozhatnak létre stream-feldolgozó alkalmazásokat. A Kafka Streams közvetlenül a Kafka klaszteren lévő adatokon operál (egy témakörből olvas, feldolgoz, majd egy másik témakörbe ír), beépítve támogatva a csúszóablakokat (sliding windows), az aggregációkat és a pontosan egyszeri (exactly-once) szemantikát.



![8-10. ábra](<../Cloud Programming_MSc_Juhasz_IId-83_1.png>)

*8-10. ábra: A Kafka helye egy stream-feldolgozó alkalmazáson belül*



![8-11. ábra](<../Cloud Programming_MSc_Juhasz_IId-83_2.png>)

*8-11. ábra: Topic-partíció megvalósítása várakozási soron (queue)*



![8-12. ábra](<../Cloud Programming_MSc_Juhasz_IId-84_1.png>)

*8-12. ábra: A topic hibatűrésének belső részletei partíció-replikáció alapján egy klaszterben*

### 8.3 Apache Beam és a GCP Dataflow
A big data ökoszisztéma egyik legnagyobb kihívása a fragmentáció: az évek során a batch és stream feldolgozásra (Hadoop, Spark, Flink, Storm) használt API-k mind inkompatibilisek voltak egymással. A Google ezt felismerve nyílt forráskódúvá tette belső adatfeldolgozási tapasztalatait (a Flume és MillWheel rendszerek utódját), így jött létre az Apache Beam.

Az Apache Beam egy egységesített programozási modell (unified programming model), amelynek mottója: "Write once, run anywhere" (Írd meg egyszer, futtasd bárhol). A Beam célja, hogy teljesen elválassza a feldolgozási logikát (az algoritmust) az azt végrehajtó konkrét futtatókörnyezettől.



![8-13. ábra](<../Cloud Programming_MSc_Juhasz_IId-86_1.png>)

*8-13. ábra: A Google Dataflow és a Beam SDK integrációja a GCP szolgáltatás-architektúrájában*

A Beam modell három fő koncepcióra épül:

Pipeline (Adatcsatorna): A teljes adatfeldolgozási feladatot (bemenet olvasása, transzformációk, kimenet írása) összefogó keret.

PCollection (Párhuzamos adathalmaz): A feldolgozandó adatokat reprezentáló elosztott adatstruktúra. A PCollection egyszerre képes leírni egy korlátos (batch) és egy korlátlan (stream) adatfolyamot is.

PTransform (Transzformáció): Az adatokon végrehajtott műveletek (pl. Map, Filter, GroupByKey), amelyek egy PCollectiont bemenetként fogadnak, és egy új PCollectiont állítanak elő.

A Beam API (amely elérhető Java, Python és Go nyelveken is) csak a logika definiálására szolgál. A program tényleges futtatásához egy Végrehajtó motorra (Runner) van szükség. A Beam varázsa abban rejlik, hogy ugyanaz a forráskód minimális módosítással (csak a Runner típusának átírásával) lefuttatható egy lokális gépen (DirectRunner), egy Apache Flink klaszteren (FlinkRunner), egy Apache Spark klaszteren (SparkRunner), vagy a Google felhőjében (DataflowRunner).



![8-14. ábra](<../Cloud Programming_MSc_Juhasz_IId-86_2.png>)

*8-14. ábra: Egyszerű Beam-pipeline három transzformációval*

#### 8.3.1 Google Cloud Dataflow
A Google Cloud Dataflow az Apache Beam hivatalos, GCP-n belüli futtatókörnyezete. A Dataflow egy teljesen felügyelt (fully managed), szerver nélküli (serverless) szolgáltatás. Ez azt jelenti, hogy a fejlesztőnek egyáltalán nem kell szervereket, virtuális gépeket vagy klasztereket telepítenie és konfigurálnia.

Amikor a fejlesztő elindít egy Beam adatcsatornát a DataflowRunner segítségével, a GCP a háttérben:

Elemzi a végrehajtandó gráfot és optimalizálja azt.

Automatikusan kiosztja (provision) a feladat elvégzéséhez szükséges számítási erőforrásokat.

Bejövő adatmennyiség (terhelés) függvényében dinamikusan skálázza a dolgozó (worker) gépek számát.

Ha a feladat (batch esetén) véget ér, automatikusan le is állítja az erőforrásokat.

A Cloud Dataflow tökéletes integrációt kínál a GCP többi adatszolgáltatásával (például adatokat képes olvasni a Cloud Storage-ból vagy a Pub/Sub-ból, az eredményeket pedig közvetlenül a BigQuery adattárházba tudja írni). Ez a szolgáltatás mentesíti az IT mérnököket az üzemeltetési terhek alól, lehetővé téve számukra, hogy kizárólag a bonyolult adatfeldolgozási algoritmusok megtervezésére összpontosítsanak. Az egyes keretrendszerek jellemzőit összefoglaló táblázat a 8-15. ábrán látható. A Beam rendszer ebben az összehasonlításban nem szerepel.

![8-15. ábra](<../Cloud Programming_MSc_Juhasz_IId-90_1.png>)

*8-15. ábra: Néhány szemléltető adatfolyam-feldolgozó keretrendszer összehasonlítása*



---

## 9. Felhőfüggvények (Cloud Functions)
A Cloud Functions a felhőalapú végrehajtási technológiák legújabb generációját képviseli. A függvények legfőbb jellemzője, hogy lehetővé teszik a felhasználók számára a kód közvetlen beküldését a felhőbe, anélkül, hogy bármilyen futtatási infrastruktúrát ki kellene építeniük. Ebből kifolyólag a függvényeket szerver nélküli kódvégrehajtásnak is nevezik, a felhőszolgáltatók pedig egy új szolgáltatástípusként, Függvény mint Szolgáltatásként (*Function-as-a-Service* – FaaS) hivatkoznak rájuk.

A függvények futtatása során a felhasználónak nem kell a szerverüzemeltetési feladatokkal (erőforrás-kiosztás, menedzsment vagy szoftverfrissítés) foglalkoznia; ezt a felelősséget a felhőszolgáltató teljes mértékben átvállalja. A függvények a terhelés függvényében automatikusan skálázódnak, és beépített monitorozási, naplózási, valamint hibakeresési képességekkel rendelkeznek. Támogatják a szerepköralapú és az egyedi függvényszintű biztonsági beállításokat, továbbá olyan hálózati funkciókat is kínálnak, amelyekkel a függvényből transzparens módon elérhetők más felhőkomponensek is.

A Cloud Functions a modern felhőtechnológia egyik legizgalmasabb vívmánya. Egységes formában valósítja meg a korábbi számítástechnikai rendszerek egykor utópisztikusnak tűnő vízióit: a zökkenőmentes programvégrehajtást földrajzilag elosztott erőforrásokon (lásd grid számítástechnika), publikus és privát szolgáltatások halmazának integrált felhasználásával (lásd szolgáltatásorientált architektúrák – SOA).

Ebben a fejezetben kizárólag a Google Cloud Functions [27] szolgáltatásra összpontosítunk. Hasonló megoldások minden nagy felhőszolgáltató kínálatában megtalálhatók, ilyen például az AWS Lambda [28] is. A fejezet hátralévő részében a „függvény” kifejezés alatt a Google megoldását értjük.

A GCP-ben kétféle függvénytípust fejleszthetünk: HTTP-függvényeket és háttérfüggvényeket. A HTTP-függvények Node.js, Python, Go, Java vagy C# nyelveken, míg a háttérfüggvények Node.js, Python, Go vagy Java nyelveken írhatók. A Cloud Functions környezet a választott implementációs nyelv alapján automatikusan kiválasztja a megfelelő futtatókörnyezetet.

HTTP-függvény

A HTTP-függvényeket úgy tervezték, hogy szabványos HTTP-kéréseken (GET, PUT, POST, DELETE és OPTIONS) keresztül lehessen őket meghívni. A kérést indító kliens addig várakozik, amíg a feldolgozás be nem fejeződik és a válasz meg nem érkezik. Java nyelvű implementáció esetén az egyedi függvénynek meg kell valósítania a com.google.cloud.functions.HttpFunction interfészt, amely egy funkcionális interfész, egyetlen service() metódussal.

Az alábbi egyszerű példa a kérések és válaszok feldolgozását mutatja be egy Java-alapú függvényben. A kód és a mögöttes logika nagyon hasonlít a Java Enterprise Platformban használt Servletek működéséhez. A HTTP-függvények programozásának további részletei a következő linken találhatók:
https://cloud.google.com/functions/docs/writing/http

Minta HTTP-függvény Java nyelven:

```java
public class HelloHttp implements HttpFunction {
  private static final Logger logger = Logger.getLogger(HelloHttp.class.getName());

  private static final Gson gson = new Gson();

  @Override
  public void service(HttpRequest request, HttpResponse response)
      throws IOException {
    // Ellenőrzi az URL paraméterek között a "name" mezőt
    // A "world" az alapértelmezett érték
    String name = request.getFirstQueryParameter("name").orElse("world");

    // Elemzi a JSON kérést és ellenőrzi a "name" mezőt
    try {
      JsonElement requestParsed = gson.fromJson(request.getReader(), JsonElement.class);
      JsonObject requestJson = null;

      if (requestParsed != null && requestParsed.isJsonObject()) {
        requestJson = requestParsed.getAsJsonObject();
      }

      if (requestJson != null && requestJson.has("name")) {
        name = requestJson.get("name").getAsString();
      }
    } catch (JsonParseException e) {
      logger.severe("Error parsing JSON: " + e.getMessage());
    }

    var writer = new PrintWriter(response.getWriter());
    writer.printf("Hello %s!", name);
  }
}
```

Kizárólag összehasonlítás céljából bemutatjuk ugyanezt a függvényt Node.js-ben implementálva is. A Java implementációhoz képest a kód tömörsége kifejezetten figyelemre méltó.

```javascript
const escapeHtml = require('escape-html');

/**
 * HTTP Cloud Function.
 *
 * @param {Object} req Cloud Function request context.
 * More info: https://expressjs.com/en/api.html#req
 * @param {Object} res Cloud Function response context.
 * More info: https://expressjs.com/en/api.html#res
 */
exports.helloHttp = (req, res) => {
  res.send(`Hello ${escapeHtml(req.query.name || req.body.name || 'World')}!`);
};
```

Háttérfüggvény

A függvények másik típusa a háttérfüggvény, amelyet a felhőinfrastruktúrából származó események aszinkron kezelésére terveztek. Ilyen esemény lehet például egy Cloud Storage tárolóvödör tartalmának megváltozása, vagy egy üzenet beérkezése egy Cloud Pub/Sub témakörbe. A Java nyelvű háttérfüggvényeknek a `com.google.cloud.functions.BackgroundFunction` interfészt kell implementálniuk. A `service()` metódus helyett ez az interfész egyetlen `accept()` metódussal rendelkezik, amely a figyelt esemény bekövetkeztekor automatikusan meghívódik.

A következő példában egy olyan háttérfüggvényt mutatunk be, amely akkor aktiválódik, ha bármilyen változás történik egy Cloud Storage vödörben. Figyeljük meg az interfész generikus típusparaméterét, amely meghatározza, hogy milyen típusú események esetén hívódjon meg ez az implementáció. A függvény kinyeri a tárolóvödörre és a fájlra vonatkozó információkat, valamint a bekövetkezett esemény típusát.

```java
import com.google.cloud.functions.BackgroundFunction;
import com.google.cloud.functions.Context;
import functions.eventpojos.GcsEvent;
import java.util.logging.Logger;

public class HelloGcs implements BackgroundFunction<GcsEvent> {
  private static final Logger logger = Logger.getLogger(HelloGcs.class.getName());

  @Override
  public void accept(GcsEvent event, Context context) {
    logger.info("Event: " + context.eventId());
    logger.info("Event Type: " + context.eventType());
    logger.info("Bucket: " + event.getBucket());
    logger.info("File: " + event.getName());
    logger.info("Metageneration: " + event.getMetageneration());
    logger.info("Created: " + event.getTimeCreated());
    logger.info("Updated: " + event.getUpdated());
  }
}
```

A háttérfüggvények írásával kapcsolatos további részletek a következő linken érhetők el:
https://cloud.google.com/functions/docs/writing/background

A függvények létrehozásának és futtatásának általános lépései a következők:

A függvény megírása

A függvény telepítése

A függvény végrehajtása vagy meghívása

A függvény monitorozása

Függvények végrehajtása

A GCP-függvények mindig izolált, biztonságos futásidejű kontextusban hajtódnak végre. A függvényekkel kapcsolatos egyik legfontosabb megkötés, hogy állapotmentesnek (stateless) kell lenniük. Ha a helyes működéshez állapot (state) fenntartása szükséges, azt valamilyen külső szolgáltatásba – például Google Cloud Storage-ba vagy Datastore-ba – kell menteni (perzisztálni). Minden egyes függvénypéldány egyetlen klienst/kérést szolgál ki egyszerre; ha nagyobb terhelés jelentkezik, a rendszer szükség szerint párhuzamosan több példányt indít el.

A GCP a következő végrehajtási garanciákat nyújtja a függvények számára: a HTTP-függvények esetében legfeljebb egyszeri (At-Most-Once), míg a háttérfüggvények esetében legalább egyszeri (At-Least-Once) szemantikát alkalmaz az üzenetkézbesítés során.

A felhőfüggvényeket különböző eseményindítók (triggerek) aktiválják. A triggerek típusai a következők lehetnek: HTTP triggerek, Cloud Pub/Sub triggerek, Cloud Storage triggerek, közvetlen (Direct) triggerek, Cloud Firestore triggerek, Analytics for Firebase triggerek, Firebase Realtime Database triggerek és Firebase Authentication triggerek. A Cloud Pub/Sub mechanizmust a következő fejezetben fogjuk részletesen megvizsgálni, hogy jobban megértsük az általános esemény- és üzenetkézbesítési megoldások működését.

Függvények telepítése

Mielőtt egy függvény végrehajthatóvá válna, üzembe kell helyezni a felhőben. Az üzembe helyezés során a függvény forráskódját tartalmazó archív fájlt fel kell tölteni egy Google Cloud Storage tárolóvödörbe. A függvény telepítéséhez az alábbi lehetőségek állnak rendelkezésre:

1. Telepítés helyi gépről
Hajtsuk végre a következő gcloud parancsot (a szükséges paraméterek behelyettesítése után):

```bash
gcloud functions deploy NAME --runtime RUNTIME TRIGGER [FLAGS...]
```

2. Telepítés verziókezelő rendszerből
Hajtsuk végre a következő gcloud parancsot (a szükséges paraméterek behelyettesítése után):

```bash
gcloud functions deploy NAME --source https://source.developers.google.com/ \
        projects/PROJECT_ID/repos/REPOSITORY_ID/moveable-aliases/master/ \
        paths/SOURCE \
        --runtime RUNTIME TRIGGER... [FLAGS...]
```

3. Telepítés a GCP konzolról
Ezt a módszert egy HTTP-függvény létrehozásán keresztül, részletesebben is bemutatjuk. Hajtsuk végre az alábbi lépéseket a megadott sorrendben:

Nyissuk meg a Cloud Console felületén a Functions Overview (Függvények áttekintése) oldalt (amint a 9-1. ábrán látható).

Győződjünk meg arról, hogy az a projekt van kiválasztva, amelyben engedélyeztük a Cloud Functions használatát.

Kattintsunk a Create function (Függvény létrehozása) gombra.

Adjuk meg a függvény nevét.

A Trigger (Eseményindító) mezőben válasszuk a HTTP lehetőséget.

Az Authentication (Hitelesítés) mezőben jelöljük be az Allow unauthenticated invocations (Nem hitelesített hívások engedélyezése) opciót.

Kattintsunk a Save (Mentés) gombra a módosítások rögzítéséhez, majd a Next (Tovább) gombra.

A Source code (Forráskód) mezőben válasszuk az Inline editor (Beépített szerkesztő) opciót. Ebben a gyakorlatban a szerkesztőben megjelenő alapértelmezett függvényt fogjuk használni.

A Runtime (Futásidejű környezet) legördülő menüből válasszuk ki a kívánt Java verziót.

Az oldal alján kattintsunk a Deploy (Telepítés) gombra.

A Deploy gombra kattintás után a Cloud Console automatikusan átirányít minket a Cloud Functions áttekintő oldalára.

Amint a telepítés befejeződött, a függvény működését úgy tesztelhetjük, hogy a függvényünk melletti menüből kiválasztjuk a Test function (Függvény tesztelése) lehetőséget (amint az a 9-2. ábrán látható).

*9-1. ábra: A Cloud Functions áttekintő oldala a Google Cloud Console-ban*

![9-1. ábra](<../Cloud Programming_MSc_Juhasz_IId-94_1.png>)

*9-2. ábra: A függvény tesztelése a Google Cloud Console felületén*

![9-2. ábra](<../Cloud Programming_MSc_Juhasz_IId-95_1.png>)

A függvény végrehajtása az automatikusan generált naplóbejegyzések megtekintésével egyszerűen ellenőrizhető. A Cloud Functions áttekintő oldalán nyissuk le a függvényhez tartozó menüt, és kattintsunk a View logs (Naplók megtekintése) opcióra. Ekkor egy, a 9-3. ábrához hasonló naplózó ablak jelenik meg.

*9-3. ábra: A Cloud Functions naplóablaka a Google Cloud Console-ban*

![9-3. ábra](<../Cloud Programming_MSc_Juhasz_IId-95_2.png>)

Egy Cloud Storage esemény által kiváltott háttérfüggvény létrehozását és tesztelését bemutató, részletes, lépésről lépésre haladó útmutató a következő linken található:
https://cloud.google.com/functions/docs/tutorials/storage

---

## 10. Szolgáltatások közötti kommunikáció: Pub/Sub

Egy felhőalkalmazás létrehozása számos kész (off-the-shelf) és egyedi felhőszolgáltatás használatát foglalja magában, amelyeknek az alkalmazás teljes életciklusa során együtt kell működniük. A szinkron, RPC-stílusú hívásokon alapuló szoros csatolás (strong coupling) nem megfelelő megközelítés a nagy, elosztott alkalmazások esetében; a lazán csatolt (loosely coupled), üzeneteken alapuló kommunikáció az egyetlen életképes stratégia a nagyméretű, skálázható rendszereknél. Ennek következtében valamennyi felhőszolgáltató kínál valamilyen üzenetküldő szolgáltatást a palettáján, amely segít a komponensek összekapcsolásában. Ebben a fejezetben a Google Cloud Platform által nyújtott üzenetküldő szolgáltatásra, a Google Pub/Sub-ra fókuszálunk.

### 10.1 A Google Pub/Sub áttekintése

A Google Pub/Sub egy magas rendelkezésre állású, aszinkron, valós idejű üzenetküldő szolgáltatás, amely a közzétevő-feliratkozó filozófián alapul. A Pub/Sub egy alacsony késleltetésű, nagy áteresztőképességű rendszer, amely valamennyi Google Cloud régióban működik, univerzális üzenetküldő és eseménytovábbító infrastruktúrát biztosítva a globális felhőalkalmazások számára. A Pub/Sub használható általános üzenetkezelő köztesrétegként, Cloud Functions-t aktiváló eseménytovábbító rendszerként, vagy akár adatfolyam-kezelő rétegként is.

A Pub/Sub a Közzétevőket (Publishers) és a Feliratkozókat (Subscribers) Témakörökön (Topics) keresztül köti össze. A témakör egy elnevezett erőforrás, amelyre a közzétevők üzeneteket küldenek. A feliratkozók Feliratkozásokat (Subscriptions) hoznak létre, amelyek szintén elnevezett erőforrások, és egyetlen, specifikus témakörhöz tartozó üzenetfolyamot reprezentálnak, amelyet a feliratkozó alkalmazáshoz kell kézbesíteni. Egy Üzenet (Message) adatokból (hasznos teher / payload) és a tartalmat leíró (opcionális) attribútumokból áll, amelyeket a közzétevő küld egy témakörre, és amelyek végül a feliratkozókhoz kerülnek kézbesítésre. Az üzenetattribútum egy kulcs-érték pár, amelyet a közzétevő határozhat meg az üzenethez.

A tényleges Pub/Sub üzenetformátum a következőképpen épül fel. Egy üzenet az adatokat és a metaadatokat tartalmazó mezőkből áll. Az alábbi mezők közül legalább egynek jelen kell lennie az üzenetben:

Az üzenet adatai (message data)

Egy rendezési kulcs (ordering key)

További metaadatokat tartalmazó attribútumok

A Pub/Sub szolgáltatás a következő mezőkkel egészíti ki az üzenetet a háttérben:

Egy, a témakörön belül egyedi üzenetazonosító (message ID)

Egy időbélyeg (timestamp) arról, hogy a Pub/Sub mikor kapta meg az üzenetet

A Pub/Sub a Google Cloud infrastruktúra szerves része, ezért minden Google szolgáltatás támogatja. Ez szinte triviális feladattá teszi a különböző GCP szolgáltatások integrációját (a 10-1. ábra mutatja a Pub/Sub-bal együtt leggyakrabban használt kulcsfontosságú szolgáltatásokat).

A Pub/Sub nagyon különböző típusú komponenseket tud egységes felhőalkalmazássá összekapcsolni. A 10-2. ábra ezt részletesebben is szemlélteti. Bármely alkalmazás, amely HTTPS kéréseket tud küldeni a pubsub.googleapis.com címre, lehet Közzétevő (Publisher). Ilyen lehet például egy App Engine alkalmazás, egy Google Compute Engine-en hosztolt webszolgáltatás, bármely más, harmadik fél hálózatán futó szolgáltatás, vagy akár egy asztali/mobil eszközre telepített alkalmazás is. Hasonlóképpen, bármely alkalmazás, amely HTTPS kéréseket tud küldeni a fenti címre, lehet lekéréses (Pull) Feliratkozó is.

*10-1. ábra: Google Pub/Sub támogatás a Google szolgáltatásokban*

![10-1. ábra](<../Cloud Programming_MSc_Juhasz_IId-97_1.png>)

*10-2. ábra: Lehetséges szolgáltatás-összekapcsolások a Pub/Sub-ban*

![10-2. ábra](<../Cloud Programming_MSc_Juhasz_IId-97_2.png>)

A Pub/Sub N-M (sok-a-sokhoz) leképezést támogat a közzétevők és feliratkozók között. A feliratkozók bármennyi közzétevőtől feliratkozhatnak üzenetek fogadására, ami akár átfedéseket is megenged. Hasonlóképpen, a közzétevők különálló feliratkozóknak vagy egy teljes feliratkozói csoportnak is küldhetnek üzeneteket. A közzétevők és feliratkozók közötti leképezés a Témakör-Feliratkozás (Topic-Subscription) konfigurációkon keresztül valósul meg.

A 10-3. ábra egy példán keresztül szemlélteti ezeket a fogalmakat. Három közzétevőnk van: A, B és C, valamint három feliratkozónk: X, Y és Z. Az X feliratkozó mind az A, mind a B közzétevőtől szeretne üzeneteket fogadni, ezért feliratkozik az A és B témakörökre. Az így létrejött XA és XB feliratkozások garantálják, hogy minden A és B témakörre küldött üzenet eljut az X feliratkozóhoz.

Az Y és Z feliratkozók ugyanakkor ugyanattól a C közzétevőtől szeretnének üzeneteket fogadni. Ebben az esetben Y és Z feliratkozik a C témakörre, aminek eredményeképpen két feliratkozás (YC és ZC) jön létre. Amikor egy üzenet érkezik a C közzétevőtől, ugyanaz az üzenet kerül kézbesítésre az YC feliratkozáson keresztül Y-hoz, illetve a ZC feliratkozáson keresztül Z-hez.

*10-3. ábra: Sok-az-egyhez és egy-a-sokhoz közzétevő-feliratkozó kapcsolatok szemléltetése*

![10-3. ábra](<../Cloud Programming_MSc_Juhasz_IId-98_1.png>)

### 10.2 A Pub/Sub üzenetfolyama

Ebben a fejezetben részletesen megvizsgáljuk az üzenetkézbesítés lépéseit. Egy közzétevőtől érkező üzenet kézbesítése a következő lépésekből áll a Pub/Sub infrastruktúrában:

A közzétevő alkalmazás létrehoz egy témakört (Topic) a Pub/Sub szolgáltatásban, és üzeneteket küld rá. Az üzenet egy hasznos adatot (payload) és a tartalmat leíró opcionális attribútumokat tartalmaz.

A szolgáltatás biztosítja, hogy a közzétett üzenetek megőrzésre kerüljenek a feliratkozások számára. Egy közzétett üzenet addig marad tárolva egy adott feliratkozás számára, amíg azt az onnan üzeneteket fogyasztó feliratkozó be nem nyugtázza (acknowledge / ack).

A Pub/Sub a témakörre érkező üzeneteket az összes feliratkozásra külön-külön továbbítja.

A feliratkozó kétféleképpen kaphat üzeneteket: a Pub/Sub vagy közvetlenül elküldi (Push) azokat a feliratkozó által választott végpontra, vagy a feliratkozó maga kéri le (Pull) azokat a szolgáltatásból.

A feliratkozó minden fogadott üzenetről visszaigazolást (nyugtát) küld a Pub/Sub szolgáltatásnak.

A szolgáltatás eltávolítja a sikeresen nyugtázott üzeneteket a feliratkozás üzenetsorából.

A Pub/Sub alapértelmezésben Legalább egyszeri (At-Least-Once) szemantikával kézbesíti az üzeneteket. Az üzenetkézbesítés alól csak egyetlen kivétel van: ha egy üzenetet nem lehet kézbesíteni a generálástól számított 7 napon belül, akkor az kézbesítés nélkül véglegesen törlődik. Hasonlóképpen, ha egy üzenetnek a generálás pillanatában nincs egyetlen feliratkozása sem, az üzenet egyáltalán nem kerül kézbesítésre.

Amikor a Pub/Sub-ot az Apache Beam SDK adatfolyam-programozási (streaming) modelljével együtt használjuk, lehetőség van a Pontosan egyszeri (Exactly-Once) szemantika elérésére is, garantáltan rendezett üzenetkézbesítéssel.

A Pub/Sub architektúra további részletei az alábbi linken találhatók:
https://cloud.google.com/pubsub/architecture

*10-4. ábra: Üzenet feldolgozásának lépései a Pub/Sub-ban*

![10-4. ábra](<../Cloud Programming_MSc_Juhasz_IId-99_1.png>)

### 10.3 Üzenetkézbesítési példa

Miután megismertük a Pub/Sub szolgáltatás általános filozófiáját és működését, most egy rövid példán keresztül a gyakorlatban is szemléltetjük azt. A példa egy háttérfüggvényből áll, amelyet egy Pub/Sub üzenet fog aktiválni.

A függvény forráskódja alább látható. Kap egy üzenetet a Pub/Sub-tól, kinyeri annak tartalmát, és beilleszti a "Hello …" kimeneti szövegbe, ezzel személyre szabott köszöntést generálva.

```java
import com.google.cloud.functions.BackgroundFunction;
import com.google.cloud.functions.Context;
import functions.eventpojos.PubSubMessage;
import java.nio.charset.StandardCharsets;
import java.util.Base64;
import java.util.logging.Level;
import java.util.logging.Logger;

public class HelloPubSub implements BackgroundFunction<PubSubMessage> {
  private static final Logger logger = Logger.getLogger(HelloPubSub.class.getName());

  @Override
  public void accept(PubSubMessage message, Context context) {
    String name = "world";
    if (message != null && message.getData() != null) {
      name = new String(
        Base64.getDecoder().decode(message.getData().getBytes(StandardCharsets.UTF_8)),
        StandardCharsets.UTF_8);
    }
    logger.info(String.format("Hello %s!", name));
    return;
  }
}
```

Amint a kód elkészült, a függvényt a felhőbe telepítjük az alábbi gcloud parancs segítségével. A témakör neve ebben a példában SAMPLE_TOPIC. Ezt a deploy parancsban a --trigger-topic opcióval adjuk meg, amely létrehozza a kapcsolatot (feliratkozást) a megadott témakörhöz.

```bash
gcloud functions deploy java-pubsub-function \
--entry-point functions.HelloPubSub \
--runtime java11 \
--memory 512MB \
--trigger-topic SAMPLE_TOPIC
```

A függvény telepítése után létrehozzuk magát a témakört is az alábbi paranccsal:

```bash
gcloud pubsub topics create SAMPLE_TOPIC
```

Végül teszteljük a példánk működését úgy, hogy egy "Einstein" tartalmú tesztüzenetet küldünk a SAMPLE_TOPIC-ra. Az egyszerűség kedvéért az üzenet generálására is a gcloud parancsot használjuk. (A következő alfejezetben megvizsgáljuk, hogyan küldhetünk és fogadhatunk üzeneteket közvetlenül az alkalmazáskódból.)

```bash
gcloud pubsub topics publish SAMPLE_TOPIC --message Einstein
```

### 10.4 Üzenetek közzététele és fogadása kódból

Most megvizsgáljuk, hogyan lehet Java kódból üzeneteket közzétenni és fogadni a Pub/Sub API használatával. Az első kódrészlet egy üzenet közzétételét illusztrálja.

Először a témakör nevét (TopicName) hozzuk létre a projekt- és a témaazonosító alapján, majd példányosítunk egy közzétevő (Publisher) objektumot. Ezt követően a megfelelő adatmezőkkel összeállítunk egy új üzenetet. Ezután az üzenet közzétételre kerül. A visszatérő Future objektumot átadjuk egy aszinkron visszahívó (callback) objektumnak, amely akkor aktiválódik, amikor az üzenet sikeresen közzétételre került, vagy ha a művelet sikertelen volt. A program a közzétevő erőforrásainak felszabadításával (shutdown) fejeződik be.

Pub/Sub üzenet közzététele (Publishing)

```java
import com.google.api.core.ApiFuture;
import com.google.api.core.ApiFutureCallback;
import com.google.api.core.ApiFutures;
import com.google.api.gax.rpc.ApiException;
import com.google.cloud.pubsub.v1.Publisher;
import com.google.common.util.concurrent.MoreExecutors;
import com.google.protobuf.ByteString;
import com.google.pubsub.v1.PubsubMessage;
import com.google.pubsub.v1.TopicName;
import java.io.IOException;
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.TimeUnit;

public class PublishWithErrorHandlerExample {

  public static void main(String... args) throws Exception {
    // TODO(developer): Futtatás előtt cserélje ki ezeket a változókat!
    String projectId = "your-project-id";
    String topicId = "your-topic-id";

    publishWithErrorHandlerExample(projectId, topicId);
  }

  public static void publishWithErrorHandlerExample(String projectId, String topicId)
      throws IOException, InterruptedException {
    TopicName topicName = TopicName.of(projectId, topicId);
    Publisher publisher = null;

    try {
      // Publisher példány létrehozása az alapértelmezett beállításokkal, a témához kötve
      publisher = Publisher.newBuilder(topicName).build();

      List<String> messages = Arrays.asList("first message", "second message");

      for (final String message : messages) {
        ByteString data = ByteString.copyFromUtf8(message);
        PubsubMessage pubsubMessage = PubsubMessage.newBuilder().setData(data).build();

        // Közzététel után egy szerver által kiosztott (témán belül egyedi) üzenetazonosítót ad vissza
        ApiFuture<String> future = publisher.publish(pubsubMessage);

        // Aszinkron visszahívás (callback) hozzáadása a siker/hiba kezelésére
        ApiFutures.addCallback(
            future,
            new ApiFutureCallback<String>() {

              @Override
              public void onFailure(Throwable throwable) {
                if (throwable instanceof ApiException) {
                  ApiException apiException = ((ApiException) throwable);
                  // Részletek az API kivételről
                  System.out.println(apiException.getStatusCode().getCode());
                  System.out.println(apiException.isRetryable());
                }
                System.out.println("Error publishing message : " + message);
              }

              @Override
              public void onSuccess(String messageId) {
                System.out.println("Published message ID: " + messageId);
              }
            },
            MoreExecutors.directExecutor());
      }
    } finally {
      if (publisher != null) {
        // Ha befejeztük, állítsuk le a publishert az erőforrások felszabadítása érdekében
        publisher.shutdown();
        publisher.awaitTermination(1, TimeUnit.MINUTES);
      }
    }
  }
}
```

A második minta azt illusztrálja, hogyan lehet egy alkalmazásban üzenetet fogadni. A Pub/Sub-ban kétféle üzenetkézbesítési mód létezik: Lekéréses (Pull) és Leküldéses (Push) kézbesítés. A lekéréses kézbesítés során a feliratkozónak explicit módon kell kérnie (le kell húznia) az üzeneteket a Pub/Sub rendszertől. A leküldéses módban a Pub/Sub rendszer kérés nélkül, proaktívan küldi az üzenetet a feliratkozó által megadott végpontra. A Pull és Push üzenetkézbesítés szekvenciadiagramjai a 10-5. és a 10-6. ábrán láthatók.

*10-5. ábra: A Pull üzenetkézbesítés szekvenciadiagramja*

![10-5. ábra](<../Cloud Programming_MSc_Juhasz_IId-102_1.png>)

*10-6. ábra: A Push üzenetkézbesítés szekvenciadiagramja*

![10-6. ábra](<../Cloud Programming_MSc_Juhasz_IId-102_2.png>)

A mi példánk csak a Pull (lekéréses) kézbesítés implementációját mutatja be. A program először lekéri a feliratkozás nevét a megadott projekt- és feliratkozás-azonosítók alapján. Ezután egy Subscriber (feliratkozó) példány jön létre a feliratkozás neve és egy üzenetfogadó (MessageReceiver) objektum felhasználásával. Ezt követően a feliratkozó elindul, és megkezdi az üzenetek aszinkron fogadását a háttérben. Minden egyes beérkező üzenet esetén aktiválódik a receiver objektum lambda kifejezése. Itt lekérjük az adatok tartalmát, majd a consumer.ack() hívással nyugtázzuk a sikeres kézbesítést.

Pub/Sub üzenet fogadása (Receiving)

```java
import com.google.cloud.pubsub.v1.AckReplyConsumer;
import com.google.cloud.pubsub.v1.MessageReceiver;
import com.google.cloud.pubsub.v1.Subscriber;
import com.google.pubsub.v1.ProjectSubscriptionName;
import com.google.pubsub.v1.PubsubMessage;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.TimeoutException;

public class SubscribeAsyncExample {
  public static void main(String... args) throws Exception {
    // TODO(developer): Futtatás előtt cserélje ki ezeket a változókat!
    String projectId = "your-project-id";
    String subscriptionId = "your-subscription-id";

    subscribeAsyncExample(projectId, subscriptionId);
  }

  public static void subscribeAsyncExample(String projectId, String subscriptionId) {
    ProjectSubscriptionName subscriptionName =
        ProjectSubscriptionName.of(projectId, subscriptionId);

    // Aszinkron üzenetfogadó (MessageReceiver) példányosítása
    MessageReceiver receiver =
        (PubsubMessage message, AckReplyConsumer consumer) -> {
          // A bejövő üzenet kezelése, majd a kézbesítés nyugtázása (ack)
          System.out.println("Id: " + message.getMessageId());
          System.out.println("Data: " + message.getData().toStringUtf8());
          consumer.ack();
        };

    Subscriber subscriber = null;
    try {
      subscriber = Subscriber.newBuilder(subscriptionName, receiver).build();
      // A feliratkozó (subscriber) elindítása
      subscriber.startAsync().awaitRunning();
      System.out.printf("Listening for messages on %s:\n", subscriptionName.toString());
      // Engedjük futni a feliratkozót 30 másodpercig, hacsak nem történik helyrehozhatatlan hiba
      subscriber.awaitTerminated(30, TimeUnit.SECONDS);
    } catch (TimeoutException timeoutException) {
      // 30 másodperc után állítsuk le a feliratkozót, az üzenetek fogadása befejeződik
      subscriber.stopAsync();
    }
  }
}
```


---

## 11. GCP szolgáltatáspéldák

Az előző fejezetekben áttekintettük a Google Cloud Platform különféle IaaS-szintű szolgáltatásait. Megvizsgáltuk, hogyan hajthatók végre nagyléptékű számítási és adatfeldolgozási feladatok kötegelt (batch) és adatfolyam-alapú (streaming) módon. Megismertük a Cloud Functions szerver nélküli világát és a Pub/Sub közzétevő-feliratkozó típusú üzenetküldő rendszerét. A Google Cloud Platform azonban számos olyan magas szintű, azonnal használható szolgáltatási komponenst is kínál, amelyek drasztikusan csökkentik a fejlesztési erőfeszítéseket, miközben jelentősen növelik az alkalmazások képességeit.

Ezeknek a szolgáltatásoknak a legizgalmasabb példái a számításilag rendkívül komplex területeken találhatók, mint amilyen a mesterséges intelligencia (AI) és az ember-gép kapcsolatot támogató interfészek. Ebben a fejezetben rövid áttekintést nyújtunk ezekről a megoldásokról. Tekintettel a folyamatosan bővülő kínálatra és funkcionalitásra, a bemutatás nem törekszik a teljességre; csupán a legérdekesebb szolgáltatásokat választottuk ki, bemutatva azok képességeit és programozási felületeit (API), hogy ízelítőt adjunk a technológia nyújtotta lehetőségekből.

A GCP AI és gépi tanulási (Machine Learning) termékpalettája az alábbi főbb szolgáltatásokat tartalmazza:

Szolgáltatás	Leírás
AutoML	
Olyan szolgáltatáscsalád, amely lehetővé teszi egyedi gépi tanulási (ML) modellek létrehozását a Google fejlett technológiáira építve. Különböző területeken alkalmazható, mint például szövegfeldolgozás (AutoML Natural Language), képosztályozás és objektumfelismerés (AutoML Vision), videóelemzés és objektumkövetés (AutoML Video Intelligence), valamint strukturált adatok elemzése (AutoML Tables).

Vision AI	
Képfelismerési és elemzési funkciókat biztosító szolgáltatás, amely előre tanított vagy egyedi modelleket használ. Képes szöveg kinyerésére és felismerésére (OCR), képcímkézésre, arc- és nevezetesség-felismerésre, valamint tartalommoderálásra.

Video AI	
Videószekvenciákban tesz lehetővé hatékony tartalomfelfedezést, objektumkövetést és snittekre (shot) bontott elemzést.

Cloud Natural Language	
Természetes nyelvfeldolgozó technológia, amely hangulatelemzést (sentiment analysis), entitásfelismerést, tartalomosztályozást és szintaktikai elemzést kínál strukturálatlan szövegek mélyebb megértéséhez.

Cloud Translation	
Dinamikus fordítást tesz lehetővé tetszőleges nyelvpárok között, megnyitva az alkalmazásokat és weboldalakat a globális piac előtt.

Text-to-Speech	
Szöveges bemenetet vagy SSML (Speech Synthesis Markup Language) adatot alakít át természetes hangzású beszéddé.

Speech-to-Text	
Lehetővé teszi a Google beszédfelismerési technológiáinak egyszerű integrálását: a beküldött audio fájlokból szöveges átiratot készít.

Dialogflow	
Intelligens beszélgető ágensekre (chatbotokra) épülő, hang- és szövegalapú párbeszédes felületek létrehozását támogató platform.

Ebből a széles kínálatból a Vision AI, a Cloud Translation és a Text-to-Speech szolgáltatásokat vizsgáljuk meg részletesebben.

### 11.1 Vision AI

A Vision AI Java API-ja (a com.google.cloud.vision.v1 csomag részeként) több száz osztályt tartalmaz. Szerencsére azonban csak néhány kulcsfontosságú elem ismerete szükséges ahhoz, hogy látványos képfelismerési feladatokat hajtsunk végre. A legfontosabb osztály az ImageAnnotatorClient, amely különböző ...Annotate...() metódusaival képes helyi vagy távoli (felhőben tárolt) fájlokon elvégezni a detektálást.

A folyamat első lépése az ImageAnnotatorClient példányosítása. Ezt követően a tényleges felismerést a batchAnnotateImages() metódussal indíthatjuk el. A válaszként kapott objektum tartalmazza a detektált elemek listáját, amelyeket egyenként dolgozhatunk fel.

```java
// A kliens inicializálása, amely a kérések küldéséért felel.
// Ezt az objektumot érdemes újrahasznosítani több kérés esetén is.
try (ImageAnnotatorClient client = ImageAnnotatorClient.create()) {
   BatchAnnotateImagesResponse response = client.batchAnnotateImages(requests);
   List<AnnotateImageResponse> responses = response.getResponsesList();
   
   // A válaszok feldolgozása...
}
```


A batchAnnotateImages() metódus bemenetként egy List<AnnotateImageRequest> típusú listát vár. Ebben a listában kell elhelyezni azokat a kéréseket, amelyek meghatározzák, hogy milyen jellemzőket (features) szeretnénk keresni a képeken. A jellemzők típusát a Feature osztály definiálja (pl. TEXT_DETECTION).

```java
List<AnnotateImageRequest> requests = new ArrayList<>();
// Szövegfelismerés (TEXT_DETECTION) típusú jellemző kérése
Feature feat = Feature.newBuilder().setType(Feature.Type.TEXT_DETECTION).build();
AnnotateImageRequest request =
        AnnotateImageRequest.newBuilder().addFeatures(feat).setImage(img).build();
requests.add(request);
```


A rendszer számos egyéb detektálási módot is támogat, mint például: FACE_DETECTION (arcfelismerés), LANDMARK_DETECTION (nevezetességek), LOGO_DETECTION (logók), LABEL_DETECTION (képcímkézés), vagy a SAFE_SEARCH_DETECTION (nemkívánatos tartalmak szűrése). Amennyiben egyszerre több dolgot (például szöveget és logókat) is szeretnénk felismerni, több jellemzőt is hozzáadhatunk a kéréshez.

A meglévő bekezdés a támogatott detektálási módok listáját is kibővíthető, hogy hűen tükrözze a PDF-beli eredeti felsorolást. A jelenlegi lista (`FACE_DETECTION`, `LANDMARK_DETECTION`, `LOGO_DETECTION`, `LABEL_DETECTION`, `SAFE_SEARCH_DETECTION`) kiegészítendő a következőkkel: `CROP_HINTS`, `DOCUMENT_TEXT_DETECTION`, `IMAGE_PROPERTIES` (a kép domináns színeinek kiszámítása), `OBJECT_LOCALIZATION`, `PRODUCT_SEARCH`, valamint `TEXT_DETECTION`.

Ezt követően érdemes beilleszteni a PDF harmadik kódpéldáját, amely azt szemlélteti, hogyan kérhető egyszerre több jellemző detektálása. A következő kódrészlet illusztrálja, hogyan építhető fel a kérések listája, ha egyidejűleg szeretnénk szöveget, kézzel írott szöveget (document text) és logókat felismerni ugyanazon a képen (image).

```java
List<AnnotateImageRequest> requests = new ArrayList<>();
Feature feat1 = Feature.newBuilder().setType(Feature.Type.TEXT_DETECTION).build();
AnnotateImageRequest request1 =
        AnnotateImageRequest.newBuilder().addFeatures(feat1)
             .setImage(img).build();
Feature feat2 = Feature.newBuilder().setType(Feature.Type.DOCUMENT_TEXT_DETECTION)
             .build();
AnnotateImageRequest request2 = AnnotateImageRequest.newBuilder()
        .addFeatures(feat2).setImage(img).build();
Feature feat3 = Feature.newBuilder().setType(Feature.Type.LOGO_DETECTION).build();
AnnotateImageRequest request3 = AnnotateImageRequest.newBuilder()
        .addFeatures(feat3).setImage(img).build();

requests.add(request1);
requests.add(request2);
requests.add(request3);
```

### 11.2 Cloud Translation

A felhőalapú fordítási szolgáltatás Java osztályai a com.google.cloud.translate csomagban találhatók. Az API használatának belépési pontja a Translate interfész, amely egy szolgáltatási proxyt (proxy) képvisel.

Az alábbi példában a TranslateOptions osztály segítségével kérünk le egy alapértelmezett fordító szolgáltatást, majd a translate() metódussal elvégezzük a fordítást.

```java
import com.google.cloud.translate.*;
Translate translate = TranslateOptions.getDefaultInstance().getService();

// Spanyol szöveg fordítása (a forrásnyelv felismerése automatikus)
Translation translation = translate.translate("¡Hola Mundo!");
System.out.printf("Lefordított szöveg:\n\t%s\n", translation.getTranslatedText());
```


A fordítás paraméterezhető is: explicit módon megadhatjuk a forrás- és a célnyelvet (például spanyolról németre), valamint kiválaszthatjuk a használni kívánt modellt is (pl. a precízebb, neurális alapú nmt modellt). Az API „Advanced” verziója olyan haladó funkciókat is kínál, mint a saját szójegyzékek (glossaries) használata vagy nagy mennyiségű szöveg kötegelt feldolgozása.

A PDF eredeti szövegében a fordítás paraméterezését konkrét kódpélda is illusztrálja, amely jelenleg kizárólag prózai leírásként szerepel a magyar változatban. Javasolt az alábbi kódrészlet beszúrása, amely explicit módon beállítja a forrásnyelvet (source language) spanyolra, a célnyelvet (target language) németre, valamint a használandó modellt a prémium, neurális gépi fordításra (`nmt`).

```java
Translation translation =
    translate.translate(
        "Hola Mundo!",
        Translate.TranslateOption.sourceLanguage("es"),
        Translate.TranslateOption.targetLanguage("de"),
        // Use "base" for standard edition, "nmt" for the premium model.
        Translate.TranslateOption.model("nmt"));
```

A Translation API „Advanced” verziója olyan további funkciókat is kínál, mint például saját fordítási szójegyzékek (glossaries) létrehozása, illetve nagy mennyiségű szöveg kötegelt fordítása a képfelismerő példában bemutatotthoz hasonló kódszerkezettel, a `TranslationServiceClient` osztály és a `client.translateText(request)` hívás segítségével. A haladó üzemmód részletei a Translation szolgáltatás dokumentációjában találhatók meg.

### 11.3 Text-to-Speech

A Text-to-Speech szolgáltatás szöveges adatok emberi hangzású beszéddé alakítására szolgál a Google fejlett beszédszintézis-motorjai segítségével. A szolgáltatás szinte az összes világnyelvet támogatja, választható férfi és női hangokkal, valamint különböző technológiákkal (pl. WaveNet).

A programozáshoz szükséges osztályok a com.google.cloud.texttospeech.v1 csomagban érhetők el. A fő osztály a TextToSpeechClient. A folyamat során először egy SynthesisInput objektumba csomagoljuk a forrásszöveget, majd a VoiceSelectionParams segítségével beállítjuk a kívánt nyelvet és hangkaraktert. A kimeneti hangformátum (pl. MP3) meghatározása után a synthesizeSpeech() hívással generáljuk le az audio tartalmat, amelyet végül fájlba menthetünk.

A PDF-beli eredeti kódrészlet a teljes, önállóan futtatható `QuickstartSample` osztályt mutatja be, beleértve az `import` direktívákat is. A magyar változatból jelenleg hiányzik az importok blokkja és a külső osztály-keret. A következő kódrészlet illusztrálja a teljes, a PDF-fel megegyező mintaalkalmazást.

```java
// Imports the Google Cloud client library
import com.google.cloud.texttospeech.v1.AudioConfig;
import com.google.cloud.texttospeech.v1.AudioEncoding;
import com.google.cloud.texttospeech.v1.SsmlVoiceGender;
import com.google.cloud.texttospeech.v1.SynthesisInput;
import com.google.cloud.texttospeech.v1.SynthesizeSpeechResponse;
import com.google.cloud.texttospeech.v1.TextToSpeechClient;
import com.google.cloud.texttospeech.v1.VoiceSelectionParams;
import com.google.protobuf.ByteString;
import java.io.FileOutputStream;
import java.io.OutputStream;

/**
 * Google Cloud TextToSpeech API sample application. Example usage: mvn package exec:java
 *  -Dexec.mainClass='com.example.texttospeech.QuickstartSample'
 */
public class QuickstartSample {

  /** Demonstrates using the Text-to-Speech API. */
  public static void main(String... args) throws Exception {
    // Instantiates a client
    try (TextToSpeechClient textToSpeechClient = TextToSpeechClient.create()) {
      // Set the text input to be synthesized
      SynthesisInput input = SynthesisInput.newBuilder().setText(
                              "Hello, World!").build();

      // Build the voice request, select the language code ("en-US")
      // and the ssml voice gender
      // ("neutral")
      VoiceSelectionParams voice =
          VoiceSelectionParams.newBuilder()
            .setLanguageCode("en-US")
            .setSsmlGender(SsmlVoiceGender.NEUTRAL)
            .build();

      // Select the type of audio file you want returned
      AudioConfig audioConfig =
          AudioConfig.newBuilder().setAudioEncoding(AudioEncoding.MP3).build();

      // Perform the text-to-speech request on the text input with
      // the selected voice parameters and
      // audio file type
      SynthesizeSpeechResponse response =
          textToSpeechClient.synthesizeSpeech(input, voice, audioConfig);

      // Get the audio contents from the response
      ByteString audioContents = response.getAudioContent();

      // Write the response to the output file.
      try (OutputStream out = new FileOutputStream("output.mp3")) {
        out.write(audioContents.toByteArray());
        System.out.println("Audio content written to file \"output.mp3\"");
      }
    }
  }
}
```
---

## 12. Felhőszolgáltatás-orkesztráció

Ennek a fejezetnek a célja, hogy szintetizálja az előző fejezetekben tárgyalt ismereteket, és megvizsgálja, miként teszi lehetővé a felhőtechnológia olyan hasznos, funkciókban gazdag és megbízható alkalmazások létrehozását, amelyek hatékonyan képesek kiszolgálni nagy számú felhasználót. Létrehozhatunk saját szolgáltatásokat specifikus funkciók biztosítására, vagy felhasználhatunk a felhőszolgáltatóktól, illetve harmadik fél fejlesztőktől származó kész szolgáltatásokat is jövőbeli alkalmazásaink komponenseiként. A szolgáltatók olyan integrációs technológiákat kínálnak, amelyekkel ezek a komponensek egyszerűen és hatékonyan összekapcsolhatók, lehetővé téve az elosztott felhőalkalmazások globális léptékű működtetését.

A Google Cloud Platform esetében a rendelkezésünkre álló kulcsfontosságú technológiák a következők: infrastrukturális szolgáltatások (Cloud Storage az adattároláshoz, valamint Dataproc vagy Dataflow a számításokhoz), a Cloud Functions és a Pub/Sub az integrációhoz, valamint a különböző alkalmazásspecifikus felhőszolgáltatások a speciális feladatok elvégzéséhez.

A szolgáltatások vagy szolgáltatáskomponensek ilyen módon történő integrációját gyakran orkesztrációnak (vagy hangszerelésnek) nevezzük. Ez a kifejezés a komponensek és szolgáltatások összehangolt használatát és végrehajtását jelenti egy komplex feladat elvégzése érdekében. Ezeket az összetett feladatokat jellemzően munkafolyamat-gráfokként (workflow graphs) írják le, amelyek feldolgozási lépések sorozatát hajtják végre lazán csatolt (loosely coupled) módon.

Ebben a fejezetben bemutatunk egy mintaprogramot, amely szemlélteti a felhőszolgáltatások integrációjának eleganciáját és az eddig tanult különféle technológiák gyakorlati alkalmazását.

### 12.1 Komplex optikai karakterfelismerő (OCR) alkalmazás példája

Az itt ismertetett program a Google Cloud Platform hivatalos dokumentációjának részét képezi. Az alkalmazás célja a felhőbe feltöltött képek elemzése, a bennük található szöveges tartalom kinyerése, a szöveg lefordítása egy megadott nyelvre, végül pedig az eredmény elmentése a felhő egy meghatározott tárhelyére. Az alkalmazás munkafolyamatát és architektúráját a 12-1. ábra szemlélteti.

*12-1. ábra: Komplex OCR alkalmazás munkafolyamata és architektúrája*

![12-1. ábra](<../Cloud Programming_MSc_Juhasz_IId-110_1.png>)


A végrehajtás sorrendje a következő:

Egy képfájl feltöltése a Google Cloud Storage-ba.

A feltöltés kivált (triggerel) egy felhőfüggvényt, amely meghívja a Vision AI szolgáltatást a kép szöveges tartalmának kinyeréséhez.

A kinyert szöveg beíródik egy meghatározott Pub/Sub témakörbe.

A témaüzenet aktivál egy újabb felhőfüggvényt, amely meghívja a Cloud Translation szolgáltatást.

A lefordított szöveges üzenetek bekerülnek egy másik Pub/Sub témakörbe.

Végül egy újabb felhőfüggvény aktiválódik, amely az eredményeket elmenti a Google Cloud Storage-ba.

A szöveg kinyeréséért felelős függvény
Az alábbi kódrészlet egy Cloud Storage esemény által kiváltott háttérfüggvényt implementál az `accept()` metódus segítségével. Ez a függvény végzi el a szövegfelismerési feladatot, és az eredményt közzéteszi egy Pub/Sub témakörben.

Az `accept()` metódus lekéri a fájlt a tárolóvödörből, majd meghívja a `detectText()` metódust. Ebben történnek a fő feldolgozási lépések: először egy `ImageAnnotatorClient` példány jön létre, majd a szöveg detektálása következik a `batchAnnotateImages` metódussal, a kérést `TEXT_DETECTION` típusúra állítva. Ezután a Vision API segítségével a rendszer megpróbálja azonosítani a kép szövegének nyelvét is a `TranslationServiceClient` használatával. Utolsó lépésként minden azonosított nyelvhez egy fordítási üzenetet tesz közzé a Pub/Sub-on keresztül.

Példa a szöveg- és nyelvfelismerést végző függvényre:

```java
import com.google.cloud.functions.BackgroundFunction;
import com.google.cloud.functions.Context;
import com.google.cloud.pubsub.v1.Publisher;
import com.google.cloud.translate.v3.DetectLanguageRequest;
import com.google.cloud.translate.v3.DetectLanguageResponse;
import com.google.cloud.translate.v3.LocationName;
import com.google.cloud.translate.v3.TranslationServiceClient;
import com.google.cloud.vision.v1.AnnotateImageRequest;
import com.google.cloud.vision.v1.AnnotateImageResponse;
import com.google.cloud.vision.v1.Feature;
import com.google.cloud.vision.v1.Image;
import com.google.cloud.vision.v1.ImageAnnotatorClient;
import com.google.cloud.vision.v1.ImageSource;
import com.google.protobuf.ByteString;
import com.google.pubsub.v1.ProjectTopicName;
import com.google.pubsub.v1.PubsubMessage;
import functions.eventpojos.GcsEvent;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;
import java.util.concurrent.ExecutionException;
import java.util.logging.Level;
import java.util.logging.Logger;

public class OcrProcessImage implements BackgroundFunction<GcsEvent> {
  // TODO<developer> set these environment variables
  private static final String PROJECT_ID = System.getenv("GCP_PROJECT");
  private static final String TRANSLATE_TOPIC_NAME = System.getenv("TRANSLATE_TOPIC");
  private static final String[] TO_LANGS = System.getenv("TO_LANG").split(",");

  private static final Logger logger = Logger.getLogger(OcrProcessImage.class.getName());
  private static final String LOCATION_NAME = LocationName.of(PROJECT_ID, "global").toString();
  private Publisher publisher;

  public OcrProcessImage() throws IOException {
    publisher = Publisher.newBuilder(
        ProjectTopicName.of(PROJECT_ID, TRANSLATE_TOPIC_NAME)).build();
  }

  @Override
  public void accept(GcsEvent gcsEvent, Context context) {

    // Validate parameters
    String bucket = gcsEvent.getBucket();
    if (bucket == null) {
      throw new IllegalArgumentException("Missing bucket parameter");
    }
    String filename = gcsEvent.getName();
    if (filename == null) {
      throw new IllegalArgumentException("Missing name parameter");
    }

    detectText(bucket, filename);
  }

  private void detectText(String bucket, String filename) {
    logger.info("Looking for text in image " + filename);

    List<AnnotateImageRequest> visionRequests = new ArrayList<>();
    String gcsPath = String.format("gs://%s/%s", bucket, filename);

    ImageSource imgSource = ImageSource.newBuilder().setGcsImageUri(gcsPath).build();
    Image img = Image.newBuilder().setSource(imgSource).build();

    Feature textFeature = Feature.newBuilder().setType(Feature.Type.TEXT_DETECTION).build();
    AnnotateImageRequest visionRequest =
        AnnotateImageRequest.newBuilder().addFeatures(textFeature).setImage(img).build();
    visionRequests.add(visionRequest);

    // Detect text in an image using the Cloud Vision API
    AnnotateImageResponse visionResponse;
    try (ImageAnnotatorClient client = ImageAnnotatorClient.create()) {
      visionResponse = client.batchAnnotateImages(visionRequests).getResponses(0);
      if (visionResponse == null || !visionResponse.hasFullTextAnnotation()) {
        logger.info(String.format("Image %s contains no text", filename));
        return;
      }

      if (visionResponse.hasError()) {
        // Log error
        logger.log(Level.SEVERE, "Error in vision API call: " +
            visionResponse.getError().getMessage());
        return;
      }
    } catch (IOException e) {
      // Log error (since IOException cannot be thrown by a Cloud Function)
      logger.log(Level.SEVERE, "Error detecting text: " + e.getMessage(), e);
      return;
    }

    String text = visionResponse.getFullTextAnnotation().getText();
    logger.info("Extracted text from image: " + text);

    // Detect language using the Cloud Translation API
    DetectLanguageRequest languageRequest =
        DetectLanguageRequest.newBuilder()
            .setParent(LOCATION_NAME)
            .setMimeType("text/plain")
            .setContent(text)
            .build();
    DetectLanguageResponse languageResponse;
    try (TranslationServiceClient client = TranslationServiceClient.create()) {
      languageResponse = client.detectLanguage(languageRequest);
    } catch (IOException e) {
      // Log error (since IOException cannot be thrown by a function)
      logger.log(Level.SEVERE, "Error detecting language: " + e.getMessage(), e);
      return;
    }

    if (languageResponse.getLanguagesCount() == 0) {
      logger.info("No languages were detected for text: " + text);
      return;
    }

    String languageCode = languageResponse.getLanguages(0).getLanguageCode();
    logger.info(String.format("Detected language %s for file %s", languageCode, filename));

    // Send a Pub/Sub translation request for every language we're going to translate to
    for (String targetLanguage : TO_LANGS) {
      logger.info("Sending translation request for language " + targetLanguage);
      OcrTranslateApiMessage message = new OcrTranslateApiMessage(
          text, filename, targetLanguage);
      ByteString byteStr = ByteString.copyFrom(message.toPubsubData());
      PubsubMessage pubsubApiMessage = PubsubMessage.newBuilder().setData(byteStr).build();
      try {
        publisher.publish(pubsubApiMessage).get();
      } catch (InterruptedException | ExecutionException e) {
        // Log error
        logger.log(Level.SEVERE, "Error publishing translation request: " + e.getMessage(), e);
        return;
      }
    }
  }
}
```

A szöveg fordításáért felelős függvény
Az alkalmazás következő fázisában történik a fordítás. Az `OcrTranslateText` osztály egy olyan háttérfüggvényt implementál, amely a Pub/Sub témakörből érkező fordítási kérésekre válaszol. Az `accept()` metódust a rendszer minden beérkező üzenethez meghívja. Első feldolgozási lépésként a metódus kinyeri a forrásszöveget és a célnyelv kódját a beérkező üzenetből, majd létrehoz egy `TranslationServiceClient` példányt. Ezt követően egy megfelelő fordítási kérés objektum készül, majd a szöveg fordítása a `translateText` metódus meghívásával történik meg. A visszakapott lefordított szöveg és a kimeneti fájl neve egy új Pub/Sub üzenetbe csomagolva kerül továbbításra a felhőbe a konstruktorban létrehozott `publisher.publish` metóduson keresztül.

Példa a fordítást végző függvényre:

```java
import com.google.cloud.functions.BackgroundFunction;
import com.google.cloud.functions.Context;
import com.google.cloud.pubsub.v1.Publisher;
import com.google.cloud.translate.v3.LocationName;
import com.google.cloud.translate.v3.TranslateTextRequest;
import com.google.cloud.translate.v3.TranslateTextResponse;
import com.google.cloud.translate.v3.TranslationServiceClient;
import com.google.protobuf.ByteString;
import com.google.pubsub.v1.ProjectTopicName;
import com.google.pubsub.v1.PubsubMessage;
import functions.eventpojos.PubSubMessage;
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.util.concurrent.ExecutionException;
import java.util.logging.Level;
import java.util.logging.Logger;

public class OcrTranslateText implements BackgroundFunction<PubSubMessage> {
  private static final Logger logger = Logger.getLogger(OcrTranslateText.class.getName());

  // TODO<developer> set these environment variables
  private static final String PROJECT_ID = getenv("GCP_PROJECT");
  private static final String RESULTS_TOPIC_NAME = getenv("RESULT_TOPIC");
  private static final String LOCATION_NAME = LocationName.of(
      PROJECT_ID, "global").toString();

  private Publisher publisher;

  public OcrTranslateText() throws IOException {
    publisher = Publisher.newBuilder(
        ProjectTopicName.of(PROJECT_ID, RESULTS_TOPIC_NAME)).build();
  }

  @Override
  public void accept(PubSubMessage pubSubMessage, Context context) {
    OcrTranslateApiMessage ocrMessage = OcrTranslateApiMessage.fromPubsubData(
        pubSubMessage.getData().getBytes(StandardCharsets.UTF_8));

    String targetLang = ocrMessage.getLang();
    logger.info("Translating text into " + targetLang);

    // Translate text to target language
    String text = ocrMessage.getText();
    TranslateTextRequest request =
        TranslateTextRequest.newBuilder()
            .setParent(LOCATION_NAME)
            .setMimeType("text/plain")
            .setTargetLanguageCode(targetLang)
            .addContents(text)
            .build();

    TranslateTextResponse response;
    try (TranslationServiceClient client = TranslationServiceClient.create()) {
      response = client.translateText(request);
    } catch (IOException e) {
      // Log error (since IOException cannot be thrown by a function)
      logger.log(Level.SEVERE, "Error translating text: " + e.getMessage(), e);
      return;
    }
    if (response.getTranslationsCount() == 0) {
      return;
    }

    String translatedText = response.getTranslations(0).getTranslatedText();
    logger.info("Translated text: " + translatedText);

    // Send translated text to (subsequent) Pub/Sub topic
    String filename = ocrMessage.getFilename();
    OcrTranslateApiMessage translateMessage = new OcrTranslateApiMessage(
        translatedText, filename, targetLang);
    try {
      ByteString byteStr = ByteString.copyFrom(translateMessage.toPubsubData());
      PubsubMessage pubsubApiMessage = PubsubMessage.newBuilder().setData(byteStr).build();

      publisher.publish(pubsubApiMessage).get();
      logger.info("Text translated to " + targetLang);
    } catch (InterruptedException | ExecutionException e) {
      // Log error (since these exception types cannot be thrown by a function)
      logger.log(Level.SEVERE, "Error publishing translation save request: " + e.getMessage(), e);
    }
  }

  // Avoid ungraceful deployment failures due to unset environment variables.
  // If you get this warning you should redeploy with the variable set.
  private static String getenv(String name) {
    String value = System.getenv(name);
    if (value == null) {
      logger.warning("Environment variable " + name + " was not set");
      value = "MISSING";
    }
    return value;
  }
}
```

Az eredmények mentéséért felelős függvény
Az alkalmazás utolsó függvénye a fordítási eredmények elmentéséért felelős egy Cloud Storage tárolóvödörbe. A Storage szolgáltatásügyfélre mutató referenciát az osztály statikus blokkja szerzi meg. Az `accept()` metódus meghívásakor a bejövő üzenetből kinyeri a kimeneti fájl nevét és a nyelvi kódot, majd ezekből összefűzéssel egy új fájlnevet hoz létre. A lefordított szöveg végül a `Storage.create()` metódus segítségével íródik ki az új fájlba.

Példa az eredmény mentését végző függvényre:

```java
import com.google.cloud.functions.BackgroundFunction;
import com.google.cloud.functions.Context;
import com.google.cloud.storage.BlobId;
import com.google.cloud.storage.BlobInfo;
import com.google.cloud.storage.Storage;
import com.google.cloud.storage.StorageOptions;
import functions.eventpojos.PubSubMessage;
import java.nio.charset.StandardCharsets;
import java.util.logging.Logger;

public class OcrSaveResult implements BackgroundFunction<PubSubMessage> {
  // TODO<developer> set this environment variable
  private static final String RESULT_BUCKET = System.getenv("RESULT_BUCKET");

  private static final Storage STORAGE = StorageOptions.getDefaultInstance().getService();
  private static final Logger logger = Logger.getLogger(OcrSaveResult.class.getName());

  @Override
  public void accept(PubSubMessage pubSubMessage, Context context) {
    OcrTranslateApiMessage ocrMessage = OcrTranslateApiMessage.fromPubsubData(
        pubSubMessage.getData().getBytes(StandardCharsets.UTF_8));

    logger.info("Received request to save file " + ocrMessage.getFilename());

    String newFileName = String.format(
        "%s_to_%s.txt", ocrMessage.getFilename(), ocrMessage.getLang());

    // Save file to RESULT_BUCKET with name newFileNaem
    logger.info(String.format("Saving result to %s in bucket %s", newFileName, RESULT_BUCKET));
    BlobInfo blobInfo = BlobInfo.newBuilder(BlobId.of(RESULT_BUCKET, newFileName)).build();
    STORAGE.create(blobInfo, ocrMessage.getText().getBytes(StandardCharsets.UTF_8));
    logger.info("File saved");
  }
}
```

Összegzés
Az alkalmazás üzembe helyezéséhez a fenti függvényeket telepíteni kell a felhőbe, majd létre kell hozni a szükséges Storage vödröket és Pub/Sub témaköröket. Amint egy képfájlt feltöltünk a bemeneti tárolóba, a teljes folyamat automatikusan végrehajtódik.

Ez a példa jól szemlélteti a felhőszolgáltatás-orkesztráció alapvető koncepcióit, valamint a lazán csatolt, üzenet- és eseményalapú kommunikáció egyszerűségét és hatékonyságát. A fejlesztőnek nem kell az infrastruktúra kezelésével foglalkoznia, kizárólag az alkalmazás logikájára fókuszálhat. A Cloud Functions automatikus skálázásának köszönhetően a rendszer tetszőleges számú kérést képes kiszolgálni további beavatkozás nélkül.

---

## 13. Következtetések

E könyv elsődleges célja az volt, hogy átfogó háttéranyagot biztosítson a Pannon Egyetem Felhőprogramozás MSc kurzusához. Ennek megfelelően nem törekedett arra, hogy a felhőalapú számítástechnika valamennyi elméleti és gyakorlati aspektusát lefedő, lezárt mű legyen. A kurzus fókusza kifejezetten a felhőrendszerek programozásán állt, szemben a felhőinfrastruktúrák kiépítésével és üzemeltetésével, ezért a rendszermenedzsmenttel kapcsolatos témákat nagyrészt érintetlenül hagytuk. Szintén nem volt célunk a programozási technikák olyan mélységű tárgyalása, amely a professzionális felhőfejlesztők napi munkájához szükséges; ugyanakkor bízom benne, hogy a könyv hasznos bevezetést nyújtott a legfontosabb alapfogalmakba. Reményeim szerint az itt bemutatott gyakorlati programozási részletek elegendő alapot adnak az érdeklődő hallgatóknak ahhoz, hogy önállóan is elinduljanak a felhőalapú számítástechnika rendkívül izgalmas világában.

Bár a jövőt soha nem lehet hajszálpontosan megjósolni, nagy biztonsággal kijelenthető, hogy a felhőrendszerek szerepe és képességei a következő években folyamatosan bővülni fognak. Ez alapvető változásokat hoz a fejlesztők munkájába és a teljes szoftveripar működésébe is. Ahogyan korábban a webes technológiák forradalmasították az asztali és mobilalkalmazásokat, úgy a felhő is hasonlóan mély hatást fog gyakorolni a jövő szoftvereire. Már ma is elvárás, hogy az alkalmazások legalább az adatbeviteli és kimeneti (I/O) műveletek szintjén integrálódjanak a felhővel, lehetővé téve az ott tárolt adatok feldolgozását vagy az eredmények felhőbe mentését. A jövő alkalmazásai egyre intenzívebben fognak támaszkodni a felhőszolgáltatásokra, ami végül valódi, felhő-natív (cloud-native) komponensekből felépülő szoftverrendszerekhez vezet.

A felhőszolgáltatók mindent megtesznek rendszereik rendelkezésre állásának, megbízhatóságának és biztonságának javítása érdekében. A fokozódó piaci verseny, valamint a tiszta energiák használata hosszú távon várhatóan csökkenti az árakat, így a felhő alapú számítástechnika az innováció és az emberiség fejlődésének megfizethető és megbízható platformjává válik. Számos olyan trend figyelhető meg, amely a jövő felhőrendszereit még a maiaknál is érdekesebbé teszi: a nagy teljesítményű számítástechnika (HPC) és a mesterséges intelligencia (AI) egyre szervesebben épül be a felhőbe. Várható, hogy a szolgáltatók hamarosan igény szerinti szuperszámítógépes erőforrásokat és speciális, AI-munkaterhelésekre tervezett infrastruktúrákat tesznek elérhetővé mindenki számára. Ez új szolgáltatások, sőt teljes iparágak kialakulásához vezethet. A Dolgok Internete (IoT) eszközeiből származó adatok elemzése várhatóan forradalmasítja a gyártást és a logisztikát, a testközeli szenzorokkal és felhőalapú diagnosztikával kombinálva pedig az egészségügyi ellátórendszereinket is gyökeresen átalakíthatja.

Ezek csupán rövid bepillantások voltak abba, amit a jövő tartogathat. Annyi bizonyos, hogy ez a jövő fényes és izgalmas távlatokat nyit. Ne maradjon le Ön sem: kövesse az eseményeket, és váljon a jövő informatikájának aktív részesévé! 

## Irodalomjegyzék

[1] L. Dagum és R. Menon: OpenMP: an industry standard API for shared-memory programming. IEEE Comput. Sci. Eng., vol. 5, no. 1, pp. 46–55, 1998. 

[2] W. Gropp: MPI: the complete reference. Vol. 2, The MPI-2 extensions. Cambridge, Mass., M.I.T. Press, 1998. 

[3] W. Gropp, E. L. Lusk és A. Skjellum: Using MPI: portable parallel programming with the Message-Passing Interface. Cambridge, Mass., MIT Press, 1994. 

[4] Nvidia: CUDA C Programming Guide. [Online]. Elérhető: https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html 

[5] R. Thurlow: RPC: Remote Procedure Call Protocol Specification Version 2. 

[6] A. D. Birrell és B. J. Nelson: Implementing remote procedure calls. 

[7] J. Waldo: Remote procedure calls and Java Remote Method Invocation. IEEE Concurr., vol. 6, no. 3, pp. 5–7, 2002. 

[8] V. S. Sunderam: PVM: A Framework for Parallel Distributed Computing. 

[9] A. S. Grimshaw és W. A. Wulf: The Legion Vision of a Worldwide Virtual Computer. Commun. ACM, vol. 40, no. 1, pp. 39–45, 1997. 

[10] I. Foster és C. Kesselman: Globus: A metacomputing infrastructure toolkit. Int. J. High Perform. Comput. Appl., vol. 11, no. 2, pp. 115–128, 1997. 

[11] K. Czajkowski, I. Foster, N. Karonis, C. Kesselman, S. Tuecke és M. Rey: A Resource Management Architecture for Metacomputing Systems. pp. 1–19. 

[12] E. J. Korpela, D. P. Anderson és J. Cobb: SETI@home-massively distributed computing for SETI. Comput. Sci. Eng., vol. 3, no. 1, pp. 78–83, 2001. 

[13] Amazon Web Services (AWS) - Cloud Computing Services. [Online]. Elérhető: https://aws.amazon.com/ 

[14] Apache Hadoop. [Online]. Elérhető: http://hadoop.apache.org/ 

[15] Apache Spark™ - Unified Analytics Engine for Big Data. [Online]. Elérhető: http://spark.apache.org/ 

[16] T. F. Chan, G. H. Golub és R. J. Leveque: Statistical computing: Algorithms for computing the sample variance: Analysis and recommendations. Am. Stat., vol. 37, no. 3, pp. 242–247, 1983. 

[17] B. P. Welford: Note on a Method for Calculating Corrected Sums of Squares and Products. Technometrics, vol. 4, no. 3, pp. 419–420, 1962. 

[18] Spark Streaming | Apache Spark. [Online]. Elérhető: https://spark.apache.org/streaming/ 

[19] Apache Flink: Stateful Computations over Data Streams. [Online]. Elérhető: https://flink.apache.org/ 

[20] Apache Storm. [Online]. Elérhető: http://storm.apache.org/ 

[21] Apache Beam. [Online]. Elérhető: https://beam.apache.org/ 

[22] D. García-Gil, S. Ramírez-Gallego, S. García és F. Herrera: A comparison on scalability for batch big data processing on Apache Spark and Apache Flink. Big Data Anal., vol. 2, no. 1, 2017. 

[23] S. Chatterjee és C. Morin: Experimental study on the performance and resource utilization of data streaming frameworks. Proceedings of the 18th IEEE/ACM CCGRID, 2018, pp. 143–152. 

[24] B. Blamey, A. Hellander és S. Toor: Apache spark streaming, kafka and harmonicio: a performance benchmark and architecture comparison for enterprise and scientific computing. LNCS, vol. 12093, pp. 335–347, 2020. 

[25] Z. Karakaya, A. Yazici és M. Alayyoub: A Comparison of Stream Processing Frameworks. International Conference on Computer and Applications (ICCA), 2017, pp. 1–12. 

[26] C. Prakash: Spark Streaming vs Flink vs Storm vs Kafka Streams vs Samza: Choose Your Stream Processing Framework. Medium, 2021. 

[27] Cloud Functions | Google Cloud. [Online]. Elérhető: https://cloud.google.com/functions 

[28] AWS Lambda – Serverless Compute. [Online]. Elérhető: https://aws.amazon.com/lambda/
