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

## 7. Nagyléptékű feladatvégrehajtás a felhőben

Ahogy korábban tárgyaltuk, a felhő a szervezetek skálázható és nagyléptékű feldolgozási igényeire adott megoldásként jelent meg. A központi kérdés az, hogy miként lehet nagyléptékű feldolgozást végezni a felhőben. Egyetlen virtuálisgép-példány létrehozása és elindítása egyszerűen megoldható, de hogyan kezelhető több száz vagy akár több ezer ilyen példány? Ráadásul magukat a számítási feladatokat is menedzselni kell. A feladatokat hozzá kell rendelni a VM-példányokhoz, el kell indítani őket, figyelni kell a hibákat, és meghibásodás esetén újra kell indítani őket. A szükséges számítási infrastruktúra létrehozásának és nagyszámú feladat végrehajtásának teljes folyamata könnyen ijesztően bonyolulttá válhat. Nem meglepő, hogy különféle szoftveres keretrendszerek jöttek létre e folyamat egyszerűsítésére.

### 7.1 A Big Data megjelenése

A nagy számítási kapacitású rendszereket kezdetben nagyméretű számítási igényű, tudományos és mérnöki problémák megoldására használták. Az elmúlt évtizedben azonban globális társadalmunk teljes digitális átalakulásának lehettünk tanúi. Az analóg adattárolás korszaka, mint a papíralapú dokumentumok, a mágneses hang- és videoszalagok vagy a bakelitlemezek világa, lezárult. A digitális adatok előállítása és tárolása ma már általános. Óriási mennyiségű vállalati és nyilvános adat keletkezik folyamatosan. A dokumentumok digitális formátumban jönnek létre és így is tároljuk őket. A gyártástól a közigazgatásig mindenféle adat percenként vár feldolgozásra.

A digitális adatforradalom egyik kulcsjellemzője, hogy az adatok jellemzően nyers formában keletkeznek és tárolódnak. Az adathalmazból az információt csak számítógépes adatfeldolgozás révén tudjuk kinyerni; az információ be van ágyazva az adatokba. A feldolgozás az egyszerű lekérdezéstől, mint az adatbázisrendszerek esetében, a bonyolult jellemzőkinyerésig és adatelemzésig terjedhet, beleértve a mesterséges intelligencia által támogatott megközelítéseket is, amelyek új mintázatok és trendek feltárására szolgálnak.

Ezt az új, nagyléptékű adatfeldolgozási technológiát Big Data-nak és Big Data-feldolgozásnak nevezzük. Pontosabban akkor beszélünk Big Data rendszerről, ha:

- az adathalmazok elég nagyok ahhoz, hogy a tipikus rendszerek már ne tudják kezelni őket, és
- új feldolgozási módszerekre van szükség ahhoz, hogy ekkora adatmennyiséget megfelelő időn belül lehessen feldolgozni.

A Big Data rendszereket gyakran a három V modellje is jellemzi, amely három kulcsszóra épül: volume, velocity és variety, azaz:

- `Volume`: az adatmennyiség nagyságrendekkel nagyobb, mint a hagyományos rendszerekben.
- `Velocity`: az információ áramlásának sebessége jelentősen nagyobb, mint a hagyományos rendszerekben.
- `Variety`: az adatok sokféle forrásból származnak, minőségük és típusuk változatos.

A Big Data rendszerek természetes következménye a nagyléptékű számítási platformok iránti igény. Ez a korábban tárgyalt adatmennyiség-robbanás miatt azt jelenti, hogy ezek a platformok döntően adatfeldolgozási, adatátalakítási és adatelemzési feladatokat fognak végezni. Úgy tűnik, hogy a nagyméretű rendszerek már nem kizárólag a numerikus szimulációkat futtató tudósok „játékszerei”.

Fontos azt is megjegyezni, hogy az adatfeldolgozás sok tekintetben eltér a hagyományos nagy teljesítményű számítástechnikától. A HPC-ben a legtöbb alkalmazás egyedi, konkrét algoritmusokra épül, amelyeket egy adott tudományos számítási probléma gyors megoldására optimalizáltak. A Big Data-feldolgozás ettől eltér, mert itt a feldolgozás viszonylag szabványos lépéssorozatot követ. Ezt nevezzük a Big Data-feldolgozás életciklusának:

`1. szakasz`
Adatok beolvasása / begyűjtése: ez a szakasz magában foglalja az adatok kinyerését, rendezését, címkézését és átalakítását.

`2. szakasz`
Az adatok tartós tárolása: ehhez elosztott fájlrendszerre vagy adatbázisra van szükség.

`3. szakasz`
Feldolgozás és elemzés: kötegelt vagy valós idejű feldolgozás, beleértve a lekérdezésfeldolgozást, valamint a statisztikai és adatelemző algoritmusokat.

`4. szakasz`
Az eredmények vizualizálása: trendek és változások feltárása, következtetések levonása.

### 7.2 Adatfeldolgozó szoftveres keretrendszerek

Korábban a nagyléptékű adatfeldolgozó alkalmazásokat nagy számítási klasztereken futtatták. A felhő megjelenésével sok ilyen rendszer a felhőbe költözött, adatfeldolgozó keretrendszerek formájában, amelyek leegyszerűsítik az ilyen alkalmazások összetett végrehajtási és erőforrás-kezelési lépéseit. Ebben a részben áttekintjük és összehasonlítjuk a legismertebb felhőalapú adatfeldolgozó keretrendszereket funkcionalitásuk, képességeik és hatékonyságuk alapján. A következő szoftvercsomagokat érintjük: Apache Hadoop, Apache Spark, Storm, Kafka, Flink, Beam. Elsősorban a nyílt forráskódú keretrendszerekre összpontosítunk, mert a felhőben a gyártóhoz való kötődés különösen veszélyes. Ha egy felhasználó olyan szolgáltatásra vagy szoftveres keretrendszerre támaszkodik, amely csak egy adott felhőben érhető el vagy futtatható, akkor a későbbi szolgáltatóváltás lehetősége gyakorlatilag megszűnik.

A keretrendszerek áttekintése előtt azonban egy alapvető, adatfeldolgozáshoz kapcsolódó fogalmat is tárgyalnunk kell, nevezetesen a kötegelt és az adatfolyam-orientált feldolgozási megközelítést, mert ez kulcsfontosságú lesz a keretrendszerek közötti különbségek megértéséhez.

#### 7.2.1 Kötegelt és adatfolyam-feldolgozás

Az adatok feldolgozásának hagyományos módja a következő. A bemeneti adatok több bemeneti fájlban vagy egy adatbázisrendszerben vannak tárolva. Elindítunk egy programot, amely feldolgozza a bemeneti adatokat és eredményt állít elő. A program beolvassa a teljes adathalmazt a memóriába, elvégzi a szükséges számítást, majd amikor az eredmények elkészültek, kimeneti fájlokba menti őket vagy eltárolja egy adatbázisban. Ennek a végrehajtási modellnek a kulcsjellemzői, hogy a bemeneti adatok végesek, statikusak és tartósan tároltak; a program hozzáfér az összes adatrekordhoz, és a végrehajtás szakaszos, vagyis adatbevitel -> adatfeldolgozás -> adatkimenet. Ezt a végrehajtási stílust kötegelt feldolgozásnak nevezzük.

Vannak helyzetek, amikor a kötegelt végrehajtási modell nem alkalmazható vagy nem praktikus. Sok modern alkalmazásban az adatok valós időben keletkeznek. Ilyenek például az élő médiatartalmak, mint a videó, hang, szöveg és üzenetküldés, az IoT-rendszerek, mint a forgalmi adatok az autonóm járművek vagy a dugók esetén, valamint a gyártási folyamat- és szerelési adatok és naplók, továbbá a fizikai és társadalmi hálózatok élő adatai, különféle naplói és biztonsági adatai. Ezekben az alkalmazásokban nem lehet megvárni, hogy a teljes bemeneti adathalmaz rendelkezésre álljon. Egy folyamatos, valós idejű adatfolyam soha nem ér véget. Az alternatíva az, hogy az adat kis részeit vagy rekordjait azonnal feldolgozzuk, amint elérhetővé válnak. Amellett, hogy így egyáltalán lehetővé válik a feldolgozás, további előnyök is jelentkeznek. Mivel egyszerre csak az adathalmaz kis része van a memóriában, az erőforrásigény alacsonyabb. Ha rekordonként dolgozzuk fel az adatokat, javul a rendszer reakciókészsége és csökken a késleltetés. Következésképpen ez a feldolgozási mód, amelyet adatfolyam-orientált feldolgozásnak vagy egyszerűen adatfolyam-feldolgozásnak nevezünk, kedvező a teljesítmény és a rendszerkihasználtság javítása szempontjából, és akkor is alkalmazható, amikor a teljes adatmennyiség egyébként rendelkezésre állna.

#### 7.2.2 Apache Hadoop/MapReduce

A Hadoop/MapReduce keretrendszer egy Apache nyílt forráskódú projekt [14], amelyet a MapReduce programozási modellen alapuló, nagyléptékű kötegelt adatfeldolgozó alkalmazások végrehajtásának támogatására hoztak létre. Az alapul szolgáló infrastruktúra olcsó, általános célú szerverek nagy klasztere. Erre épül rá a Hadoop, egy Java nyelven írt szoftverrendszer, amely hibatűrő és platformfüggetlen végrehajtási környezetet biztosít. A rendszer fő komponensei a következők:

- `HDFS`: a Hadoop Distributed File System
- `YARN`: klaszterkoordinátor és ütemező
- `MapReduce`: a kötegelt feldolgozó motor
- `Hadoop common`: közös segédprogramok gyűjteménye

A Hadoop/MapReduce filozófiája az, hogy a nagy adatfeldolgozási feladatokat párhuzamosan hajtjuk végre. A bemeneti adatokat kisebb részekre osztjuk, amelyeket különböző szerverekhez rendelünk egyidejű feldolgozásra, ez a `Map` fázis, majd a részleges eredményeket összegyűjtjük, hogy előálljon a végső eredmény, ez a `Reduce` fázis. A bemeneti adatok egy nagy, hibatűrő, elosztott fájlrendszerben vannak tárolva. A Hadoop abból a feltételezésből indul ki, hogy elosztott rendszerben a meghibásodás nem kivétel, hanem megszokott jelenség. Ha több ezer szervert használunk, mindig lesz köztük olyan, amelyik éppen nem működik, ezért a hibatűrésnek a futtatórendszer alapvető tulajdonságának kell lennie. A Hadoop alkalmazásszintű hibatűrési támogatást nyújt.

A rendszer számítási és tároló csomópontokból áll; ezek jellemzően ugyanazok a gépek, ami lehetővé teszi a feladatok végrehajtását felesleges extra adatmozgatás nélkül. A feladatokat a kliensek küldik be a rendszerbe, ezután a Hadoop végrehajtási környezete átveszi az ütemezést és a menedzsmentet. A végrehajtást a YARN motor vezérli, amely egyetlen mester `ResourceManager` komponensből, klasztercsomópontonként egy `NodeManager` munkafolyamatból és alkalmazásonként egy `MRAppMaster` komponensből áll. A feladatot, vagyis a JAR fájlt vagy futtatható állományt, a `ResourceManager` fogadja, ez ütemezi az alfeladatokat a csomópontokra, és a `NodeManager` komponensektől kapott információk alapján figyelést és visszajelzést biztosít a kliensek számára.

Egy MapReduce alkalmazás egyszerű szerkezetű, és interfészekkel megadott programozási modell szerint építhető fel. A végrehajtási modell a következő:

1. az adathalmaz beolvasása a fájlrendszerből
2. az adatok részekre bontása, kulcs-érték párokra
3. a számítás alkalmazása az egyes részhalmazokra különböző csomópontokon: `Map` folyamat
4. az egyes kulcsokhoz tartozó értékek összesítése: `Reduce` folyamat
5. az eredmény visszaírása a fájlrendszerbe

Általánosságban egy MapReduce program a végrehajtás különböző szakaszaiban kulcs-érték párok sorozatát állítja elő, az alábbi módon:

`(input) <k1,v1> -> map -> <k2,v2> -> combine -> <k2,v2> -> reduce -> <k3,v3> (output)`

`K1`, `K2`, `K3` és `V1`, `V2`, `V3` különböző kulcs- és értékosztályokat jelölnek, amelyeknek a végrehajtáshoz mind szerializálhatónak kell lenniük. A program futása több fázisból áll:

- `Input` fázis: a bemeneti fázis beolvassa és értelmezi a bemeneti adatokat, majd kulcs-érték párok formájában továbbítja azokat a `Mapper` számára.
- `Map` fázis: a felhasználó által definiált feldolgozás egy olyan függvényben valósul meg, amely a bejövő kulcs-érték párokat feldolgozza, és új kimeneti kulcs-érték párokat hoz létre. A köztes kulcsok és értékek szolgálnak arra, hogy a `Mapper` eredményei a következő fázisba kerüljenek.
- `Combiner` fázis: opcionális lépés, amely lokális összesítést végez egyetlen csomóponton, a `Mapper` folyamat eredményein.
- `Shuffle and Sort` fázis: ez a `Reducer` folyamat induló lépése. A `Reducer` a bemeneti kulcs-érték párokat a kulcsok szerint rendezi, hogy az összesítés hatékonyabb legyen.
- `Reducer` fázis: ebben a fázisban hajtódik végre a felhasználó által definiált összesítő függvény, amely aggregálja, szűri vagy kombinálja a `Map` folyamatok által előállított adatokat. A `Reducer` nulla vagy több kulcs-érték párt adhat vissza a program eredményeként.
- `Output` fázis: a program utolsó szakasza, amely a végeredményül kapott kulcs-érték párokat a kívánt formátumban a fájlrendszerbe menti.

A végrehajtás könnyebb megértéséhez egy egyszerű programot használunk szemléltetésként. A példa egy egyszerű `Word Count` alkalmazás, amely megszámolja az egyes szavak előfordulásainak számát egy adott bemeneti adathalmazban. A végrehajtás fázisai a 7-4. ábrán láthatók. A példa két osztályt használ a szükséges funkcionalitás megvalósítására. A `TokenizerMapper` osztály implementálja a `Mapper` interfészt, a bemeneti fájlt szavakra bontja, és eredményként `<word, 1>` párokat bocsát ki. Az `IntSumReducer` osztály implementálja a `Reducer` interfészt, és kiszámítja egy adott szöveges kulcshoz tartozó értékek összegét. Ezt az osztályt lokális, azaz csomópontszintű és globális, vagyis rendszerszintű `Reducer` szerepben is használjuk. A program `main` metódusa konfigurálja a futást: először létrehozzuk a job konfigurációját, beállítjuk a futtatható JAR fájlt, megadjuk a mapper, combiner és reducer osztályokat, végül pedig a kimeneti kulcs- és értékosztályokat, valamint a bemeneti és kimeneti útvonalakat. A program a `waitForCompletion()` metódus meghívásakor indul el.

`WordCount` példa:

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

#### 7.2.3 Apache Spark

A Hadoop/MapReduce keretrendszer széles körben használt rendszer rendkívül nagy adathalmazok feldolgozására. Van azonban egy alapvető korlátja: a köztes adatok továbbítására a fájlrendszert használja. Ez komoly teljesítménybeli szűk keresztmetszet, mivel a fájlrendszer sávszélessége több nagyságrenddel kisebb, mint a memória sávszélessége. Ha egy rendszert nagy adathalmazok feldolgozására használunk, ez akár kizáró problémává is válhat. E hiányosság felismerésével 2009-ben elindult egy mellékprojekt, amely a MapReduce memóriában működő változatát kívánta létrehozni. Néhány évvel később ez önálló Apache projektté vált Spark néven [15].

A Spark egy nagyon gyors alternatív keretrendszer, amely MapReduce jellegű programokat hajt végre. Memóriabeli műveletek használatakor akár százszor gyorsabb is lehet, mint egy Hadoop/MapReduce program. Ha lemezeket használ, még akkor is akár tízszer gyorsabb lehet a szükséges I/O műveletek alacsonyabb száma miatt. A sebességen túl a Sparknak más előnyei is vannak. Több programozási nyelvhez kínál API-kat, és a `Map` és `Reduce` lépéseknél gazdagabb funkcionalitást nyújt: támogatja az SQL-lekérdezéseket, a gépi tanulást, a gráfanalitikai műveleteket, valamint az adatfolyam-feldolgozást is.

A Spark saját beépített klaszterkezelő rendszerrel rendelkezik, ami azt jelenti, hogy más klaszter-végrehajtási környezet segítsége nélkül is futtatható. Szükség esetén azonban képes külső klaszterfuttató környezeteket is használni. A Spark végrehajtási módjai a következők:

- `Standalone mode`: a Spark önálló, klaszteralapú környezetként fut.
- `Hadoop mode`: a Spark a Hadoop YARN klaszterkezelő rendszer tetején fut.
- `Spark in MapReduce mode`: a Spark feladatok Hadoop/MapReduce feladatokként hajtódnak végre. Ez a mód segíti a régebbi MapReduce programok integrálását a Sparkkal.

A Spark napjainkra vezető adatfeldolgozó és adatelemző keretrendszerré vált. Gazdag funkcionalitása és nagy teljesítménye számos alkalmazási területen sikeressé tette. A Spark réteges architektúrája, valamint a különféle alkalmazásprogramozási technológiák, futtatási környezetek és adatforrások támogatása jól szemlélteti ezt.

Ahogy korábban, most is bemutatjuk a `Word Count` példát, de ezúttal Spark Java megvalósításban. A kód a program kulcslépéseit szemlélteti. Először létrejön egy Spark-munkamenet, amelyet a bemenet elérésére és a program leállítására használunk. A bemenetet a Spark belső adatábrázolási szerkezetére, az `RDD`, azaz `Resilient Distributed Dataset` formára alakítjuk. Ez az elosztott adatszerkezet lehetővé teszi, hogy a Spark nagy hatékonysággal hajtson végre műveleteket párhuzamosan különböző csomópontokon. A MapReduce esetén a különböző számítási szakaszok között a párok a fájlrendszerben, lemezen tárolódnak. Ezzel szemben a Spark a köztes tárolásra az elosztott memóriát, vagyis az `RDD`-t használja. A fájlrendszert csak a program elején és végén éri el.

Miután a program előállította a szavak listáját, létrejönnek a kulcs-érték párok, amelyek a `ones` adatszerkezetben tárolódnak a `map` lépés eredményeként. A következő sor végrehajtja az összesítést a `ones` adatszerkezeten, és ennek eredményeként jön létre a `counts`. Végül a `counts` egy `List` típussá alakul, és az eredmények kiírásra kerülnek a konzolra.

`WordCount` Spark példa:

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

#### 7.3 MapReduce és Spark feladatok végrehajtása GCP-n

Ebben a részben azt vizsgáljuk meg, hogyan hajthatók végre MapReduce és Spark feladatok a Google Cloud Platformon. A GCP natív Hadoop- és Spark-feladatvégrehajtást támogat a GCP Dataproc szolgáltatás segítségével. A Dataproc egy menedzselt GCP-szolgáltatás, amely lehetővé teszi számítási klaszterek gyors létrehozását és adatfeldolgozási feladatok hatékony végrehajtását. Amellett, hogy MapReduce vagy Spark feladatokat képes futtatni, a Dataproc szorosan integrálódik más GCP-szolgáltatásokkal is, például a BigQuery, a Cloud Storage, a Cloud Bigtable, a Cloud Logging és a Cloud Monitoring szolgáltatásokkal, így teljes adatplatformot biztosít.

A Dataproc többféleképpen is elérhető: `i.` a REST API-n keresztül, `ii.` a Cloud SDK segítségével, `iii.` a Cloud Dataproc felhasználói felületén keresztül, illetve `iv.` a Cloud Client Libraries használatával.

A Google Cloud Platformon történő végrehajtás szemléltetésére a `WordCount` példaprogramot használjuk. Feltételezzük, hogy a minta MapReduce- és Spark-változata már le van fordítva, és JAR fájlokban rendelkezésre áll. A Dataproc működéséről további információ a következő címen található:

`https://cloud.google.com/dataproc/docs`

##### 7.3.1 MapReduce feladatok futtatása GCP-n

A példa hagyományos végrehajtási parancsa egy telepített és futó Hadoop klaszteren a következő lenne:

```bash
hadoop jar hadoop-mapreduce-example.jar WordCount /sample/input /sample/output
```

Mivel a Google Cloudot használjuk, némileg módosított parancssorra és további előkészítő lépésekre lesz szükség. A program GCP-n történő futtatása a következő lépésekből áll:

1. a Java mintaprogram lefordítása
2. egy Storage bucket létrehozása, majd a feldolgozandó fájl feltöltése
3. egy Google Cloud Dataproc klaszter létrehozása
4. a feladat beküldése végrehajtásra
5. az eredmény ellenőrzése

Az 1. lépést kihagyjuk, mert feltételezzük, hogy a program már le van fordítva. A program a Google Cloud Client Libraries könyvtárait fogja használni a szolgáltatások eléréséhez.

`Tárhely létrehozása és a bemeneti fájl feltöltése`

A példában a Google Cloud Storage szolgál adattárolási platformként. Hozzunk létre egy egyedi bucketet, például `word-count-bucket` néven:

```text
gs://test-bucket22/*
```

Ezután töltsük fel a bemeneti fájlt a Storage-ba. Hozzunk létre egy `words.txt` nevű bemeneti fájlt a következő tartalommal, majd töltsük fel a `test-bucket22` bucketbe:

```text
apple pear apple microsoft pear door window table chair chair
```

`A klaszter létrehozása és a program végrehajtása`

Ha az előző lépések elkészültek, létrehozhatunk egy Hadoop klasztert a Google Cloud Shellből:

```bash
gcloud dataproc clusters create hadoop-cluster --region europe-west4
```

A `create hadoop-cluster` opció a létrehozott klaszternek a `hadoop-cluster` nevet adja, és a Dataproc natív Hadoop klaszterként fogja használni. A klaszter indulásának gyorsnak kell lennie. Miután a klaszter elindult, a program a következő paranccsal futtatható:

```bash
gcloud dataproc jobs submit hadoop --cluster hadoop-cluster --jar \
gs://test-bucket22/WordCountMapReduce.jar -- wordcount.WordCount \
gs://test-bucket22/words.txt gs://test-bucket22/results
```

Az eredmények a megadottak szerint a `gs://test-bucket22/results` helyre kerülnek. A fájl tartalma a következő paranccsal listázható:

```bash
gsutil cat gs://test-bucket22/results/*
```

```text
microsoft      1
window         1
pear           2
chair          2
apple          2
door           1
table          1
```

##### 7.3.2 Spark feladatok futtatása GCP-n

Egy Spark feladat végrehajtása nem bonyolultabb az előző példánál. Ugyanúgy hozzuk létre a klasztert, vagy újrahasználjuk a már meglévőt, majd beküldünk egy Spark feladatot. A bemeneti és kimeneti fájlok ugyanazok maradnak. Ismét feltételezzük, hogy a Spark-példát tartalmazó program már le van fordítva és JAR fájlban rendelkezésre áll.

Ha az előző lépések elkészültek, létrehozhatunk egy Hadoop klasztert a Google Cloud Shellből:

```bash
gcloud dataproc clusters create spark-cluster --region europe-west4
```

Miután a klaszter elindult, a program a következő paranccsal hajtható végre:

```bash
gcloud dataproc jobs submit spark --cluster spark-cluster --jar \
gs://test-bucket22/WordCountSpark.jar -- wordcount.WordCount \
gs://test-bucket22/words.txt gs://test-bucket22/results
```

Az eredmények ugyanúgy a `gs://test-bucket22/results` helyen jelennek meg.

Mindkét esetben a végrehajtási naplók a Cloud Console Dataproc szolgáltatásán belül találhatók meg és tekinthetők meg. Ha Cloud Logging használatára is szükség van, a klaszter létrehozásakor a következő tulajdonságot kell beállítani:

```text
dataproc:dataproc.logging.stackdriver.enable=true
```

Ha engedélyezni akarjuk a YARN konténernaplók job-szintű erőforrásnaplózását, akkor a klaszter létrehozásakor a következő tulajdonság szükséges:

```text
dataproc:dataproc.logging.stackdriver.job.yarn.container.enable=true
```

A GCP monitorozási képességeket is biztosít. A program végrehajtása és a klaszter tulajdonságai a Dataproc felületén követhetők nyomon.

## 8. Adatfolyam-feldolgozás

Ahogy a 7.2.1 szakaszban tárgyaltuk, nem minden adatfeldolgozási feladat végezhető el kötegelt végrehajtási stílusban. A folyamatos adatfolyamok, például a valós idejű mérési vagy monitorozási adatok, nem kezelhetők a hagyományos bemenet-feldolgozás-kimenet paradigmával. Ezekben az esetekben az adatfolyam-feldolgozás és a stream algoritmusok jelentenek megoldást.

Amellett, hogy végrehajtási mechanizmust biztosít, az adatfolyam-feldolgozás javíthatja a rendszer teljesítményét is, csökkentheti a késleltetést, valamint mérsékelheti az erőforrás-felhasználást, mivel egy adott időpontban az adatoknak csak egy kisebb része van feldolgozás alatt.

Ebben a fejezetben röviden áttekintjük az adatfolyam-feldolgozás fő jellemzőit, majd bemutatjuk és összehasonlítjuk a legnépszerűbb stream adatfeldolgozó keretrendszereket. A fejezetet a Beam keretrendszer és annak Google Cloud Platformon történő használatának rövid ismertetésével zárjuk.

### 8.1 Stream algoritmusok

Az adatfolyam-feldolgozás legfontosabb jellemzője, amely megkülönbözteti a kötegelt feldolgozástól, a folyamatos, nem korlátos bejövő adatfolyam. Az algoritmusoknak képesnek kell lenniük az adatok feldolgozására úgy, hogy az adatelemek beérkezésük pillanatában kerülnek feldolgozásra, anélkül hogy a teljes, teljes egészében rendelkezésre álló bemeneti adathalmazhoz hozzáférnénk.

Ezt a különbséget jól megvilágítja egy egyszerű statisztikai számítási feladat. Tegyük fel, hogy `N` darab `xᵢ`, `i = 1, … , N` adatminta varianciáját kell kiszámítanunk. Ha hozzáférünk a teljes adathalmazhoz, vagyis az összes `N` elemhez a memóriában vagy egy bemeneti fájlban, az egyik megoldás egy kétlépéses algoritmus használata. Az első lépésben az átlagot számítjuk ki, a másodikban pedig a varianciát. A Java megvalósítás a következő:

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

Csábító lehet a két bejárás kiváltása úgy, hogy az implementációt egyetlen ciklusba vonjuk össze egy alternatív képlet segítségével. Ennek Java megvalósítása a következő:

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

Ennek a megoldásnak az a problémája, hogy a `sumOfSquares` és a `(sum * sum)/data.length` értékei nagyon hasonlóak lehetnek, így a különbségük olyan kicsi értéket eredményezhet, amelyet a lebegőpontos ábrázolás rendelkezésre álló pontossága már nem tud megfelelően kezelni. Ezt a problémát katasztrofális kioltásnak nevezzük [16], és hibás eredményekhez vezet. Ennek megfelelően ezt az algoritmust gyakorlatban nem szabad használni.

Olyan egylépéses algoritmust, amely helyes eredményt ad és nem szenved a katasztrofális kioltás problémájától, Welford mutatott be [17]. Ez egy egylépéses, más néven online algoritmus, amely az új minták beérkezésekor frissíti az átlagot és a varianciát. Az algoritmus jelentősége abban áll, hogy numerikusan stabil egylépéses módszert ad az átlag és a variancia kiszámítására, és úgy is használható, hogy a teljes adathalmaz nem ismert előre. Ismeretlen hosszúságú adatsorokra is alkalmazható. Egyben azt is jól szemlélteti, hogy a stream algoritmusok gyakran algoritmikai változtatásokat követelnek meg, és sokszor vissza kell nyúlni az alapvető matematikai levezetéshez ahhoz, hogy az adatfolyam-feldolgozásban is használható megoldást kapjunk.

Tegyük fel, hogy van egy termelő-fogyasztó rendszerünk, ahol a termelő adatelemek sorozatát állítja elő és továbbítja a fogyasztónak, amely az adatok átlagát és varianciáját számítja ki. A Welford-algoritmus használható ennek az adatfolyamnak a feldolgozására anélkül, hogy az adatelemeket memóriában kellene tárolni. Az alábbi Java-kód a fogyasztó implementációját mutatja. Feltételezzük továbbá, hogy a termelő és a fogyasztó egy `ArrayBlockingQueue` példányon keresztül kommunikál.

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
ex.printStacktrace();
}
}
}
}
```

Természetesen nem minden probléma írható le pusztán egyedi adatelemekkel. Ha egy alkalmazásnak például egy adott időszakra, mondjuk napi, heti vagy havi átlaghőmérsékletre vagy csapadékösszegre van szüksége, akkor a stream algoritmusok adatablakokon működnek. Ezek az ablakok lehetnek átfedők vagy nem átfedők. Ha az ablakok nem fedik egymást, gyakran adatszegmensekről beszélünk. Az átfedő ablakokat tipikusan csúszó ablakoknak nevezzük. A csúszó ablakokat rendszeresen használják idősorelemzésben különféle statisztikai mérőszámok és trendek meghatározására.

Az adatfolyam-feldolgozó rendszerek tipikusan folyamatokból felépülő csővezeték formájában valósulnak meg, a termelő-fogyasztó rendszer általános mintája szerint. A folyamatok háttérszálak, amelyek folyamatosan fogyasztják, feldolgozzák és továbbítják az adatokat, amíg le nem állítjuk őket. A folyamatok korlátos csatornákon keresztül kapcsolódnak egymáshoz, amelyeket rendszerint üzenetsorok valósítanak meg.

Az adatfolyam-feldolgozó rendszerek implementálása összetett feladat. A hatékonyság, a megbízhatóság, a hibatűrés, a skálázhatóság és a programozhatóság kulcsfontosságú követelmények. Mivel az ilyen rendszerek összetettségének jelentős része a futtatórendszerben összpontosul, ésszerű törekvés a végrehajtási logika és a futtatókörnyezet szétválasztása. A fejezet további részében az ilyen futtató keretrendszerek fejlődésének eredményeit, valamint azt vizsgáljuk meg, hogyan segítik ezek az adatfolyam-alkalmazások fejlesztését.

### 8.2 Népszerű adatfolyam-feldolgozó keretrendszerek

A felhőben elérhető, napi 24 órás folyamatos működésű alkalmazások megjelenése magával hozta az adatfolyam-alkalmazások elterjedését is. Ha a felhőben folyamatosan lehet számolni, miért ne használnánk ezt a képességet folyamatos adatfolyamok feldolgozására is? Ezeknek az alkalmazásoknak az elterjedése természetes módon vezetett az adatfolyam-feldolgozó keretrendszerek kialakulásához. Először a Spark Streaminget nézzük meg, amely mikrokötegek formájában támogatja az adatfolyam-feldolgozást. Sok felhasználó ezt az absztrakciót és az elérhető teljesítményt nem találta megfelelőnek, ezért az elmúlt évtizedben több új stream keretrendszer is megjelent. Ezek áttekintése következik.

#### 8.2.1 Spark Streaming

A Spark Streaming [18] a Spark kiterjesztése, amely élő adatfolyamok feldolgozását támogatja. Többféle adatforrásból képes adatot fogadni, és a feldolgozás eredményét fájlrendszerbe vagy adatbázisokba menteni. A megvalósítás a mikrokötegek fogalmára épül. A Spark Streaming a folyamatos bemeneti adatot kis adathalmazokra, úgynevezett mikrokötegekre bontja, amelyeket aztán a hagyományos Spark-rendszerhez továbbít végrehajtásra, egymást követő kötegelt feladatok sorozataként. Ezeket a mikrokötegeket a rendszer belsőleg diszkretizált adatfolyamokként, röviden `DStream`-ekként absztrahálja. A `DStream` adatstruktúra a Spark Streamingben `RDD`-k sorozata.

A kötegelt `Word Count` példa implementációját módosítani kell ahhoz, hogy adatfolyam-műveleteket is támogasson. A stream változat egy socket alapú adatfolyamot használ a szavak folyamatos fogadására. Minden bemeneti egység egy szövegsor lesz, amelyet egy `JavaReceiverInputDStream` típusú változó tárol. Ezen hajtjuk végre a jól ismert `map` műveletet, amely szavak sorozatát állítja elő `JavaDStream` típusban, majd ezen végrehajtjuk a `reduce` műveletet, amely kulcs-érték párokat ad vissza `JavaPairDStream` formájában. Fontos megjegyezni, hogy ezek egyelőre csak konfigurációs lépések. A tényleges adatfolyam-feldolgozás akkor indul el, amikor az `ssc` streaming kontextuson meghívjuk a `start()` metódust.

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
```

#### 8.2.2 Apache Flink

Az adatfolyam-feldolgozás egyik legzavaróbb sajátossága, hogy új implementációkat kíván meg a jól ismert, hagyományos kötegelt algoritmusainkhoz. Más szóval diszruptív technológia. Ha valaki élő adatfeldolgozást akar végezni, új implementációkra, vagyis új programozási munkára van szükség. Ez pedig azt jelenti, hogy a fejlesztőknek két külön kódbázist kell fejleszteniük és karbantartaniuk: egyet a kötegelt, egyet pedig az adatfolyam-feldolgozáshoz, ami kifejezetten kedvezőtlen.

Itt lép be a képbe az Apache Flink [19]. A Flink fejlesztői azt a célt tűzték ki, hogy a stream és a batch programozási modellt egy közös programozási modellbe egyesítsék. A Flink kulcsfogalma az adatfolyam, amelyen belül megkülönböztetünk korlátos és nem korlátos adatfolyamokat. A csak kezdettel, de véggel nem rendelkező nem korlátos adatfolyamok az élő stream adatokat reprezentálják, míg a jól definiált kezdettel és véggel rendelkező korlátos adatfolyamok a kötegelt feldolgozású adatokat írják le. Ha a hagyományos batch bemenetet korlátos adatfolyamként kezeljük, megszűnik a duplikált implementációk szükségessége. Ugyanaz az algoritmus így mindkét típusú adatfolyamon működhet.

A Flink funkciókban gazdag adatfolyam-feldolgozó motor. Sokféle forrásból képes adatot fogadni, különféle végrehajtási és tárolási rendszerekkel tud együttműködni, és eredményeit többféle fogyasztó felé képes továbbítani, például fájlrendszerbe, adatbázisokba, alkalmazásokba vagy eseménysorokba.

`Állapotkezelés`

A nagy elosztott rendszerek egyik kulcskérdése az állapot. Meghibásodások és hibák jelenlétében nagyon nehéz az alkalmazás állapotát konzisztensen fenntartani. Emiatt sok nagyméretű elosztott rendszer az állapotmentes tervezést részesíti előnyben, vagy kifejezetten ezt követeli meg.

Nyilvánvalóan nem minden alkalmazás lehet állapotmentes. A legtöbb nem triviális alkalmazásnak szüksége van állapotra. A Flink egyik megkülönböztető sajátossága az állapotfüggő műveletek támogatása. Az állapot elsőrangú fogalom a Flinkben, és a megvalósítás nagyon hatékony, mert memóriabeli állapotábrázolásra épül. A Flink különféle állapotprimitíveket biztosít, például atomi értékekhez, listákhoz vagy map struktúrákhoz. A fejlesztők a függvény hozzáférési mintája alapján választhatják ki a leghatékonyabb állapotprimitívet. Az alkalmazás állapotát egy cserélhető állapotháttérrendszer kezeli és checkpointolja. Hatékony implementációjának köszönhetően a Flink terabájtos nagyságrendű alkalmazásállapotokat is képes kezelni.

Az idő szintén fontos jellemzője az adatfolyam-alkalmazásoknak. A valós életben az eseményeknek oksági viszonyuk van: egy esemény nem történhet meg egy másik előtt, például nem hallhatjuk meg a lövés hangját azelőtt, hogy a fegyvert elsütötték volna. Ennek következtében az adatfolyamok legtöbbször időbélyegeket tartalmaznak, amelyek segítségével biztosítható az események oksági sorrendje. Ennek megfelelően a stream rendszerek megkülönböztetnek eseményidő és feldolgozási idő alapú működést. Eseményidő módban az alkalmazások az események időbélyege alapján dolgoznak, így az eredmény konzisztens marad attól függetlenül, hogy maga a feldolgozás mennyi ideig tart. Feldolgozási idő módban az alkalmazások a feldolgozás pillanatát veszik alapul, például olyan valós idejű alkalmazásokban, ahol meghatározott késleltetési követelmények vannak. Ilyenkor csak a feldolgozási határidőig beérkezett események kerülnek figyelembevételre, vagyis egyes események kimaradhatnak. A Flink mindkét időkezelési módot támogatja. Az alkalmazások használhatják az eseményidő vagy a feldolgozási idő szemantikáját. Eseményidő módban további finomabb mechanizmusok, például a vízjelek támogatása és a késve érkező események kezelése segíthetnek a kívánt szemantika elérésében.

Az eseményfolyamok többségének eleve van időszemantikája, hiszen minden esemény egy adott időpontban keletkezik. Emellett sok gyakori stream számítás időalapú, például az ablakos aggregációk, a munkamenetek képzése, a mintafelismerés vagy az időalapú összekapcsolások. Az adatfolyam-feldolgozás egyik fontos kérdése az, hogy az alkalmazás miként méri az időt, vagyis mi a különbség az eseményidő és a feldolgozási idő között. Ennek részletei a Flink dokumentációjában találhatók meg.

#### 8.2.3 Apache Storm / Trident

Az Apache Storm [20] a MapReduce és az adatfolyam-feldolgozás problémájának egy alternatív megközelítését kínálja. A Storm a nem korlátos adatfolyam-feldolgozási architektúra szemszögéből közelít. Képzeljünk el egy alkalmazást, amely folyamatosan fut, amíg le nem állítjuk. A bejövő adatokat egy általános termelő-fogyasztó rendszer dolgozza fel folyamatosan, adatfolyam-motorként működve. A Storm célja ennek a motornak az absztrakciója és az ilyen végrehajtási stratégiához illeszkedő alkalmazások fejlesztésének leegyszerűsítése.

Egy Java alapú termelő-fogyasztó implementáció létrehozása önmagában viszonylag egyszerű. Olyan rendszert azonban, amelyben több adatútvonal van, hibatűrő és skálázható, vagyis új csomópontok tetszőlegesen hozzáadhatók és eltávolíthatók újraindítás nélkül, rendkívül bonyolult felépíteni.

A Storm alapfogalma a `Topology`, amely a fenti általános termelő-fogyasztó adatfolyam-gráfot reprezentálja. A topológia bejövő adatfolyamokat dolgoz fel, vagyis a rendszerbe folyamatosan érkező, nem korlátos adatokat. Az adatfolyamok forrásait a topológia szélén `Spout` nevű speciális objektumok reprezentálják. Az adatforrás lehet API, üzenetsor stb., amely olyan adatot állít elő, amelyen műveleteket kell végezni. A topológia csomópontjai a `Bolt` elemek, amelyek egy-egy feldolgozási lépést jelentenek. Egy `Bolt` képes adatfolyamokat fogyasztani, azokon műveletet végrehajtani, majd az eredményt új adatfolyamként kiadni. A `Bolt` elemek a `Spout` elemekhez, majd egymáshoz kapcsolódnak a szükséges feldolgozási lánc kialakításához. Az összekötő élek kommunikációs kapcsolatok, amelyeken adatfolyam-elemek, vagyis tuple-ök haladnak át. A topológia végén egy utolsó `Bolt` kimenete egy másik, kapcsolódó rendszer bemeneteként is felhasználható.

Egy Storm topológia elosztott klaszterarchitektúra felett fut. A klaszter belépési pontja a `Nimbus` komponens. Ez hasonló szerepet tölt be, mint a Hadoop klaszter beküldési pontja. A `Zookeeper` klasztermenedzserként működik, ütemezi és figyeli a `Worker` csomópontokat. A `Worker` folyamatok helyi `Supervisor` komponenssel futnak, amely lokális erőforrás-kezelőként működik.

A Storm programozási modelljének szemléltetésére nézzük meg a szóelőfordulás-számlálás Storm implementációját. A magas szintű topológia szerint egy `Spout` mondatokat állít elő, amelyeket egy `Bolt` szavakra bont, majd egy másik `Bolt` megszámolja az egyes szavakat és előállítja az eredményt.

Kezdjük a mondatokat előállító `Spout` implementációjával. Itt a kulcsmetódus a `nextTuple()`, amely 100 milliszekundumonként egy véletlenszerűen kiválasztott mondatot küld a topológiába.

```java
public class RandomSentenceSpout extends BaseRichSpout {
SpoutOutputCollector _collector;
Random _rand;

@Override
public void open(Map conf, TopologyContext context,
SpoutOutputCollector collector) {
_collector = collector;
_rand = new Random();
}
@Override
public void nextTuple() {
Utils.sleep(100);
String[] sentences = new String[]{ "the cow jumped over the moon",
"an apple a day keeps the doctor away",
"four score and seven years ago", "snow white and the seven dwarfs",
"i am at two with nature" };
String sentence = sentences[_rand.nextInt(sentences.length)];
_collector.emit(new Values(sentence));
}
@Override
public void ack(Object id) {
}
@Override
public void fail(Object id) {
}
@Override
public void declareOutputFields(OutputFieldsDeclarer declarer) {
declarer.declare(new Fields("word"));
}
}
```

A következő osztály az első `Bolt` implementációja, amely a mondatokat szavakra bontja. Ebben az osztályban a legfontosabb a `execute()` metódus. Ez kiolvassa a bejövő `Tuple` tartalmát, szavakra bontja a mondatot, majd egy ciklusban minden egyes szót kibocsát a topológiába.

```java
public static class SplitSentence extends BaseBasicBolt {
@Override
public void declareOutputFields(OutputFieldsDeclarer declarer) {
declarer.declare(new Fields("word"));
}
@Override
public Map<String, Object> getComponentConfiguration() {
return null;
}
public void execute(Tuple tuple, BasicOutputCollector basicOutputCollector) {
String sentence = tuple.getStringByField("sentence");
String words[] = sentence.split(" ");
for (String w : words) {
basicOutputCollector.emit(new Values(w));
}
}
}
```

A következő `Bolt` maga a szógyakoriság-számláló folyamat. Az `execute` metódus hasonlóan indul, mint az előzőnél: kiolvassa a bejövő `Tuple` tartalmát. Az osztály egy mapben tárolja a `<word,count>` kulcs-érték párokat. Fontos megfigyelni, hogy minden beérkező szó új kimeneti tuple-t vált ki. A belső map folyamatosan frissül a tuple-ök feldolgozásával, így az egyes szavakhoz tartozó kibocsátott számlálók a program előrehaladtával változnak. Ez a kötegelt és az adatfolyam-feldolgozás egyik legfontosabb különbsége: stream módban több köztes szógyakorisági érték keletkezik, amelyek a feldolgozás aktuális állapotát és a bemenet részleges nézetét tükrözik.

```java
public static class WordCount extends BaseBasicBolt {
Map<String, Integer> counts = new HashMap<String, Integer>();
@Override
public void execute(Tuple tuple, BasicOutputCollector collector) {
String word = tuple.getString(0);
Integer count = counts.get(word);
if (count == null)
count = 0;
count++;
counts.put(word, count);
collector.emit(new Values(word, count));
}
@Override
public void declareOutputFields(OutputFieldsDeclarer declarer) {
declarer.declare(new Fields("word", "count"));
}
}
```

A példa utolsó lépése a program topológiájának létrehozása. Erre a `TopologyBuilder` osztály szolgál. Kompozicionális módon expliciten állítjuk be a `Spout` és `Bolt` elemeket. Miután a topológia elkészült, külső vagy lokális klaszter indítja el a feldolgozást a `submitTopology()` meghívásával.

```java
public static void main(String[] args) throws Exception {
TopologyBuilder builder = new TopologyBuilder();
builder.setSpout("spout", new RandomSentenceSpout(), 5);
builder.setBolt("split", new SplitSentence(), 8).shuffleGrouping("spout");
builder.setBolt("count", new WordCount(), 12).fieldsGrouping("split",
new Fields("word"));
Config conf = new Config();
conf.setDebug(true);
if (args != null && args.length > 0) {
conf.setNumWorkers(3);
StormSubmitter.submitTopologyWithProgressBar(args[0], conf,
builder.createTopology());
} else {
conf.setMaxTaskParallelism(3);
LocalCluster cluster = new LocalCluster();
cluster.submitTopology("word-count", conf, builder.createTopology());
Thread.sleep(10000);
cluster.shutdown();
}
}
```

#### 8.2.4 Apache Kafka

Az Apache Kafka [20] nagy teljesítményű üzenetközvetítő architektúra, amelyet valós idejű adatfolyam-csővezetékek felépítésére terveztek. Különféle adatfolyam-alkalmazásokban gyakran használják adatszállító rendszerként. Bár a Kafka önmagában is használható adatfolyam-feldolgozásra, elsődleges felhasználási területe tipikusan az adatfolyamok továbbítása.

A Kafka adatfolyamai rekordokból állnak. A rekordok kategóriákba tartoznak, amelyeket a Kafka `topic` néven jelöl. Minden rekord egy kulcsból, egy értékből és egy időbélyegből áll.

A hagyományos pont-pont alapú üzenetküldő rendszerekkel szemben a Kafka publish-subscribe architektúrát használ. A témákhoz belsőleg több üzenetsort alkalmaz, és a feliratkozók feliratkozhatnak az adott témába érkező üzenetekre. A rendszer garantálja, hogy minden feliratkozó megkapja az őt érdeklő eseményt. A Kafka megbízható, hibatűrő rendszer. Elosztott klasztert használ automatikus particionálással és replikációval, amely hardverhibák jelenlétében is zéró üzenetvesztést biztosít. Emellett nagyon gyors, és jól integrálható az Apache Spark és a Storm rendszerekkel.

A Kafka magas szintű működésében több termelő táplálhatja rekordokkal a rendszert, amelyeket több fogyasztó felé továbbít. Ezenfelül a Kafka összekapcsolható adatbázisokkal és stream processzorokkal is, hogy adatfeldolgozás történjen.

Egy Kafka klaszter több Kafka brokerből áll. A broker tulajdonképpen a Kafka klaszter egy csomópontja. A broker kezeli a termelőket és fogyasztókat, tárolja az üzeneteket, és replikáció segítségével biztosítja a hibatűrést. A terheléselosztás és a megbízhatóság támogatására minden téma több üzenetpartíció formájában tárolódik a brokerben. A partíció egy olyan sor, amelyben a rendszer gyűjti az üzeneteket. Egy partíción egy termelő a sor végére ír, miközben több fogyasztó olvassa az üzeneteket. Az üzenetek pozícióját offset értékek jelzik.

Két brokerből álló klaszter esetén például az egyik csomópont vezető, a másik pedig követő szerepet tölthet be. A követők feladata a vezető által tárolt adatok replikálása, és vezetőhiba esetén a szerep átvétele. A vezetőválasztás és a partícióreplikáció automatikusan, a háttérben történik. Amikor a termelők üzeneteket küldenek a klaszterbe, a rendszer automatikusan a megfelelő vezetőhöz irányítja az üzenetet; hasonlóképpen a fogyasztók is attól a vezetőtől kapják az üzeneteket, amely partícióból azok származnak. Az üzenetperzisztencia, visszaigazolás és replikáció részletesebb működését itt nem tárgyaljuk, de ennyi is jól mutatja, milyen összetett feladat egy hibatűrő, megbízható és skálázható üzenetküldő rendszer implementálása.

`Kafka Streaming`

Ahogy a rész elején említettük, a Kafka eredetileg üzenettovábbító rendszer volt. A `0.10.0` verzió óta azonban adatfolyam-feldolgozó API-t is tartalmaz, így önálló stream adatfeldolgozó rendszerré vált, és a Kafka-felhasználóknak adott esetben nincs is szükségük külön stream keretrendszerre alkalmazásaik megvalósításához. Mivel az írás idején az aktuális Kafka-verzió a `2.7`, jól látható, hogy az adatfolyam-feldolgozási támogatás nem tekinthető régen kiforrott funkciónak.

Röviden áttekintve a Kafka streamfeldolgozási képességeit: a stream programozás a `Kafka Stream API` révén valósul meg. Egy stream alkalmazás létrehozásának fő lépései: `i.` az alkalmazás konfigurálása, `ii.` a feldolgozási lépések definiálása, `iii.` a végrehajtási topológia létrehozása és az alkalmazás elindítása.

Minden alkalmazásnak szüksége van alkalmazásazonosítóra, szerverparaméterekre, valamint a kulcs-érték szerializációs osztályok definíciójára. Miután ezeket programtulajdonságként beállítottuk, a számítási logikát vagy a `Topology` osztállyal hozzuk létre, amelyben a `Processor` elemek kapcsolhatók össze, vagy a `StreamBuilder` osztállyal, amely magas szintű tartományspecifikus nyelvet biztosít a feldolgozási szakaszok leírására. A következő példában a `StreamBuilder` osztályt használjuk. Ebben a példában a `"my-input-topic"` témából érkező `String` hosszát küldjük a `"my-output-topic"` témába. Utolsó lépésként a `StreamBuilder` kimenetét átadjuk a `KafkaStreams` objektumnak, és a program elindítható.

```java
Properties props = new Properties();
props.put(StreamsConfig.APPLICATION_ID_CONFIG,
"my-stream-processing-application");
props.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");
props.put(StreamsConfig.DEFAULT_KEY_SERDE_CLASS_CONFIG,
Serdes.String().getClass());
props.put(StreamsConfig.DEFAULT_VALUE_SERDE_CLASS_CONFIG,
Serdes.String().getClass());

StreamsBuilder builder = new StreamsBuilder();
builder.<String, String>stream("my-input-topic")
.mapValues(value -> String.valueOf(value.length()))
.to("my-output-topic");
KafkaStreams streams = new KafkaStreams(builder.build(), props);
streams.start();
```

Ezután térjünk vissza a `Word Count` példához, és mutassuk meg annak Kafka stream implementációját. Ebben az esetben a tulajdonságkonfiguráció részleteit elhagyjuk. A bemeneti mondatot ismét szavakra bontjuk, de most egy extra lépést is beiktatunk: a `"the"` szót kiszűrjük a sorozatból, majd az egyes szavak előfordulási számát megszámoljuk és eredményként kiírjuk.

```java
KStreamBuilder builder = new KStreamBuilder();
KStream<String, String> source = builder.stream("wordcount-input");
final Pattern pattern = Pattern.compile("\\W+");
KStream counts = source.flatMapValues(value->
Arrays.asList(pattern.split(value.toLowerCase())))
.map((key, value) -> new KeyValue<Object, Object>(value, value))
.filter((key, value) -> (!value.equals("the")))
.groupByKey()
.count("CountStore")
.mapValues(value-> Long.toString(value))
.toStream();
counts.to("wordcount-output");
```

Miután a stream felépült, átadjuk a `KafkaStreams` példánynak, majd elindítjuk a programot. Mivel normál esetben a program korlátlan ideig futna, ebben a példában 5 másodperc után leállítjuk.

```java
KafkaStreams streams = new KafkaStreams(builder, props);
streams.start();
// usually the stream application would be running forever, in this example we
// just let it run for some time and stop since the input data is finite.
Thread.sleep(5000L);
streams.close();
```

#### 8.2.5 Apache Beam/GCP Dataflow

Az utolsó tárgyalt adatfolyam-keretrendszer az Apache Beam [21], amely egységes programozási absztrakciót nyújt a kötegelt és az adatfolyam-feldolgozáshoz. Nyílt forráskódú keretrendszer, akárcsak a korábban említett Apache rendszerek, jelentősége azonban abból fakad, hogy ezt a programozási rendszert használja a Google Dataflow, vagyis a GCP adatfolyam-feldolgozó szolgáltatása. Ha tehát nagyméretű adatfolyam-alkalmazást szeretnénk futtatni a Google Cloud Platformon, a Beam természetes választás, mivel szorosan integrálódik a Dataflow szolgáltatáshoz mint háttérrendszerhez. A Dataflow további előnye, hogy jól illeszkedik más Google szolgáltatásokhoz is, ami nagyon erős alkalmazásfejlesztési és végrehajtási platformmá teszi.

Kezdjük a Beam rendszer és programozási modelljének rövid áttekintésével. A Beam a `pipeline` fogalmát használja a program leírására. A pipeline a program teljes folyamatát reprezentálja elejétől a végéig, felelős az adatbevitelért, a feldolgozásért és az adatkimenetért. Miután létrehoztuk a pipeline-t, egy háttérrendszeren futtatható, amelyet `runner`-nek nevezünk. A Beam pipeline Java programban a `Pipeline` osztály egy példányaként jelenik meg. A modell következő eleme a `PCollection` osztály, amely a Beam program futása során használt elosztott adathalmazt reprezentálja. A `PCollection` lehet korlátos vagy nem korlátos attól függően, milyen bemenetet használunk. A modell harmadik eleme a `PTransform` osztály, amely a program egy feldolgozási lépését jelenti. A transzformációk módosíthatják, szűrhetik, csoportosíthatják, elemezhetik vagy más módon feldolgozhatják a `PCollection` elemeit. Egy transzformáció új kimeneti `PCollection`-t hoz létre anélkül, hogy módosítaná a bemeneti kollekciót. Egy transzformáció bemenetként egy vagy több `PCollection`-t kaphat, és kimenetként nulla vagy több `PCollection` objektumot állíthat elő.

Egy egyszerű pipeline a Beam Java programozási modellben a következő kódsablonnal írható le:

```text
[Final Output PCollection] =
[Initial Input PCollection]
.apply([First Transform])
.apply([Second Transform])
.apply([Third Transform]);
```

Az adatbázisbeolvasási művelet által létrehozott kezdeti `PCollection` objektum szolgál az első transzformáció végrehajtásához. Ez egy köztes `PCollection`-t ad vissza, amely a második transzformáció bemenete lesz. A következő visszaadott objektumot a harmadik transzformáció futtatására használjuk, amelynek eredménye az utolsó `PCollection`, amely már perzisztálható például adatbázisba. Az adatok pipeline-ba történő beolvasásához és onnan való kiírásához I/O transzformációkra van szükség. A Beam többféle specializált I/O transzformációt biztosít, amelyek a külső világgal való bemeneti és kimeneti műveleteket végzik. Érdemes megfigyelni a `PCollection` osztály `apply()` metódusát; ez felelős a transzformáció végrehajtásáért a pipeline adott pontján.

Számos alaptranszformáció már eleve implementálva van a Beamben, például a `ParDo`, `GroupByKey`, `CoGroupByKey`, `Combine`, `Flatten` és `Partition`. A `ParDo` párhuzamosan alakítja át a `PCollection` minden egyes elemét; használható elemek transzformálására, új `PCollection`-be írására vagy számítások végrehajtására az elemeken. A többi transzformáció leírása a Beam dokumentációjában található.

Miután a pipeline felépült, szükség van egy driver programra, amely a kiválasztott háttérrendszeren végrehajtja azt. A driver program feladata a háttérrendszer konfigurálása, a pipeline létrehozása és a program futtatása.

`WordCount` mintaprogram

Ezt a részt a `Word Count` példa Beam implementációjával zárjuk. A program egy olyan pipeline-t hoz létre, amely egymást követő transzformációkat hajt végre az adatokon:

1. egy gyökértranszformáció, a `TextIO.Read`, beolvassa a bemeneti szövegfájlokat; a visszatérési érték egy `PCollection`, amelynek minden eleme a bemeneti szöveg egy sora
2. egy `FlatMapElements` transzformáció a `PCollection<String>` sorait szavakra bontja, ahol minden elem Shakespeare műveinek egy-egy szava
3. egy `Count` transzformáció megszámolja az egyes szavak előfordulásait, és egy új kulcs-érték párokat tartalmazó `PCollection`-t ad vissza
4. végül a `TextIO.Write` kiírja a `PCollection` tartalmát szövegfájlok sorozatába

```java
public class MinimalWordCount {
public static void main(String[] args) {
// Create a PipelineOptions object.
PipelineOptions options = PipelineOptionsFactory.create();
...configuration skipped...
// Create the Pipeline object with the options we defined above
Pipeline p = Pipeline.create(options);
p.apply(TextIO.read().from("gs://apache-beam-samples/shakespeare/*"))
.apply(FlatMapElements.into(TypeDescriptors.strings())
.via((String line) -> Arrays.asList(line.split("[^\\p{L}]+"))))
// We use a Filter transform to avoid empty word
.apply(Filter.by((String word) -> !word.isEmpty()))
.apply(Count.perElement())
// Apply a MapElements transform that formats our PCollection of word counts into a
// printable string, suitable for writing to an output file.
.apply(
MapElements.into(TypeDescriptors.strings())
.via( (KV<String, Long> wordCount) ->
wordCount.getKey() + ": " + wordCount.getValue()))
.apply(TextIO.write().to("wordcounts"));
p.run().waitUntilFinish();
}
}
```

A program a GCP Dataflow szolgáltatáson a következő paranccsal futtatható. Figyeljük meg a `--runner` opcióban megadott `DataflowRunner` értéket, amely a Google Dataflow háttérrendszert választja ki, valamint a Google Storage bucketnév-sablonokat, amelyeket valós környezetben természetesen ki kell cserélni.

```bash
mvn compile exec:java -Dexec.mainClass=org.apache.beam.examples.WordCount \
-Dexec.args="--runner=DataflowRunner
--gcpTempLocation=gs://YOUR_GCS_BUCKET/tmp \
--project=YOUR_PROJECT --region=GCE_REGION \
--inputFile=gs://apache-beam-samples/shakespeare/*
--output=gs://YOUR_GCS_BUCKET/counts" \
-Pdataflow-runner
```

### 8.3 Az adatfolyam-keretrendszerek összehasonlítása

Az előző részben jó néhány adatfolyam-feldolgozó keretrendszert áttekintettünk anélkül, hogy teljességre törekedtünk volna. Több más rendszert a terjedelmi korlátok miatt kihagytunk. Felmerül tehát a kérdés: ha ennyi stream keretrendszer létezik, hogyan választhatjuk ki, melyik a legjobb, vagy melyiket érdemes egy adott probléma megoldására használni. Összehasonlíthatók-e ezek objektív módon?

Ebben a részben iránymutatást adunk arra, hogyan érdemes ezeket a keretrendszereket összehasonlítani, milyen tulajdonságokat és jellemzőket célszerű megvizsgálni, amikor egy rendszert implementációk alapjául választunk.

Mivel a szoftveres keretrendszerek használatának fő célja a fejlesztési idő csökkentése a meglévő implementációkra támaszkodva, az első vizsgált kategóriák a keretrendszert mint fejlesztői eszközt érintik: a komplexitás, a karbantarthatóság, a használhatóság és az érettség.

`Keretrendszer-komplexitás`
Meg kell vizsgálni, mennyire nehéz a rendszer telepítése és monitorozása, milyen szintű támogatást nyújt ezekhez a feladatokhoz, mennyire összetett a függőségek halmaza, vannak-e verziókorlátok, visszafelé kompatibilitási problémák stb.

`Keretrendszer-karbantarthatóság`
Itt az érdekel minket, hogy a keretrendszer gyártóspecifikus-e vagy felhőszolgáltató-független, használható-e tetszőleges konténertechnológiákkal, ha erre szükség van, illetve rendelkezik-e megfelelő és jó minőségű dokumentációval.

`Keretrendszer-barátságosság`
Kulcstulajdonság, hogy mennyire könnyű megérteni a működési modellt és a programozási absztrakciót. Emellett fontos kérdés az is, hány paramétert kell finomhangolni ahhoz, hogy a rendszer optimálisan működjön. Az API gazdagsága és letisztultsága szintén jelentős tényező. Végül a fejlesztők előnyben részesítik azokat a keretrendszereket, amelyek több programozási nyelvből vagy több nyelvvel együtt használhatók.

`Keretrendszer-érettség`
Mivel egy keretrendszer kiválasztása hosszú időre meghatározhatja a további fejlesztéseket, nagyon fontos, hogy a rendszer mögött erős támogatás álljon. A nyílt forráskódú rendszerek esetében ez jellemzően közösségi támogatást jelent. Ezért a felhasználói közösség mérete és aktivitása nagyon fontos indikátor. A közreműködők száma, a commit aktivitás, a hibajavítások átfutási ideje, a kiadások gyakorisága és a keretrendszert alkalmazó vállalatok száma mind jó mutatói egy sikeres rendszernek.

Továbblépve a technikaibb szempontok felé, összehasonlíthatjuk például a támogatott stream típusát, az üzenetkézbesítési garanciákat, a késleltetést és az áteresztőképességet, az erőforrás-felhasználást és a programozási modellt. Számos publikáció foglalkozik a stream keretrendszerek mélyreható összehasonlításával [22]–[26], itt azonban csak a legfontosabb jellemzőket emeljük ki.

A stream feldolgozás típusa lehet natív vagy mikroköteg alapú. A natív stream feldolgozás azt jelenti, hogy minden beérkező egyedi adatrekord külön feldolgozásra kerül. A mikroköteg ezzel szemben több rekordot gyűjt össze kis köteggé, amelyet a rendszer egyetlen művelettel dolgoz fel. A natív stream feldolgozás természetesen alacsonyabb késleltetést biztosít, ugyanakkor az üzenet-checkpointolás jelenlétében kedvezőtlenül hathat az áteresztőképességre. A mikroköteg alapú működés nagyobb késleltetéssel jár, viszont a kisebb üzenetkezelési többlet miatt jobb áteresztőképességet eredményezhet.

Bármely stream rendszer egyik legfontosabb tulajdonsága a megbízhatóság és a hibatűrés. Ezt rendszerint az üzenetkézbesítési garanciák fejezik ki. Három alapvető üzenetkézbesítési szemantika létezik elosztott rendszerekben: `At-Most-Once`, `At-Least-Once` és `Exactly Once`. Az `At-Most-Once` szemantika azt jelenti, hogy minden üzenet kézbesítését legfeljebb egyszer kísérli meg a rendszer. Ha a kézbesítés valamilyen okból meghiúsul, nem történik újraküldés. Röviden: az ilyen rendszerben üzenetek elveszhetnek. Az `At-Least-Once` szemantika garantálja, hogy minden üzenet eljut a fogyasztóhoz, de bizonyos üzenetek hiba esetén többször is megérkezhetnek az ismételt küldések miatt. Ilyen rendszerekben az alkalmazásnak nyomon kell követnie az üzeneteket, és kezelnie kell a felesleges duplikációkat. Az `Exactly Once` a legerősebb garancia: minden üzenet pontosan egyszer jut el a fogyasztóhoz. Az alkalmazásnak nem kell a duplikált üzenetek miatt aggódnia. Az üzenetkézbesítési szemantikák rendszerint együtt járnak az üzenetsorrend garanciáival is. `At-Most-Once` és `At-Least-Once` esetén az üzenetek kézbesítési sorrendje nem feltétlenül egyezik a küldési sorrenddel. Az `Exactly Once` szemantika pontos üzenetsorrendet is biztosít.

További technikai kérdés, hogy a keretrendszer milyen programozási absztrakciót használ az adatfolyam-feldolgozás kifejezésére. Az egyik stílus a kompozicionális megközelítés, ahol a programozónak kézzel kell felépítenie a feldolgozási topológiát építőelemekből, például adatforrásokból, operátorokból, transzformációkból és adatkimenetekből, és a komponensek interfészek formájában vannak definiálva. A másik stílus a deklaratív megközelítés, ahol a feldolgozási csővezeték a háttérben automatikusan jön létre, a programozónak csak az operátorokat kell függvényekként megadnia vagy használnia. Ez a működés funkcionális programozási stílushoz vezet, és erősen támaszkodhat lambda kifejezésekre.

Mivel az összes ismert stream keretrendszer mélyreható összehasonlítása túlmutat e könyv keretein, ezt a részt egy kisebb, szemléltető példával zárjuk, amely megmutatja, hogyan hasonlíthatók össze ezek a rendszerek. A Beam rendszer ebben az összehasonlításban nem szerepel. A Beam technikai összevetése más keretrendszerekkel a következő linken található:

`https://beam.apache.org/documentation/runners/capability-matrix`

## 9. Cloud Functions

A Cloud Functions a felhőalapú végrehajtási technológia legújabb fejleményeit képviseli. A függvények fő jellemzője, hogy lehetővé teszik a felhasználók számára, hogy közvetlenül a felhőbe töltsenek fel kódot anélkül, hogy külön futtatási infrastruktúrát kellene létrehozniuk. Ennek megfelelően a függvényeket szerver nélküli kódfuttatásnak tekintjük, és a felhőszolgáltatók ma már új szolgáltatástípusként írják le őket `Function-as-a-Service`, azaz `FaaS` néven.

A függvények végrehajtása során nem kell a szerverek menedzselésével foglalkoznunk, vagyis nem szükséges azok üzembe helyezése, kezelése vagy frissítése; ezt a felelősséget a felhőszolgáltató veszi át. A függvények a terheléshez igazodva automatikusan skálázódhatnak, és beépített monitorozási, naplózási és hibakeresési képességeket kínálnak. Támogatják a szerepalapú, illetve függvényenkénti biztonsági beállításokat, valamint rendelkeznek hálózati képességekkel is, hogy a függvényből más felhőkomponensek elérhetők legyenek.

A függvények a modern felhőtechnológia egyik legizgalmasabb elemei. Egységes módon valósítják meg a korábbi számítástechnikai rendszerek egykor utópisztikusnak tűnő elképzeléseit: a földrajzilag elosztott erőforrásokon történő zökkenőmentes végrehajtást, vagyis a grid számítást, valamint a nyilvános és privát szolgáltatások készletére épülő működést, vagyis a szolgáltatásorientált architektúrák világát.

Ebben a részben kizárólag a Google Cloud Functions szolgáltatásra [27] összpontosítunk. Hasonló rendszerek minden felhőszolgáltató kínálatában megtalálhatók, például az AWS Lambda [28]. Ettől a ponttól kezdve a `Function` szó a Google Cloud Functions szolgáltatásra utal.

A GCP-hez kétféle függvényt fejleszthetünk: `HTTP Function` és `Background Function`. A `HTTP Function` fejleszthető `Node.js`, `Python`, `Go`, `Java` vagy `C#` nyelven, míg a `Background Function` esetében `Node.js`, `Python`, `Go` vagy `Java` használható. A Cloud Functions környezet automatikusan kiválasztja a megfelelő futási környezetet a választott implementációs nyelv alapján.

### HTTP Function

A `HTTP Function` típust szabványos HTTP-kérések, például `GET`, `PUT`, `POST`, `DELETE` és `OPTIONS` meghívására tervezték. A kérés megvárja, amíg a kiszolgálás befejeződik és a válasz visszaérkezik. Javában egy egyedi függvénynek a `com.google.cloud.functions.HttpFunction` interfészt kell megvalósítania, amely egy funkcionális interfész, egyetlen `service()` metódussal. Az alábbi egyszerű példa bemutatja a kérés- és válaszfeldolgozást egy Java alapú függvényimplementációban. A kód és a működési logika nagyon hasonló ahhoz, amit a Java Enterprise Platform Servletjeinél láthatunk. A HTTP-függvények programozásáról további részletek itt találhatók:

`https://cloud.google.com/functions/docs/writing/http`

Minta HTTP-függvény Java nyelven:

```java
public class HelloHttp implements HttpFunction {
private static final Logger logger = Logger.getLogger(HelloHttp.class.getName());
private static final Gson gson = new Gson();
@Override
public void service(HttpRequest request, HttpResponse response)
throws IOException {
// Check URL parameters for "name" field
// "world" is the default value
String name = request.getFirstQueryParameter("name").orElse("world");

// Parse JSON request and check for "name" field
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

Pusztán összehasonlítás céljából ugyanennek a függvénynek a `Node.js` implementációját is bemutatjuk. A Java megvalósításhoz viszonyítva a kód tömörsége figyelemre méltó.

```javascript
const escapeHtml = require('escape-html');
/**
* HTTP Cloud Function.
*
* @param {Object} req Cloud Function request context.
*
More info: https://expressjs.com/en/api.html#req
* @param {Object} res Cloud Function response context.
*
More info: https://expressjs.com/en/api.html#res
*/
exports.helloHttp = (req, res) => {
res.send(`Hello ${escapeHtml(req.query.name || req.body.name || 'World')}!`);
};
```

### Background Function

A másik függvénytípus a `Background Function`, amelyet a felhő-infrastruktúrából származó események kezelésére terveztek, például egy Cloud Storage bucketben bekövetkező változás vagy egy Cloud Pub/Sub témába érkező üzenet esetén. A Java alapú háttérfüggvényeknek a `com.google.cloud.functions.BackgroundFunction` interfészt kell megvalósítaniuk. A `service()` helyett ez az interfész egyetlen `accept()` metódust tartalmaz, amely akkor hívódik meg, amikor a figyelt esemény bekövetkezik.

A következő példában egy olyan `Background Function` látható, amely akkor aktiválódik, amikor valamilyen változás történik egy Cloud Storage bucketben. Figyeljük meg az interfész generikus típusparaméterét, amely meghatározza, hogy ez az implementáció milyen eseménytípusokra fog meghívódni. A függvény kinyeri a bucket és a fájl adatait, valamint a bekövetkezett esemény típusát.

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

A háttérfüggvények írásáról további részletek itt találhatók:

`https://cloud.google.com/functions/docs/writing/background`

A függvények létrehozásának általános lépései a következők:

1. függvények megírása
2. függvények telepítése
3. függvények végrehajtása vagy meghívása
4. függvények monitorozása

### Függvényvégrehajtás

A GCP-függvények mindig izolált, biztonságos futási környezet-kontextusban hajtódnak végre. A függvények egyik fontos korlátja, hogy állapotmentesnek kell lenniük. Ha a helyes működéshez állapotra van szükség, azt Google Storage-ban vagy Datastore-ban kell tartósan tárolni. Egy függvénypéldány egyetlen klienskérést szolgál ki; szükség esetén több példány indul el.

A GCP a függvényekre a következő végrehajtási garanciákat adja: a HTTP-függvények `At-Most-Once`, míg a háttérfüggvények `At-Least-Once` szemantikával hívódnak meg.

A Cloud Functions futását triggerek indítják el. A triggerek típusai lehetnek: `HTTP Triggers`, `Cloud Pub/Sub Triggers`, `Cloud Storage Triggers`, `Direct Triggers`, `Cloud Firestore Triggers`, `Analytics for Firebase Triggers`, `Firebase Realtime Database Triggers` és `Firebase Authentication Triggers`. A következő fejezetben a Cloud Pub/Sub mechanizmust vizsgáljuk meg részletesebben, hogy megértsük az általános esemény- és üzenetkézbesítési mechanizmusokat.

### Függvények telepítése

Mielőtt egy függvény végrehajtható lenne, telepíteni kell a felhőbe. A telepítés magában foglalja egy olyan archívum feltöltését egy Google Cloud Storage bucketbe, amely a függvény forráskódját tartalmazza. A függvény telepítésére a következő lehetőségek állnak rendelkezésre.

`1. Telepítés a helyi gépről`

A szükséges paraméterek behelyettesítése után hajtsuk végre a következő `gcloud` parancsot:

```bash
gcloud functions deploy NAME --runtime RUNTIME TRIGGER [FLAGS...]
```

`2. Telepítés forráskódkezelő rendszerből`

A szükséges paraméterek behelyettesítése után hajtsuk végre a következő `gcloud` parancsot:

```bash
gcloud functions deploy NAME --source https://source.developers.google.com/
projects/PROJECT_ID/repos/REPOSITORY_ID/moveable-aliases/master/
paths/SOURCE
--runtime RUNTIME TRIGGER... [FLAGS...]
```

`3. Telepítés a GCP Console felületéről`

Ezt példaként részletesebben is megnézzük egy HTTP-függvény létrehozása közben.

Végezzük el a következő lépéseket sorban:

1. Nyissuk meg a `Functions Overview` oldalt a Cloud Console felületen.
2. Győződjünk meg róla, hogy az a projekt van kiválasztva, amelyen a Cloud Functions engedélyezve van.
3. Kattintsunk a `Create function` gombra.
4. Adjunk nevet a függvénynek.
5. A `Trigger` mezőben válasszuk a `HTTP` opciót.
6. Az `Authentication` mezőben válasszuk az `Allow unauthenticated invocations` lehetőséget.
7. Kattintsunk a `Save` gombra a módosítások mentéséhez, majd kattintsunk a `Next` gombra.
8. A `Source code` mezőben válasszuk az `Inline editor` lehetőséget. Ebben a gyakorlatban a szerkesztő által felkínált alapértelmezett függvényt használjuk.
9. A `Runtime` legördülő menüben válasszuk ki a kívánt Java futási környezetet.
10. Az oldal alján kattintsunk a `Deploy` gombra.
11. A `Deploy` gomb megnyomása után a Cloud Console visszairányít a `Cloud Functions Overview` oldalra.
12. Amint a telepítés befejeződött, a függvény működését úgy tesztelhetjük, hogy megnyitjuk a függvény menüjét és a `Test function` lehetőségre kattintunk.

A függvény végrehajtása az automatikusan létrejövő naplóbejegyzések megtekintésével ellenőrizhető. A `Cloud Functions Overview` oldalon nyissuk meg a függvény menüjét, majd kattintsunk a `View logs` lehetőségre, hogy megjelenjen egy naplóablak.

Egy teljes, lépésről lépésre végigvezetett példa egy Storage által kiváltott háttérfüggvény létrehozására és tesztelésére az alábbi linken található:

`https://cloud.google.com/functions/docs/tutorials/storage`

## 10. Szolgáltatások közötti kommunikáció: Pub/Sub

Egy felhőalkalmazás létrehozása több kész és egyedi felhőszolgáltatás használatát jelenti, amelyeknek az alkalmazás teljes életciklusa során együtt kell működniük. Az erős csatolású, szinkron RPC stílusú hívások nem megfelelőek nagy elosztott alkalmazásokhoz; a laza csatolású, üzenetalapú kommunikáció az egyetlen életképes stratégia nagyméretű, skálázható alkalmazások esetén. Ennek megfelelően minden felhőszolgáltató kínál valamilyen üzenetküldő szolgáltatást, amely segít az egyes komponensek összekapcsolásában. Ebben a részben a Google Cloud Platform által nyújtott üzenetküldő szolgáltatásra, a Google Pub/Sub szolgáltatásra összpontosítunk.

### 10.1 A Google Pub/Sub áttekintése

A Google Pub/Sub egy magas rendelkezésre állású, aszinkron, valós idejű üzenetküldő szolgáltatás, amely a publish-subscribe elvre épül. A Pub/Sub alacsony késleltetésű, nagy áteresztőképességű rendszer, amely a Google Cloud összes régiójában működik, és univerzális üzenetküldési és eseménykézbesítési infrastruktúrát biztosít a globális felhőalkalmazások számára. A Pub/Sub használható általános üzenetküldő middleware-ként, Cloud Functions függvényeket kiváltó eseménykézbesítési rendszerként vagy adatfolyam-rétegként is.

A Pub/Sub a közzétevőket és a feliratkozókat témákon keresztül kapcsolja össze. A `Topic` egy névvel ellátott erőforrás, amelyre a közzétevők üzeneteket küldenek. A feliratkozók `Subscription` erőforrásokat hoznak létre, amelyek egy adott témából származó üzenetfolyamot reprezentálnak, és ezt a feliratkozó alkalmazásnak kézbesítik. A `Message` olyan adatok és opcionális attribútumok kombinációja, amelyet a közzétevő egy témára küld, és amely végül eljut a feliratkozókhoz. Az üzenetattribútum egy kulcs-érték pár, amelyet a közzétevő tetszőlegesen meghatározhat egy adott üzenethez.

A Pub/Sub üzenet tényleges formátuma a következő. Egy üzenet az üzenet adatait és metaadatait tartalmazó mezőkből áll. Az alábbi mezők közül legalább egynek szerepelnie kell az üzenetben:

- az üzenet adatai
- egy sorrendezési kulcs
- további metaadatokat tartalmazó attribútumok

A Pub/Sub szolgáltatás a következő mezőket adja hozzá az üzenethez:

- a témán belül egyedi üzenetazonosító
- időbélyeg arról, hogy a Pub/Sub szolgáltatás mikor fogadta az üzenetet

A Pub/Sub a Google Cloud infrastruktúra szerves része, ezért az összes Google szolgáltatás támogatja. Emiatt a GCP-szolgáltatások integrációja szinte triviális feladattá válik.

A Pub/Sub nagyon különböző típusú komponenseket képes egységes felhőalkalmazásba kapcsolni. Bármely alkalmazás, amely képes HTTPS-kéréseket küldeni a `pubsub.googleapis.com` címre, lehet közzétevő, például egy App Engine alkalmazás, egy Google Compute Engine-en hosztolt webszolgáltatás, bármely más külső hálózaton futó rendszer, vagy akár egy asztali vagy mobil eszközre telepített alkalmazás. Hasonlóképpen bármely alkalmazás, amely képes HTTPS-kéréseket küldeni a `pubsub.googleapis.com` címre, lehet lekérő feliratkozó is.

A Pub/Sub `N az M-hez` leképezést támogat a közzétevők és a feliratkozók között. A feliratkozók tetszőleges számú témából fogadhatnak üzeneteket, akár átfedésekkel is. Hasonlóképpen a közzétevők is kézbesíthetnek üzeneteket különálló vagy csoportosított feliratkozóknak. A közzétevők és a feliratkozók közötti leképezést a téma-feliratkozás konfigurációk valósítják meg.

Egy szemléletes példában legyen három közzétevőnk `A`, `B` és `C`, valamint három feliratkozónk `X`, `Y` és `Z`. Az `X` feliratkozó szeretne üzeneteket kapni mind `A`, mind `B` közzétevőtől, ezért feliratkozik az `A` és `B` témákra. Az így létrejövő `XA` és `XB` feliratkozások garantálják, hogy az `A` és `B` témákra küldött minden üzenet eljut `X`-hez. Ezzel szemben `Y` és `Z` ugyanattól a `C` közzétevőtől szeretnének üzeneteket kapni. Ebben az esetben `Y` és `Z` a `C` témára iratkoznak fel, ami `YC` és `ZC` feliratkozásokat hoz létre. Ha `C` közzétevőtől érkezik egy üzenet, ugyanaz az üzenet a `YC` feliratkozáson keresztül eljut `Y`-hoz, a `ZC` feliratkozáson keresztül pedig `Z`-hez.

### 10.2 A Pub/Sub üzenetfolyama

Ebben a részben részletesen megvizsgáljuk az üzenetkézbesítés lépéseit. Egy közzétevő által küldött üzenet kézbesítése a Pub/Sub infrastruktúrában a következő lépésekből áll:

1. Egy közzétevő alkalmazás létrehoz egy témát a Pub/Sub szolgáltatásban, majd üzeneteket küld erre a témára. Az üzenet tartalmaz egy hasznos adatot és opcionális attribútumokat, amelyek leírják a hasznos adat tartalmát.
2. A szolgáltatás biztosítja, hogy a közzétett üzenetek a feliratkozások nevében megőrzésre kerüljenek. Egy közzétett üzenet addig marad meg egy adott feliratkozás számára, amíg azt valamelyik, abból a feliratkozásból üzeneteket fogyasztó feliratkozó nyugtázza.
3. A Pub/Sub a témáról minden feliratkozás felé külön-külön továbbítja az üzeneteket.
4. A feliratkozó kétféleképpen kaphat üzenetet: vagy a Pub/Sub push módon továbbítja azt a feliratkozó által megadott végpontra, vagy a feliratkozó pull módban lekéri azt a szolgáltatástól.
5. A feliratkozó minden fogadott üzenethez nyugtát küld a Pub/Sub szolgáltatásnak.
6. A szolgáltatás eltávolítja a nyugtázott üzeneteket a feliratkozás üzenetsorából.

A Pub/Sub alapértelmezés szerint `At-Least-Once` szemantikával kézbesíti az üzeneteket. Az üzenetkézbesítés egyetlen kivétele az, ha egy üzenet a létrejöttétől számított hét napon belül nem kézbesíthető; ebben az esetben hét nap után kézbesítés nélkül törlődik. Hasonlóképpen, ha egy üzenet létrejöttekor nincs hozzá tartozó feliratkozás, az az üzenet egyáltalán nem kerül kézbesítésre.

Ha a Pub/Sub szolgáltatást a Beam SDK stream programozási modelljével együtt használjuk, akkor lehetőség van `Exactly-Once` szemantika és rendezett üzenetkézbesítés elérésére.

A Pub/Sub architektúrájáról további részletek a következő linken találhatók:

`https://cloud.google.com/pubsub/architecture`

### 10.3 Példa az üzenetkézbesítésre

Miután áttekintettük a Pub/Sub szolgáltatás általános filozófiáját és működését, most nézzünk meg egy kis példát, amely ezt a gyakorlatban szemlélteti. A példa egy olyan háttérfüggvényből áll, amelyet egy Pub/Sub üzenet indít el.

A függvény forráskódja alább látható. A függvény fogad egy Pub/Sub üzenetet, kinyeri annak tartalmát, majd beilleszti azt a `"Hello ..."` formájú kimeneti sztringbe, ezzel személyre szabott üdvözlést hozva létre.

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

Miután a kód elkészült, a függvényt a felhőbe telepítjük az alábbi `gcloud` paranccsal. A téma neve ebben a példában `SAMPLE_TOPIC`. A téma nevét a telepítési parancsban a `--trigger-topic` opcióval adjuk meg, amely a `SAMPLE_TOPIC` nevű Pub/Sub témához tartozó kiváltó eseményt határozza meg.

```bash
gcloud functions deploy java-pubsub-function \
--entry-point functions.HelloPubSub \
--runtime java11 \
--memory 512MB \
--trigger-topic SAMPLE_TOPIC
```

A függvény telepítése után a következő paranccsal hozzuk létre a témát:

```bash
gcloud pubsub topics create SAMPLE_TOPIC
```

Végül a minta működését úgy teszteljük, hogy egy `"Einstein"` tartalmú tesztüzenetet küldünk a `SAMPLE_TOPIC` témára. Az egyszerűség kedvéért az üzenet létrehozására a `gcloud` parancsot használjuk. A következő részben azt is megnézzük, hogyan lehet üzeneteket küldeni és fogadni közvetlenül az alkalmazáskódból.

```bash
gcloud pubsub topics publish SAMPLE_TOPIC --message Einstein
```

### 10.4 Üzenetek közzététele és fogadása kódból

Most azt vizsgáljuk meg, hogyan lehet üzeneteket közzétenni és fogadni Java nyelvű Pub/Sub API használatával. Az első kódrészlet egy üzenet közzétételét szemlélteti.

Először a téma nevét a téma- és projektazonosító alapján kérjük le, majd létrehozunk egy `publisher` objektumot. Ezt követi egy új üzenet létrehozása a megfelelő adatmezőkkel. Ezután az üzenetet közzétesszük. A visszakapott `future` objektumot egy aszinkron callback objektumnak adjuk át, amely akkor lép működésbe, amikor az üzenet közzététele sikeres volt vagy amikor a közzététel hibával meghiúsult. A program a közzétevő leállításával zárul.

Pub/Sub üzenet közzététele:

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
// TODO(developer): Replace these variables before running the sample.
String projectId = "your-project-id";
String topicId = "your-topic-id";
publishWithErrorHandlerExample(projectId, topicId);
}
public static void publishWithErrorHandlerExample(String projectId, String topicId)
throws IOException, InterruptedException {
TopicName topicName = TopicName.of(projectId, topicId);
Publisher publisher = null;
try {
// Create a publisher instance with default settings bound to the topic
publisher = Publisher.newBuilder(topicName).build();
List<String> messages = Arrays.asList("first message", "second message");
for (final String message : messages) {
ByteString data = ByteString.copyFromUtf8(message);
PubsubMessage pubsubMessage = PubsubMessage.newBuilder().setData(data).build();
// Once published, returns a server-assigned message id (unique within the topic)
ApiFuture<String> future = publisher.publish(pubsubMessage);
// Add an asynchronous callback to handle success / failure
ApiFutures.addCallback(
future,
new ApiFutureCallback<String>() {
@Override
public void onFailure(Throwable throwable) {
if (throwable instanceof ApiException) {
ApiException apiException = ((ApiException) throwable);
// details on the API exception
System.out.println(apiException.getStatusCode().getCode());
System.out.println(apiException.isRetryable());
}
System.out.println("Error publishing message : " + message);
}
@Override
public void onSuccess(String messageId) {
// Once published, returns server-assigned message ids (unique within
// the topic)
System.out.println("Published message ID: " + messageId);
}
},
MoreExecutors.directExecutor());
}
} finally {
if (publisher != null) {
// When finished with the publisher, shutdown to free up resources.
publisher.shutdown();
publisher.awaitTermination(1, TimeUnit.MINUTES);
}
}
}
}
```

A második példa azt szemlélteti, hogyan lehet üzenetet fogadni egy alkalmazásban. A Pub/Sub-ban kétféle üzenetkézbesítés létezik: `Pull` és `Push`. Pull kézbesítés esetén a feliratkozónak explicit módon le kell kérnie az üzenetet a Pub/Sub rendszertől. Push módban a Pub/Sub rendszer közvetlenül elküldi az üzenetet a feliratkozónak anélkül, hogy külön kérést várna.

A példánk csak a `Pull` kézbesítés implementációját mutatja be. A program először lekéri a feliratkozás nevét a megadott projekt- és feliratkozásazonosítók alapján. Ezután létrehoz egy `subscriber` példányt a feliratkozás nevével és egy `receiver` objektummal. A feliratkozó ezután elindul, hogy megkezdje az üzenetek fogadását. A feliratkozó a háttérben kapcsolódik a Pub/Sub rendszerhez és üzeneteket kér le. Amikor egy üzenet megérkezik, a feliratkozónak paraméterként átadott `receiver` objektum lambda kifejezése aktiválódik, amelyben az adat tartalma kiolvasásra kerül és az üzenet kézbesítése nyugtázásra kerül.

Pub/Sub üzenet fogadása:

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
// TODO(developer): Replace these variables before running the sample.
String projectId = "your-project-id";
String subscriptionId = "your-subscription-id";
subscribeAsyncExample(projectId, subscriptionId);
}
public static void subscribeAsyncExample(String projectId, String subscriptionId) {
ProjectSubscriptionName subscriptionName =
ProjectSubscriptionName.of(projectId, subscriptionId);
// Instantiate an asynchronous message receiver.
MessageReceiver receiver =
(PubsubMessage message, AckReplyConsumer consumer) -> {
// Handle incoming message, then ack the received message.
System.out.println("Id: " + message.getMessageId());
System.out.println("Data: " + message.getData().toStringUtf8());
consumer.ack();
};
Subscriber subscriber = null;
try {
subscriber = Subscriber.newBuilder(subscriptionName, receiver).build();
// Start the subscriber.
subscriber.startAsync().awaitRunning();
System.out.printf("Listening for messages on %s:\n", subscriptionName.toString());
// Allow the subscriber to run for 30s unless an unrecoverable error occurs.
subscriber.awaitTerminated(30, TimeUnit.SECONDS);
} catch (TimeoutException timeoutException) {
// Shut down the subscriber after 30s. Stop receiving messages.
subscriber.stopAsync();
}
}
}
```

## 11. GCP szolgáltatáspéldák

Az előző fejezetekben a Google Cloud Platform különböző IaaS szintű szolgáltatásait vizsgáltuk. Azt is áttekintettük, hogyan lehet nagy számítási és adatfeldolgozási feladatokat kötegelt és adatfolyam-alapú módon végrehajtani. Megismertük a Cloud Functions szolgáltatást és a Pub/Sub publish-subscribe alapú üzenet- és eseménykézbesítési rendszert. A Google Cloud Platform ugyanakkor több magas szintű, azonnal használható szolgáltatáskomponenst is kínál, amelyek felhőalkalmazásokban felhasználhatók, jelentősen növelve ezek képességeit, miközben drasztikusan csökkentik a fejlesztési ráfordítást.

A legizgalmasabb példák ezek közül a számításigényes és nehezen megvalósítható területekről kerülnek ki, mint a mesterséges intelligencia és az ember-gép interfészek világa. Ebben a fejezetben ezek közül néhány szolgáltatás rövid áttekintését és bevezetését adjuk meg. Mivel ezeknek a szolgáltatásoknak a száma és funkcionalitása folyamatosan nő, a tárgyalás semmiképpen sem teljes; csak néhány különösen érdekes szolgáltatást választunk ki, és ezek képességeit, illetve programozási API-jait mutatjuk be. A cél mindössze az, hogy ízelítőt adjunk a lehetőségekből.

Az írás időpontjában a GCP mesterséges intelligencia és gépi tanulási termékei közé a következő szolgáltatások tartoznak:

`AutoML`
Olyan szolgáltatás, amely gépi tanulási funkcionalitást biztosít a Google gépi tanulási képességeire építve. Egyedi ML-modellek egyszerűen létrehozhatók több alkalmazási területre, például szövegfeldolgozásra (`AutoML Natural Language`), képosztályozásra és objektumfelismerésre (`AutoML Vision`), videóintelligenciára és objektumkövetésre (`AutoML Video Intelligence`), valamint adatelemzésre (`AutoML Tables`).

`Vision AI`
Olyan szolgáltatás, amely tanítás nélkül, egyedi vagy előtanított modellek használatával biztosít képfelismerési és képértelmezési funkciókat, beleértve a szövegkinyerést és felismerést (`OCR`), a képcímkézést, az arc- és nevezetesség-felismerést, valamint a tartalomcímkézést.

`Video AI`
Olyan szolgáltatás, amely erőteljes tartalomfeltárási, felismerési, objektumkövetési és snittelemzési képességeket nyújt videószekvenciákon.

`Cloud Natural Language`
Olyan szolgáltatás, amely természetesnyelv-feldolgozási technológiákat biztosít a fejlesztők számára, többek között érzelemelemzést, entitáselemzést, entitásérzelem-elemzést, tartalomosztályozást és szintaktikai elemzést, hogy strukturálatlan szövegből nyerjen ki információt.

`Cloud Translation`
Olyan szolgáltatás, amely tetszőleges nyelvpárok között képes dinamikusan fordítani, ezzel növelve az alkalmazások és webhelyek használhatóságát a globális piacon.

`Text-to-Speech`
Olyan szolgáltatás, amely a szöveget vagy a `Speech Synthesis Markup Language`, azaz `SSML` bemenetet természetes hangzású beszéddé alakítja gépi tanulás segítségével.

`Speech-to-Text`
Ez a szolgáltatás lehetővé teszi a Google beszédfelismerő technológiáinak egyszerű integrálását fejlesztői alkalmazásokba. Az alkalmazás hanganyagot küld a szolgáltatásnak, amely szöveges átírást ad vissza.

`Dialogflow`
Olyan szolgáltatás, amely beszélgető ügynökökre épülő, vonzó hang- és szövegalapú társalgási interfészek létrehozását segíti.

A szolgáltatások széles köréből most a `Vision AI`, a `Cloud Translation` és a `Text-to-Speech` szolgáltatásokat nézzük meg részletesebben.

### 11.1 Vision AI

A Vision AI Java API több száz osztályt tartalmaz a `com.google.cloud.vision.v1` csomag részeként. Szerencsére ezek közül csak néhányra van valóban szükség ahhoz, hogy izgalmas műveleteket hajtsunk végre képeken. Mi a képfelismerési feladatokra összpontosítunk. Ebben a környezetben a kulcsfontosságú osztály az `ImageAnnotatorClient`. Ennek az osztálynak több különféle `...Annotate...()` metódusa is van, amelyek helyi vagy távoli fájlokon végzik el a felismerési műveleteket.

A folyamat első lépése egy `ImageAnnotatorClient` példány létrehozása, ahogy az alábbiakban látható. Ezt a példányt használva Vision API kliensként, a felismerés a `batchAnnotateImages()` metódus meghívásával hajtható végre. Miután a felismerés lefutott, a rendszer egy válaszobjektumot ad vissza, amely a detektált objektumok listáját tartalmazza. Ezek egyenként kiolvashatók, és a program későbbi részeiben tetszés szerint felhasználhatók.

```java
// Initialize client that will be used to send requests.
// This client only needs to be created once, and can be reused for multiple
// requests. After completing all of your requests, call
// the "close" method on the client to safely clean up any remaining background
// resources.
try (ImageAnnotatorClient client = ImageAnnotatorClient.create()) {
BatchAnnotateImagesResponse response = client.batchAnnotateImages(requests);
List<AnnotateImageResponse> responses = response.getResponsesList();
...
// process responses
...
```

A `batchAnnotateImages()` metódus egy `List<AnnotateImageRequest>` típusú kéréslistát vár paraméterként. Ennek a listának olyan annotációs kérésobjektumokat kell tartalmaznia, amelyek megadják, milyen felismerhető jellemzőket keresünk a képeken. Minden egyes jellemző egy külön builder objektummal hozható létre. A jellemzőtípusokat a `Feature` osztály definiálja. Az alábbi példában a kiválasztott jellemző a `TEXT_DETECTION`. Az `img` változó az a célkép, helyi vagy távoli fájl, amelyen a felismerést végre szeretnénk hajtani.

```java
List<AnnotateImageRequest> requests = new ArrayList<>();
Feature feat = Feature.newBuilder().setType(Feature.Type.TEXT_DETECTION).build();
AnnotateImageRequest request =
AnnotateImageRequest.newBuilder().addFeatures(feat).setImage(img).build();
requests.add(request);
```

A jelenlegi API által támogatott további jellemzőtípusok közé tartozik a `CROP_HINTS`, `DOCUMENT_TEXT_DETECTION`, `FACE_DETECTION`, `IMAGE_PROPERTIES`, amely különféle képtulajdonságokat, például a domináns színeket számítja ki, továbbá a `LABEL_DETECTION`, `LANDMARK_DETECTION`, `LOGO_DETECTION`, `OBJECT_LOCALIZATION`, `PRODUCT_SEARCH`, `SAFE_SEARCH_DETECTION`, amely potenciálisan nem biztonságos vagy nem kívánatos tartalmat észlel, valamint a `TEXT_DETECTION`.

Ha például nemcsak nyomtatott szöveget, hanem kézírást és logókat is szeretnénk felismerni, akkor a jellemzők builder kódja a következőképpen nézne ki:

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

A Cloud Translation Java API osztályai a `com.google.cloud.translate` csomag részei. Az API használatának belépési pontja a `Translate` interfész. Ez egy olyan szolgáltatásproxy, amely a kívánt fordítás végrehajtására használható. Az alábbi példában egy alapértelmezett fordítószolgáltatást kérünk le a `TranslateOptions` osztály segítségével. Miután megkaptuk a szolgáltatás referenciáját, a `translate()` metódus meghívásával végrehajtjuk a fordítást. Az eredményként kapott `Translation` objektum tartalmazza a lefordított szöveget.

```java
import com.google.cloud.translate.*;
Translate translate = TranslateOptions.getDefaultInstance().getService();
Translation translation = translate.translate("¡Hola Mundo!");
System.out.printf("Translated Text:\n\t%s\n", translation.getTranslatedText());
```

A fordításhoz pontosabb paramétereket is megadhatunk. Az előző példában a nyelvfelismerés automatikusan történt. Ha akarjuk, explicit módon is beállíthatjuk a forrás- és célnyelvet, például spanyolról németre fordítva:

```java
Translation translation =
translate.translate(
"Hola Mundo!",
Translate.TranslateOption.sourceLanguage("es"),
Translate.TranslateOption.targetLanguage("de"),
// Use "base" for standard edition, "nmt" for the premium model.
Translate.TranslateOption.model("nmt"));
```

A Translation API rendelkezik egy `Advanced` változattal is, amely további funkciókat tartalmaz, például fordítási szószedetek létrehozásának lehetőségét, illetve nagy mennyiségű szöveg kötegelt fordítását, a képfelismerési példánál látott kódsablonhoz hasonló módon, a `TranslationServiceClient` osztály és a `client.translateText(request)` metódushívás használatával. A speciális mód részletei a Translation szolgáltatás dokumentációjában találhatók:

`https://cloud.google.com/translate/docs/basic/quickstart`

### 11.3 Text-to-Speech

A `Text-to-Speech` szolgáltatás arra használható, hogy szöveget emberi hangzású beszéddé alakítson a Google beszédgeneráló motorjai segítségével. A szolgáltatás a világ szinte összes fontos nyelvét támogatja férfi és női hangokkal, választható beszédgenerálási technológiák alapján. A támogatott nyelvek teljes listája a következő linken található:

`https://cloud.google.com/text-to-speech/docs/voices`

A Java API a `com.google.cloud.texttospeech.v1` csomag része. A szolgáltatás használatának fő osztálya a `TextToSpeechClient`. A következő példa létrehoz egy példányt ebből az osztályból, majd felépít egy `SynthesisInput` objektumot a `"Hello World"` szöveggel mint forrásszöveggel. A következő lépésben a beszédszintézis paramétereit, például a célnyelvet és a hangot, a `VoiceSelectionParams` osztály metódusaival állítjuk be. Miután megadtuk a kimeneti hangfájl formátumát, meghívjuk a `synthesizeSpeech` metódust a `textToSpeechClient` objektumon. A program végül egy kimeneti fájlba menti az eredményt.

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
* Google Cloud TextToSpeech API sample application. Example usage: mvn package
exec:java
* -Dexec.mainClass='com.example.texttospeech.QuickstartSample'
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

## 12. Felhőszolgáltatások orchestrációja

Ennek a résznek a célja az, hogy összefoglalja mindazt, amiről az előző fejezetekben szó volt, és megmutassa, hogyan teszi lehetővé a felhőtechnológia hasznos, funkciógazdag és megbízható alkalmazások nagyon hatékony létrehozását, nagy számú felhasználó kiszolgálása mellett. Létrehozhatunk szolgáltatásokat meghatározott funkcionalitások biztosítására, vagy használhatunk felhőszolgáltatók, illetve külső fejlesztők által nyújtott szolgáltatásokat jövőbeli alkalmazások komponenseiként. A gyártók integrációs technológiákat is biztosítanak ezeknek a komponenseknek az egyszerű és hatékony összekapcsolására, lehetővé téve az elosztott felhőalkalmazások globális léptékű működését.

A Google Cloud Platformon a főbb használható technológiák a következők: infrastruktúraszolgáltatások, vagyis tárhely és számítási szolgáltatások Dataproc vagy Dataflow alapon, integrációra a Cloud Functions és a Pub/Sub, valamint alkalmazásspecifikus felhőszolgáltatások, amelyek feladatspecifikus funkciókat biztosítanak.

A szolgáltatások vagy szolgáltatáskomponensek ilyen jellegű integrációját gyakran orchestrációnak nevezzük. Ez a komponensek és szolgáltatások koordinált használatára és végrehajtására utal egy összetett feladat megoldása során. Ezeket az összetett feladatokat tipikusan munkafolyamat-gráfok írják le, amelyek lazán csatolt módon hajtanak végre feldolgozási lépések sorozatát.

Ebben a fejezetben egy mintaprogramot mutatunk be, amely jól szemlélteti a felhőszolgáltatások integrációjának eleganciáját és az eddig tárgyalt különféle technológiák együttes használatát.

### 12.1 Egy összetett optikai karakterfelismerő alkalmazás példája

Az itt ismertetett program a Google Cloud Platform dokumentációjának része [17]. Az alkalmazás célja, hogy megvizsgálja a felhőbe feltöltött képeket, kinyerje belőlük a szöveges tartalmat, lefordítsa azt egy megadott nyelvre, majd az eredményt a felhő egy adott helyére mentse. Az alkalmazás munkafolyamata és architektúrája a 12-1. ábrán látható.

A végrehajtás sorrendje a következő:

`1. lépés:` egy képet feltöltünk a Google Storage-ba  
`2. lépés:` elindul egy felhőfüggvény, amely a Vision API-t hívja a kép szövegtartalmának kinyerésére  
`3. lépés:` a kinyert szöveg egy Pub/Sub témába kerül  
`4. lépés:` egy, a témaüzenet által kiváltott felhőfüggvény meghívja a Translation szolgáltatást  
`5. lépés:` a lefordított szöveges üzenetek egy Pub/Sub témába íródnak  
`6. lépés:` egy újabb felhőfüggvény elmenti az eredményt a Google Storage-ba

A fejezet további részében a fenti lépések implementációs részleteit és a program végrehajtását írjuk le.

`17`
A további részletek itt találhatók: `https://cloud.google.com/functions/docs/tutorials/ocr`

Függvény a szövegkinyeréshez

Az alábbi kódrészlet egy háttérfüggvényt valósít meg, amelyet egy Storage esemény vált ki, vagyis az `accept()` metódus hajtódik végre, és amely szövegfelismerési feladatot futtat, majd Pub/Sub üzenetet küld egy témába. Az `accept()` metódus lekéri a fájlt a Storage bucketből, majd meghívja a `detectText()` metódust. Ebben történnek a fő feldolgozási lépések. Először létrejön egy `ImageAnnotatorClient` példány, majd a szövegfelismerés a `batchAnnotateImages` metódus meghívásával hajtódik végre, ahol a bemeneti jellemzőkérés `Feature.Type.TEXT_DETECTION` értékre van állítva. Ezután a Vision API-t ismét felhasználjuk annak meghatározására, hogy a képen található szöveg milyen nyelven íródott. Ehhez létrehozunk egy `TranslationServiceClient` példányt, amelyen a `detectLanguage` metódust hívjuk meg. Utolsó lépésként minden detektált nyelvhez egy fordítási üzenet kerül közzétételre a konstruktorban létrehozott Pub/Sub közzétevő segítségével, a `publish` metódus meghívásával.

Függvény, amely képeken szöveg- és nyelvfelismerést végez:

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
private static final String LOCATION_NAME = LocationName.of(PROJECT_ID,
"global").toString();
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
logger.log(Level.SEVERE, "Error publishing translation request: " + e.getMessage(),
e);
return;
}
}
}
```

Az alkalmazás következő lépése maguknak a fordításoknak az elvégzése. Az alábbi `OcrTranslateText` osztály egy háttérfüggvényt valósít meg, amely fordítási kérésüzenetekre reagál. Az `accept` metódus minden beérkező üzenetre meghívódik. A feldolgozás első lépéseként a metódus kinyeri a forrásszöveget és a célnyelv kódját a bejövő üzenetből, majd létrehoz egy `TranslationServiceClient` példányt. Ezután létrejön a megfelelő fordítási kérésobjektum, majd a szöveg a `translateText` metódus meghívásával lefordításra kerül. A visszaadott fordított szöveget és a kimeneti fájl nevét egy új Pub/Sub üzenetbe csomagoljuk, és a konstruktorban létrehozott közzétevő `publish` metódusával elküldjük a felhőbe.

Szövegfordítást végző függvény:

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
logger.log(Level.SEVERE, "Error publishing translation save request: " +
e.getMessage(), e);
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

Az alkalmazás utolsó függvénye a fordítási eredmények Storage bucketben történő tárolásáért felel. A Storage szolgáltatás kliensére mutató referencia az osztály statikus blokkjában jön létre. Miután az `accept` metódus meghívódik, a bejövő üzenetből kiolvassuk a kimeneti fájl nevét és a nyelvi kódot, ezek összefűzésével pedig új fájlnevet állítunk elő. A lefordított szöveget ezután az új fájlba mentjük a `Storage.create` metódus meghívásával.

Függvény az eredmények Storage-ba mentéséhez:

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
logger.info("Received request to save file " +
ocrMessage.getFilename());

String newFileName = String.format(
"%s_to_%s.txt", ocrMessage.getFilename(), ocrMessage.getLang());
// Save file to RESULT_BUCKET with name newFileNaem
logger.info(String.format("Saving result to %s in bucket %s", newFileName,
RESULT_BUCKET));
BlobInfo blobInfo = BlobInfo.newBuilder(BlobId.of(RESULT_BUCKET, newFileName)).build();
STORAGE.create(blobInfo, ocrMessage.getText().getBytes(StandardCharsets.UTF_8));
logger.info("File saved");
}
}
```

Az alkalmazás befejezéséhez a fenti függvényeket telepíteni kell a felhőbe, majd létre kell hozni a bemeneti és kimeneti Storage bucketeket, valamint a Pub/Sub témákat. Ha ezek a lépések elkészültek, akkor egy képfájl feltöltése a bemeneti bucketbe kiváltja az alkalmazás teljes végrehajtását.

Ez a minta jól szemléltette a felhőszolgáltatás-orchestráció kulcsfogalmait, valamint azt az egyszerűséget és eleganciát, amellyel a szolgáltatások közötti laza csatolású üzenet- és eseménykommunikáció használható. A fejlesztőnek nem kell az infrastruktúra-kezelés részleteivel foglalkoznia, kizárólag az alkalmazáslogikára koncentrálhat. A Cloud Functions automatikus skálázási tulajdonságának köszönhetően az alkalmazás tetszőleges számú klienst képes kiszolgálni további beavatkozás nélkül.

Az érdeklődő olvasó további szolgáltatás-orchestrációs mintákért forduljon a Google Cloud dokumentációhoz.

## 13. Következtetések

Ennek a könyvnek az volt a célja, hogy háttéranyagot biztosítson a Pannon Egyetem felhőprogramozás MSc kurzusához. Ennek megfelelően nem az volt a szándéka, hogy a felhőalapú számítástechnika minden elméleti és gyakorlati aspektusát lefedő, végleges kézikönyv legyen. A kurzus fókusza a felhőrendszerek programozásán van, szemben a felhő-infrastruktúrák létrehozásával és menedzselésével, ezért a rendszerüzemeltetési témákat nagyrészt figyelmen kívül hagytuk. A cél az sem volt, hogy olyan részletességgel tárgyaljuk a programozást, amilyenre professzionális felhőfejlesztőknek szükségük lenne. Ennek ellenére remélem, hogy hasznos bevezetésként szolgál a legfontosabb fogalmakhoz, és elegendő gyakorlati programozási részletet ad ahhoz, hogy az érdeklődő hallgatók elinduljanak a felhőalapú számítástechnika rendkívül izgalmas világában.

Tudjuk, hogy a jövő soha nem jelezhető előre teljes pontossággal, de nagy biztonsággal kijelenthetjük, hogy a felhőrendszerek szerepe és képessége az elkövetkező években folyamatosan bővülni fog. Ennek fontos következményei lesznek a fejlesztők és a teljes szoftveripar számára. Ahogyan a webtechnológia jelentős hatást gyakorolt az asztali és mobilalkalmazásokra, úgy várható, hogy a felhő hasonlóan meghatározó hatással lesz a jövő szoftvereire is. Az alkalmazásoktól már ma is elvárt, hogy legalább a bemeneti és kimeneti műveletek tekintetében integrálódjanak a felhővel, hogy a felhőben tárolt adatainkat feldolgozhassuk, vagy az eredményeinket a felhőbe menthessük. A jövő alkalmazásai egyre inkább felhőszolgáltatásokra támaszkodnak majd, ami valódi, felhőszolgáltatás-komponensekből felépülő felhőalapú alkalmazásokhoz vezet.

A felhőszolgáltatók mindent megtesznek majd rendszereik rendelkezésre állásának, megbízhatóságának és biztonságának további javításáért, és várható, hogy a növekvő verseny, valamint a tiszta energia használata hosszú távon csökkenteni fogja az árakat, így a felhőrendszerek és a felhőalapú számítástechnika megfizethető és megbízható platformmá válik az emberiség számára. Több olyan tendencia is látható, amely a jövő felhőalapú számítástechnikáját még izgalmasabbá teszi, mint amilyen ma. A nagy teljesítményű számítástechnika és a mesterséges intelligencia egyaránt utat talál a felhőrendszerekbe. Várható, hogy a felhőszolgáltatók hamarosan igény szerint elérhető szuperszámítógépes erőforrásokat, valamint kifejezetten MI-terhelésekre tervezett infrastruktúrához való hozzáférést kínálnak majd. Ez platformot biztosít az innovációnak, és akár új szolgáltatások, sőt új iparágak kialakulásához is vezethet. Az Internet of Things alapú adatelemzés várhatóan forradalmasítja a gyártást és a logisztikát. Ha testszenzorokkal, valamint felhőalapú egészségügyi és diagnosztikai rendszerekkel párosul, a felhőalapú számítástechnika az egészségügyi rendszerünket is forradalmasíthatja.

Ezek csak néhány példák, vagy inkább pillanatképek voltak arról, mit hozhat a jövő a felhőalapú számítástechnikában, de azt biztosan kijelenthetjük, hogy ez a jövő fényes és izgalmas. Ne maradj le róla, figyelj továbbra is erre a területre, és légy részese a jövőnek!

## Irodalomjegyzék
