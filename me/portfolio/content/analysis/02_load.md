---
Title: 02_load
Description: This is my report page.
Template: report
sidebar: false
---

<div class="report-container">
</div>


Undersökning av prestanda och laddningstid på högskolor/universitets hemsidor
=======================

En analys av 3 olika högskolors hemsidors prestanda och användbarhet.

Urval
-----------------------

Jag valde 3 olika högskolor/universitet i södra Sverige för denna undersökning. Mina val blev Lunds Universitet, Linnéuniversitet och Blekinge tekniska högskola.

Metod
-----------------------

För att undersöka hemsidornas prestanda och användbarhet (Performance, Accessibility, Best Practice, Search Enginge Optimization) använder jag 'Google pagespeed'. Jag anväder även Google Chromes devtools (Network) för att undersöka laddningstider, antal requests och hur mycket data som hämtas (disable cache kommer vara i-bockad och jag kommer göra en hård-reload vid varje mätning). Uppenbarligen kommer en viss skillnad i hämtade resurser uppstå på vissa sidor beroende på exempelvis vilken skärmstorlek man sitter på, i detta fall är mätningar gjorda på en 14tums laptopskärm. Datan kommer sedan sammanställas med hjälp av Google Sheets.

Resultat
-----------------------

<h3> Blekinge tekniska högskola (BTH) </h3>
Bth:s hemsida hämtar ca 1.9mb data. Det som är anmärkningsvärt här är att förvånansvärt lite av datan är bilder (initialt). Hemsidan verkar hämta bilderna och andra resurser allt eftersom man scrollar ner och sedan dynamiskt fylla på sidan med content. Däremot ligger hemsidans laddningstid ganska högt, ca 2.3 sekunder (statistik finns i excelarket längre ner).
<picture>
    <img src="%base_url%/image/bthreport.png?w=40%" alt="bth hemsida">
</picture>

<h3>    Lunds Universitet (LU) </h3>
En tydlig skillnad som utmärker Lunds universitet hemsida är att sidan laddar in många stora bilder (ganska jämt fördelat jpeg och png). Den största bilden är 1.2mb och sedan finns 9 andra bilder som också tillhör dem största resurserna som laddas in. En grov uppskattning är att ca 80% av det som hämtas är bilder i olika storlekar. Dem totala resurserna som hämtas från sidan är ca 6mb (statistik finns i excelarket längre ner).
<picture>
    <img src="%base_url%/image/lundreport.png?w=40%" alt="lund universitet hemsida">
</picture>
<h3>Linnéuniversitetet (LNU)</h3>
Linnéuniversitets hemsida får bäst resultat i majoriteten av testerna som utförts. Notera att laddningstiderna för denna hemsida är ca 2-3 gånger snabbare än dem andra två hemsidorna. Sidan hämtar initialt relativt lite data och uppdaterar sedan dynamiskt sidan allt eftersom man scrollar ner(desktop)(statistik finns i excelarket längre ner). 
<picture>
    <img src="%base_url%/image/linnereport.png?w=40%" alt="linné universitet hemsida">
</picture>

<h2>Statistik</h2>
<iframe title="statistics fram" class="excel-load-data" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vToga3hX3zBEUV3epSZU6gLKLye4WddU4cXy0KzVy85QiWKGUqTBThT0dWMtXCcjCL-iEioCwmuSE5x/pubhtml?widget=true&amp;headers=false"></iframe>
<br>
<h3>Sammanfattning och vinnare</h3>
Vinnare på i princip alla test är LNU då dem lyckats hålla storleken och laddningstiden på hemsidan nere utan att kompromissa på det första intryck en besökare får. På andraplats hamnar BTH:s hemsida då dem lyckats ganska väl med att hålla nere storleken på sidan men däremot faller sidan ganska hårt på dem långa laddningstiderna. På sista plats hamnar LU:s hemsida. Dem har lyckats hålla ner laddningstiderna vilket såklart är ett stort plus. Men den största anledningen till att dem hamnar på sista plats är att sidan är väldigt stor jämfört med BTH/LNU samt riskerar sidan att ladda in onödiga resurser vid besök. Den stora mängden data som sidan(LU) skickar går emot dagens energiklimat där man bör minska sin förbrukning där det går och dem har både möjlighet att komprimera bilder samt undvika att skicka orelevant data.  

Analys
-----------------------

Det som ansvarar för mycket trafik mellan webbläsaren och servern verkar, till stor del, vara bilder. Det märks att både BTH och LNU hemsidor är anpassade för att inte hämnta mer data än nödvändigt. Med det syftar jag till att det dem båda sidorna har gemensamt är att båda laddar in den data som behövs för att visa hemsidans 'above the fold' på aktuell skärm. Scrollar man sedan nedåt på sidan så uppdateras mängden data i transfer-delen på devtools(chrome). Ett förtydligande, står jag längst upp på BTH:s hemsida så laddas, i mitt fall, endast 2 jpeg-filer in. Men så fort jag börjar scrolla ner så fylls datan på och b.l.a flera jpeg-filer laddas in. 

I detta avseende skiljer sig LU från tidigare nämnda. LU:s hemsida hämtar omedelbart sina ca 6mb. I dessa 6mb så inkluderas en mängd olika stora bilder varav den största är 1.2mb, alltså är en enda bild nästan lika stor som hela LNU:s hemsida. Jag uppskattar att ca 80% av den data som laddas in på LU:s hemsida är någon form av bild. Det leder till att oehört mycket onödigt trafik flyttas varje gång någon besöker hemsidan. Hade LU:s hemsida också designats (likt BTH och LNU) för att dynamiskt uppdatera sig i takt med att användaren scrollar ner så hade man minst kunnat (beroende på skrämstorlek) halvera mängden initial data som skickas. Dem flesta normalstora skärmar (24-inch eller valfri vanlig laptop-skärm) ser endast den översta bilden (ej inkluderat favikoner samt andra 'meny-liknande' bilder som kan finnas längst upp på startsidan) på hemsidan vid första ankomst. Denna bild är dessutom inte ens den största bilden och användaren behöver scrolla en bra bit innan man sett alla/andra bilder. Ser man detta ur ett hållbarhetsperspektiv så skickas mycket data i onödan varje gång någon besöker hemsidan. Det känns även rimligt att anta att långt ifrån alla besökare faktiskt scrollar hela vägen ner på hemsidan för att ta del av allt material då majoriteten av alla intressanta och nödvändiga länkar bör ligga så tillgängligt som möjligt, förslagvis längst upp på sidan i en navbar eller likvärdigt. <br>
Om vi föreställer oss att detta antagande är sant så kan vi snabbt göra en enkel räkneövning som visar hur mycket överflödig data som skickas varje gång någon besöker hemsidan gentemot hur mycket data som faktiskt behövs för att ge besökaren ett trevligt välkomnande. Om det går 0.5kWh per 1GB[1] och vi utgår ifrån mitt påstående om att hälften av datan som skickas på LU:s hemsida hade kunnat sparas in, så innebär det att 1Gb (1024Mb ca 1000Mb ) delat på hälften av sidans data (3mb) är ungefär lika med 333. Det innebär att ca var 333:e unika/o-cachade besök på LU:s hemsida så går det åt ca 0.5kWh till att hämta data som, troligen, inte behövs. Detta exempel ska endast ses ett räkneexempel/ögonöppnare grundat ur rimliga, teoretiska antaganden baserat på jämförelsen mellan hur mycket data BTH/LNU:s och LU:s hemsidor hämtar initialt och vid fortsatt scrollande. <br><br>

Enligt testet på LU:s hemsida som gjordes med Google pagespeed beräknas man kunna spara in ännu mer datatrafik på just bilder än mitt tidigare exempel genom att anpassa storleken på bilder och använda sig av mer moderna filformat, så som webP eller AVIF istället för png och jpeg.
<picture>
    <img src="%base_url%/image/lupicsizesave.png?w=80%" alt="LU savings">
</picture>
<br>
Mycket tyder på att den mest resultatgivande förbättringen LU:s hemsida kan genomgå är just bildhantering samt se över om det faktiskt är nödvändigt att ladda in bilder som inte inte tillhör (och i vissa fall ligger långt under) "above the fold" innnan man laddat in den bild som faktiskt syns överst på sidan. I bilden under är den bild som visas på 'above the fold' (på LU:s hemsida) den som är blåmarkerad och vi kan tydligt se att det är en av bilderna som laddas in sist bland axplocket på bilden, vilket såklart bidrar till onödig väntetid samt att dem användare som bara vill klicka sig vidare till sin eftersökta del på hemsidan tvingas hämta all onödig information bara för att kunna klicka sig vidare.
LU:s hemsida lyckas dock oavsett hålla en ganska acceptabel laddningstid, i detta avseende anser jag att allt under 2 sekunder är acceptabelt. 
<picture>
    <img src="%base_url%/image/lujpegloadorder.png?w=52%" alt="lu load order">
</picture> 
<br>
BTH:s sida ligger på över två sekunders laddtid men här verkar inte bilder vara boven utan snarare serverrelaterade problem så som att responstiden kan vara lång, rimligtvis kan det vara olika flaskhalsar som hindrar sidan från att ladda in optimalt. Områden som kan förbättras enligt BTH:s Page speedtest (destop och mobil) är tidigare nämnda responstid från servern, render-blockerande resurser (typ statiska filer som HTML, CSS och fonter) där troligtvis inte alla filer är nödvändiga för sidans så kallade "First meaningful paint (när man ser vad det faktiskt ska bli)" samt att reducera oanvänd JavaScript. BTH lyckas dock, i jämförelse med LU, ganska bra med att inte belasta användarens upplevelse med onödiga resurser men faller istället på att sidan är och upplevs långsam (laddningstider) att använda. <br><br>

LNU:s hemsida lyckas generellt bra på alla testerna. Sidan lyckas genomsnittligt med att hålla en laddningstid under 1 sekund vilket upplevs snabbt och levande. Även storleken på LNU:s hemsida är mindre jämfört med BTH/LU trots att dem har en hero-bild. Sidan verkar också, likt BTH:s hemsida, uppdateras dynamisk och undviker att ladda in resurser som inte tillhör eller är nära nog 'above the fold'. Allt eftersom man scrollar ner på LNU så laddas bilder och resurser in i takt med att man scrollar. Det ger få förbättringsförslag från PageSpeed varav det huvudsakliga är att använda moderna filformat för bilder, alltså WebP och AVIF istället för PNG och JPEG.

-----------------------

Referenser:
1. https://youtu.be/CRR51p3HVos?list=PLKtP9l5q3ce_j6UiS_djpsbwBolxz8WZ8&t=3849 (2023-01-10)

Övrigt
-----------------------

Skrivet av Emil Karlsson
