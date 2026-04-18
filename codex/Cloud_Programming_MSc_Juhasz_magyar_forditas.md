# Felhőprogramozás
Juhász Zoltán

Pannon Egyetem
2020

## Előszó

A felhőtechnológia a számítástechnika viszonylag új, ugyanakkor rendkívül izgalmas területe. A tudományos világ és az ipar több évtizedes kutatás-fejlesztési munkája az elosztott rendszerek, a hálózatok, a virtualizáció és a szolgáltatásorientált számítástechnika terén mára gyakorlati valósággá érett. Ennek eredményeként szinte korlátlan számítási és tárolási kapacitás áll rendelkezésre, amelyre új típusú alkalmazások és szolgáltatások épülhetnek, felhasználók millióit kiszolgálva.

Ez a könyv a felhőrendszerek programozási vonatkozásaihoz kíván bevezetést nyújtani.

Mivel a felhőrendszereket egyre inkább nagy technológiai vállalatok magasan specializált adatközpontjai üzemeltetik, az egyéni fejlesztők és a kisebb cégek számára a legnagyobb lehetőségek a szoftveroldalon rejlenek.

Az a témamennyiség, amelyet ebben a könyvben feldolgozhatnánk, óriási. Ezért elsősorban a legalapvetőbb fogalmak, módszerek és programozási technikák bemutatására koncentrálunk. A cél az, hogy ezek megfelelő alapot adjanak a hallgatóknak a későbbi, specializáltabb tanulmányokhoz.

E könyv tartalma szorosan kapcsolódik a Pannon Egyetem Műszaki Informatikai Karának MSc hallgatók számára meghirdetett Cloud Programming kurzusához. Bár a könyv bevezető jellegű, a kurzus elvégzéséhez szükséges a Java programozás gyakorlati ismerete, valamint a számítógép-architektúra, az operációs rendszerek és az elosztott rendszerek alapfogalmainak ismerete. A fejezeteket nem feltétlenül kell a könyvben szereplő sorrendben olvasni, de azok számára, akik még nem jártasak a témában, ez a sorrend valószínűleg a legcélszerűbb.

Bár mindent megtettünk a hibátlan kézirat elkészítéséért, előfordulhatnak benne hibák és hiányosságok. Ezekért kizárólag a szerző vállal felelősséget. A könyv továbbfejlesztése érdekében a szerző örömmel fogad minden olvasói visszajelzést és észrevételt.

Az Európai Unió és a Magyar Kormány EFOP-3.4.3-A.2.3 számú támogatásáért ezúton is köszönetet mondunk.

Dr. Juhász Zoltán

## 1. Bevezetés

Az elmúlt évtizedben a „felhő” közismert fogalommá vált. Adatainkat a felhőben tároljuk, és nap mint nap olyan szolgáltatásokat használunk, mint a Gmail, az Amazon, a Netflix, a Spotify, különféle webáruházak vagy online hírszolgáltatások, anélkül hogy belegondolnánk, fizikailag hol működnek, hogyan valósulnak meg, vagy miként üzemeltetik őket. Létezésüket és rendelkezésre állásukat magától értetődőnek vesszük.

A számítástechnikai és informatikai iparnak több évtizednyi kutatás-fejlesztésre és több ezer emberévnyi munkára volt szüksége ahhoz, hogy ezek a rendszerek, és mindenekelőtt maga a felhő megszülessen. Mindannyian ismerjük a felhő körüli hívószavakat: korlátlan tárhely és számítási kapacitás, igény szerinti használat, alacsony költség, skálázhatóság, magas rendelkezésre állás, rugalmasság, a szolgáltatások integrálhatósága és hasonlók. Azt is tudjuk, hogy valahol a világban hatalmas adatközpontok adják a felhőinfrastruktúra gerincét. Ezeket jellemzően globális nagyvállalatok üzemeltetik, részben a felhőszolgáltatóvá váláshoz szükséges rendkívül magas beruházási igény, részben pedig a valóban világszintű szolgáltatásnyújtás követelményei miatt.

Ez a könyv a felhőt egy szoftverfejlesztő szemszögéből vizsgálja. Nem a működtetési vagy napi üzemeltetési kérdésekre koncentrálunk, hanem arra, hogy ez az új közeg miként alakítja át a szoftverfejlesztési gyakorlatot, illetve az alkalmazások létrehozásának és telepítésének módját.

A felhőhöz kapcsolódó gyakori kifejezések közül, mint a Cloud Computing, a Cloud Architecture és a Cloud Programming, ebben a könyvben elsősorban a felhőprogramozással foglalkozunk részletesen.

E könyvnek, és magának a kurzusnak sem pusztán az a célja, hogy gyakorlati programozási ötleteket adjon. A remény az, hogy a kurzus végére a hallgatók tágabb perspektívát és mélyebb megértést szereznek azokról az elméleti és technológiai folyamatokról, amelyek iparágunkat a felhő felé terelték. A modern számítástechnika és szoftverfejlesztés fő kihívásainak megértéséhez a 2. fejezet rövid áttekintést ad azokról a kulcsfontosságú fejleményekről, amelyek a felhőtechnológia előzményeinek és előfeltételeinek tekinthetők. Olyan témákat érintünk majd, mint az erőforrás-megosztás, a hálózati technológiák fejlődése, a különböző nagy teljesítményű számítástechnikai rendszerek vagy az elosztott rendszerek programozási kihívásai. E területek érettsége teremtette meg azt az alapot, amelyre a felhő épülhetett.

A könyv következő része általános szempontból tárgyalja a felhőt. Bemutatjuk legfontosabb jellemzőit, valamint architekturális, működési és szoftveres vonatkozásait. Ezt követi a meghatározó felhőszolgáltatók áttekintése: rövid történetük, piaci szerepük és jelentőségük, illetve szolgáltatáskínálatuk főbb elemei.

Ezután áttérünk a programozási kérdésekre. Az infrastruktúra-összetevőkkel kezdünk: a tárolással, a számítási kapacitással és az adatátvitellel, mivel ezek jelentik minden felhőrendszer alapvető építőköveit.

Ezek után következnek a magasabb szintű szolgáltatások, amelyek megkönnyítik a fejlesztők munkáját. Ide tartoznak például az alkalmazásszolgáltatások és a webalapú rendszerek fejlesztésében gyakran használt speciális alkalmazásplatformok.

A skálázhatóság fogalmára építve megvizsgáljuk, hogyan hajthatók végre nagy számítási feladatok több végrehajtási szolgáltatás együttes használatával. Áttekintjük a népszerű végrehajtási mintákat is, például a MapReduce megközelítést.

A végrehajtási példákat, és általában a könyv gyakorlati példáit a Google Cloud Platformra építjük. Ennek oka, hogy a Google évek óta nagylelkűen biztosít ingyenes hozzáférést hallgatóink számára a felhőrendszeréhez, emellett magas szintű támogatás és jó dokumentáció áll rendelkezésre az érdeklődők számára. A könyv utolsó fejezeteiben szó lesz az adatfolyam-feldolgozásról, a Cloud Functionsről, a publish/subscribe kommunikációról, az AI-szolgáltatásokról és a szolgáltatás-orkesztrációról is.

A könyv fő célja, hogy segítse a felhőalapú számítástechnika általános megértését és megbecsülését, valamint hogy a hallgatók megfelelő szintű ismereteket szerezzenek azokról a technológiákról és szoftveres módszerekről, amelyekre későbbi pályájuk során építhetnek.

MSc képzésünkben az anyagot gyakorlati programozási foglalkozások egészítik ki, amelyek során a hallgatók meglévő felhőalkalmazás-mintákat futtathatnak és módosíthatnak, valamint tapasztalatot szerezhetnek önálló programok fejlesztésében is. Azoknak az olvasóknak, akik önállóan dolgozzák fel az anyagot, érdemes az egyes fejezetekhez kapcsolódó mintaprogramokat is megkeresniük.

## 2. A múlt technológiai fejlesztései: út a felhőalapú számítástechnikához

A számítástechnika Szent Grálja egy olyan rendszer, amely rendkívül nagy teljesítményű, ingyenesen vagy nagyon olcsón használható, bárki számára hozzáférhető, megbízható és széles körben elérhető, továbbá gyors, hatékony és egyszerű módszereket kínál alkalmazások fejlesztésére és telepítésére, miközben a végfelhasználók számára a lehető legjobb használhatóságot biztosítja. Ezt a varázslatos rendszert még nem találtuk meg, de a jelenlegi jelöltek közül valószínűleg a felhő áll hozzá a legközelebb.

Ennek a fejezetnek az a célja, hogy bemutassa a nagy számítástechnikai rendszerekben tipikusan felmerülő problémákat, és áttekintse azokat a technológiai megoldásokat, amelyeket az elmúlt évtizedekben dolgoztak ki ezek kezelésére. Azt is szeretnénk érzékeltetni, hogy a felhőalapú számítástechnika nem teljesen új és egyedi fogalom, hanem az elosztott számítástechnikai rendszerekben végzett több évtizedes, szisztematikus kutatás és fejlesztés eredménye.

Ebben a fejezetben a technológiai fejlődés áttekintése nem annyira az egyes technológiák műszaki részleteire összpontosít, hanem inkább azokra a problémákra, amelyeket megpróbáltak megoldani, arra, hogy ezt milyen módon tették, és arra a fogalmi útra, amely a felhőalapú számítástechnika megjelenéséhez vezetett. Az egyes alfejezetek végén kiemeljük, hogy az adott technológia vagy annak alapfogalmai hogyan illeszkednek a modern felhőrendszerek világába.

### 2.1 A számítási erőforrásokhoz való hozzáférés és azok megosztása

Az első központi problématerület, amelyet megvizsgálunk, az, amit az erőforrás-megosztás problémájának nevezhetünk. Egy számítástechnikai rendszert úgy kell birtokolni és üzemeltetni, hogy a költsége minimális legyen, a kihasználtsága maximális legyen, és a felhasználók által érzékelt teljesítmény is a lehető legjobb maradjon. Ezek azonban egymásnak ellentmondó követelmények, amelyeket nehéz egyszerre kielégíteni. Tekintsünk vissza a számítástechnika történetére, és nézzük meg, milyen formában és milyen szinten jelent meg az erőforrás-megosztás kérdése a különböző számítástechnikai rendszerekben.

#### 2.1.1 Korlátozott erőforrású rendszerek: a nagyszámítógépek

A számítástechnika korai időszakában a számítógépek nagyok, drágák és ritkák voltak, és jellemzően speciális számítóközpontokban kaptak helyet. Ezek a nagyszámítógépek különlegesen képzett műszaki személyzetet igényeltek mind az üzemeltetéshez, mind a programozáshoz. A gépek többnyire csak kevés, speciális célú programot futtattak, amelyeket egy-egy kutatási vagy üzleti feladatra készítettek.

A legtöbb rendszer egyszerre csak egyetlen programot tudott végrehajtani, ezért a futási időréseket előre le kellett foglalni. Mivel a számítógépeket központilag helyezték el és kezelték, a rendszergazdák optimalizált futtatási ütemterveket tudtak készíteni, amelyek magas kihasználtságot és ebből következően alacsonyabb fajlagos költséget eredményeztek. Fontos megjegyezni, hogy egy számítógépes rendszer egységnyi működési költsége erősen függ a kihasználtságtól. Ha egy rendszer, amelynek induló költsége például 10 000 USD, 100 000 órán keresztül, vagyis nagyjából 11 éven át, 100%-os kihasználtsággal működik, akkor egy óra programfuttatás költsége 0,1 dollár. Ha ugyanez a rendszer az idő 90%-ában tétlen, akkor az effektív programfuttatási költség 1 USD/órára nő. Ezért a magas kihasználtság fenntartása alapvető cél volt az ilyen rendszerek üzemeltetésében.

A későbbi technológiai fejlődés nyomán megjelentek az időosztásos és időszeletelt működési módok, amelyekben a felhasználók terminálokon keresztül egy időben használhatták ugyanazt a számítógépet. A folyamatos fejlődés ellenére ezeknek a központosított nagyszámítógépes rendszereknek több hátránya is volt a végfelhasználók szempontjából:

- A számítógép megosztott jellege miatt a felhasználóknak várniuk kellett egymásra; egy programot nem lehetett elindítani, amíg az előző futás be nem fejeződött.
- Időszeletelt, multiplexált működés esetén minden felhasználói program csökkentett sebességgel futott. A teljesítménycsökkenés arányos volt az egyidejűleg csatlakozott felhasználók számával.
- A központi adminisztráció szigorú szabályokat eredményezett, amelyek meghatározták, hogy mikor és hogyan lehetett hozzáférni a rendszerhez, illetve milyen programok futtathatók rajta.

Érdemes megfigyelni a rendszer architektúráját bemutató ábrát is, amelyen a terminálok a központi kiszolgálóhoz kapcsolódnak. Ez már erősen emlékeztet egy modern hálózatba kapcsolt számítógépes rendszerre. A különbség az, hogy a terminálok ekkor még nem valódi számítógépek voltak, csupán bemeneti és kimeneti eszközök, amelyek a központi géphez csatlakoztak.

#### 2.1.2 Személyi számítógépek, hálózatok és kliens-szerver rendszerek

Az 1980-as évektől kibontakozó személyi számítógépes forradalom radikálisan megváltoztatta a megosztott számítógépes rendszerekről alkotott képet. A miniatürizálás, különösen az integrált áramkörök tömeggyártása következtében a számítógépek ára olyan szintre csökkent, amely előbb a kisvállalkozások, majd később a magánszemélyek számára is lehetővé tette számítógép birtoklását.

A személyi számítógép melletti egyik legfontosabb érv az volt, hogy a felhasználóknak többé nem kellett megosztaniuk a számítógépüket másokkal: akkor és arra használhatták, amikor és amire akarták. Arról azonban már kevésbé szólt a reklám, hogy a felhasználóknak saját maguknak kellett megtanulniuk a gépek kezelését, adminisztrálását és karbantartását.

A számítógépekkel együtt a perifériák iránti igény is megjelent. A felhasználók kis nyomtatókat, szalagos biztonsági mentő eszközöket és más kiegészítőket kezdtek vásárolni. Ezeket az eszközöket általában viszonylag ritkán használták. Üzleti környezetben az egyéni nyomtatók többletköltsége mellett az adatmegosztás problémája is egyre hangsúlyosabbá vált. Az egyes PC-k az adatokat a saját helyi merevlemezükön tárolták. Azoknak, akik egy nagyobb projekt különböző fázisain dolgoztak, rendszeresen másolniuk és fizikailag továbbítaniuk kellett egymásnak a szükséges fájlokat. A technológia fejlődésével ez csak részben változott meg: a hajlékonylemezeket CD-k váltották fel, de a probléma lényege ugyanaz maradt.

Szerencsére a PC-forradalommal együtt a számítógépes hálózati technológia is megfizethetővé vált. A helyi hálózatok lehetővé tették, hogy a PC-k kommunikáljanak egymással, ami lendületet adott az olyan köztes szoftverek fejlesztésének, amelyek megkönnyítették az adatok és a perifériák megosztását. Egy sikeres példa erre a Novell NetWare volt, amely lehetővé tette a kisvállalkozások számára nyomtatószerverek létrehozását, vagyis kevesebb nyomtató hatékonyabb kihasználását, valamint közös könyvtárak használatát, amelyekre a felhasználók elhelyezhették a megosztandó adatokat.

Az 1980-as évektől kezdve a hálózati technológia rendkívül gyors fejlődésnek indult. Az Ethernet-hálózatok általánossá váltak, a rendelkezésre álló sávszélesség pedig néhány évente ugrásszerűen nőtt. A helyi hálózatokat hamarosan követték a földrajzilag távoli számítógépek összekapcsolását lehetővé tevő nagy kiterjedésű hálózatok. A különálló, elszigetelt hálózati „szigetekre” építve, valamint a TCP/IP és a Domain Name System technológiák elterjedésével kialakult a globális Internet, amelyhez az 1990-es évek végére a legtöbb ország csatlakozott.

A nem megosztott számítógépek gyors elterjedése után az intézmények többsége felismerte, hogy a megosztásra továbbra is szükség van, méghozzá pénzügyi és működési hatékonysági okokból egyaránt. A hálózatok biztosították azt az összekötő infrastruktúrát, amelyre az elosztott számítástechnikai rendszerek épülhettek.

Az elosztott rendszer legegyszerűbb formája a kliens-szerver architektúra, amelyben egy központi szerver jól meghatározott funkcionalitást nyújt, amelyet több kliens is igénybe vehet. A szerverek a megvalósított funkciójuknak megfelelően szolgálják ki a klienskéréseket. Gyakori példák az FTP-, e-mail-, időkiszolgáló-, adatbázis- és webszerverek. Fontos hangsúlyozni, hogy a szerverek egy adott funkció vagy alkalmazástípus kiszolgálására specializálódnak. Ahhoz, hogy egy kliens használni tudjon egy adott szervert, ismernie kell annak elérési módját és használati részleteit. A kliens-szerver rendszerek érdekes programozási kihívásokat vetnek fel, amelyeket a következő alfejezetben vizsgálunk meg.

#### 2.1.3 Szuperszámítógépek

Bár a személyi számítógépek valóban háttérbe szorították a klasszikus nagyszámítógép-ipart, az gyorsan nyilvánvalóvá vált, hogy nem minden számítási feladat oldható meg személyi számítógépekkel. Azokhoz a problémákhoz, amelyek számítási szempontból rendkívül nagy igényűek voltak, speciális, sokkal nagyobb teljesítményű gépeket fejlesztettek ki. Ezek a szuperszámítógépek vették át a korábbi nagyszámítógépek szerepét.

A szuperszámítógépek definíció szerint egy adott időpontban a világ legerősebb számítógépei. Rendkívül drágák, ezért központosított szuperszámítógép-központokban helyezik el őket. A nagy országokban több ilyen központ is található, a kisebbekben esetenként egy vagy egyetlen ilyen rendszer sincs. A hozzáférés erősen korlátozott: csak egy kiválasztott és jóváhagyott felhasználói kör futtathat programokat ezeken a rendszereken.

A programfuttatás jellemzően kötegelt végrehajtási módban történik. Ez azt jelenti, hogy a program a bemeneti adatokat fájlokból olvassa be, végrehajtódik, majd az eredményeket kimeneti fájlokba írja. Az interaktív futtatás általában nem támogatott. A felhasználói programok, amelyeket ezekben a rendszerekben gyakran joboknak neveznek, csak akkor indulnak el, amikor a feladathoz szükséges összes erőforrás, például a processzor, a memória és a tárhely rendelkezésre áll. Emiatt a szuperszámítógépes rendszerek sorban állási mechanizmusokat használnak a feladatok végrehajtásához. A felhasználók elküldik a jobjaikat valamelyik végrehajtási sorba, majd megvárják, amíg a program lefut és eredményt ad.

Ez erősen emlékeztet a korai nagyszámítógépes rendszerekre, ahol a felhasználóknak előre kellett lefoglalniuk a számítási időt a programjaik futtatásához. A szuperszámítógépek megosztása elengedhetetlen ahhoz, hogy magas kihasználtságot lehessen elérni, és így az üzemeltetési költség a lehető legalacsonyabb maradjon.

A szuperszámítógépek teljesítményét az egy másodperc alatt végrehajtható lebegőpontos műveletek számával mérik, ezt flop/s formában adják meg. A teljesítményt általában a flop ezerszereseinek megfelelő mértékegységekben fejezik ki, például Mflop/s, Gflop/s, Tflop/s, Pflop/s és így tovább. Az első szuperszámítógépnek tekintett rendszer a Control Data Corporation által gyártott CDC 6600 volt, amelyet később a Cray Research Cray-1 rendszere követett. Az első 1 Gflop/s teljesítményt elérő rendszer a Cray Y-MP volt. A következő mérföldkő, az 1 Tflop/s, az ASCI Red rendszerhez köthető. A petaflops tartományt először az IBM Roadrunner érte el. A könyv írásának idején már folyamatban van az első exaflop/s teljesítményű szuperszámítógép megvalósítása is.

A korai szuperszámítógépek szekvenciális számítógépek voltak, amelyek egyetlen utasításfolyamot hajtottak végre. Sebességüket speciális hardvertervezés, gyorsabb félvezető-technológia és a hagyományos gépekénél magasabb órajel biztosította. Később különféle hardveres gyorsítási technikák, például a vektorműveletek és a belső pipeline-olás is megjelentek. A modern szuperszámítógépek ezzel szemben párhuzamos rendszerek, amelyek gyakran több százezer processzormagot tartalmaznak.

Az ilyen párhuzamos szuperszámítógépek csak akkor képesek valóban nagy teljesítményre, ha megfelelően megírt és optimalizált párhuzamos program fut rajtuk. Ezekhez a programokhoz jellemzően Fortran, C vagy C++ nyelveket használnak, megfelelő párhuzamos programozási kiterjesztésekkel, például OpenMP-vel, MPI-vel vagy CUDA-val.

### 2.2 Kliens-szerver rendszerek programozása

Amint korábban említettük, az elosztott rendszerek legegyszerűbb formája a kliens-szerver architektúra. Ebben a részben ezeknek a rendszereknek a programozási vonatkozásait vizsgáljuk meg. Az itt áttekintett technológiák mind azzal a céllal születtek, hogy magasabb absztrakciós szintre emeljék a programozást, növeljék a fejlesztők hatékonyságát, és ezzel párhuzamosan javítsák a létrejövő kód minőségét és karbantarthatóságát.

Emlékeztetőként: egy általános kliens-szerver rendszerben a kliens feladata különféle kérések elküldése a szervernek, majd a válasz megvárása. A szerver folyamatosan figyeli a beérkező kéréseket, értelmezi azokat, kiszolgálja a kérést, majd előállítja és visszaküldi a választ a kliensnek.

Az ilyen rendszerek programozásának klasszikus megközelítése az üzenetküldés, amelyhez az operációs rendszer olyan függvényeit használjuk, amelyek hálózati kapcsolatot létesítenek a szerverrel, majd elküldik az összeállított üzenetet, és fogadják a választ. Ez a megközelítés működőképes, de sok ismétlődő, alacsony szintű részletet terhel a fejlesztőre. Éppen ezért a kliens-szerver programozás történetében számos olyan technológia jelent meg, amely ezeket a részleteket igyekezett elrejteni, és a fejlesztő számára kényelmesebb, magasabb szintű programozási modellt kínálni.

#### 2.2.1 Távoli eljáráshívás

Nem meglepő, hogy ezt a problémát az elosztott rendszerek programozásával foglalkozó közösség már nagyon korán felismerte, ezért hamar megindult a szabványosítási munka. Az első igazán nagy hatású javaslat a Sun Microsystems által kidolgozott Remote Procedure Call (RPC) volt [5]. Az RPC alapgondolata az, hogy a távoli szerver eléréséhez és használatához olyan programozási felületet adjon, amely a fejlesztők számára már ismerős. Ez a természetes, közös absztrakció az eljárás- vagy függvényhívás, amelyet minden programozó jól ismer. Ha el tudjuk rejteni a kapcsolat felépítésének, az üzenetek összeállításának és továbbításának részleteit és bonyolultságát, akkor a programozók inkább a programlogikára koncentrálhatnak, és ezzel egyidejűleg a programok minősége is javul. Egy ilyen szabványosított rendszer csak akkor működhet, ha létezik egy speciális futási környezet, amely a programozó helyett elvégzi ezeket a háttérfeladatokat. Az elosztott rendszerek terminológiájában ezt a futási környezetet middleware-nek nevezik: ez egy szoftverréteg, amely az elosztott alkalmazás és az operációs rendszer között helyezkedik el. A middleware réteg feladata, hogy olyan közös absztrakciós réteget hozzon létre, amelyet az elosztott rendszer minden együttműködő szereplője ismer.

A middleware réteghez, vagyis az RPC futási környezethez való hozzáféréshez speciális kódrészeket kell létrehozni, ezeket csonkoknak (stuboknak) nevezzük; ezek kapcsolják össze a kliens- és szerverkódot a middleware-rel [6]. A 2-10. ábra az RPC-hívás működését szemlélteti a csonkokon keresztül. A csonkokat egy RPC-fordító generálja.

*2-10. ábra. Az RPC mechanizmus megvalósítása*

Itt most nem foglalkozunk a megvalósítás és a fordítás folyamatával, csak egy egyszerűsített kódrészletet mutatunk be, amely a kliens és a szerver együttműködését szemlélteti.^6 A kliens a szerverhez a `clnt_create()` függvény segítségével kapcsolódik, majd siker esetén egy távoli műveletet hajt végre, vagyis kiírat egy elemlistát a `print_list_1()` függvény meghívásával. Ha ezt összevetjük az előző, socket-szintű megvalósítással, akkor a leegyszerűsítés nyilvánvaló.

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

^6 https://www.cprogramming.com/tutorial/rpc/remote_procedure_call_start.html

#### 2.2.2 Távoli metódushívás

A Java platformfüggetlensége miatt különleges helyet foglal el az elosztott rendszerekben. A Java Virtual Machine a Java-alkalmazások számára azonos futtatási környezetet biztosít, függetlenül attól, hogy az adott számítógép milyen hardvert és operációs rendszert használ. Mivel a Java támogatja az objektum-perzisztenciát, vagyis a szerializációt, nemcsak adatok, hanem Java-osztályok is továbbíthatók egyik virtuális gépből a másikba. Ez adja az RPC Java-változatának, illetve újramegvalósításának, a Remote Method Invocation (RMI) technológiának [7] az alapját.

Az RMI célja, hogy távoli metódushívási mechanizmust biztosítson Java-programok számára. Mivel egy Java-program a JVM-ben fut, és el van szigetelve a hardvertől, a hagyományos Java-metódushívási mechanizmus nem alkalmas távoli számítógépek elérésére. Az RMI tervezői egy köztes szoftverréteget vezettek be, amely az alatta lévő operációs rendszerrel együttműködve kapcsolatokat épít fel, és adatokat továbbít a távoli félhez. Emellett, mivel a Java teljes mértékben objektumorientált nyelv, bevezettek egy speciális absztrakciót is, a csonkosztályt (`stub class`), amely működés közben a távoli szervert a kliens számára közönséges Java-objektumként jeleníti meg.

Az RMI működéséhez némi további infrastruktúrára is szükség van. Mivel az objektumok szerializációs mechanizmusa csak az objektum állapotát viszi át, külön megoldást kell biztosítani arra, hogy a lefordított Java-osztályok is eljussanak a másik félhez, így a távoli VM osztálybetöltője (`classloader`) betöltéskor meg tudja találni az osztályt. Az RMI HTTP-szervereket használ az osztályfájlok exportálására. Az utolsó fontos elem az, hogy a kliensek és a szerver hogyan találnak egymásra az RMI-ben. Az IP-címen és portszámon alapuló egyszerű címzéssel szemben az RMI interfészekre épülő keresési mechanizmust használ. A távoli szervereket az az interfész írja le, amely rögzíti a szerver funkcionalitását. Ez azt jelenti, hogy a kliensnek ismernie kell a használni kívánt interfészt, mivel ez tartalmazza azokat a nyilvános metódusokat, amelyeket meghívhat. Az interfészek használata a portszámoknál jóval pontosabb leírást ad a távoli funkcionalitásról. Így egy távoli rendszer tetszőleges számú szolgáltatást tehet elérhetővé a kliensek számára, amennyiben ezek metódus-szignatúrákkal leírhatók. A Java erős típusossága biztosítja, hogy a kliensek csak olyan szolgáltatásokat érhessenek el és használhassanak, amelyekre kifejlesztették őket. E komponensek együttműködését a 2-11. ábra mutatja.

*2-11. ábra. A Java RMI rendszer komponensei és architektúrája*

A következő rész egy RMI-alapú kliens-szerver alkalmazás fejlesztésének fő lépéseit mutatja be. Csak a legfontosabb kódrészleteket ismertetjük. Példaként egy képzeletbeli távoli bankot használunk, amely lehetővé teszi az ügyfél számára, hogy pénzt fizessen be bankszámlára, pénzt vegyen fel, illetve átutalást végezzen. A szerver funkcionalitását egy Java-interfész írja le. Az előírás szerint a távoli szerver interfészének a `Remote` interfészből kell származnia, és minden metódus deklarációjában szerepelnie kell a `throws RemoteException` résznek.

```java
import java.rmi.Remote;
import java.rmi.RemoteException;
public interface BankInterface extends Remote {
int deposit(int amount) throws RemoteException;
int withdraw(int amount) throws RemoteException;
int getBalance() throws RemoteException;
}
```

A szerver ezt az interfészt egy olyan Java-osztállyal valósítja meg, amely a `UnicastRemoteObject` osztályból származik, és induláskor regisztrálja magát az `RMIregistry`-ben.

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

A kliens a programban két fő lépést hajt végre. Először az `RMIRegistry` segítségével megkeresi a távoli szervert, majd a szervert reprezentáló `stub`/proxy objektumon végrehajtott lokális metódushívásokkal meghívja a távoli funkciókat. A klienskód jól szemlélteti, hogy az RMI milyen magas szintű absztrakciót és eleganciát kínál kliens-szerver rendszerek megvalósításához.

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
while (! finished){
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

#### 2.2.3 A lazán csatolt rendszerek melletti érvek

Az RPC- és RMI-alapú programozási absztrakció nagy segítséget jelent az összetettség és a programhibák csökkentésében az elosztott szoftverek fejlesztése során. Természetes kiterjesztését adják a jól ismert függvény-, eljárás- és metódushívási technikáknak. Ugyanakkor hamar kiderül, hogy hibák jelenlétében ezek a megoldások meglehetősen sérülékenyek. Az alacsony szintű kommunikáció részleteinek elrejtése, valamint az a látszat, hogy a szerver csupán egy objektum másik hétköznapi függvénye vagy metódusa, sok programozóban azt az érzetet kelti, mintha a rendszer pontosan ugyanúgy viselkedne, mint egy hagyományos, lokálisan futó program. Ennél nagyobb tévedés aligha lehetne. Az elosztott szerverek számos olyan hibát mutathatnak, amelyek szekvenciális programokban nem fordulnak elő. Megszakadhat a hálózati kapcsolat, a szerveren felléphet átmeneti vagy végzetes hiba, ami hibás eredményt vagy éppen semmilyen eredményt nem ad. Ezeket a helyzeteket függvényhívásokon keresztül nehéz megfigyelni és kezelni. Az RMI speciális Java-kivételeket, például `RemoteException`-t használ arra, hogy jelezze a hívó félnek, ha valami hiba történt.

Az igazi nehézség a hosszú metódushívási láncokban jelentkezik, amikor több elosztott rendszerkomponens hívja egymást egy összetett feladat végrehajtásához. Vegyünk egy példát, amelyben egy `C` kliens meghívja az `A` szervert. Az `A` szerver ezután segítségért a `B` szervert hívja, amely pedig továbbhívja a `D` szervert. A kliens erről a megvalósítási részletről nem is feltétlenül tud, hiszen ő csak az `A` szerverhez kapcsolódott. Ha nincs hiba, a rendszer tökéletesen működik, de ha hiba történik, az egész rendszer állapota könnyen sérülhet. Gondoljunk például egy tranzakciós integritást igénylő feladatra. Hogyan garantálható, hogy a feladat csak akkor hajtódjon végre, ha minden részfeladat hibátlanul lefut? Ha a hívási lánc bármely tagja hibát jelez, dominóhatás indul el, és a kivételek vagy hibakódok visszafelé gyűrűznek végig a rendszerben. Ráadásul ha egy metódushívás határozatlan időre elakad, például várakozás vagy holtpont miatt, akkor minden hívó metódus blokkolódik. Ezt a működési módot az elosztott rendszerekben erős csatolásnak nevezzük.

Más szóval, az egyik komponensben fellépő hiba közvetlenül befolyásolja egy másik komponens működését. Egyetlen szerver teljes kiesése az egész rendszert megbéníthatja, és a feladatok többé nem hajthatók végre. Amint azt a 2-12. ábra mutatja, egy elosztott metódushívási láncban számos lehetséges hibaforrás található. Egyetlen visszakapott `RemoteException` példány alapján meglehetősen nehéz pontosan feltárni a hiba valódi okát; ráadásul ilyen helyzetben még nehezebb garantálni a rendszer állapotintegritását.

*2-12. ábra. Lehetséges hibaforrások egy RPC/RMI-hívásban*

Ahogy a fejlesztők egyre nagyobb és nagyobb elosztott rendszereket próbáltak létrehozni, világossá váltak az erősen csatolt metódusláncolási absztrakció velejáró skálázhatósági problémái. Az ipar ezért a lazán csatolt, kommunikáló rendszerek felé fordult, amelyek üzenettovábbításon alapuló kommunikációra és aszinkron végrehajtásra támaszkodnak. Ezeket később részletesebben is megvizsgáljuk.

### 2.3 Szolgáltatásorientált rendszerek

A szolgáltatásorientáció fogalma a kliens-szerver rendszerekből és a szerverek funkcionalitását leíró interfészek használatából nőtt ki. Annak érdekében, hogy az elosztott rendszerek rugalmasabbak legyenek, és kevésbé kötődjenek a hardverhez, a kutatók olyan megoldásokat kerestek, amelyek szétválasztják a szerverkódot futtató rendszert attól a funkcionalitástól, amelyet a szerver megvalósít. Erre megfelelő általánosításként jelent meg a szolgáltatás fogalma. A szolgáltatás olyan, hardverben vagy szoftverben megvalósított funkcionalitás, amely hasznos műveletet biztosít a kliens számára. A szolgáltatást a szolgáltató és a szolgáltatásfogyasztó közötti szolgáltatási szerződés írja le. A szolgáltatásorientált szoftverrendszerek legfontosabb újdonsága az, hogy a szolgáltatókat a nyújtott szolgáltatás alapján lehet megtalálni, nem pedig azon szervercím alapján, amely fizikailag végrehajtja azt. Ha például egy dokumentumot németről angolra szeretnénk fordítani, akkor csak azok az online szolgáltatások érdekelnek, amelyek képesek ezt a fordítást elvégezni. Nem az számít, hol futnak ezek a szolgáltatások, például mi az IP-címük, hanem az, hogy a fordítás elkészüljön. A továbbiakban azt látjuk, hogyan valósítható ez meg.

A szolgáltatásorientált rendszerek a következő alapelvekre épülnek:

1. A szolgáltatást egy interfész írja le.
2. Létezik egy jegyzék, amely közvetít a kliensek és a szolgáltatások között: a szolgáltatások regisztrálnak benne, a kliensek pedig itt keresik meg a számukra megfelelő szolgáltatásokat.
3. A kliensek és a szolgáltatások csak a szolgáltatás végrehajtásának idejére lépnek kapcsolatba.
4. A kliensek és a szolgáltatások nyílt, szabványosított technológiákat és protokollokat használnak.

*2-13. ábra. Egy szolgáltatásorientált rendszer általános architektúrája és működése*

A szolgáltatásorientáció 2000 körül kezdett népszerűvé válni. Mint minden heterogén elosztott rendszer esetében, itt is az első kulcsprobléma egy platformfüggetlen kommunikációs és protokollkeretrendszer kialakítása volt. Ezt követően lehetett megkezdeni a szolgáltatásorientált rendszerek tervezését és megvalósítását. A szolgáltatásorientált számítástechnika ígérete az volt, hogy jól definiált funkcionalitású, interneten elérhető „komponensekből” lehessen nagyobb és összetettebb alkalmazásokat létrehozni viszonylag egyszerű integrációs folyamatok révén.

Az első lehetséges middleware-technológia az XML volt. Érdekes módon ez nem programozási nyelv, hanem leíró nyelv. Az XML-t azonban eleve számítógépek számára tervezték, nem emberek számára; szigorú, szabályalapú megközelítést alkalmaz az adatok és a műveletek leírására. Az elképzelés az volt, hogy az XML-t használják a szolgáltatások funkcionalitásának leírására, valamint az adatkommunikációban és a szolgáltatáshívások során is. Ehhez további eszközöket kellett fejleszteni, amelyek a szolgáltatásinterfészekből csonkokat (`stub`) generáltak a célprogramozási nyelvekhez. Nem meglepő módon az első XML-alapú szolgáltatási rendszerek RPC-stílusú szolgáltatáshívást használtak.

#### 2.3.1 XML-alapú szolgáltatások – webszolgáltatások

Amikor az XML-t és a szolgáltatásorientált megközelítést a HTTP protokoll fölött használjuk, akkor webszolgáltatás-technológiáról beszélünk. A webszolgáltatások olyan szolgáltatások, amelyeket interneten keresztüli meghívásra terveztek, webes protokollok használatával. Eredetileg azt a célt szolgálták, hogy az üzleti partnerek közötti új generációs alkalmazások gerincét adják, egyszerűbbé tegyék az online üzleti folyamatokat, valamint olyan rendszereket tegyenek lehetővé, amelyek a jövőben könnyen karbantarthatók és módosíthatók. A 2-14. ábra egy webszolgáltatás-alapú szolgáltatásorientált rendszer általános architektúráját szemlélteti.

A szolgáltatásokat egy XML-alapú WSDL (Web Service Description Language) interfészleíró írja le, amely információt tartalmaz a szolgáltatás helyéről, az általa nyújtott funkcionalitásról és az elérés módjáról. Ezt a leírást egy nyilvános jegyzékben tárolják, amelynek neve UDDI (Universal Description, Discovery, and Integration). Ez a jegyzék szintén XML-alapú. A kliensek az UDDI jegyzék segítségével keresik meg a megfelelő szolgáltatásokat, lekérik a szolgáltatás eléréséhez szükséges információkat, majd XML-alapú SOAP (Simple Object Access Protocol) üzenetek használatával kapcsolódnak a szolgáltatáshoz, és végrehajtják a kiválasztott funkciókat.

*2-14. ábra. A Web Service architektúra*

A webszerverekhez hasonlóan a webszolgáltatások esetében is az ajánlás az, hogy állapotmentes szolgáltatásokat valósítsunk meg. Az állapotmentes szolgáltatások nem függenek a hívások sorrendjétől, nem módosítják saját állapotukat, és minden beérkező kérésre mindig ugyanazt a műveletet hajtják végre, ezért jól tűrik az elosztott rendszerekben gyakran előforduló hibák számos típusát. Sajnos sok szolgáltatás, különösen a kliensfüggő üzleti szolgáltatások állapotfüggők, ami az állapotkezelés támogatásához vezetett a szolgáltatásokban. A növekvő komplexitás szükségessé tette az egyszerű WSDL-SOAP alapú kliens-szolgáltatás interakciós technológia kibővítését. A webszolgáltatás-technológiai veremben több új réteg és komponens jelent meg, amint azt a 2-15. ábra mutatja, amelyek különféle kiegészítő működési funkciókért feleltek, például az elosztott tranzakciók kezeléséért, a kontextus biztosításáért, a szolgáltatás-orchestrációért vagy az üzleti munkafolyamatok leírásáért. Ez azonban sajnálatos módon olyan összetett és nagyméretű technológiai rendszert eredményezett, amelyet szinte lehetetlen teljes egészében átlátni. A Web Service specifikációk összessége, amelyet köznyelvben „WS-* stack”-nek neveznek, több mint 70 specifikációt tartalmaz.

*2-15. ábra. A Web Service technológiai verem*

#### 2.3.2 RESTful szolgáltatások

A Representational State Transfer, röviden REST, Roy Fielding 2000-ben készült doktori munkájának eredménye, és egy alternatív megközelítés alapját adja nagyméretű elosztott szolgáltatási rendszerek létrehozásához. Mivel Fielding elégedetlen volt a főáramú szolgáltatásorientált megközelítések bonyolultságával, egy egyszerű, erőforrás-orientált módot javasolt a szolgáltatások leírására. Míg a hagyományos megközelítések a számítás fogalma köré szerveződtek, vagyis valamilyen művelet végrehajtására a kliens nevében, addig a REST az adatok szempontjából közelítette meg a problémát. Fielding azt javasolta, hogy minden, akár egyetlen bájt a memóriában is, rendelkezhet URL-lel, amelyen keresztül az állapota lekérdezhető és módosítható. Ehhez elegendő a GET és a POST HTTP-parancsok használata, valamint az erőforrásra mutató URL. Kidolgozott egy módszert a szolgáltatásinterfészek leírására URL-ek, illetve GET és POST parancsok segítségével.

A REST-alapú, vagyis RESTful szolgáltatások egyszerűsége miatt ez a megközelítés nagyon gyorsan népszerűvé vált, és komoly véleményütközést okozott a webszolgáltatási közösségen belül. Mára azonban úgy tűnik, hogy a REST egyértelműen győzött, és az XML-alapú webszolgáltatásokat új rendszerek fejlesztésénél már csak kivételes esetekben használják. A REST részletei megtalálhatók Fielding doktori értekezésében, illetve a következő Wikipedia-bejegyzésben: https://en.wikipedia.org/wiki/Representational_state_transfer.

### 2.4 Grid számítás

A grid számítás az 1990-es évek végén két egymástól független, de egy időben kibontakozó fejlődési irány eredményeként jelent meg. Az Egyesült Államok szuperszámítógépei elszigetelten működtek, ami jelentős regionális különbségeket okozott a terhelésükben. Előfordult, hogy egy szuperszámítógép-központ túlterheltté vált, ezért a felhasználói feladatok várakoztak a sorban, miközben egy másik központ ugyanebben az időben alulhasznosított maradt. A kutatók azt javasolták, hogy e központok összekapcsolásával, valamint a feladatok automatikus, a legalkalmasabb helyre történő továbbításával növelhető a szuperszámítógép-központok hatékonysága és kihasználtsága, miközben a felhasználók várakozási ideje is csökken.

Ezzel párhuzamosan a hálózati és elosztott rendszerek fejlettsége elérte azt a szintet, amely lehetővé tette nagyméretű számítási klaszterek létrehozását helyi hálózatra kapcsolt számítógépekből. A kutatók ezt a modellt kiterjesztették a nagy kiterjedésű hálózatokra is: távoli számítógépeket kívántak összekapcsolni, hogy nagy virtuális párhuzamos számítógépeket hozzanak létre. Az első irányzat a szuperszámítógépek összekötésére épült, a második pedig számítógép-klaszterek hasonló célú összekapcsolását tervezte. Mindkét megközelítés közös célja a meglévő számítási erőforrások jobb kihasználása volt, egy hatékony terheléselosztó szoftverréteg segítségével.

A Grid Computing elnevezést a számítási erőforrásokhoz való hozzáférés és a villamos energia elérésének analógiája ihlette. Az Egyesült Államokban a villamosenergia-elosztó rendszert Power Gridnek nevezik. Az alapgondolat az volt, hogy a kutatók földrajzi elhelyezkedésüktől függetlenül juthassanak számítási és tárolási kapacitáshoz. Ha egy számítógép csatlakozik a Gridhez, hozzáférhet az erőforrásokhoz, ahogyan az elektromos hálózatra csatlakoztatott eszköz is energiához jut. A korai fejlesztések többféle szoftverrendszert eredményeztek, amelyek magas szintű programozási felületet kívántak biztosítani elosztott klasztereken futó párhuzamos programok létrehozásához és végrehajtásához. Az ismert rendszerek közé tartozott a Parallel Virtual Machine (PVM), a Legion és a Globus Toolkit. Ezek a korai megoldások kezdetben kisebb, klaszteralapú rendszerekre összpontosítottak, és azt vizsgálták, miként használhatók ki hatékonyan az egyetemi klaszterekben rendelkezésre álló, éppen tétlen gépek. A tapasztalatok bővülésével azonban egyre nagyobb, földrajzilag elosztott rendszerek kiépítésére is sor került. 2005-re csaknem minden fejlett ország létrehozta saját nemzeti gridrendszerét. Európában a CERN vezetésével megvalósított DataGrid projekt sikeresen demonstrálta ezt a koncepciót, jóllehet ez a rendszer egyetlen konkrét feladatra, a Large Hadron Collider által előállított adatok feldolgozására készült.

A middleware-fejlesztések közül a legsikeresebbnek a Globus Toolkit bizonyult. Ez a rendszer arra törekedett, hogy új programozási absztrakciók, például a PVM vagy a Legion helyett meglévő rendszereket, szoftverkomponenseket és szabványos protokollokat, például az FTP-t használja fel. Egy Globus-publikáció példáján keresztül jól megérthetők a grid számítás alapelvei.

Tegyük fel, hogy egy kutató egy szimulációs programot kíván futtatni. Ez a program elosztott szimuláció, ráadásul interaktív módban működik. Az interaktív működés köztudottan nehezen kezelhető kötegelt végrehajtási környezetben, és még nagyobb kihívást jelent több helyszínt érintő esetben. Minden egyes helyszínnek elegendő erőforrást kell biztosítania ahhoz, hogy a program a többivel egy időben futhasson. Ideális lenne, ha ezt a koordinációt maga a rendszer végezné el a felhasználó helyett. Egy grid erőforrás-kezelő rendszerben ezért feltételezhető egy, az elosztott szimulációkra specializált erőforrás-közvetítő jelenléte, amely átveszi a konfigurációs feladatokat a felhasználótól. Ez a komponens a felhasználói igényt a számítógépes rendszerek számára értelmezhető formára fordítja le, majd megkezdi azoknak a szuperszámítógépes helyszíneknek a felkutatását, amelyek képesek kiszolgálni a kérést. Valós idejű információkat gyűjt egy második szintű közvetítőtől, a szuperszámítógépes erőforrás-közvetítőtől, és ennek segítségével több helyszínen egyidejűleg foglal le erőforrásokat a szimuláció végrehajtásához. Miután a közös erőforrás-allokáció megtörtént, a szimuláció elindul. A felhasználó mindebből csupán a kezdeti kérést és a futó szimulációs programot látja; a technikai részletek rejtve maradnak.

*2-16. ábra. A felhasználó által kezdeményezett erőforráslekérdezés végrehajtásának magas szintű áttekintése*

A gyakorlati megvalósítás természetesen összetett. Felmerül a kérdés, milyen szoftverkomponensek szükségesek a programfuttatás irányításához. Az ilyen erőforrás-kezelő rendszer a Resource Specification Language segítségével írja le az erőforrás- és ütemezési követelményeket. Minden helyszínen működik egy helyi Globus Resource Allocation Manager (GRAM), amely összegyűjti és továbbítja az erőforrás-információkat az Information Service felé, feldolgozza az RSL-kéréseket, elfogadja vagy elutasítja azokat, továbbá felügyeli és kezeli a futó feladatokat. Az erőforrás-közvetítők az Information Service-ből olvassák ki a gridre vonatkozó információkat, és a klienskérés feldolgozása során speciális lekérdezéseket hoznak létre; szükség esetén további, szakterület-specifikus közvetítőkkel is kapcsolatba léphetnek. Amikor a szükséges erőforrás-feltételek teljesülnek, a Broker együttműködik a co-allocator komponenssel a szükséges szoftverelemek lefoglalása, allokálása és végrehajtása érdekében.

*2-17. ábra. A Globus erőforrás-kezelő rendszer architektúrája*

A grid számítás fejlődése során megjelent a szolgáltatásorientált szemlélet is, mint hasznos absztrakció. Ennek következtében a Globus Toolkit jelentős átalakuláson ment keresztül, és Web Services alapokra épülő, szolgáltatásorientált változattá alakult. Az új rendszer neve Open Grid Service Architecture (OGSA) lett. A fejlesztést egy nemzetközi bizottság irányította, amelyben az akadémiai és az üzleti szféra képviselői egyaránt részt vettek.

### 2.5 Önkéntes erőforrás-megosztás

A beküldéses, vagyis push jellegű grid rendszerek egyik alternatívája az önkéntes számítási modell, amelyben a számítógépek tulajdonosai saját gépeik szabad erőforrásait ajánlják fel programok futtatására. A programok telepítése és a feladatok kiosztása lekéréses, vagyis pull jelleggel történik: a kliensek egy központi feladatadatbázishoz kapcsolódva kérnek munkát.

Az ilyen rendszerek első és legismertebb példája a SETI@home projekt. A projekt 1999-ben indult a Kaliforniai Egyetem berkeley-i campusán azzal a céllal, hogy a tétlen számítógépes kapacitásokat rádióteleszkópos adatok elemzésére használják fel földönkívüli élet nyomainak keresésére. A rendszerben a felhasználók egy olyan programot telepítettek, amely képernyővédőként működött, de a véletlenszerű grafika megjelenítése helyett a SETI szerveréhez kapcsolódott, letöltött egy adatszegmenst, majd elvégezte annak elemzését. A rendszer leegyszerűsített architektúráját a 2-18. ábra mutatja.

Érdekes sajátosság, hogy ebben a rendszerben az elemzőprogramokat futtatni kívánó fél a szerver oldalon jelenik meg, míg a számítási erőforrásokat biztosító felhasználók kliensként vesznek részt. További fontos tulajdonság, hogy a munkaelosztás teljesen automatikus, a működés pedig hibatűrő: a rendszer klienshibák vagy kapcsolatmegszakadások esetén is folyamatosan üzemképes marad. A projekt rendkívül sikeres volt: felhasználók milliói ajánlották fel számítógépük idejét, és az összesített számítási teljesítmény meghaladta a korszak vezető szuperszámítógépeiét.

*2-18. ábra. A SETI@home rendszer architektúrája*

A projekt sikere egy új alprojekt elindításához is vezetett, amely a futási környezet általánosítását és támogatását célozta. Ennek eredményeként jött létre a Berkeley Open Infrastructure for Network Computing, röviden BOINC, amelyet olyan projektek számára tettek elérhetővé, amelyek hasonló módon kívántak elosztott számítási erőforrásokat igénybe venni. A BOINC infrastruktúrát több mint harminc tudományos projekt használja; ezekben közel 800 000 aktív számítógép vesz részt, az összesített számítási teljesítmény pedig meghaladja a 40 petaFLOP/s értéket.

Hasonló, de a BOINC ernyőjén kívül működő projekt a Folding@home, amely a fehérjeszerkezet-kutatás egyik fontos platformja. A könyv írásának idején a projekt kiemelt célja olyan molekulák keresése volt, amelyek potenciális gyógyszerjelöltként szolgálhatnak a COVID-19 vírus elleni küzdelemben.

### 2.6 Hoszting és a kialakuló közüzemi számítástechnikai modell

Az 1990-es évek végére, illetve a 2000-es évek elejére a számítógépek a vállalatok mindennapi működésének nélkülözhetetlen eszközeivé váltak. Egyre több számítógépet állítottak üzembe az üzleti szférában, és nyilvánvalóvá vált, hogy e rendszerek professzionális támogatást és karbantartást igényelnek. Kezdetben a cégek saját informatikai szakembereket alkalmaztak erre a feladatra, ez azonban komoly nehézséget jelentett azoknak a kis- és középvállalkozásoknak, amelyeknek fő tevékenysége nem az informatika volt. Egy értékesítéssel, gyártással vagy más üzleti területtel foglalkozó kisebb vállalkozás számára nem volt sem gazdaságos, sem hatékony teljes állású informatikai személyzetet fenntartani pusztán a vállalati webhely vagy a belső számítógépes infrastruktúra működtetésére.

Néhány éven belül ezért új iparág alakult ki: a kiszervezett webhoszting. Gazdaságosabbnak bizonyult egyetlen helyszínen, nagy sebességű összeköttetésekkel ellátott szerverfarmot üzemeltetni, és azon több kisebb vállalkozás webhelyeit hosztolni. A méretgazdaságosság alacsonyabb árakat eredményezett, a vállalatoknak nem kellett a webhelyüzemeltetés technikai részleteivel foglalkozniuk, és saját alaptevékenységükre koncentrálhattak. A webhosztingot hamarosan az általános hoszting követte, amelynek során a szolgáltató a megrendelő számára teljes számítógépes rendszereket kezelt és üzemeltetett, tetszőleges alkalmazások futtatásával. A vállalatok kedvelték ezt a modellt, mert a szolgáltatásokért fix havi díjat fizethettek, amely könnyen tervezhető volt az éves költségvetésben. Ez jelentette annak a modellnek a kezdetét, amelyet ma közüzemi számítástechnikának nevezünk.

Az ilyen típusú számítástechnika üzleti lehetőségeit elsőként a SUN Microsystems ismerte fel a nagy informatikai vállalatok közül. Ez jól illeszkedett a „The Network Is The Computer” jelmondatukhoz. Ennek szellemében hozták létre a Sun Container megoldást, egy hordozható szerverkonténert, amelyet eredetileg olyan nagy ügyfelek számára terveztek, akiknek többlet számítási kapacitásra volt szükségük. A SUN 2005-ben ezeket a rendszereket már saját üzemeltetésben működtette, és az erőforrásokhoz használatalapú díjazás mellett biztosított hozzáférést. A Sun Grid számítási közüzemi szolgáltatás esetében az ár 1 amerikai dollár volt CPU-óránként, míg a Sun Grid tárolási közüzemi szolgáltatásnál 1 amerikai dollár gigabájtonként és havonta. A rendszer jelentős sikert aratott, azonban a 2008-as pénzügyi válság következtében a SUN csődbe jutott, ami a vállalat megszűnéséhez vezetett.

*2-19. ábra. A SUN Grid konténer*

### 2.7 Virtualizáció

A virtualizáció mint technológia régóta ismert, és a nagyszámítógépes rendszerekben már korán rutinszerűen alkalmazták. Célja, hogy egy szoftverrendszert elvonatkoztasson, illetve leválasszon a fizikai hardverkörnyezetről egy virtuális környezet létrehozásával, amely a legtöbb esetben virtuális gép formájában jelenik meg. A virtualizáció a hosztingszolgáltatók és adatközpontok elterjedésével került ismét a figyelem középpontjába.

Korábban egy szoftver jellemzően csak azon a hardveren volt futtatható, amelyre lefordították. Ez merev infrastruktúrát és gyártói függőséget eredményezett. Ha például egy számítógép elavulttá vált, egyre nehezebbé vált a szükséges hardverkörnyezet fenntartása és a szoftver működőképességének megőrzése. Hasonlóképpen, egy adott operációs rendszerre történő fejlesztés gyakorlatilag életre szóló döntésnek számított, mert az elkészült alkalmazást utólag nem lehetett más platformra áthelyezni.

A virtuális gépek használata rugalmasabb és hatékonyabb számítási infrastruktúra kialakítását teszi lehetővé. Virtualizációval ma már lehetőség van hardvererőforrások virtualizálására, és így tetszőleges operációs rendszer futtatására ugyanazon a fizikai hardveren.

*2-20. ábra. A virtualizáció lehetővé teszi különböző operációs rendszerek futtatását ugyanazon a hardveren*

Hasonló módon egy operációs rendszer is virtualizálható, így alkalmazások futtathatók rajta akkor is, ha az alapul szolgáló platform egyébként inkompatibilis operációs rendszert használ.

A 2-21. ábra szemlélteti, hogy a virtualizációnak számos területe van: ide tartozik többek között a hardver, a hálózat, a tárolás és a memória virtualizációja. Hardvervirtualizáció esetén egy Virtual Machine Monitor (VMM) nevű virtualizációs réteg felelős azért, hogy az operációs rendszer számára emulálja a hardvert. A hardvervirtualizáció célja, hogy teljes operációs rendszerek módosítás nélkül legyenek futtathatók különféle hardvereken. A virtualizációs réteg ehhez olyan utasításkészlet-architektúrát és hardvernézetet emulál, amelyre a vendég operációs rendszernek szüksége van.

*2-21. ábra. Az erőforrás-virtualizáció különböző formái*

A teljes virtualizáció (`Full Virtualization`) esetében a tényleges hardver teljes szimulációja történik meg annak érdekében, hogy a szoftver egy módosítatlan vendég operációs rendszeren is futtatható legyen.

A paravirtualizáció (`Paravirtualization`) a hardvervirtualizáció egy sajátos megközelítése. Ennél a megoldásnál a virtualizációs réteg egy speciális API-t biztosít az operációs rendszer számára, amely lehetővé teszi, hogy az operációs rendszer bizonyos funkciói közvetlenül a gazdagépen, ne pedig az emulált rétegen keresztül hajtódjanak végre. Ez növeli a teljesítményt és a végrehajtás hatékonyságát. Hátránya viszont, hogy ehhez módosítani kell az operációs rendszer kódját. Egyes operációs rendszerek rendelkeznek paravirtualizált disztribúciókkal.

A teljes virtualizáció és a paravirtualizáció szoftveralapú megközelítések. Ilyenkor a vendégrendszer utasításait bináris formában kell a gazdarendszer megfelelő utasításaira lefordítani, ami jelentős teljesítményveszteséggel járhat. Napjainkban a hardvervirtualizáció legelterjedtebb formája a hardveresen támogatott virtualizáció, amely a processzorgyártók speciális hardvertámogatására épül. Ebben az üzemmódban az operációs rendszer vagy az alkalmazásszoftver számos funkciója közvetlenül használhatja a gazdagép fizikai hardvererőforrásait, elsősorban a CPU-t, ami jóval nagyobb teljesítményt eredményez, mint a teljesen szoftveres emuláción alapuló virtualizációs technikák.

Összefoglalva, a virtualizáció legfontosabb előnyei a következők:

- Lehetővé teszi az erőforrások hatékony kezelését. Az alkalmazások és rendszerek pillanatképek segítségével tetszés szerint indíthatók és leállíthatók, szükség esetén pedig új hardverre migrálhatók.
- Növeli az informatikai üzemeltetés hatékonyságát. Egyetlen fizikai számítógépen több virtuális gép is futtatható, így a processzorok kihasználtsága jóval jobb lehet, mint a hagyományos, egy alkalmazás egy szerver felállásban, amely sok üres CPU-ciklust eredményez.
- Megkönnyíti a biztonsági mentést és a katasztrófa utáni helyreállítást. A virtuálisgép-képek és állapot-pillanatképek egyszerűen létrehozhatók, tárolhatók és archiválhatók.
- Költségmegtakarítást eredményez a hardverberuházások csökkenése révén, ami az erőforrások jobb kihasználásából fakad.

A virtualizációnak ugyanakkor vannak hátrányai is:

- A többletrétegek miatt bizonyos teljesítményveszteséggel kell számolni, ami az alkalmazások valamelyest alacsonyabb futási sebességét eredményezheti.
- Egyes kereskedelmi szoftvercsomagok esetében a virtualizált futtatás kifejezetten tiltott lehet, vagy magasabb licencköltséget vonhat maga után.
- A virtualizációt alkalmazó szervezeteknek gondoskodniuk kell az informatikai személyzet megfelelő képzéséről.

## 3. A felhőtechnológia alapjai

A felhőtechnológia a modern mindennapok szerves része. Egyszerű megfogalmazásban olyan nagyméretű, virtualizált és rugalmasan bővíthető számítási és tárolási infrastruktúrát jelent, amelyet felhőszolgáltatók üzemeltetnek, és amely üzleti szereplők vagy magánfelhasználók számára igény szerint vehető igénybe sokféle célra. A felhő legfontosabb előnye, hogy tehermentesíti az informatikai felhasználókat a hardver- és szoftverelemek fenntartásának, illetve adminisztrációjának feladatai alól. Legjellegzetesebb tulajdonságai az egyszerű használhatóság és az igény szerinti skálázhatóság.

A számítógépekre építő modern vállalatok informatikai infrastruktúrájának működtetésében két, egymással ellentétes cél jelenik meg. Az egyik cél az infrastruktúra méretének minimalizálása, hogy a beruházási és üzemeltetési költségek alacsonyak maradjanak. A másik cél ugyanakkor az, hogy elegendő erőforrás álljon rendelkezésre a nyereséges működéshez szükséges feladatok ellátására. Ha egy vállalkozás számítási igénye állandó és kiegyensúlyozott, vagyis folyamatosan hasonló számú alkalmazást futtat, akkor a szükséges kapacitás viszonylag könnyen megtervezhető. Ingadozó terhelés esetén azonban a helyzet jóval összetettebb, különösen akkor, ha a terhelés kiszámíthatatlanul, hirtelen megugrások formájában jelentkezik.

Mivel a vállalatoknak szélsőséges terhelés mellett is működőképesnek kell maradniuk, az informatikai vezetők rendszerint a várható maximális terhelésre méretezik a rendszereket. Ingadozó vagy lökésszerű igénybevétel esetén ez azt eredményezi, hogy az informatikai infrastruktúra az idő nagy részében kihasználatlan marad. A kihasználatlanság erőforráspazarlást és felesleges üzemeltetési költségeket jelent. Gazdaságosabb lenne az átlagos terhelési szintre tervezni, ez azonban sebezhetővé tenné a rendszert, és éppen a legkritikusabb időszakokban, a nagy terhelésű intervallumokban okozhatna működési problémákat.

*3-1. ábra. A változó számítási terhelés és annak következménye a kapacitástervezésre*

Ezért különösen értékes minden olyan megbízható külső infrastruktúra, amely csúcsterhelés idején többleterőforrást tud biztosítani a vállalatok számára. Ennek segítségével a cégek csökkenthetik saját informatikai infrastruktúrájuk költségeit: a belső erőforrásokat elegendő a normál terhelés kiszolgálására méretezni, míg a csúcsidőszakokban külső kapacitásra támaszkodhatnak. A felhőtechnológia az első olyan megoldás, amely ezt globális léptékben, üzleti szintű megbízhatósággal képes nyújtani.

Önmagában ez a tulajdonság is elegendő lenne ahhoz, hogy a felhő vonzó és sikeres szolgáltatássá váljon az üzleti világban. A technológia különlegessége azonban abban rejlik, hogy gazdaságilag is kedvező, és olyan infrastruktúrát biztosít, amely számos további, még érdekesebb lehetőséget teremt.

### 3.1 Alapfogalmak

A felhőszolgáltatók nagyon nagy adatközpontokat üzemeltetnek, amelyek több ezer szerverből állnak. Ez a szerverállomány alkotja a felhő gerincét. A virtualizációs technológiának köszönhetően ezeken a rendszereken különféle operációs rendszerek futtathatók hatékony módon, úgy, hogy közben a felügyeletük, kezelésük és migrációjuk is egyszerű marad.

Szükség esetén az alacsony szintű erőforrások, vagyis a szerverek, a tárolókapacitás és a hálózati infrastruktúra közvetlenül is igénybe vehetők szervezetektől vagy magánfelhasználóktól, mintha egy hagyományos szerverhoszting-szolgáltató biztosítaná őket. Ezt a szolgáltatási modellt Infrastructure-as-a-Service-nek, röviden IaaS-nek nevezzük. Az IaaS a szolgáltatási piramis legalsó szintjét képviseli. Ez a modell maximális rugalmasságot ad a felhasználónak abban, hogy mit és hogyan futtat a rendszeren, ugyanakkor a nagyobb szabadság együtt jár azzal is, hogy az erőforrások kezelésének felelőssége döntően a felhasználóra hárul.

Nem minden ügyfél igényel ekkora rugalmasságot. Sok esetben elegendő számukra egy webhely beépített funkciókkal, például webáruház, közműszolgáltatói ügyfélportál vagy más hasonló alkalmazás. Az ilyen rendszerek rendszerint szabványosított alkalmazásfejlesztési keretrendszereket igényelnek, és működtetésük jelentősen leegyszerűsíthető, ha a szükséges futtatási környezetet maga a felhőszolgáltató üzemelteti és menedzseli. Ilyen lehet például egy ASP.Net-, Spring- vagy NodeJS-alapú webalkalmazás megfelelő háttéradatbázissal. Ebben az esetben a felhasználó számára nem csupán az infrastruktúra, hanem maga a futtatási platform is rendelkezésre áll. Ezt a modellt Platform-as-a-Service-nek, azaz PaaS-nek nevezzük. A felhasználó feladata ilyenkor többnyire arra korlátozódik, hogy elkészítse és telepítse az alkalmazást a rendelkezésre bocsátott platformra.

*3-2. ábra. A felhő különböző szolgáltatási rétegei*

A szolgáltatási szintek ennél magasabb absztrakciós fokot is elérhetnek. Ilyenkor egy teljes szoftverrendszer válik közvetlenül elérhetővé a felhőben. Ennek legegyszerűbb példája a felhőalapú e-mail szolgáltatás. A felhasználókat nem érdekli a szolgáltatás működtetésének technikai részlete, sem a szerverek földrajzi elhelyezkedése, sem a szoftver kezelése. Számukra az a fontos, hogy elektronikus leveleket tudjanak küldeni és fogadni. A Software-as-a-Service, vagyis a SaaS jól szemlélteti, miként lehet egy hasznos funkciót szolgáltatásként absztrahálni és felhasználók milliói számára elérhetővé tenni.

Ahogy a szolgáltatási piramis magasabb szintjei felé haladunk, a felhasználó részvétele a rendszer üzemeltetésében és kezelésében egyre kisebb lesz. Másképpen fogalmazva: minél magasabb szintű a szolgáltatás, annál kevesebb menedzsmentfeladat marad a felhasználónál.

*3-3. ábra. A menedzsmentfelelősség változása a felhő különböző absztrakciós rétegeiben*

Az utóbbi időben az IaaS, PaaS és SaaS hagyományos rétegei mellett újabb szolgáltatástípusok is megjelentek, mindenekelőtt a Container-as-a-Service (CaaS) és a Function-as-a-Service (FaaS). Ezekkel a későbbi, programozással foglalkozó fejezetek részletesebben is foglalkoznak.

### 3.2 A felhő gazdaságossága

A felhő egyik legfontosabb vonzereje a kedvező költségszint, a hatékonyság és a megbízhatóság. Ezek alapja a méretgazdaságosság. A felhőalapú adatközpontok rendkívül nagy, központosított szerverparkok, amelyekben igen magas a szerver- és tárolósűrűség. A nagy lépték lehetővé teszi, hogy a szolgáltatók az alkatrészeket kedvezményes áron szerezzék be, és hasonló előnyök érvényesülhetnek az energiaellátás költségeiben is. A központosítás emellett megkönnyíti a kiemelkedő szintű fizikai és informatikai biztonság megvalósítását. Mivel az adatközpontban működő rendszerek nagyrészt hasonló felépítésűek, számos adminisztratív feladat teljes mértékben automatizálható, így az informatikai személyzet költsége viszonylag alacsony szinten tartható.

*3-4. ábra. A Google egyik felhő-adatközpontja*

*3-5. ábra. Az Amazon egyik felhő-adatközpontja*

A központosított kialakítás azt is lehetővé teszi, hogy a felhőszolgáltatók rendkívül hatékonyan üzemeltessék központjaikat. Az ilyen működési hatékonyság és a rendelkezésre álló biztonsági megoldások szintje hagyományos vállalati informatikai infrastruktúrában általában csak nagyon nehezen érhető el.

Természetesen a felhőszolgáltató feladata nem merül ki abban, hogy egy IaaS-, PaaS- vagy SaaS-szolgáltatáspéldányt biztosítson. Az üzemeltetésnek számos további olyan tényezője van, amelyre egy szolgáltatónak figyelmet kell fordítania. Ezek közé tartozik például a belső menedzsment, a szabályozói megfelelés és az auditálás, valamint a magasabb szintű szolgáltatások nyújtása, például a szolgáltatásközvetítés.

*3-6. ábra. Egy Amazon-adatközpont belseje*

*3-7. ábra. Egy Google-adatközpont belseje*

*3-8. ábra. A Google adatközponti hűtőrendszerének gépészeti tere*

*3-9. ábra. Egy általános felhőtechnológiai verem. Jól látható, hogy a szolgáltatások (IaaS, PaaS, SaaS) csak kis részét alkotják egy valós felhőrendszer teljes léptékének*

A felhőtechnológiai verem egészét tekintve jól látható, hogy az IaaS-, PaaS- és SaaS-rétegek csupán viszonylag kis részét alkotják egy valós felhőrendszer teljes működési és szervezeti összetettségének.

### 3.3 Felhasználói és használati támogatás a felhőben

A felhasználói támogatást eddig elsősorban a menedzsment részvételének szempontjából vizsgáltuk. A felhőszolgáltatások azonban más módon is megkülönböztethetők, mégpedig a felhasználók funkcionális igényei alapján. A felhőben dolgozó szoftverfejlesztők számára elsősorban fejlesztői támogatási elemekre van szükség, például forráskód-tárakra, tesztkörnyezetekre és egyéb fejlesztési eszközökre. Az ipari végfelhasználók ezzel szemben gyakran az adott szakterületükhöz kapcsolódó speciális technológiákat igénylik, ilyen például a dolgok internete (IoT) támogatása. Az adatközpontú felhasználók számára pedig a különféle adattárolási és adatelemzési lehetőségek széles választéka a legfontosabb. Ezek a különbségek jól mutatják, hogy a felhőplatformok szolgáltatásai eltérő felhasználói közösségek igényeihez igazodnak.

*3-10. ábra. Egy felhőplatform különböző szolgáltatásai, eltérő felhasználói közösségek számára*

### 3.4 Egy kis felhőtörténelem

Mielőtt részletesen áttekintenénk a nagy felhőszolgáltatókat, szolgáltatásaikat és a hozzájuk kapcsolódó programozási lehetőségeket, érdemes röviden végignézni az elmúlt két évtized fejleményeit. Ez segít megérteni, hogyan jelentek meg a modern felhőszolgáltatók, valamint milyen motivációk, okok és üzleti lehetőségek vezettek a mai helyzet kialakulásához.

Napjaink legnagyobb felhőszolgáltatói az Amazon, a Microsoft és a Google, őket pedig az Alibaba, az Oracle, az IBM és más szereplők követik. A 3-11. ábra elemző diagramja szerint a világpiaci részesedés és az éves növekedési ütem koordinátarendszerében az Amazon egyértelműen uralja a globális piacot. A Microsoft és a Google gyors növekedést mutat, de kérdéses, hogy piaci részesedésben utolérhetik-e az Amazont. Az Oracle és az IBM ezzel szemben kisebb szereplőnek tűnik, mérsékeltebb növekedési potenciállal.

*3-11. ábra. A globális felhőszolgáltatók helyzete piaci részesedés és éves növekedési ütem alapján*

A Gartner Group egy másik elemzése a felhőszolgáltatókat egy négymezős mátrixban helyezte el, összvíziójuk és annak megvalósítási képessége alapján. A kategóriák a következők: vezetők, kihívók, jövőképpel rendelkezők és piaci réskitöltők. A 3-12. ábra a 2015 és 2020 közötti eredmények négy pillanatfelvételét mutatja be. Ezek alapján jól látható, hogy az Amazon globális vezető szerepe egyértelmű, ugyanakkor különösen érdekes megfigyelni, hogy a Google folyamatosan erősödik, és egyre inkább csökkenti a Microsofttal szembeni lemaradását.

*3-12. ábra. A felhőszolgáltatók helyzetének változása a Gartner Group négymezős elemzésében 2015 és 2020 között*

#### 3.4.1 Az Amazon felhőszolgáltatásának eredete

Az Amazon vállalatot 1994-ben alapították azzal a céllal, hogy könyveket, zenéket és elektronikai cikkeket értékesítsen az interneten. Joggal merül fel a kérdés, hogyan jutott el a cég a felhőszolgáltatások világába, és miként vált annak egyik vezető szereplőjévé. A történet egyaránt tanulságos és figyelemre méltó.

Az Amazon eredeti üzleti elképzelése az volt, hogy nagy léptékben és nagyon alacsony áron értékesítsen termékeket online. Az alacsony árak eléréséhez ki kellett iktatni a közvetítőket az értékesítési folyamatból, vagyis az árukat közvetlenül a raktárból kellett eljuttatni a vevőkhöz. Ehhez az is szükséges volt, hogy a rendelések felvétele, feldolgozása és a kiszállítás a lehető leggyorsabban, korszerű számítógépes megoldások segítségével történjen. Az első években a belső szoftverfejlesztés meglehetősen ad hoc módon zajlott, hosszú távú működési és növekedési szempontok érdemi figyelembevétele nélkül. Az 1990-es évek végére a vállalat egyre nehezebben tudott hatékonyan új rendszereket fejleszteni. Ez különösen komoly problémává vált akkor, amikor a cég a Target és a Marks & Spencer számára online vásárlási technológiákat fejlesztett. Kiderült, hogy a felhalmozott tapasztalat ellenére sem sikerül csökkenteni a teljes fejlesztési időt, mert számos infrastruktúra- és háttérkomponenst minden alkalommal a nulláról kellett felépíteni.

A probléma felismerése nyomán a vállalat 2000 körül új belső szabályokat vezetett be. Minden fejlesztőcsoportnak szolgáltatásorientált tervezési módszertant kellett alkalmaznia, és az általa készített rendszerekhez jól meghatározott interfészeket, vagyis API-kat kellett kialakítania. Egy másik fontos előírás szerint az egyes csoportoknak a vállalaton belül már meglévő, más csapatok által készített szolgáltatásokat kellett használniuk, és lehetőség szerint ezekre kellett építeniük saját megoldásaikat. Új szolgáltatás fejlesztésére csak akkor kerülhetett sor, ha az adott funkció még nem állt rendelkezésre. Néhány év alatt ez a szemlélet alapvetően átalakította a vállalat működését, és az Amazon fokozatosan szolgáltatásközpontú céggé vált. A szolgáltatásorientált megközelítés az infrastruktúra szintjén is megjelent: a szerverek rugalmasabbá és könnyebben kezelhetővé tétele érdekében virtuális gépeket kezdtek alkalmazni. Ennek az átalakulásnak az első látványos eredménye a 2002-ben közzétett SOAP/XML API volt, amely lehetővé tette az Amazon webáruház-katalógusának programozott elérését a partnerek számára. 2003-ban a vállalat vezetése felismerte, hogy az informatikai üzemeltetésben és a szolgáltatáskomponensek kialakításában megszerzett tapasztalat kiemelkedő erősséget jelent, ezért létrehozta az Amazon Web Services (AWS) nevű szervezeti egységet, amely már külső ügyfelek számára is kínált erőforrásokat és szolgáltatásokat.

Három év fejlesztés után, 2006-ban az Amazon elindította néhány alapvető szolgáltatását: a Simple Storage Service (S3), az Elastic Compute Cloud (EC2) és a Simple Queue Service (SQS) rendszereket. Ekkor még kevesen gondolták, hogy ez a lépés a világ legnagyobb felhőszolgáltatójának megszületését jelenti. A siker és az azt követő növekedés sokak számára váratlan volt. 2009-ben az EC2 szolgáltatásai Európában is elérhetővé váltak. A fejlesztés azóta is folyamatos, miközben a versenytársak csak többéves késéssel reagáltak. Az Amazon időközben nemcsak felhőszolgáltatóvá vált, hanem a világ egyik legnagyobb és legértékesebb vállalatává is, amely gyakorlatilag szinte mindent értékesít, amit el lehet képzelni. A háttérben a cég az évek során jelentős szakértelmet halmozott fel a gépi tanulás és a mesterséges intelligencia területén is, így ezen a területen szintén meghatározó szereplővé lépett elő.

#### 3.4.2 A Microsoft és a felhő

A Microsoft felhőplatformjának fejlesztése 2008-ban indult. Az eredetileg Windows Azure néven bevezetett rendszer 2010-ben jelent meg, majd később Microsoft Azure névre nevezték át. A Microsoft kezdetben elsősorban üzleti partnereire összpontosított: számukra az informatikai infrastruktúra üzemeltetésének lényegesen egyszerűbb alternatíváját kínálta, valamint lehetővé tette, hogy meglévő alkalmazásaikat a kód módosítása nélkül akár több millió felhasználóra skálázzák.

Később ez a fókusz jelentősen kibővült, és ennek eredményeként egy világszinten működő, széles szolgáltatáspalettát nyújtó rendszer jött létre, amely egyaránt kiszolgálja a végfelhasználókat és a vállalatokat. A Microsoft törekvéseinek sikerét jól mutatja, hogy a felhőszolgáltatók között a második helyet foglalja el.

#### 3.4.3 Google Cloud

A Google keresőszolgáltatóként működő vállalatként hatalmas szerverfarmokra támaszkodott, amelyek percenként keresési lekérdezések millióit szolgálták ki, ezért jelentős tapasztalatot halmozott fel a szerverek hatékony üzemeltetése és menedzselése terén. Nem meglepő tehát, hogy a cég érdeklődni kezdett a felhőszolgáltatások nyújtása iránt. Első ilyen szolgáltatásukat, a webalkalmazások számára platformot biztosító Google App Engine-t 2008-ban indították el. Ezt egymás után további szolgáltatások követték: 2010-ben jelent meg a Google Cloud Storage és a BigQuery, 2011-ben a Google Cloud SQL, majd 2013-ra a Google Compute Engine is elérhetővé vált. A vállalat rendkívül agresszív fejlesztési és növekedési stratégiát követett a felhő területén, ennek eredményeként pedig mára a leggyorsabban növekvő felhőszolgáltatóvá vált. A Google-on belül a felhőüzletág lett a vállalat leggyorsabban bővülő és egyben legnagyobb nyereséget termelő részlege.

#### 3.4.4 IBM és Oracle

A felhőpiac viszonylag későn belépő szereplői közé tartozik az IBM és az Oracle. Az IBM 2013-ban kezdte el saját felhőrendszerének fejlesztését, kezdetben az infrastruktúra mint szolgáltatás (IaaS) megoldásokra összpontosítva. 2016-ban már platformszolgáltatásokat is bevezetett, 2017-re pedig a szolgáltatási piramis valamennyi rétegében megjelent. Az Oracle 2016-ban indította el felhőszolgáltatását, majd ezt fokozatosan bővítette, hogy sokféle felhasználási esetet lefedjen, és különböző alkalmazási területek igényeit is támogassa.

### 3.5 Árazás

Emlékezzünk vissza a utility computing modellre és a Sun konténerére, amelyek egységes, 1 USD/CPU-óra árat alkalmaztak. Ezt az árazási sémát fix árú on-demand, illetve pay-as-you-go árazásnak nevezzük. Az Amazon 2006-ban szolgáltatásai esetében ugyanezt a fix áras modellt használta, óránkénti elszámolással. Az óránkénti elszámolás azt jelentette, hogy ha egy erőforrást a felhasználó csak 5 percig vett igénybe, akkor is a teljes óradíjat kellett megfizetnie. Néhány évvel később ez a séma tovább fejlődött: az elszámolási egység előbb 5 percre, majd 1 percre, végül 1 másodpercre csökkent. A perc- és másodpercalapú díjszabás különösen hasznosnak bizonyult az olyan lökésszerű terhelések esetén, amelyek rövid ideig tartanak, de nagy számítási kapacitást igényelnek. A fix áras modell általában kedvező a vállalatok számára, mert az erőforrás-felhasználás tervezését, költségvetését és könyvelését egyszerűvé és jól áttekinthetővé teszi.

Az árazási stratégiák további fejlődése a kedvezményes és a dinamikus árazás megjelenéséhez vezetett. A reserved pricing esetében a felhasználó előre foglalási díjat fizet egy meghatározott mennyiségű erőforrásért, amelyet ezt követően alacsonyabb, kedvezményes áron használhat. Ez a megközelítés fogalmilag hasonló a Grid számítási rendszerek erőforrás-közvetítési mechanizmusához, ahol a felhasználóknak erőforrásokat kellett lefoglalniuk a különböző számítógépeken történő egyidejű végrehajtáshoz. Egy másik lehetőség a spot pricing, amely dinamikus, aukcióalapú árképzési mechanizmust alkalmaz. A spot pricing jellemzően a kihasználatlan erőforrások esetén használatos, ahol az alacsony induló ár célja az, hogy felkeltse a felhasználók érdeklődését az egyébként tétlen kapacitások iránt. E három alapvető árazási séma számos finomabb változatban is megjelenik. Ezek közül néhányat a kiválasztott felhőszolgáltatások részletes áttekintése során fogunk megvizsgálni.

### 3.6 Programozás

Mivel a felhőkörnyezet elsődleges célja számítási feladatok végrehajtása, legyen szó webalkalmazásokról, adatfeldolgozásról vagy gépi tanulási munkafolyamatokról, természetes módon merül fel a programozási nyelvek kérdése. Mely programozási nyelv vagy nyelvek használhatók felhőalkalmazások létrehozására?

Ezzel kapcsolatban két, egymással ellentétes követelmény jelenik meg. A felhasználók azt szeretnék, hogy programjaik a lehető legszélesebb erőforráskészleten legyenek futtathatók; ideális esetben ez teljes platformfüggetlenséget jelent. Ugyanakkor meg kívánják őrizni és továbbra is használni szeretnék meglévő forráskódjukat, komponenseiket és alkalmazásaikat, és elvárják, hogy ezek a felhőben is közvetlenül, kódmódosítás nélkül használhatók legyenek.

Természetesen a szolgáltatók számára is az lenne kedvező, ha csak egyetlen nyelvet vagy legfeljebb néhány nyelvet kellene támogatniuk, mivel minden támogatott nyelv esetén az adott felhőprogramozási API teljes megvalósítását is el kell készíteni az adott nyelven. Ez növeli a kódbázis méretét, valamint a tesztelési, karbantartási és továbbfejlesztési ráfordításokat.

E követelmények ütközésének eredményeként napjainkban a legtöbb felhőszolgáltató arra törekszik, hogy minél több programozási nyelvet támogasson. A legelterjedtebb nyelvek közé tartozik a JavaScript, a Java, a Python és a C#, de egyes szolgáltatóknál számos további nyelv is elérhető.

## 4. Amazon AWS

Az Amazon Web Services a világ legnagyobb és vezető felhőrendszere. A felhasználók számára a szolgáltatások legszélesebb választékát kínálja, egyaránt elérhetők önálló komponensszolgáltatások és teljes alkalmazások. Az AWS weboldalán a szolgáltatások több kategóriába sorolva jelennek meg; az egyes kategóriákon belül több konkrét szolgáltatás található.

*4-1. ábra. Szolgáltatáskategóriák az Amazon Web Services rendszerében*

Az AWS számos iparág számára kínál speciális megoldásokat, amelyek megkönnyítik a felhőalapú technológiák bevezetését. Az alábbiakban néhány fontosabb iparág és a hozzájuk kapcsolódó jellemző felhőmegoldások láthatók:

- `Reklám és marketing`: adatelemzésre, személyre szabásra, üzenetküldésre és marketingkampányok támogatására szolgáló megoldások.
- `Autóipar`: összekapcsolt járművekhez, autonóm vezetési fejlesztésekhez, gyártáshoz és ellátásilánc-menedzsmenthez kapcsolódó megoldások.
- `Fogyasztási cikkek`: intelligens gyárak, ellátási láncok, előrejelzések, okosotthonok, intelligens termékek és személyre szabás támogatása.
- `Oktatás`: általános és középiskolák, valamint egyetemek számára online tanulási, távoktatási, virtuális labor- és tantermi, streaming- és kapcsolattartási megoldások.
- `Energetika`: szeizmikus adatgyűjtéshez, tároláshoz és elemzéshez, tározószimulációhoz, mezőfejlesztési tervezéshez és felszín alatti adatok kezeléséhez készült megoldások.
- `Pénzügyi szolgáltatások`: banki, fizetési, tőkepiaci és biztosítási intézmények számára skálázható feldolgozási infrastruktúra, adatelemzés és gépi tanulás.
- `Játékipar`: adatbázis-, számítási, analitikai és gépi tanulási erőforrások játékfejlesztők és online játékszolgáltatók számára.
- `Kormányzati szféra`: közigazgatási és önkormányzati felhasználásra szánt kereskedelmi felhőszolgáltatások, minden biztonsági besorolási szinten.
- `Egészségügy és élettudományok`: egészségügyi szolgáltatók, biztosítók, gyógyszeripari és biotechnológiai szereplők, valamint genomikai alkalmazások támogatása adattárolással, skálázható számítással, analitikával és gépi tanulással.
- `Gyártás`: termék- és gyártástervezés, párhuzamos szimulációk, adatfeldolgozás, intelligens gyárak, valamint IoT- és Big Data-alapú intelligens termékek és szolgáltatások.
- `Média és szórakoztatóipar`: digitális tartalom-előállításra és -terjesztésre szolgáló megoldások, például videós alkalmazások, felhőalapú stúdiók és biztonságos tartalomstreamelés.
- `Nonprofit szféra`: weboldalakhoz, marketingkampányokhoz és IoT-alapú megfigyelési feladatokhoz készült megoldások.
- `Kiskereskedelem`: webes és online vásárlási rendszerek, ügyfélkapcsolat-kezelés, adatelemzés és gépi tanulás támogatása.
- `Távközlés`: számlázási, tartalomkézbesítési és ügyfélszolgálati megoldások.
- `Utazás és vendéglátás`: személyre szabás, az IT-költségek csökkentése és az ügyfélkiszolgálás javítása.

Az Amazon szolgáltatásait a világ legnagyobb felhőinfrastruktúrájára építi. Az AWS 245 országban érhető el, és 24 földrajzi régióban működtet adatközpontokat. Minden régió több Availability Zone-ból áll, amelyeket alacsony késleltetésű, nagy áteresztőképességű és redundáns hálózatok kapcsolnak össze a magas rendelkezésre állás és a hibatűrés biztosítása érdekében. A zónák önálló hibahatárolási egységeknek tekinthetők. A következő alfejezetekben az AWS néhány kulcsfontosságú szolgáltatását tekintjük át.

*4-2. ábra. A meglévő és tervezett AWS-régiók világszerte*

### 4.1 IaaS-rétegbeli szolgáltatások

Az AWS infrastruktúrarétegének alapvető szolgáltatásai az általános számítógépes rendszerek legfontosabb elemeit absztrahálják, vagyis a számítási, tárolási és hálózati képességeket.

#### 4.1.1 Számítási szolgáltatások

Az Amazon Elastic Compute Cloud, röviden Amazon EC2, az Amazon egyik legkorábban bevezetett szolgáltatása, amely webszolgáltatásként elérhető virtuális gépeket biztosít. A virtuális gépek különböző hardvererőforrásokon futtathatók, amelyek az alábbi példánytípus-csoportok valamelyikébe tartoznak: általános célú, számításra optimalizált, memóriára optimalizált, tárolásra optimalizált, illetve gyorsítóalapú rendszerek, például GPU- vagy FPGA-megoldások.

Az általános célú példányok üzletileg kritikus alkalmazásokhoz, kis- és közepes méretű adatbázisokhoz, valamint webes alkalmazási rétegekhez készültek. A számításra optimalizált csoport nagy teljesítményű számítási feladatokhoz, kötegelt feldolgozáshoz és videókódoláshoz ideális. A memóriára optimalizált példányok nagy teljesítményű adatbázisok, elosztott, webes méretű in-memory gyorsítótárak és valós idejű Big Data-elemzések támogatására alkalmasak. A tárolásra optimalizált példányok különösen jól használhatók NoSQL-adatbázisokhoz, adattárházakhoz és elosztott fájlrendszerekhez. A gyorsítóval ellátott példányok elsősorban számításigényes gépi tanulási feladatokra, grafikaigényes alkalmazásokra, HPC-algoritmusokra és játékokra ajánlhatók.

Minden példánycsoport több példányosztályt tartalmaz, amelyek az adott hardverplatform jellemzőit írják le. Az AWS általános célú csoportjába például az `A1`, `M4`, `M5`, `M5a`, `M5n`, `M6g`, `T2`, `T3`, `T3a` és `T4g` osztályok tartoznak. Az `A1` osztály Amazon ARM-alapú, 64 bites Graviton processzort használ. Az `M4` és `M5` osztályok Intel Xeon CPU-kra épülnek, míg az `M5a` AMD EPYC processzorokat alkalmaz. Az `M5n` az `M5` osztály nagyobb hálózati sávszélességű változata. A `T` osztályok, vagyis a `T2-T4` típusok úgynevezett burstable példányok, amelyek sajátos használati modellt kínálnak. Ezek alapértelmezett teljesítményszintet nyújtanak, de átmeneti, csúcsterheléses helyzetekben magasabb teljesítmény leadására is képesek. Az alacsony kihasználtságú időszakokban krediteket gyűjtenek, amelyek a burst üzemmód többleterőforrás-igényének fedezésére használhatók fel.

A magok száma, a memória típusa és mérete, valamint a hálózati sávszélesség széles tartományban változhat. A magszám például `1` és `96` virtuális CPU között, a memória `8 GB` és `24 TB` között, a hálózati sávszélesség pedig `1` és `100 Gbps` között alakulhat. Az alábbi táblázat az általános célú `M4` példánytípus elérhető konfigurációit mutatja be.

| Példány | vCPU | Memória (GiB) | Tárolás | Dedikált EBS-sávszélesség (Mbps) | Hálózati teljesítmény |
|---|---:|---:|---|---:|---|
| `m4.large` | 2 | 8 | EBS-only | 450 | Moderate |
| `m4.xlarge` | 4 | 16 | EBS-only | 750 | High |
| `m4.2xlarge` | 8 | 32 | EBS-only | 1,000 | High |
| `m4.4xlarge` | 16 | 64 | EBS-only | 2,000 | High |
| `m4.10xlarge` | 40 | 160 | EBS-only | 4,000 | 10 Gigabit |
| `m4.16xlarge` | 64 | 256 | EBS-only | 10,000 | 25 Gigabit |

Az EC2 számítási szolgáltatásnak több további változata is létezik. Az Amazon EC2 Autoscaling szolgáltatás automatikusan hozzáadja vagy eltávolítja a számítási kapacitást a terhelés változásainak megfelelően. Az Amazon EC2 Spot a `spot pricing` modellt használja, és hibatűrő feladatok esetén akár `90%`-os költségmegtakarítást is lehetővé tehet. Az AWS Batch olyan esetekre nyújt támogatást, amikor több számítási feladatot kell végrehajtani. A szolgáltatás leegyszerűsíti a folyamatot, mert nincs szükség fix méretű klaszter létrehozására, sem feladatütemező és -kezelő szoftver telepítésére. A rendszer automatikusan ütemezi és végrehajtja a feladatokat, és dinamikus skálázással annyi erőforrást használ fel, amennyire az adott munkához szükség van. Ez a szolgáltatás különösen hasznos tudományos vizsgálatok, például molekuladinamikai szimulációk, genetikai kutatások és fizikai paraméterseprések esetén, valamint a médiaszektorban is, például animációs filmek készítésekor vagy utómunka során végzett speciális effektusfeldolgozáskor.

#### 4.1.2 Tárolási szolgáltatások

Az Amazon három fő felhőalapú tárolási lehetőséget kínál: objektumtárolási, fájltárolási és blokkszintű tárolási szolgáltatásokat. A három megoldás közötti különbség elsősorban a tervezett felhasználási célban és az adatelérési interfészben rejlik.

**Amazon Simple Storage Service S3**

Az `S3` szolgáltatásban az adatok objektumokként, úgynevezett tárolóvödrökben (`buckets`) tárolódnak. Egyetlen objektum mérete legfeljebb `5 TB` lehet. A szolgáltatás képes a tárolókapacitást automatikusan fel- vagy leskálázni a változó igényekhez igazodva. Az `S3` adattartósságát `99.999999999%`-ra tervezik. Ennek biztosítása érdekében az `S3` automatikusan több rendszeren hoz létre és tárol másolatokat minden `S3`-objektumról.

Az `S3` emellett képes metaadatcímkéket rendelni az objektumokhoz, kezelni az adathozzáférési jogosultságokat, védeni az adatokat a jogosulatlan felhasználókkal szemben, nagyméretű adatelemzési feladatokat támogatni, valamint monitorozni az adatokat objektum- és bucket-szinten. Az objektumok elérhetők `S3 Access Points` használatával, illetve közvetlenül a bucket hosztnevén keresztül. A szolgáltatás különböző tárolási osztályokat alkalmaz, amelyek az adatelérési idő, a redundancia és a tárolási méret szempontjából térnek el egymástól. Ezek az `S3 Storage Classes` a következők: `S3 Standard`, `S3 Intelligent-Tiering`, `S3 Standard-Infrequent Access`, `S3 One Zone-Infrequent Access`, `Amazon S3 Glacier`, `Amazon S3 Glacier Deep Archive` és `S3 Outposts`.

Az `S3` egyik figyelemre méltó tulajdonsága, hogy az adatok hozzáférési mintázata alapján automatikusan képes áthelyezni az objektumokat a különböző tárolási osztályok között. Ez a művelet felhasználói beavatkozás nélkül történik, és jelentős költségmegtakarítást eredményezhet.

*4-3. ábra. Intelligens adattierelés az AWS S3 szolgáltatásban*

**Amazon Elastic File System**

Az Amazon Elastic File System (`Amazon EFS`) hagyományosabb jellegű adattárolást valósít meg. Egy egyszerűen használható, skálázható, teljes mértékben menedzselt, rugalmas `NFS` fájlrendszert biztosít, amely `AWS Cloud` szolgáltatásokkal és helyszíni erőforrásokkal egyaránt használható. Az `EFS` egyik kulcsfontosságú jellemzője, hogy igény szerint akár petabájtos méretig képes skálázódni anélkül, hogy ez megzavarná az alkalmazások működését. Az `EFS`-ben két tárolási osztály érhető el: a `Standard storage class` és az `Infrequent Access storage class (EFS IA)`. Az `Infrequent Access` olyan fájlok esetén kínál kedvező ár/teljesítmény arányt, amelyekhez nem szükséges napi szintű hozzáférés. Az `EFS Lifecycle Management` segítségével az ilyen ritkán használt fájlok automatikusan és transzparens módon áthelyezhetők az `EFS IA` osztályba.

**Amazon Elastic Block Store**

Az Amazon Elastic Block Store (`EBS`) olyan munkaterhelésekhez készült, amelyek nagy átviteli teljesítményt vagy intenzív tranzakciókezelést igényelnek, például relációs és nem relációs adatbázisokhoz, vállalati alkalmazásokhoz, konténerizált alkalmazásokhoz és big data elemzőmotorokhoz. A szolgáltatás egy könnyen használható, nagy teljesítményű blokkszintű tárolási megoldás, amelyet `Amazon Elastic Compute Cloud (EC2)` környezetben való használatra terveztek. Az optimális ár és teljesítmény egyensúlyának eléréséhez öt különböző kötettípus közül lehet választani. Az egyik végletet az egy számjegyű ezredmásodperces késleltetést biztosító megoldások jelentik, amelyek nagy teljesítményű adatbázis-terhelésekhez alkalmasak, míg a másik végletet a `GB/s` nagyságrendű átviteli sebességet nyújtó kötettípusok képviselik, amelyek nagy, szekvenciális munkaterhelésekhez, például `Hadoop`-feladatokhoz ideálisak. A kötettípusok teljesítménye finomhangolható, a kötetek mérete pedig az alkalmazások megszakítása nélkül növelhető. Az `EBS`-köteteket egy `Availability Zone (AZ)`-on belül replikálják a kritikus rendszerek támogatása érdekében.

**Adatbiztonság**

A felhőben történő adattárolással kapcsolatban az egyik leggyakoribb aggodalom a biztonság. Mennyire vannak biztonságban az adataink? Sok felhasználó jelentős előnyökhöz juthatna a felhő használatából, mégis elutasítja azt, mert úgy érzi, hogy adatai nincsenek megfelelően védve. Természetesen léteznek olyan helyzetek is, amikor például jogszabályi előírások tiltják az adatok üzleti szervezeten vagy intézményen kívüli tárolását. Jó példát jelentenek erre a pénzügyi és az egészségügyi intézmények. Minden más esetben azonban az adatvesztéstől való félelem többnyire indokolatlan.

Alapértelmezés szerint a felhőben az adatok mindig titkosítva vannak. Titkosítottak az átvitel során, és titkosítva tárolódnak a tárolóeszközökön is. Az Amazon S3 támogatja mind a szerveroldali titkosítást, három különböző kulcskezelési lehetőséggel, mind pedig a kliensoldali titkosítást adatfeltöltések esetén. Még ha egy adat véletlenül ki is szivárog, titkosított formában kerül ki, így a támadók számára gyakorlatilag használhatatlan marad. A legtöbb ismert felhős adatszivárgási eset hátterében emberi hiba állt. Az olyan felhőszolgáltatók, mint az Amazon, a Microsoft és a Google a világ legjobb biztonsági szakembereit alkalmazzák, és a helyszíni IT-infrastruktúrákhoz képest rendszerint jóval szigorúbb biztonsági szintet működtetnek.

A titkosításon túl az Amazon `S3` rugalmas biztonsági funkciókat is kínál a jogosulatlan hozzáférések megakadályozására. Minden adat alapértelmezés szerint csak annak a felhasználónak érhető el, aki létrehozta. Megosztásra kizárólag kifejezett beállítás esetén van lehetőség, amelyet az `AWS access pointok` szabályoznak az `Identity and Access Management (IAM)` rendszer felügyelete mellett. Ha még erősebb elszigetelésre van szükség, virtuális magánfelhők, azaz `Virtual Private Cloud (VPC)` környezetek is létrehozhatók, például `Amazon Virtual Private Cloud (Amazon VPC)` formájában.

#### 4.1.3 Hálózati szolgáltatások

Az informatikai infrastruktúra harmadik fő összetevője a számítási és tárolási szolgáltatások mellett a hálózat. Felmerülhet a kérdés, hogy miért tekintjük ezt külön szolgáltatási területnek: vajon nem csupán a rendszerkomponensek közötti automatikus kapcsolatot jelenti? A felhőalkalmazások esetében azonban a hálózati igények rendkívül sokfélék lehetnek. A felhasználók köre azoktól az egyéni ügyfelektől terjed, akik a felhőt például családi fényképek biztonsági mentésére használják, egészen a nagy multinacionális vállalatokig, amelyek teljes működésüket felhőinfrastruktúrára építik.

E sokféle követelmény támogatására az AWS több, egymással kombinálható hálózati szolgáltatást kínál, amelyek együtt biztosítják a szükséges kapcsolati réteget. Ide tartozik az `Amazon Virtual Private Cloud (Amazon VPC)`, az `AWS Transit Gateway`, az `AWS PrivateLink`, az `Amazon Route 53`, az `Elastic Load Balancing`, az `AWS Global Accelerator`, az `AWS Shield`, az `AWS WAF`, az `AWS Firewall Manager` és az `AWS Virtual Private Network (VPN)`. Ezek a szolgáltatások szerepük szerint három fő csoportba sorolhatók: hálózatépítést, hálózati skálázást és hálózatbiztonságot támogató megoldások.

Az `Amazon VPC` feladata a felhőbeli hálózat kialakítása, vagyis egy logikailag elkülönített hálózati környezet meghatározása és létrehozása az AWS-erőforrások számára. Az `AWS Transit Gateway` központi összeköttetést biztosít a különböző `Virtual Private Cloud`-ok és a helyben üzemeltetett, úgynevezett `on-premises` hálózatok között. Ha szükséges, az `AWS PrivateLink` segítségével privát, dedikált és nem megosztott kapcsolat is létrehozható a felhő felé. Az `Amazon Route 53` menedzselt `DNS`-szolgáltatásként működik, és az internetes alkalmazásokhoz irányítja a felhasználókat. Az `AWS Virtual Private Network (VPN)` pedig lehetővé teszi, hogy az ügyfelek titkosított kommunikációs csatornákon keresztül kapcsolódjanak a felhőben lévő erőforrásokhoz, úgy, mintha azok helyi infrastruktúrában lennének elérhetők.

Az AWS a hálózatok skálázására is kínál szolgáltatásokat. Az `Elastic Load Balancing` például automatikusan osztja el a forgalmat egy erőforráshalmaz között, amelybe például virtuális géppéldányok, konténerek, IP-címek vagy `Lambda`-függvények tartozhatnak. A hálózati forgalom védelmét több biztonsági megoldás segíti. Az `AWS Shield` az AWS-en futó alkalmazásokat védi a `DDoS`-támadásokkal szemben, az `AWS WAF` a webalkalmazásokat óvja a gyakori webes támadásoktól és sérülékenységektől, míg az `AWS Firewall Manager` központi felületről teszi lehetővé a tűzfalszabályok konfigurálását és kezelését.

E fogalmak és szolgáltatások gyakorlati alkalmazását a 4-4. ábra szemlélteti, amely egy felhőalkalmazás hálózati felépítésében együtt jeleníti meg a privát és nyilvános alhálózatokat, a terheléselosztást és az automatikus skálázást.

*4-4. ábra. Privát és nyilvános alhálózatok, terheléselosztás és automatikus skálázás kombinációja egy felhőalkalmazás hálózati konfigurációjában*

### 4.2 PaaS-rétegbeli szolgáltatások

A fent tárgyalt különböző infrastruktúrarétegbeli szolgáltatások nagyfokú rugalmasságot biztosítanak a felhőalkalmazások fejlesztői számára. Hátrányuk ugyanakkor, hogy az alkalmazás és felhasználói köreinek növekedésével egyre több szolgáltatás bevonására van szükség a bonyolultság kezeléséhez, ami viszont magát az alkalmazást és annak üzemeltetését is összetettebbé teszi.

A `Platform as a Service (PaaS)` modellt ennek a problémának az enyhítésére hozták létre. A felhasználó, illetve a fejlesztő elől el vannak rejtve az alacsony szintű infrastruktúrarészletek, és számára elsősorban az alkalmazási réteg válik láthatóvá. Az Amazon ennek megfelelően az `Elastic Beanstalk` szolgáltatást kínálja univerzális felhőalkalmazás-futtatási platformként.

#### 4.2.1 AWS Elastic Beanstalk

Az `AWS Elastic Beanstalk` egy könnyen használható szolgáltatás webalkalmazások és szolgáltatások telepítésére, valamint skálázására. Az `Elastic Beanstalk` támogatja a `Go`, `Java`, `.NET`, `Node.js`, `PHP`, `Python` és `Ruby` nyelveken fejlesztett alkalmazásokat. Amikor egy alkalmazást telepítünk az `Elastic Beanstalk` környezetébe, például egy Java `*.war` állomány formájában, a rendszer létrehozza a kiválasztott támogatott platformverzióhoz tartozó futtatási környezetet, és az alkalmazás működtetéséhez egy vagy több AWS-erőforrást, például `Amazon EC2` példányokat biztosít.

Az `Elastic Beanstalk` automatikusan kezeli a kapacitásbiztosítás, a terheléselosztás, a skálázás és az alkalmazásállapot-figyelés feladatait. Az alkalmazás elindítása után a felhasználó maga is felügyelheti és monitorozhatja annak működését. Az alkalmazás telepítésének, indításának és kezelésének munkafolyamatát a 4-5. ábra szemlélteti.

*4-5. ábra. Az alkalmazáskezelés munkafolyamata*

Java alkalmazások esetén a futtatási környezetet egy `Apache Tomcat` webkonténer biztosítja, amely támogatja a `Java Servlets` és a `Java Server Faces` technológiákat.

### 4.3 SaaS-rétegbeli szolgáltatások

Bizonyos esetekben egy adott funkcionalitás önálló szolgáltatásként jelenik meg a felhasználók számára. Ilyenkor a felhasználóknak nincs szükségük arra, hogy ismerjék a szolgáltatás megvalósításának vagy üzemeltetésének részleteit. Számukra elegendő a felhasználói szintű működés ismerete, vagyis például az, hogyan lehet e-mailt küldeni vagy fogadni, fényképet megnyitni és szerkeszteni, illetve hasonló műveleteket végrehajtani. Az ilyen szolgáltatások jelentik a felhő legmagasabb absztrakciós szintjét, és `Software-as-a-Service (SaaS)` néven ismertek.

Az AWS legmagasabb szintű SaaS-kínálata számos alkalmazási területet lefed, többek között az infrastruktúra, az üzleti alkalmazások, az ipari megoldások, a gépi tanulás és az `IoT` területét. Az AWS-re épülő több száz külső SaaS-alkalmazás mellett az Amazon saját SaaS-szolgáltatásokat is kínál, például a `WorkDocs`, a `WorkMail` és a `Chime` irodai együttműködést támogató megoldásokat, valamint a `QuickSight` adatelemző szolgáltatást. Emellett több olyan SaaS-komponens is rendelkezésre áll, amelyek meglévő alkalmazásokba integrálva fejlett funkciókat biztosítanak, például szövegelemzést (`Comprehend`), fordítást (`Translate`), kép- és videóelemzést (`Rekognition`), beszédszintézist (`Polly`), illetve beszédfelismerést és -értelmezést (`Transcribe`).

### 4.4 Szolgáltatásvezérlés és API-k

Az AWS-szolgáltatások és -alkalmazások többféle programozási nyelven is elérhetők. Az egyes nyelvek támogatása `SDK (Software Development Kit)` formájában történik. Az AWS által támogatott SDK-k: `JavaScript`, `Python`, `PHP`, `.NET`, `Ruby`, `Java`, `Go`, `Node.js` és `C++`.

A legtöbb szolgáltatás a parancssori felületről (`Command Line Interface`, `CLI`) is vezérelhető. Az általános felület az `AWS CLI`, amely minden szolgáltatáshoz parancssori hozzáférést biztosít. Emellett külön specializált parancssori felületek is rendelkezésre állnak az `ECS`, az `Elastic Beanstalk`, az `Amplify`, az `Amazon Machine Image` és a `serverless` alkalmazások számára. A `CLI`-parancsok segítségével a felhasználók több AWS-szolgáltatást is irányíthatnak. Szkriptek írásával a gyakori feladatok automatizálása is megoldható. Az `AWS CLI` szolgáltatásai közé tartoznak a továbbfejlesztett telepítők, az új konfigurációs lehetőségek, például az `AWS Single Sign-On (SSO)`, az operációs rendszer shell-parancsainak végrehajtása, valamint különféle interaktív funkciók, mint a `fuzzy auto-completion` és a dinamikus beágyazott dokumentáció. Néhány rövid példa:

```bash
$ aws ec2 describe-instances
$ aws ec2 start-instances --instance-ids i-1348636c
$ aws sns publish --topic-arn arn:aws:sns:us-east-1:546419318123:OperationsError -message "Script Failure"
$ aws sqs receive-message --queue-url https://queue.amazonaws.com/546419318123/Test
$ aws help
```

A Java SDK átfogó osztálykészletet biztosít a különféle AWS-szolgáltatások vezérléséhez és programozásához. Az API dokumentációja itt érhető el: `https://sdk.amazonaws.com/java/api/latest/`. Érdemes megjegyezni, hogy az AWS Java SDK több mint `73000` Java-osztályt és interfészt tartalmaz. Ez hozzávetőleg tízszerese a `Java SE` platform osztályainak számának. Ez jól érzékelteti az AWS szolgáltatási infrastruktúrájának méretét és gazdagságát.

A Java SDK dokumentációja számos példaprogramot is tartalmaz, amelyek bemutatják az osztályok használatát, valamint különféle felhasználási eseteken keresztül a szolgáltatások integrációját és vezérlését. A példák itt találhatók: `https://github.com/awsdocs/aws-doc-sdk-examples/tree/master/javav2`. Ebben a fejezetben csak néhány reprezentatív példát tekintünk át. Az első mintaprogram egy Elastic Compute példányt hoz létre.

```java
String name = args[0];
String amiId = args[1];

// name of the instance
// OS image ID

Region region = Region.US_WEST_2;
Ec2Client ec2 = Ec2Client.builder()
    .region(region)
    .build();

// create an instance
String instanceId = createEC2Instance(ec2, name, amiId);
System.out.println("The Amazon EC2 Instance ID is " + instanceId);
ec2.close();

RunInstancesRequest runRequest = RunInstancesRequest.builder()
    .imageId(amiId)
    .instanceType(InstanceType.T1_MICRO)
    .maxCount(1)
    .minCount(1)
    .build();

// once created, start the instance
RunInstancesResponse response = ec2.runInstances(runRequest);
String createdInstanceId = response.instances().get(0).instanceId();

Tag tag = Tag.builder()
    .key("Name")
    .value(name)
    .build();

CreateTagsRequest tagRequest = CreateTagsRequest.builder()
    .resources(createdInstanceId)
    .tags(tag)
    .build();

try {
    ec2.createTags(tagRequest);
    System.out.printf(
        "Successfully started EC2 Instance %s based on AMI %s",
        createdInstanceId, amiId);
} catch (Ec2Exception e) {
    System.err.println(e.awsErrorDetails().errorMessage());
    System.exit(1);
}
```

A második mintaprogram egy futó, `instanceId` alapján azonosított `EC2` példányt ér el, és bekapcsolja annak monitorozását.

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
System.out.printf("Successfully enabled monitoring for instance %s", instanceId);
```

## 5. Google Cloud Platform

A Google valószínűleg a világ leggyorsabban növekvő felhőszolgáltatója. A Google Cloud Platform (GCP) szolgáltatások széles körét kínálja a legalacsonyabb, infrastruktúra-szinttől egészen a legabsztraktabb szoftveres és serverless szolgáltatástípusokig. A Google Cloud Platform több mint 200 országban érhető el. A Google a világ számos pontján üzemeltet adatközpontokat (lásd az 5-1. ábrát).

*5-1. ábra. A GCP adatközpontjainak elhelyezkedése*

A GCP-ben az erőforrások régiókba szerveződnek, amelyek több zónából állnak. A könyv írásakor a GCP összesen 73 zónát használva 24 régióban működik. A fizikai és virtuális GCP-erőforrások lehetnek globális, regionális vagy zónaszintű típusúak. A globális hatókörű erőforrások, vagyis amelyek mindenhol elérhetők, közé tartoznak az előre konfigurált lemezképek, lemezpillanatképek és hálózatok. A regionális erőforrások, például a Central US, Western Europe vagy East Asia, jellemzően a statikus külső IP-címeket foglalják magukban. Az erőforrások többsége zónaszintű hatókörű, például a virtuálisgép-példányok és a lemezek. A zónák egy-egy önálló hibadomént jelentenek. A zónaszintű felépítésnek több előnye is van. Egyrészt helyben tartja az adott alkalmazás erőforrásait, így a szükséges erőforrások gyorsabban érhetők el, ha ugyanabban a zónában vannak; az alacsony hálózati késleltetés tipikusan 1 ms alatti oda-vissza idő. Másrészt elszigeteli az erőforrásokat másoktól, ami növeli a biztonságot. További zónák használata és az alkalmazások replikálása redundanciát biztosíthat, ami javítja a szolgáltatás megbízhatóságát, rendelkezésre állását, teljesítményét, valamint a katasztrófa utáni helyreállíthatóságát. A zónaszintű rendszer és a hozzá tartozó erőforrások szemléltetése az 5-2. ábrán látható.

A GCP több mint 100 terméket tartalmaz; ezek egy kis részét az 5-3. ábra mutatja be. A termékek között IaaS-, PaaS- és SaaS-szolgáltatások, valamint Container és Function as a Service megoldások, továbbá fejlesztői, biztonsági és menedzsmenttermékek is megtalálhatók. A fejezet további részében áttekintjük a különböző szolgáltatáskategóriák legfontosabb termékeit. Ezt az áttekintést követően néhány kiválasztott szolgáltatást részletesebben is megvizsgálunk, különös tekintettel arra, hogyan programozhatók és hogyan integrálhatók felhőalkalmazásokba.

*5-2. ábra. A globális, regionális és zónaszintű erőforrásfogalom szemléltetése*

*5-3. ábra. A Google Cloud Platform elérhető termékeinek reprezentatív részhalmaza*

### 5.1 GCP-szolgáltatások az IaaS-rétegben

Az infrastruktúraszolgáltatások közé a számítási, tárolási és hálózati komponensek tartoznak. Az IaaS-réteg alapvető szolgáltatása a Compute Engine, amely egy adott hardver- és operációsrendszer-platformon futó virtuális gép (VM) példányát jelenti. Ahogy más felhőszolgáltatóknál is, a GCP mögöttes hardverei rendeltetésük szerint csoportokba vannak rendezve. A GCP esetében ezek a csoportok a General Purpose (E2, N1, N2, N2D), Compute (C2), Memory (M2) és Accelerator (A2) optimalizált gépeket jelentik. A General Purpose gépek webkiszolgáló- és adatbázis-alkalmazásokhoz készültek. Jó ár-teljesítmény arányt biztosítanak. Nagy teljesítményű és játékalkalmazásokhoz, valamint mérnöki tervezési feladatokhoz a Compute optimized gépek ajánlottak. A Memory optimized gépek nagy memóriakapacitást kínálnak, ezért ideálisak adatelemző alkalmazásokhoz és memóriában működő adatbázisokhoz. Ha mesterségesintelligencia-alkalmazásokat szeretnénk futtatni, amelyek GPU-kat igényelnek, vagy tömegesen párhuzamos HPC-feladatokat valósítunk meg, akkor a gyorsítóra optimalizált gépek használhatók, amelyek különféle NVIDIA GPU-típusokat kínálnak.

A virtuális CPU-k magjainak száma 1 és 96 mag között változhat. A memória mérete VM-enként akár 1,4 TB-ig is növelhető. A VM konfigurációja természetesen befolyásolja az árat. A GCP Compute Engine példányok másodperc alapú díjazással, rögzített díjszabás szerint kerülnek elszámolásra a beállított magok száma és RAM-méret alapján. Az ár csökkentésére több lehetőség is van. A GCP automatikus `sustained use discount` kedvezményt alkalmaz. Ha a GCP azt érzékeli, hogy az alkalmazásunk egy adott hónapban hosszabb ideig fut, automatikusan kedvezményt ad. Ha az alkalmazásunk használati mintázata egyenletes és előre jelezhető, `committed use discount` is igénybe vehető. Ez akár 50%-os kedvezményt is eredményezhet. Végül, ha a programunk megszakítható VM-en is futtatható, a `pre-emptible` VM-ek jó választást jelentenek, akár 80%-os kedvezménnyel.

A GCP Compute Engine további érdekes funkciókat is kínál. Szükség esetén a VM-ek `sole-tenant node`-okon is futtathatók, ami azt jelenti, hogy egy fizikai szervercsomópont kizárólag a mi Compute Engine példányainkat futtatja. A csomópontot nem osztják meg más felhasználók VM-példányaival. Ez megfelel annak, mintha az irodánkban lenne egy dedikált gép, amely az alkalmazásainkat futtatja, csak éppen a felhőben található. A biztonsági garancia egy másik formája a `Confidential VMs` használatának lehetősége. Ezek a VM-ek a bizalmas számítástechnika (`Confidential Computing`) technológiáját használják, amely lehetővé teszi a felhasználói adatok titkosítását a számítás során. A hagyományos felhős végrehajtás az adatok tárolás közbeni titkosítására (`encryption at rest`) és átvitel közbeni titkosítására (`encryption in transit`) épül, de amikor az adat betöltődik a memóriába és feldolgozásra kerül, visszafejtik. A `Confidential Computing` segítségével ma már lehetséges a számításokat közvetlenül a CPU-chipen belül elvégezni az adatok visszafejtése nélkül. Az élő migráció (`Live migration`) funkció használatával a GCP garantálni tudja, hogy a VM-ünk rendszerkarbantartási időszakok alatt is működőképes marad. A 24/7 működés nem jelenti azt, hogy egy szerver megszakítás nélkül fut. Időről időre a szervereket le kell állítani, például rendszerfrissítések vagy hardverkomponens-csere miatt. Az élő migráció lehetővé teszi, hogy a VM-eket a felhasználó beavatkozása nélkül áthelyezzék ugyanazon felhőzóna egy másik csomópontjára.

Az infrastruktúraréteg következő kulcsszolgáltatása az adattárolás. A GCP-ben ezt a szolgáltatást egyszerűen Cloud Storage néven találjuk. A Cloud Storage objektumtárolást biztosít adatok számára. A tárhely mérete gyakorlatilag korlátlan. A Cloud Storage világszerte alacsony késleltetéssel érhető el, és nagy tartósságot biztosít (éves tartósság: 99.999999999%). Ha szükséges, geo-redundáns működés is választható. Ebben az esetben az adatok `multi-region` vagy `dual-region` módon kerülnek tárolásra. A Cloud Storage rendeltetésszerű használata alapján több tárolási osztály is elérhető:

- A Standard Storage a legjobb választás gyakran elért adatokhoz, például weboldalakhoz, streaming videókhoz és mobilalkalmazásokhoz.
- A Nearline Storage alacsony költségű megoldás olyan adatokhoz, amelyek legalább 30 napig hozzáférés nélkül tárolhatók, például biztonsági mentésekhez és ritkán elért multimédiás tartalmakhoz.
- A Coldline Storage nagyon alacsony költségű tárolási lehetőség, ha az adat legalább 90 napig visszaolvasás nélkül tárolható. Ez az osztály ideális katasztrófa utáni helyreállításhoz.
- Az Archive Storage kizárólag hosszú távú adattárolásra szolgál. Ez a legolcsóbb tárolási osztály, de megköveteli, hogy az adatot legalább 365 napig tárolják az olvasási műveletek között. Ez a tárolóosztály különösen alkalmas hosszú távú, például szabályozási célú archiválásra.

A GCP hálózati szolgáltatásai lefedik ugyanazokat a funkciókat, amelyeket korábban az Amazon AWS fejezetben tárgyaltunk. A Cloud Interconnect bármilyen infrastruktúrát képes a Google Cloudhoz kapcsolni. A Cloud VPN virtuális magánhálózatok létrehozására szolgál, a Virtual Private Cloud pedig regionális vagy globális felhőrendszerek kialakítását teszi lehetővé. A Cloud Load Balancing szolgáltatás segít a szolgáltatáskérések elosztásában a felhőerőforrások között, a Cloud Armor pedig megvédi ezeket a szolgáltatásokat a külső DoS- és webes támadásokkal szemben.

*5-4. ábra. A Google Cloud Platform világméretű hálózati kapcsolatai*

### 5.2 PaaS-rétegbeli szolgáltatások

A skálázható felhőalkalmazások telepítésének és futtatásának egyszerűsítésére, a felhőinfrastruktúra konfigurálásának és kezelésének bonyolultsága nélkül, a Google Cloud Platform más felhőszolgáltatókhoz hasonlóan szintén kínál egy platform mint szolgáltatás terméket, a GCP App Engine-t. Az App Engine biztosítja az erőforrások kezelésének jelentős részét, például az automatikus skálázódást, a biztonsági frissítéseket és a részletes menedzsmentet is, beleértve az alkalmazás telepítését, indítását, valamint az alkalmazás és az erőforrások monitorozását.

Az App Engine támogatja az alábbi nyelveken és platformokon írt alkalmazások futtatását: Go, Java, .NET, Node.js, PHP, Python vagy Ruby. Emellett egyéni futtatókörnyezetek is használhatók, így más nyelveken írt programok is támogatást kaphatnak.

Az App Engine automatikusan kapcsolódik olyan tárolási termékekhez, mint a Cloud Storage, a Cloud SQL, a Firestore, a MongoDB, valamint a helyben futó, harmadik fél által üzemeltetett adatbázisokhoz vagy külső szolgáltatói megoldásokhoz.

### 5.3 SaaS-rétegbeli szolgáltatások

A Google világszerte ismert innovatív alkalmazásairól és szolgáltatásairól. A Gmail, a Google Calendar, a Google Docs és a Google Maps kiváló példák erre. Ezek az alkalmazások önmagukban is felhőalkalmazások, vagyis szoftverszolgáltatások (`Software as a Service`, `SaaS`), de a Google Cloudban ennél jóval több olyan szoftverszolgáltatás és komponens érhető el, amelyek nagyobb alkalmazások építőelemeiként használhatók, például gépi látási, médiakezelési, gépi fordítási és adatelemzési komponensek. Ezek közül néhánnyal később ebben a könyvben még találkozunk, és használni is fogjuk őket.

## 6. A Google Cloud Platform használata

### 6.1 A GCP-projekt

A Google Cloud Platform használatához a felhasználóknak először GCP-fiókot kell létrehozniuk, majd egy GCP-projektet kell létrehozniuk.

A GCP-projekt a GCP-használat alapvető egysége, mivel egy adott alkalmazáshoz csoportosítja az erőforrásokat, és ez képezi a számlázás alapját is.

Minden projektnek rendelkeznie kell `i)` névvel, `ii)` azonosítóval és `iii)` egy egyedi projektszámmal. A projekt létrehozható a GCP konzolon keresztül (`https://console.cloud.google.com/`), amely a GCP webalapú felülete.

A kezdőlapot a 6-1. ábra mutatja. A Cloud Console egyszerű és intuitív webes felületet biztosít a GCP-hez, lehetővé téve a projektek és erőforrások kezelését, a monitorozást, a konfigurálást, valamint közvetlen hozzáférést adva az egyes GCP-szolgáltatásokhoz és a kiterjedt dokumentációhoz.

*6-1. ábra. A Google Cloud Platform Console*

### 6.2 A GCP-erőforrások elérésének módjai

A felhőkonzol, amelyet korábban már bemutattunk, nem az egyetlen módja a GCP-erőforrások elérésének. Többféle alternatív lehetőség is van a GCP és szolgáltatásai elérésére. Ezek egyike a `gcloud` parancssori felület, amely különösen hasznos a tapasztalt felhőadminisztrátorok számára. A `gcloud` különféle parancsokat kínál, hierarchikus rendszerbe rendezve, amelyekkel a különböző GCP-szolgáltatások érhetők el és kezelhetők. A Google Cloud SDK része, amelyet a `gcloud` használata előtt telepíteni kell. Az alábbi két egyszerű példa bemutatja a használatát. További példák később, az egyes szolgáltatások tárgyalásánál szerepelnek majd.

Az első példa felsorolja a GCP `us-central1-a` zónájában létrehozott összes Compute Engine-példányt:

```bash
gcloud compute instances list --filter="zone:us-central1-a"
```

A parancs első kulcsszava, a `compute`, azt jelzi, hogy a parancsot a Compute Engine szolgáltatásnak küldjük. A következő két kulcsszó azt adja meg, hogy a szűrőfeltételben megadott zónában elérhető példányokat szeretnénk kilistázni.

A következő parancs az összes, egy felhasználóhoz tartozó projektet táblázatos formában sorolja fel, beleértve a projekt létrehozásának dátumát és időpontját is, helyi időzóna szerint megadva:

```bash
gcloud projects list \
--format="table(name, project_id, createTime.date(tz=LOCAL))"
```

Itt is az első kulcsszó jelzi, hogy a parancs a `projects` szolgáltatásnak lesz elküldve, a második pedig azt adja meg, hogy a projektek listázása a cél.

Hasonló parancssori felület a GCP Console kezdőlapján is elérhető. Miután a Konzol jobb felső sarkában a `>_` ikonra kattintunk, a Google Cloud Shell ablaka a lap alján aktiválódik (lásd a 6-2. ábrát), és innen `gcloud` parancsok adhatók ki az erőforrásokra. A Cloud Shell a háttérben létrehoz egy ideiglenes Compute Engine virtuálisgép-példányt, amely végrehajtja a parancsokat. A VM 5 GB perzisztens lemezterülettel, előre telepített Google Cloud SDK-val, valamint beépített kódszerkesztő formájában Java, Go, Python, Node.js, PHP, Ruby és .NET támogatással érkezik. Emellett beépített jogosultságkezelést is biztosít a GCP Console projektjeihez és erőforrásaihoz való hozzáféréshez.

*6-2. ábra. A Google Cloud Shell használata a GCP Console-ból*

A szolgáltatások elérésének és vezérlésének egy további formája a rendszerszintű, szolgáltatásszintű vagy alkalmazásszintű programokból történő programozott hozzáférés. A Google Cloud Platformon ezt a szoftveres hozzáférést a Cloud Client Libraries biztosítják, amelyek SDK formájában nyújtanak API-t a szoftverfejlesztők számára. A Client Libraries a következő programozási nyelveken érhetők el: `C#`, `C++`, `Java`, `Node.js`, `Go`, `Python`, `Ruby` és `PHP`.

### 6.3 A Compute Engine használata

Ebben a szakaszban bemutatjuk, hogyan lehet programból listázni, elindítani és leállítani a Compute Engine-példányokat a Java Client Library használatával. Csak a kódrészletek szerepelnek; a teljes mintaprogram itt érhető el: `https://github.com/alfonsof/google-cloud-javaexamples/tree/master/gcloudcomputeengine/src/main/java/example`

#### Példányok listázása

```java
Page<Instance> instancePage;
// Instantiate a client
Compute compute = ComputeOptions.getDefaultInstance().getService();
System.out.println("Listing VM instances ...");
// List instances
instancePage = compute.listInstances();
System.out.printf("Instances:\n");
Iterator<Instance> iterator = instancePage.iterateAll();
while (iterator.hasNext()) {
Instance instance = iterator.next();
System.out.printf("Instance: %s\n", instance.getInstanceId().getInstance());
System.out.printf("Data instance:\n%s\n\n", instance);
}
```

#### Példány indítása

```java
// Instantiate a client
Compute compute = ComputeOptions.getDefaultInstance().getService();
System.out.println("Starting VM instance ...");
// Start instance
Operation operation = compute.start(instanceId);
if (operation == null) {
System.out.printf("Error: Instance \"%s\" does NOT exist.\n", instanceId);
return;
}
// Wait for operation to complete
try {
operation = operation.waitFor();
} catch (InterruptedException e) {
e.printStackTrace();
} catch (TimeoutException e) {
e.printStackTrace();
}
```

#### Példány leállítása

```java
// Instantiate a client
Compute compute = ComputeOptions.getDefaultInstance().getService();
System.out.println("Starting VM instance ...");
// Stop instance
Operation operation = compute.stop(instanceId);
if (operation == null) {
System.out.printf("Error: Instance \"%s\" does NOT exist.\n", instanceId);
return;
}
// Wait for operation to complete
try {
operation = operation.waitFor();
} catch (InterruptedException e) {
e.printStackTrace();
} catch (TimeoutException e) {
e.printStackTrace();
}
```

### 6.4 A Cloud Storage használata

Ezzel a néhány kódrészlettel zárjuk a Google Cloud Platform használatáról szóló fejezetet, amelyek a Cloud Storage szolgáltatás programozott elérését és vezérlését szemléltetik. Először létrehozunk egy új bucketet, majd kilistázzuk az összes elérhető bucketet a Storage-ban.

#### Bucket létrehozása

```java
import com.google.cloud.storage.Bucket;
import com.google.cloud.storage.BucketInfo;
import com.google.cloud.storage.Storage;
import com.google.cloud.storage.StorageClass;
import com.google.cloud.storage.StorageOptions;
public class CreateBucketWithStorageClassAndLocation {
public static void createBucketWithStorageClassAndLocation(
String projectId, String bucketName) {
// The ID of your GCP project
// String projectId = "your-project-id";
// The ID to give your GCS bucket
// String bucketName = "your-unique-bucket-name";
Storage storage = StorageOptions.newBuilder().setProjectId(projectId)
.build().getService();
// See the StorageClass documentation for other valid storage classes:
// https://googleapis.dev/java/google-cloudclients/latest/com/google/cloud/storage/StorageClass.html
StorageClass storageClass = StorageClass.COLDLINE;
// See this documentation for other valid locations:
// http://g.co/cloud/storage/docs/bucket-locations#location-mr
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

#### Bucketek listázása

```java
import com.google.api.gax.paging.Page;
import com.google.cloud.storage.Bucket;
import com.google.cloud.storage.Storage;
import com.google.cloud.storage.StorageOptions;
public class ListBuckets {
public static void listBuckets(String projectId) {
// The ID of your GCP project
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
