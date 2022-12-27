---
Title: Load
Description: Report about color analysis
Template: report
---

Utvärdering av webbplatsers laddningstid och användarbarhet
=======================

I denna rapport kommer inladdningstiden att analyseras för tre stycken webbplatser och utifrån det ta fram eventuella förbättringar.

Urval
-----------------------

Webbplatserna som har valts att analyseras är baserat på mest besökta hemsidorna i Sverige under November 2022 enligt similarweb.com.[^1]
Medvetet har de tre första webbsidorna valts bort, google.com, youtube.com och facebook.com.

De tre valda webbsidorna:
-aftonbladet.se
-expressen.se
-wikipedia.org

Metod
-----------------------

Mätningarna utförs i bland annat nätverksfliken i Google Chromes devtools men även med hjälp utav webbsidan PageSpeed Insights.[^2]
Berätta kort om din "metod", hur du gör för att utföra undersökningen. Berätta om du använder något speciellt verktyg.

Resultat
-----------------------

Nedan syns bilder tagna från de valda hemsidorna tillsammans med bild från mätningarna utförda med hjälp utav PageSpeed Insight.

#### Aftonbladet

<figure>
    <img src="%base_url%/assets/img/rapport/load/aftonbladet.JPG" alt="Aftonsbladets hemsida">
    <figcaption>Figur 1. Snapshot Aftonbladets hemsida.</figcaption>
</figure>

Vid test av viktiga webbvärden för dator får Aftonbladet inte godkänt enligt PageSpeed Insight.
Det är bland annat webbvärdena Cumulative Layout Shift (CLS) och Largest Contentful Paint (LCP) som sticker ut, se figur 2. CLS är ett mätvärde för hur mycket en webbsida oväntat förändras när användaren har den öppen, exempelvis banners/reklam/annonser som plötsligt laddas in. Ett godkänt CLS värde ligger under 0,1. Mellan 0,1 och 0,25 krävs förbättring. [^3]
LCP är ett mätvärde för när huvudinnehållet på webbsidan har laddats in, LCP-värde under 2,5 sekunder anses vara godkänt enligt web.dev. [^4]

<figure>
    <img src="%base_url%/assets/img/rapport/load/aftonbladet_dator.JPG" alt="Aftonbladet pagespeed dator">
    <figcaption>Figur 2. Aftonbladet PageSpeedmätning för dator</figcaption>
</figure>

I figur 3 presenteras samma test men för mobila enheter och även där får Aftonbladet inte godkänt, bland annat LCP och CLS som sticker ut men även Interaction to Next Paint (INP) som är ett mått för responsivitet där ett värde under 200ms anses vara godkänt. [^5]

<figure>
    <img src="%base_url%/assets/img/rapport/load/aftonbladet_mobil.JPG" alt="Aftonbladet pagespeed mobilt">
    <figcaption>Figur 3. Aftonbladet PageSpeedmätning för mobilt</figcaption>
</figure>


#### Expressen

<figure>
    <img src="%base_url%/assets/img/rapport/load/expressen.JPG" alt="Expressens hemsida">
    <figcaption>Figur 4. Snapshot Expressens hemsida.</figcaption>
</figure>

Som vi kan se i figur 5 så går Expressen igenom testet av viktiga webbvärden, det är tillgängligheten som kan förbättras där bland annat bildelementen saknas alt-attribut samt att vissa länkar saknar ett igenkännligt namn.

<figure>
    <img src="%base_url%/assets/img/rapport/load/expressen_dator.JPG" alt="Expressen pagespeed dator">
    <figcaption>Figur 5. Expressen PageSpeedmätning dator.</figcaption>
</figure>

Även för mobila enheter går Expressen igenom testet, se figur 6. För mobila enheter är tillgängligheten bättre men prestandan försämras, det är främst Total Blocking Time (TBT) som drar ner prestandan då det värdet ligger på 880 ms.
TBT är den tid webbsidan är blockerad från att användaren ska kunna intergrera med den. [^6]

<figure>
    <img src="%base_url%/assets/img/rapport/load/expressen_mobil.JPG" alt="Expressen pagespeed mobilt">
    <figcaption>Figur 6. Expressen PageSpeedmätning mobilt.</figcaption>
</figure>


#### Wikipedia

<figure>
    <img src="%base_url%/assets/img/rapport/load/wikipedia.JPG" alt="Wikipedias hemsida">
    <figcaption>Figur 7. Snapshot Wikipedias hemsida.</figcaption>
</figure>

Enligt figur 8 går Wikipedia igenom PageSpeed Insights test av viktiga webbvärden utan problem, det som möjligtvis drar ner betyget är tillgängligheten som kan vara bättre.

<figure>
    <img src="%base_url%/assets/img/rapport/load/wikipedia_dator.JPG" alt="Wikipedia pagespeed dator">
    <figcaption>Figur 8. Wikipedia PageSpeedmätning dator.</figcaption>
</figure>

Mobila enheter har liknande resultat som dator-enhet när testet utförs och även för mobila enheter är det tillgängligheten som drar ner betyget på grund av att alla ARIA-id:n inte är unika

<figure>
    <img src="%base_url%/assets/img/rapport/load/wikipedia_mobil.JPG" alt="Wikipedia pagespeed mobilt">
    <figcaption>Figur 9. Wikipedia PageSpeedmätning mobilt.</figcaption>
</figure>

#### Sammanställd mätning

Nedan är en tabell med mätningar utförda med Google Chromes DevTools samt PageSpeed Insight.
<iframe class="measure" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT_GB6FIp_Oe_RQi8E9bB0tfycVr3t3eWHThsyyr7vcUIiJySm-lulHh_OEclNdkvrKW0XLaDtBuZ16/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false" title="Webbplatsmätning" width="900" height="450"></iframe>

Eventuell justering för att förbättra prestandan på Aftonbladet och Expressen kan vara att minimera eller ta bort JavaScript som inte används medans Wikipedia kan minimera sitt DOM-träd.

Analys
-----------------------

Kikar vi på prestandan för respektive hemsida är Wikipedia en vinnare medans nyhetssajterna Aftonbladet och Expressen ligger efter.
Både Aftonbladet och Expressen innehåller väldigt mycket mer än bara nyheter, det finns en del reklam och annonser som behöver laddas in och förbättringar för dessa webbsidor är att reducera den JavaScript och CSS som inte används. Wikipedia innehåller ingen reklam då hemsidan inte bygger på reklamintäkter utan utvecklas av frivilliga bidragsgivare men också frivilliga donationer.
Anledningen till att just Aftonbladet och Expressen får förbättringsåtgärder att reducera JavaScript kan vara att man använder sig av JavaScript för att bland annat visualisera reklam och annonser.

Utifrån mätvärdena enligt PageSpeed Insight ser rangordningen ut så här:

1. Wikipedia
2. Expressen
3. Aftonbladet

Wikipedia håller hög prestanda och tillgänglighet på både mobila enheter och via dator jämfört med Expressen och Aftonbladet. Aftonbladet har något bättre tillgänglighet än Expressen men prestandamässigt är Expressen betygsatt mycket bättre än Aftonbladet och därav hamnar Expressen före Aftonbladet.

I mätningar har "läs in" tiden tagits för respektive webbplats, detta för att det ständigt skickas responser via Aftonbladet och Expressen så den totala tiden är flera minuter och fortsätter att öka ju längre webbplatsen är öppen.

En absolut laddningstid som är acceptabel i dagens samhälle med någorlunda snabb hastighet på närverkat för att inte tappa trafik bör ligga runt 3 sekunder enligt mig.
Enligt testerna är det endast Wikipedia som klarar av detta då de två andra nyhetssajterna ständigt löser förfrågningar/response så den slutgiltiga laddningstiden enligt devtools blir flera minuter.

Övrigt
-----------------------

Medlemmar:
Adam Franzén, adfb14

Referenser
-----------------------
[^1]: https://www.similarweb.com/top-sites/sweden/ (Besökt 2022-12-25)
[^2]: https://pagespeed.web.dev/ (Besökt 2022-12-25)
[^3]: https://web.dev/cls/ (Besökt 2022-12-27)
[^4]: https://web.dev/lcp/ (Besökt 2022-12-27)
[^5]: https://web.dev/inp/ (Besökt 2022-12-27)
[^6]: https://gtmetrix.com/total-blocking-time.html (Besökt 2022-12-27)