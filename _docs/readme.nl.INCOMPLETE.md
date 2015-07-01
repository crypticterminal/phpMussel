## Documentatie voor phpMussel (Nederlandse).

### Inhoud
- 1. [PREAMBULE](#SECTION1)
- 2A. [HOE TE INSTALLEREN (VOOR WEBSERVERS)](#SECTION2A)
- 2B. [HOE TE INSTALLEREN (VOOR CLI)](#SECTION2B)
- 3A. [HOE TE GEBRUIKEN (VOOR WEBSERVERS)](#SECTION3A)
- 3B. [HOE TE GEBRUIKEN (VOOR CLI)](#SECTION3B)
- 4A. [BROWSER RICHTLIJNEN](#SECTION4A)
- 4B. [CLI (COMMANDLIJN INTERFACE)](#SECTION4B)
- 5. [BESTANDEN IN DIT PAKKET](#SECTION5)
- 6. [CONFIGURATIEOPTIES](#SECTION6)
- 7. [HANDTEKENINGFORMAAT](#SECTION7)
- 8. [BEKENDE COMPATIBILITEITSPROBLEMEN](#SECTION8)

---


###1. <a name="SECTION1"></a>PREAMBULE

Bedankt voor het gebruik van phpMussel, een PHP script ontworpen om detecteren trojans, virussen, malware en andere bedreigingen binnen bestanden geüpload naar uw systeem waar het script is aangesloten, gebaseerd op ClamAV handtekeningen en anderen.

PHPMUSSEL COPYRIGHT 2013 en verder GNU/GPLv2 van Caleb M (Maikuolan).

Dit script is vrije software; je kan herdistribueren en/of wijzigen dit onder de voorwaarden van de GNU General Public License zoals gepubliceerd door de Free Software Foundation; ofwel versie 2 van de Licentie, of (naar uw keuze) enige latere versie. Dit script wordt gedistribueerd in de hoop dat het zal zijn nuttig, maar ZONDER ENIGE GARANTIE; zonder zelfs de impliciete garantie van VERKOOPBAARHEID of GESCHIKTHEID VOOR EEN BEPAALD DOEL. Zie de GNU General Public License voor meer details, gelegen in de "LICENCE" bestand in de `_docs` bestandsmap van de bijbehorende pakket en repository voor deze bestanden en ook beschikbaar uit:
- <http://www.gnu.org/licenses/>.
- <http://opensource.org/licenses/>.

Speciale dank aan [ClamAV](http://www.clamav.net/) voor zowel project inspiratie en voor de handtekeningen dat dit script maakt gebruik daarvan, zonder welke, het script zou waarschijnlijk niet bestaan, of op zijn best, zou zeer beperkte waarde.

Speciale dank aan Sourceforge en GitHub voor het hosten van de project-bestanden, ann [Spambot Security](http://www.spambotsecurity.com/forum/viewforum.php?f=55) voor het hosten van de phpMussel discussies forums, en de extra bronnen van een aantal handtekeningen gebruikt door phpMussel: [SecuriteInfo.com](http://www.securiteinfo.com/), [PhishTank](http://www.phishtank.com/), [NLNetLabs](http://nlnetlabs.nl/) en anderen, en speciale dank aan allen die het project steunen, aan iemand anders die ik anders misschien vergeten te vermelden, en voor u, voor het gebruik van het script.

Dit document en de bijbehorende pakket kan worden gedownload voor gratis van:
- [Sourceforge](http://phpmussel.sourceforge.net/).
- [GitHub](https://github.com/Maikuolan/phpMussel/).

---


###2A. <a name="SECTION2A"></a>HOE TE INSTALLEREN (VOOR WEBSERVERS)

Ik hoop te stroomlijnen dit proces door maken een installateur op een bepaald punt in de niet al te verre toekomst, maar tot die tijd, volg deze instructies te werken phpMussel om meeste systemen en CMS:

1) Door je dit leest, ben ik ervan uit u al een gearchiveerde kopie van het script gedownload, uitgepakt zijn inhoud en hebben het ergens op uw lokale computer. Vanaf hier, je nodig hebt om bepalen waar op uw host of CMS die inhoud te plaatsen. Een bestandsmap zoals `/public_html/phpmussel/` of soortgelijk (hoewel, het maakt niet uit welke je kiest, zolang het is iets veilig en iets waar je blij mee bent) zal volstaan. *Voordat u het uploaden begint, lees verder..*

2) Open `phpmussel.php`, zoek naar de lijn die begint met `$vault=`, en vervang de string tussen de volgende aanhalingstekens op die lijn met de exacte ware locatie van de "gewelf" bestandsmap van phpMussel. U zult hebben gemerkt zo'n bestandsmap in het archief zou je hebt gedownload (tenzij je zin om opnieuw coderen van de hele script jezelf, je nodig hebt om dezelfde bestanden en bestandsmap structuur te behouden zoals het was in het archief oorspronkelijk). Deze bestandsmap `vault` moet men bestandsmap niveau waarboven de bestandsmap die de `phpmussel.php` bestand zal bestaan in zijn. Bestand opslaan, sluiten.

4) (Facultatief; Sterk aanbevolen voor ervaren gebruikers, maar niet aan te raden voor beginners of voor de onervaren): Open `phpmussel.ini` (gelegen binnen `vault`) - Dit bestand bevat alle beschikbare phpMussel configuratie opties. Boven elke optie moet een korte opmerking te beschrijven wat het doet en wat het voor. Pas deze opties als het je past, volgens welke geschikt is voor uw configuratie. Sla het bestand, sluiten.

4) Upload de inhoud (phpMussel en zijn bestanden) naar de bestandsmap die u zou op eerder besloten (je nodig niet de `*.txt`/`*.md` bestanden opgenomen, maar meestal, je moeten uploaden alles).

5) CMHOD de bestandsmap `vault` naar "777". De belangrijkste bestandsmap opslaan van de inhoud (degene die je eerder koos), gewoonlijk, kan worden genegeerd, maar CHMOD-status moet worden gecontroleerd als u machtigingen problemen hebt gehad in het verleden op uw systeem (standaard, moet iets zijn als "755").

6) Volgende, je nodig hebt om "haak" phpMussel om uw systeem of CMS. Er zijn verschillende manieren waarop je kunt "haak" scripts zoals phpMussel om uw systeem of CMS, maar het makkelijkste is om gewoon omvatten voor het script aan het begin van een kern bestand van uw systeem of CMS (een die het algemeen altijd zal worden geladen wanneer iemand heeft toegang tot een pagina in uw website) met behulp van een require() of include() opdracht. Meestal is dit wel iets worden opgeslagen in een bestandsmap zoals `/includes`, `/assets` of `/functions`, en zal vaak zijn vernoemd iets als `init.php`, `common_functions.php`, `functions.php` of soortgelijk. Je nodig hebt om te bepalen welk bestand dit is voor uw situatie; Als je problemen ondervindt in het werken dit uit voor jezelf, bezoek de phpMussel support forums en laat het ons weten; Het is mogelijk dat ofwel mijzelf of een andere gebruiker kan ervaring met de CMS die u gebruikt hebt (je nodig hebt om ons te laten weten welke CMS u gebruikt), en dus, in staat zijn om wat hulp te bieden in dit gebied. Om dit te doen [te gebruiken require() of include()], plaatst u de volgende regel code aan het begin op die kern bestand, vervangen van de string die binnen de aanhalingstekens met het exacte adres van het `phpmussel.php` bestand (lokaal adres, niet het HTTP-adres; zal vergelijkbaar zijn met de eerder genoemde vault adres).

`<?php require("/user_name/public_html/phpmussel/phpmussel.php"); ?>`

Opslaan bestand, sluiten, heruploaden.

-- OF ALTERNATIEF --

Als u gebruik een Apache webserver en als je toegang hebt `php.ini`, u kunt gebruiken de `auto_prepend_file` richtlijn naar prepend phpMussel wanneer een PHP verzoek wordt gemaakt. Zoiets als:

`auto_prepend_file = "/user_name/public_html/phpmussel/phpmussel.php"`

Of dit in het `.htaccess` bestand:

`php_value auto_prepend_file "/user_name/public_html/phpmussel/phpmussel.php"`

7) Op dit punt, je bent klaar! Echter, je moet waarschijnlijk test het uit om ervoor te zorgen dat het werken correct. Voor het testen van het bestand upload protecties, proberen om de testen bestanden te uploaden opgenomen in het pakket als `_testfiles` naar uw website via uw gebruikelijke browser-gebaseerde uploaden methoden. Wanneer alles werkt, verschijnt er een bericht uit phpMussel bevestigen dat de upload met succes werd geblokkeerd. Wanneer er niets, is er iets niet correct werkt. Als je met behulp van een geavanceerde functies of als je met behulp van de andere types van het scannen mogelijk met het gereedschap, ik stel het uit te proberen met die ervoor zorgen dat het werkt zoals verwacht, ook.

---


###2B. <a name="SECTION2B"></a>HOE TE INSTALLEREN (VOOR CLI)

Ik hoop te stroomlijnen dit proces door maken een installateur op een bepaald punt in de niet al te verre toekomst, maar tot die tijd, volg deze instructies te werken phpMussel met CLI (beseffen dat op dit moment, CLI is alleen bekend om te werken met Windows-gebaseerde systemen; Linux en andere systemen zal binnenkort komen tot een latere versie van phpMussel):

1) Door je dit leest, ben ik ervan uit u al een gearchiveerde kopie van het script gedownload, uitgepakt zijn inhoud en hebben het ergens op uw lokale computer. Wanneer je hebt beslist dat je bent tevreden met de gekozen phpMussel locatie, voortzetten.

2) phpMussel vereist van php moet worden geïnstalleerd op de host machine om uit te werken correct. Als je niet php hebt geïnstalleerd op uw machine, installeer php op uw machine, volgende instructies door de php installateur geleverd.

3) Open `phpmussel.php`, zoek naar de lijn die begint met `$vault=`, en vervang de string tussen de volgende aanhalingstekens op die lijn met de exacte ware locatie van de "gewelf" bestandsmap van phpMussel. U zult hebben gemerkt zo'n bestandsmap in het archief zou je hebt gedownload (tenzij je zin om opnieuw coderen van de hele script jezelf, je nodig hebt om dezelfde bestanden en bestandsmap structuur te behouden zoals het was in het archief oorspronkelijk). Deze bestandsmap `vault` moet men bestandsmap niveau waarboven de bestandsmap die de `phpmussel.php` bestand zal bestaan in zijn. Bestand opslaan, sluiten.

4) (Facultatief; Sterk aanbevolen voor ervaren gebruikers, maar niet aan te raden voor beginners of voor de onervaren): Open `phpmussel.ini` (gelegen binnen `vault`) - Dit bestand bevat alle beschikbare phpMussel configuratie opties. Boven elke optie moet een korte opmerking te beschrijven wat het doet en wat het voor. Pas deze opties als het je past, volgens welke geschikt is voor uw configuratie. Sla het bestand, sluiten.

5) (Facultatief) U kunt maken te phpMussel in CLI-modus makkelijker voor jezelf door het creëren van een batch-bestand om automatisch te laden php en phpMussel. Om dit te doen, open een platte tekst editor zoals Notepad of Notepad++, typt u het volledige pad naar de `php.exe` bestand in de bestandsmap van uw php-installatie, gevolgd door een spatie, gevolgd door het volledige pad naar de `phpmussel.php` bestand in de bestandsmap van uw phpMussel installatie, Sla het bestand op met een ".bat" extensie ergens dat je het gemakkelijk vinden, en dubbelklik op het bestand om phpMussel draaien in de toekomst.

6) Op dit punt, je bent klaar! Echter, je moet waarschijnlijk test het uit om ervoor te zorgen dat het werken correct. Om phpMussel testen, draaien phpMussel en probeer het scannen van de `_testfiles` bestandsmap die bij het pakket.

---


###3A. <a name="SECTION3A"></a>HOE TE GEBRUIKEN (VOOR WEBSERVERS)

phpMussel is bedoeld te zijn een script dat zal adequaat functioneren direct uit de doos met een minimum niveau van de eisen van uw kant: Eenmaal geïnstalleerd, in principe, het gewoon moeten werken.

Het scannen van het bestanden uploaden is geautomatiseerd en ingeschakeld door standaard, zo niets is vereist op namens u voor deze specifieke functie.

Echter, je bent ook in staat om te instrueren phpMussel om te scannen naar bestanden, bestandsmappen of archieven dat je impliciet aangeven. Om dit te doen, ten eerste, moet u ervoor zorgen dat de juiste configuratie is ingesteld in het `phpmussel.ini` configuratiebestand (cleanup moet worden uitgeschakeld), en als je klaar bent, in een php-bestand dat wordt gehaakt op phpMussel, gebruik de volgende functie in uw code:

`phpMussel($what_to_scan,$output_type,$output_flatness);`

Waar:
- `$what_to_scan` is ofwel een string of een array, wijzen ofwel naar een doelgerichte bestand, een doelgerichte bestandsmap of een array op doelgerichte bestanden en/of doelgerichte bestandsmappen.
- `$output_type` is een integer, met vermelding van het formaat waarin de resultaten van de scan zijn om terug te keren als. Een waarde van 0 instrueert de functie om de resultaten terug te keren als een integer (een geretourneerd gevolg van -2 geeft aan dat corrupte data tijdens de scan werd gedetecteerd en dus de scan niet voltooid, -1 geeft aan dat uitbreidingen of toevoegingen vereist door php om de scan uit te voeren ontbraken en dus de scan niet voltooid, 0 geeft aan dat de scan doelgroep bestaat niet en dus was er niets te scannen, 1 geeft aan dat de doelwit met succes werd gescand geen problemen waren gedetecteerd, en 2 geeft aan dat de doelwit met succes werd gescand en problemen waren gedetecteerd). Een waarde van 1 instrueert de functie om de resultaten als mensen leesbare tekst. Een waarde van 2 beide instrueert de functie om de resultaten als mensen leesbare tekst en om de resultaten te exporteren een globale variabele. Deze variabele is optioneel, en is 0 door standaard.
- `$output_flatness` is een integer, aangeeft of er kunnen resultaten worden geretourneerd als een matrix of niet. Doorgaans, als de scan doel bevatte meerdere items (bijvoorbeeld als een directory of matrix) het resultaten zal worden geretourneerd in een array (standaard waarde van 0). Een waarde van 1 instrueert de functie te imploderen dergelijke matrix vóór ingang, resulterend in platte tekenreeks waarin de resultaten worden geretourneerd. Deze variabele is optioneel, en is 0 door standaard.

Voorbeelden:

`$results=phpMussel("/user_name/public_html/my_file.html",1,1);
echo $results;`

Retourneren iets als dit (als een string):

`Wed, 16 Sep 2013 02:49:46 +0000 Started.`

`> Verifiëren '/user_name/public_html/my_file.html':`

`-> Geen problemen gevonden.`

`Wed, 16 Sep 2013 02:49:47 +0000 Afgewerkt.`

Voor een volledige beschrijving van de soorten van de handtekeningen gebruikt door phpMussel tijdens de scans en hoe het omgaat met deze handtekeningen, raadpleeg de Handtekeningformaat sectie van dit README bestand.

Als u tegenkomen enig valse positieven, als u tegenkomen iets nieuws dat je denkt dat zou moeten worden geblokkeerd, of voor iets anders met betrekking tot handtekeningen, contact met mij over zodat ik kunnen maken veranderingen, die, als je geen contact met mij op, ik niet noodzakelijkerwijs weten over.

Om de handtekeningen die bij phpMussel uitschakelen (zoals als je het ervaren van een vals positief specifiek voor uw doeleinden dat mag niet normaal van Streamline worden verwijderd), verwijzen naar de Greylisting aantekeningen binnen de Browser Commando sectie van dit README bestand.

In aanvulling op de standaard bestand uploaden scannen en de optionele scannen van andere bestanden en/of directories opgegeven via de bovenstaande functie, in phpMussel een functie bestemd voor het scannen van het lichaam van emailberichten. This function behaves similarly to the standard phpMussel() function, but focuses solely on matching against the ClamAV email-based signatures. I have not tied these signatures into the standard phpMussel() function, because it is highly unlikely that you'd ever find the body of an incoming email message in need of scanning within a file upload targeted to a page where phpMussel is hooked, and thus, to tie these signatures into the phpMussel() function would be redundant. However, that said, having a separate function to match against these signatures could prove to be extremely useful for some, especially for those whose CMS or webfront system is somehow tied into their email system and for those parsing their emails via a php script that they could potentially hook into phpMussel. Configuration for this function, like all others, is controlled via the `phpmussel.ini` file. To use this function (you'll need to do your own implementation), in a php file that is hooked to phpMussel, use the following function in your code:

`phpMussel_mail($body);`

Where $body is body of the email message you wish to scan (additionally, you could try scanning new forum posts, inbound messages from your online contact form or similar). If any error occurs preventing the function from completing its scan, a value of -1 will be returned. If the function completes its scan and does not match anything, a value of 0 will be returned (meaning clean). If, however, the function does match something, a string will be returned containing a message declaring what it has matched.

In addition to the above, if you look at the source code, you may notice the function phpMusselD() and phpMusselR(). These functions are sub-functions of phpMussel(), and should not be called directly outside of that parent function (not because of adverse effects.. More-so, simply because it'd serve no purpose, and most probably won't actually work correctly anyhow).

There are many other controls and functions available within phpMussel for your use, too. For any such controls and functions which, by the end of this section of the README, have not yet been documented, please continue reading and refer to the Browser Commands section of this README file.

---


###3B. <a name="SECTION3B"></a>HOE TE GEBRUIKEN (VOOR CLI)

Raadpleeg de "HOE TE INSTALLEREN (VOOR CLI)" sectie van dit README bestand.

Gelieve bewust te zijn, hoewel toekomstige versies van phpMussel andere systemen moet ondersteunen, momenteel, phpMussel CLI-modus ondersteuning is alleen geoptimaliseerd voor gebruik op Windows gebaseerde systemen (U kunt, natuurlijk, probeer het op andere systemen, maar ik kan niet garanderen dat het zal werken zoals bedoeld).

Also be aware that phpMussel is not the functional equivalent of a complete anti-virus suite, and unlike conventional anti-virus suites, does not monitor active memory or detect viruses on-the-fly! It will only detect viruses contained by those specific files that you explicitly tell it to scan.

---


###4A. <a name="SECTION4A"></a>BROWSER RICHTLIJNEN

Once phpMussel has been installed and is correctly functioning on your system, if you've set the script_password and logs_password variables in your configuration file, you will be able to perform some limited number of administrative functions and input some number of commands to phpMussel via your browser. The reason these passwords need to be set in order to enable these browser-side controls is both to ensure proper security, proper protection of these browser-side controls and to ensure that there exists a way for these browser-side controls to be entirely disabled if they are not desired by you and/or other webmasters/administrators using phpMussel. So, in other words, to enable these controls, set a pasword, and to disable these controls, set no password. Alternatively, if you choose to enable these controls and then choose to disable these controls at a later date, there is a command to do this (such can be useful if you perform some actions that you feel could potentially compromise the delegated passwords and need to quickly disable these controls without modifying your configuration file).

A couple of reasons why you _**SHOULD**_ enable these controls:
- Provides a way to greylist signatures on-the-fly in instances such as when you discover a signature that is producing a false-positive while uploading files to your system and you don't have time to manually edit and reupload your greylist file.
- Provides a way for you to allow someone other than yourself to control your copy of phpMussel without the implicit need to grant them access to FTP.
- Provides a way to provide controlled access to your log files.
- Provides an easy way to update phpMussel when updates are available.
- Provides a way for you to monitor phpMussel when FTP access or other conventional access points for monitoring phpMussel are not available.

A couple of reasons why you should _**NOT**_ enable these controls:
- Provides a vector for potential attackers and undesirables to determine whether you are using phpMussel or not (although, this could be both a reason for and a reason against, depending on perspective) by way of blindly sending commands to servers as a means to probe. On one hand, this could discourage attackers from targeting your system if they learn that you are using phpMussel, assuming that they are probing because their attack method is rendered ineffective as a result of using phpMussel. However, on the other hand, if some unforeseen and currently unknown exploit within phpMussel or a future version thereof comes to light, and if it could potentially provide an attack vector, a positive result from such probing could actually encourage attackers to target your system.
- If your delegated passwords were ever compromised, unless changed, could provide a way for an attacker to bypass whatever signatures may be otherwise normally preventing their attacks from succeeding, or even potentially disable phpMussel altogether, thus providing a way to render the effectiveness of phpMussel moot.

Either way, regardless of what you choose, the choice is ultimately yours. By default, these controls will be disabled, but have a think about it, and if you decide you want them, this section explains both how to enable them and how to use them.

A list of available browser-side commands:

scan_log
- Password required: logs_password
- Other requirements: scan_log must be set.
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?logspword=[logs_password]&phpmussel=scan_log`
- What it does: Prints the contents of your scan_log file to the screen.

scan_kills
- Password required: logs_password
- Other requirements: scan_kills must be set.
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?logspword=[logs_password]&phpmussel=scan_kills`
- What it does: Prints the contents of your scan_kills file to the screen.

controls_lockout
- Password required: logs_password OR script_password
- Other requirements: (none)
- Required parameters: (none)
- Optional parameters: (none)
- Example 1: `?logspword=[logs_password]&phpmussel=controls_lockout`
- Example 2: `?pword=[script_password]&phpmussel=controls_lockout`
- What it does: Disables all browser-side controls. This should be used if you suspect that either of your passwords have been compromised (this can happen if you're using these controls from a computer that's not secured and/or not trusted). controls_lockout works by creating a file, `controls.lck`, in your vault, that phpMussel will check for before performing any commands of any kind. Once this happens, to reenable controls, you'll need to manually delete the `controls.lck` file via FTP or similar. Can be called using either password.

disable
- Password required: script_password
- Other requirements: (none)
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=disable`
- What it does: Disables phpMussel. This should be used if you're performing any updates or changes to your system or if you're installing any new software or modules to your system that either does or potentially could trigger false positives. This should also be used if you're having any problems with phpMussel but don't wish to remove it from your system. Once this happens, to reenable phpMussel, use "enable".

enable
- Password required: script_password
- Other requirements: (none)
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=enable`
- What it does: Enables phpMussel. This should be used if you've previously disabled phpMussel using "disable" and want to reenable it.

update
- Password required: script_password
- Other requirements: update.dat and update.inc must exist.
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=update`
- What it does: Checks for updates to both phpMussel and its signatures. If update checks succeed and updates are found, will attempt to download and install these updates. If update checks fail, update will abort. Results of the entire process are printed to the screen. I recommend checking at least once per month to ensure that your signatures and your copy of phpMussel are kept up to-date (unless, of course, you're checking for updates and installing them manually, which, I'd still recommend doing at least one per month). Checking more than twice per month is probably pointless, considering I'm (at the time of writing this) working on this project by myself and I'm very unlikely to be able to produce updates of any kind more frequently than that (nor do I particularly want to for the most part).

greylist
- Password required: script_password
- Other requirements: (none)
- Required parameters: [Name of signature to be greylisted]
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=greylist&musselvar=[Signature]`
- What it does: Add a signature to the greylist.

greylist_clear
- Password required: script_password
- Other requirements: (none)
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=greylist_clear`
- What it does: Clears the entire greylist.

greylist_show
- Password required: script_password
- Other requirements: (none)
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=greylist_show`
- What it does: Prints the contents of the greylist to the screen.

---


###4B. <a name="SECTION4B"></a>CLI (COMMANDLIJN INTERFACE)

phpMussel can be run as an interactive file scanner in CLI mode under Windows-based systems. Refer to the "HOW TO INSTALL (FOR CLI)" section of this readme file for more details.

For a list of available CLI commands, at the CLI prompt, type 'c', and press Enter.

---


###5. <a name="SECTION5"></a>BESTANDEN IN DIT PAKKET

Het volgende is een lijst van alle bestanden die had moeten worden opgenomen in de gearchiveerde kopie van dit script als je het gedownload het, alle bestanden die mogelijk kan worden gemaakt als gevolg van uw gebruik van dit script, samen met een korte beschrijving van wat al deze bestanden voor zijn.

Bestand                                    | Beschrijving
-------------------------------------------|--------------------------------------
/phpmussel.php                             | Loaderbestand. Laadt de belangrijkste script, updater, ezv. Dit is wat je zou moeten worden inhaken in (essentieel)!
/web.config                                | Een ASP.NET-configuratiebestand (in dit geval, naar de directory "vault" te beschermen tegen toegang door niet-geautoriseerde bronnen indien het script is geïnstalleerd op een server op basis van ASP.NET technologieën).
/_docs/                                    | Documentatie directory (bevat verschillende bestanden).
/_docs/change_log.txt                      | Een overzicht van wijzigingen in het script tussen verschillende versies (niet vereist voor een goede werking van het script).
/_docs/readme.de.txt                       | Documentatie: DEUTSCH
/_docs/readme.en.txt                       | Documentatie: ENGLISH
/_docs/readme.es.txt                       | Documentatie: ESPAÑOL
/_docs/readme.fr.txt                       | Documentatie: FRANÇAIS
/_docs/readme.id.txt                       | Documentatie: BAHASA INDONESIA
/_docs/readme.it.txt                       | Documentatie: ITALIANO
/_docs/readme.nl.txt                       | Documentatie: NEDERLANDSE
/_docs/readme.pt.txt                       | Documentatie: PORTUGUÊS
/_docs/signatures_tally.txt                | Net-shift tally van meegeleverde handtekeningen (niet vereist voor een goede werking van het script).
/_testfiles/                               | Testbestanden directory (bevat verschillende bestanden). Alle opgenomen bestanden zijn testbestanden voor het testen als phpMussel correct op uw systeem is geïnstalleerd, en je hoeft niet om deze map of een van de bestanden, behalve bij het doen van dergelijke testen te uploaden.
/_testfiles/ascii_standard_testfile.txt    | Testbestand voor het testen phpMussel genormaliseerde ASCII handtekeningen.
/_testfiles/coex_testfile.rtf              | Testbestand voor het testen phpMussel complexe uitgebreide handtekeningen.
/_testfiles/exe_standard_testfile.exe      | Testbestand voor het testen phpMussel PE handtekeningen.
/_testfiles/general_standard_testfile.txt  | Testbestand voor het testen phpMussel algemene handtekeningen.
/_testfiles/graphics_standard_testfile.gif | Testbestand voor het testen phpMussel grafische handtekeningen.
/_testfiles/html_standard_testfile.txt     | Testbestand voor het testen phpMussel genormaliseerde HTML handtekeningen.
/_testfiles/md5_testfile.txt               | Testbestand voor het testen phpMussel MD5 handtekeningen.
/_testfiles/metadata_testfile.txt.gz       | Testbestand voor het testen phpMussel metadata handtekeningen en voor het testen van GZ bestandsondersteuning op uw systeem.
/_testfiles/metadata_testfile.zip          | Testbestand voor het testen phpMussel metadata handtekeningen en voor het testen van ZIP bestandsondersteuning op uw systeem.
/_testfiles/ole_testfile.ole               | Testbestand voor het testen phpMussel OLE handtekeningen.
/_testfiles/pdf_standard_testfile.pdf      | Testbestand voor het testen phpMussel PDF handtekeningen.
/_testfiles/pe_sectional_testfile.exe      | Testbestand voor het testen phpMussel PE Sectionele handtekeningen.
/_testfiles/swf_standard_testfile.swf      | Testbestand voor het testen phpMussel SWF handtekeningen.
/_testfiles/xdp_standard_testfile.xdp      | Testbestand voor het testen phpMussel XML/XDP-Brok handtekeningen.
/vault/                                    | Vault directory (bevat verschillende bestanden).
/vault/cache/                              | Cache directory (tijdelijke data).
/vault/cache/.htaccess                     | Een hypertext toegang bestand (in dit geval, om gevoelige bestanden die behoren tot het script te beschermen tegen toegang door niet-geautoriseerde bronnen).
/vault/lang/                               | Bevat phpMussel taaldata.
/vault/lang/.htaccess                      | Een hypertext toegang bestand (in dit geval, om gevoelige bestanden die behoren tot het script te beschermen tegen toegang door niet-geautoriseerde bronnen).
/vault/lang/lang.de.inc                    | Taaldata: DEUTSCH
/vault/lang/lang.en.inc                    | Taaldata: ENGLISH
/vault/lang/lang.es.inc                    | Taaldata: ESPAÑOL
/vault/lang/lang.fr.inc                    | Taaldata: FRANÇAIS
/vault/lang/lang.id.inc                    | Taaldata: BAHASA INDONESIA
/vault/lang/lang.it.inc                    | Taaldata: ITALIANO
/vault/lang/lang.ja.inc                    | Taaldata: 日本語
/vault/lang/lang.nl.inc                    | Taaldata: NEDERLANDSE
/vault/lang/lang.pt.inc                    | Taaldata: PORTUGUÊS
/vault/lang/lang.ru.inc                    | Taaldata: РУССКИЙ
/vault/lang/lang.zh.inc                    | Taaldata: 中文（简体）
/vault/lang/lang.zh-tw.inc                 | Taaldata: 中文（傳統）
/vault/quarantine/                         | Quarantaine directory (bestanden in quarantaine bevat).
/vault/quarantine/.htaccess                | Een hypertext toegang bestand (in dit geval, om gevoelige bestanden die behoren tot het script te beschermen tegen toegang door niet-geautoriseerde bronnen).
/vault/.htaccess                           | Een hypertext toegang bestand (in dit geval, om gevoelige bestanden die behoren tot het script te beschermen tegen toegang door niet-geautoriseerde bronnen).
/vault/ascii_clamav_regex.cvd              | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/ascii_clamav_regex.map              | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/ascii_clamav_standard.cvd           | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/ascii_clamav_standard.map           | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/ascii_custom_regex.cvd              | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/ascii_custom_standard.cvd           | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/ascii_mussel_regex.cvd              | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/ascii_mussel_standard.cvd           | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/coex_clamav.cvd                     | Bestand voor Complexe Uitgebreide handtekeningen.
/vault/coex_custom.cvd                     | Bestand voor Complexe Uitgebreide handtekeningen.
/vault/coex_mussel.cvd                     | Bestand voor Complexe Uitgebreide handtekeningen.
/vault/elf_clamav_regex.cvd                | Bestand voor ELF handtekeningen.
/vault/elf_clamav_regex.map                | Bestand voor ELF handtekeningen.
/vault/elf_clamav_standard.cvd             | Bestand voor ELF handtekeningen.
/vault/elf_clamav_standard.map             | Bestand voor ELF handtekeningen.
/vault/elf_custom_regex.cvd                | Bestand voor ELF handtekeningen.
/vault/elf_custom_standard.cvd             | Bestand voor ELF handtekeningen.
/vault/elf_mussel_regex.cvd                | Bestand voor ELF handtekeningen.
/vault/elf_mussel_standard.cvd             | Bestand voor ELF handtekeningen.
/vault/exe_clamav_regex.cvd                | Bestand voor Portable Executable bestand (EXE) handtekeningen.
/vault/exe_clamav_regex.map                | Bestand voor Portable Executable bestand (EXE) handtekeningen.
/vault/exe_clamav_standard.cvd             | Bestand voor Portable Executable bestand (EXE) handtekeningen.
/vault/exe_clamav_standard.map             | Bestand voor Portable Executable bestand (EXE) handtekeningen.
/vault/exe_custom_regex.cvd                | Bestand voor Portable Executable bestand (EXE) handtekeningen.
/vault/exe_custom_standard.cvd             | Bestand voor Portable Executable bestand (EXE) handtekeningen.
/vault/exe_mussel_regex.cvd                | Bestand voor Portable Executable bestand (EXE) handtekeningen.
/vault/exe_mussel_standard.cvd             | Bestand voor Portable Executable bestand (EXE) handtekeningen.
/vault/filenames_clamav.cvd                | Bestand voor bestandsnaam handtekeningen.
/vault/filenames_custom.cvd                | Bestand voor bestandsnaam handtekeningen.
/vault/filenames_mussel.cvd                | Bestand voor bestandsnaam handtekeningen.
/vault/general_clamav_regex.cvd            | Bestand voor algemene handtekeningen.
/vault/general_clamav_regex.map            | Bestand voor algemene handtekeningen.
/vault/general_clamav_standard.cvd         | Bestand voor algemene handtekeningen.
/vault/general_clamav_standard.map         | Bestand voor algemene handtekeningen.
/vault/general_custom_regex.cvd            | Bestand voor algemene handtekeningen.
/vault/general_custom_standard.cvd         | Bestand voor algemene handtekeningen.
/vault/general_mussel_regex.cvd            | Bestand voor algemene handtekeningen.
/vault/general_mussel_standard.cvd         | Bestand voor algemene handtekeningen.
/vault/graphics_clamav_regex.cvd           | Bestand voor grafische handtekeningen.
/vault/graphics_clamav_regex.map           | Bestand voor grafische handtekeningen.
/vault/graphics_clamav_standard.cvd        | Bestand voor grafische handtekeningen.
/vault/graphics_clamav_standard.map        | Bestand voor grafische handtekeningen.
/vault/graphics_custom_regex.cvd           | Bestand voor grafische handtekeningen.
/vault/graphics_custom_standard.cvd        | Bestand voor grafische handtekeningen.
/vault/graphics_mussel_regex.cvd           | Bestand voor grafische handtekeningen.
/vault/graphics_mussel_standard.cvd        | Bestand voor grafische handtekeningen.
/vault/greylist.csv                        | CSV van greylisted handtekeningen aangeeft om phpMussel waarop handtekeningen moet worden negeren (bestand automatisch aangemaakt opnieuw als verwijderd).
/vault/hex_general_commands.csv            | Hex-gecodeerde CSV van algemene commando detecties optioneel gebruikt door phpMussel.
/vault/html_clamav_regex.cvd               | Bestand voor genormaliseerde HTML handtekeningen.
/vault/html_clamav_regex.map               | Bestand voor genormaliseerde HTML handtekeningen.
/vault/html_clamav_standard.cvd            | Bestand voor genormaliseerde HTML handtekeningen.
/vault/html_clamav_standard.map            | Bestand voor genormaliseerde HTML handtekeningen.
/vault/html_custom_regex.cvd               | Bestand voor genormaliseerde HTML handtekeningen.
/vault/html_custom_standard.cvd            | Bestand voor genormaliseerde HTML handtekeningen.
/vault/html_mussel_regex.cvd               | Bestand voor genormaliseerde HTML handtekeningen.
/vault/html_mussel_standard.cvd            | Bestand voor genormaliseerde HTML handtekeningen.
/vault/lang.inc                            | Taaldata.
/vault/macho_clamav_regex.cvd              | Bestand voor Mach-O handtekeningen.
/vault/macho_clamav_regex.map              | Bestand voor Mach-O handtekeningen.
/vault/macho_clamav_standard.cvd           | Bestand voor Mach-O handtekeningen.
/vault/macho_clamav_standard.map           | Bestand voor Mach-O handtekeningen.
/vault/macho_custom_regex.cvd              | Bestand voor Mach-O handtekeningen.
/vault/macho_custom_standard.cvd           | Bestand voor Mach-O handtekeningen.
/vault/macho_mussel_regex.cvd              | Bestand voor Mach-O handtekeningen.
/vault/macho_mussel_standard.cvd           | Bestand voor Mach-O handtekeningen.
/vault/mail_clamav_regex.cvd               | Bestand voor mail handtekeningen.
/vault/mail_clamav_regex.map               | Bestand voor mail handtekeningen.
/vault/mail_clamav_standard.cvd            | Bestand voor mail handtekeningen.
/vault/mail_clamav_standard.map            | Bestand voor mail handtekeningen.
/vault/mail_custom_regex.cvd               | Bestand voor mail handtekeningen.
/vault/mail_custom_standard.cvd            | Bestand voor mail handtekeningen.
/vault/mail_mussel_regex.cvd               | Bestand voor mail handtekeningen.
/vault/mail_mussel_standard.cvd            | Bestand voor mail handtekeningen.
/vault/mail_mussel_standard.map            | Bestand voor mail handtekeningen.
/vault/md5_clamav.cvd                      | Bestand voor MD5 gebaseerde handtekeningen.
/vault/md5_custom.cvd                      | Bestand voor MD5 gebaseerde handtekeningen.
/vault/md5_mussel.cvd                      | Bestand voor MD5 gebaseerde handtekeningen.
/vault/metadata_clamav.cvd                 | Bestand voor archief metadata handtekeningen.
/vault/metadata_custom.cvd                 | Bestand voor archief metadata handtekeningen.
/vault/metadata_mussel.cvd                 | Bestand voor archief metadata handtekeningen.
/vault/ole_clamav_regex.cvd                | Bestand voor OLE handtekeningen.
/vault/ole_clamav_regex.map                | Bestand voor OLE handtekeningen.
/vault/ole_clamav_standard.cvd             | Bestand voor OLE handtekeningen.
/vault/ole_clamav_standard.map             | Bestand voor OLE handtekeningen.
/vault/ole_custom_regex.cvd                | Bestand voor OLE handtekeningen.
/vault/ole_custom_standard.cvd             | Bestand voor OLE handtekeningen.
/vault/ole_mussel_regex.cvd                | Bestand voor OLE handtekeningen.
/vault/ole_mussel_standard.cvd             | Bestand voor OLE handtekeningen.
/vault/pdf_clamav_regex.cvd                | Bestand voor PDF handtekeningen.
/vault/pdf_clamav_regex.map                | Bestand voor PDF handtekeningen.
/vault/pdf_clamav_standard.cvd             | Bestand voor PDF handtekeningen.
/vault/pdf_clamav_standard.map             | Bestand voor PDF handtekeningen.
/vault/pdf_custom_regex.cvd                | Bestand voor PDF handtekeningen.
/vault/pdf_custom_standard.cvd             | Bestand voor PDF handtekeningen.
/vault/pdf_mussel_regex.cvd                | Bestand voor PDF handtekeningen.
/vault/pdf_mussel_standard.cvd             | Bestand voor PDF handtekeningen.
/vault/pe_clamav.cvd                       | Bestand voor PE Sectionele handtekeningen.
/vault/pe_custom.cvd                       | Bestand voor PE Sectionele handtekeningen.
/vault/pe_mussel.cvd                       | Bestand voor PE Sectionele handtekeningen.
/vault/phpmussel.inc                       | Kern Script; De belangrijkste lichaam van phpMussel (essentiële)!
/vault/phpmussel.ini                       | Configuratiebestand; Bevat alle configuratieopties van phpMussel, het vertellen wat te doen en hoe om te werken correct (essentiële)!
※ /vault/scan_log.txt                     | Een record van alles gescand door phpMussel.
※ /vault/scan_kills.txt                   | Een record van elk bestand uploaden geblokkeerde/gedood door phpMussel.
/vault/swf_clamav_regex.cvd                | Bestand voor the Shockwave handtekeningen.
/vault/swf_clamav_regex.map                | Bestand voor the Shockwave handtekeningen.
/vault/swf_clamav_standard.cvd             | Bestand voor the Shockwave handtekeningen.
/vault/swf_clamav_standard.map             | Bestand voor the Shockwave handtekeningen.
/vault/swf_custom_regex.cvd                | Bestand voor the Shockwave handtekeningen.
/vault/swf_custom_standard.cvd             | Bestand voor the Shockwave handtekeningen.
/vault/swf_mussel_regex.cvd                | Bestand voor the Shockwave handtekeningen.
/vault/swf_mussel_standard.cvd             | Bestand voor the Shockwave handtekeningen.
/vault/switch.dat                          | Controles en sets bepaalde variabelen.
/vault/template.html                       | Sjabloonbestand; Sjabloon voor HTML-uitvoer geproduceerd door phpMussel voor zijn geblokkeerd bestand te uploaden bericht (het bericht gezien te de uploader).
/vault/update.dat                          | Bestand met versie-informatie voor zowel de phpMussel script en de phpMussel handtekeningen. Als je ooit wilt te automatisch update phpMussel of willen phpMusel updaten via uw browser, dit bestand is essentieel.
/vault/update.inc                          | Update Script; Vereist voor automatische updates en voor het bijwerken van phpMussel via uw browser, maar niet anders vereist.
/vault/whitelist_clamav.cvd                | Bestand-specifieke whitelist.
/vault/whitelist_custom.cvd                | Bestand-specifieke whitelist.
/vault/whitelist_mussel.cvd                | Bestand-specifieke whitelist.
/vault/xmlxdp_clamav_regex.cvd             | Bestand voor XML/XDP-Brok handtekeningen.
/vault/xmlxdp_clamav_regex.map             | Bestand voor XML/XDP-Brok handtekeningen.
/vault/xmlxdp_clamav_standard.cvd          | Bestand voor XML/XDP-Brok handtekeningen.
/vault/xmlxdp_clamav_standard.map          | Bestand voor XML/XDP-Brok handtekeningen.
/vault/xmlxdp_custom_regex.cvd             | Bestand voor XML/XDP-Brok handtekeningen.
/vault/xmlxdp_custom_standard.cvd          | Bestand voor XML/XDP-Brok handtekeningen.
/vault/xmlxdp_mussel_regex.cvd             | Bestand voor XML/XDP-Brok handtekeningen.
/vault/xmlxdp_mussel_standard.cvd          | Bestand voor XML/XDP-Brok handtekeningen.

※ Bestandsnaam kan verschillen, afhankelijk van de configuratie bedingen (van `phpmussel.ini`).

####*REGARDING SIGNATURE FILES*
CVD is an acronym for "ClamAV Virus Definitions", in reference both to how ClamAV refers to its own signatures and to the use of those signatures for phpMussel; Files ending with "CVD" contain signatures.

Files ending with "MAP", quite literally, map which signatures phpMussel should and shouldn't use for individual scans; Not all signatures are necessarily required for every single scan, so, phpMussel uses maps of the signature files to speed up the scanning process (a process that would otherwise be extremely slow and tedious).

Signature files marked with "_regex" contain signatures that utilise regular expression pattern checking (regex).

Signature files marked with "_standard" contain signatures that specifically don't utilise any form of pattern checking.

Signature files marked with neither "_regex" nor "_standard" will be as one or the other, but not both (refer to the Signature Format section of this README file for documentation and specific details).

Signature files marked with "_clamav" contain signatures that are sourced entirely from the ClamAV database (GNU/GPL).

Signature files marked with "_custom", by default, don't contain any signatures at all; These such files exist to give you somewhere to place your own custom signatures, if you come up with any of your own.

Signature files marked with "_mussel" contain signatures that specifically are not sourced from ClamAV, signatures which, generally, I've either come up with myself and/or based on information gathered from various sources.


---


###6. <a name="SECTION6"></a>CONFIGURATIEOPTIES
The following is a list of variables found in the `phpmussel.ini` configuration file of phpMussel, along with a description of their purpose and function.

####"general" (Categorie)
General configuration for phpMussel.

"script_password"
- As a convenience, phpMussel will allow certain functions (including the ability to update phpMussel on-the-fly) to be manually triggered via POST, GET and QUERY. However, as a security precaution, to do this, phpMussel will expect a password to be included with the command, as to ensure that it's you, and not someone else, attempting to manually trigger these functions. Set script_password to whatever password you would like to use. If no password is set, manual triggering will be disabled by default. Use something you will remember but which is hard for others to guess.
- Has no influence in CLI mode.

"logs_password"
- The same as script_password, but for viewing the contents of scan_log and scan_kills. Having separate passwords can be useful if you want to give someone else access to one set of functions but not the other.
- Has no influence in CLI mode.

"cleanup"
- Unset script variables and cache after execution. If you aren't using the script beyond the initial scanning of uploads, should set to yes, to minimize memory usage. If you are using the script for purposes beyond the initial scanning of uploads, should set to no, to avoid unnecessarily reloading duplicate data into memory. In general practise, it should probably be set to yes, but, if you do this, you won't be able to use the script for anything other than scanning file uploads.
- Has no influence in CLI mode.

"scan_log"
- Filename of file to log all scanning results to. Specify a filename, or leave blank to disable.

"scan_kills"
- Filename of file to log all records of blocked or killed uploads to. Specify a filename, or leave blank to disable.

"ipaddr"
- Where to find IP address of connecting request? (Useful for services such as Cloudflare and the likes) Default = REMOTE_ADDR. WARNING: Don't change this unless you know what you're doing!

"forbid_on_block"
- Should phpMussel send 403 headers with the file upload blocked message, or stick with the usual 200 OK? 0 = No (200) [Default], 1 Yes (403).

"delete_on_sight"
- Enabling this directive will instruct the script to attempt to immediately delete any scanned attempted file upload matching any detection criteria, whether via signatures or otherwise. Files determined to be "clean" won't be touched. In the case of archives, the entire archive will be deleted (regardless of if the offending file is only one of several files contained within the archive). For the case of file upload scanning, usually, it isn't necessary to turn this option on, because usually, php will automatically purge the contents of its cache when execution has finished, meaning that it'll usually delete any files uploaded through it to the server unless they've moved, copied or deleted already. The option is added here as an extra measure of security for the extra paranoid and for those whose copies of php may not always behave in the manner intended. 0 - After scanning, leave the file alone [Default], 1 - After scanning, if not clean, delete immediately.

"lang"
- Specify the default language for phpMussel.

"lang_override"
- Specify if phpMussel should, when possible, override the language specification with the language preference declared by inbound requests (HTTP_ACCEPT_LANGUAGE). 0 - No [Default], 1 - Yes.

"quarantine_key"
- phpMussel is able to quarantine flagged attempted file uploads in isolation within the phpMussel vault, if this is something you want it to do. Casual users of phpMussel that simply wish to protect their websites or hosting environment without having any interest in deeply analysing any flagged attempted file uploads should leave this functionality disabled, but any users interested in further analysis of flagged attempted file uploads for malware research or for similar such things should enable this functionality. Quarantining of flagged attempted file uploads can sometimes also assist in debugging false-positives, if this is something that frequently occurs for you. To disable quarantine functionality, simply leave the `quarantine_key` directive empty, or erase the contents of that directive if it isn't already empty. To enable quarantine functionality, enter some value into the directive. The "quarantine_key" is an important security feature of the quarantine functionality required as a means of preventing the quarantine functionality from being exploited by potential attackers and as a means of preventing any potential execution of data stored within the quarantine. The `quarantine_key` should be treated in the same manner as your passwords: The longer the better, and guard it tightly. For best effect, use in conjunction with "delete_on_sight".

"quarantine_max_filesize"
- The maximum allowable filesize of files to be quarantined. Files larger than the value specified will NOT be quarantined. This directive is important as a means of making it more difficult for any potential attackers to flood your quarantine with unwanted data potentially causing run-away data usage on your hosting service. Value is in KB. Default =2048 =2048KB =2MB.

"quarantine_max_usage"
- The maximum memory usage allowed for the quarantine. If the total memory used by the quarantine reaches this value, the oldest quarantined files will be deleted until the total memory used no longer reaches this value. This directive is important as a means of making it more difficult for any potential attackers to flood your quarantine with unwanted data potentially causing run-away data usage on your hosting service. Value is in KB. Default =65536 =65536KB =64MB.

"honeypot_mode"
- When honeypot mode is enabled, phpMussel will attempt to quarantine every single file upload that it encounters, regardless of whether or not the file being uploaded matches any included signatures, and no actual scanning or analysis of those attempted file uploads will actually occur. This functionality should be useful for those that wish to use phpMussel for the purposes of virus/malware research, but it's neither recommended to enable this functionality if the intended use of phpMussel by the user is for actual file upload scanning, nor recommended to use the honeypot functionality for purposes other than honeypotting. By default, this option is disabled. 0 = Disabled [Default], 1 = Enabled.

"scan_cache_expiry"
- For how long should phpMussel cache the results of scanning? Value is the number of seconds to cache the results of scanning for. Default is 21600 seconds (6 hours); A value of 0 will disable caching the results of scanning.

####"signatures" (Categorie)
Configuration for signatures.
- %%%_clamav = ClamAV signatures (both mains and daily).
- %%%_custom = Your custom signatures (if you've written any).
- %%%_mussel = phpMussel signatures included in your current signatures set that aren't from ClamAV.

Check against MD5 signatures when scanning? 0 = No, 1 = Yes [Default].
- "md5_clamav"
- "md5_custom"
- "md5_mussel"

Check against general signatures when scanning? 0 = No, 1 = Yes [Default].
- "general_clamav"
- "general_custom"
- "general_mussel"

Check against normalised ASCII signatures when scanning? 0 = No, 1 = Yes [Default].
- "ascii_clamav"
- "ascii_custom"
- "ascii_mussel"

Check against normalised HTML signatures when scanning? 0 = No, 1 = Yes [Default].
- "html_clamav"
- "html_custom"
- "html_mussel"

Check PE (Portable Executable) files (EXE, DLL, etc) against PE Sectional signatures when scanning? 0 = No, 1 = Yes [Default].
- "pe_clamav"
- "pe_custom"
- "pe_mussel"

Check PE (Portable Executable) files (EXE, DLL, etc) against PE signatures when scanning? 0 = No, 1 = Yes [Default].
- "exe_clamav"
- "exe_custom"
- "exe_mussel"

Check ELF files against ELF signatures when scanning? 0 = No, 1 = Yes [Default].
- "elf_clamav"
- "elf_custom"
- "elf_mussel"

Check Mach-O files (OSX, etc) against Mach-O signatures when scanning? 0 = No, 1 = Yes [Default].
- "macho_clamav"
- "macho_custom"
- "macho_mussel"

Check graphics files against graphics based signatures when scanning? 0 = No, 1 = Yes [Default].
- "graphics_clamav"
- "graphics_custom"
- "graphics_mussel"

Check archive contents against archive metadata signatures when scanning? 0 = No, 1 = Yes [Default].
- "metadata_clamav"
- "metadata_custom"
- "metadata_mussel"

Check OLE objects against OLE signatures when scanning? 0 = No, 1 = Yes [Default].
- "ole_clamav"
- "ole_custom"
- "ole_mussel"

Check filenames against filename based signatures when scanning? 0 = No, 1 = Yes [Default].
- "filenames_clamav"
- "filenames_custom"
- "filenames_mussel"

Allow scanning with phpMussel_mail()? 0 = No, 1 = Yes [Default].
- "mail_clamav"
- "mail_custom"
- "mail_mussel"

Enable file specific whitelist? 0 = No, 1 = Yes [Default].
- "whitelist_clamav"
- "whitelist_custom"
- "whitelist_mussel"

Check XML/XDP chunks against XML/XDP-chunk signatures when scanning? 0 = No, 1 = Yes [Default].
- "xmlxdp_clamav"
- "xmlxdp_custom"
- "xmlxdp_mussel"

Check against Complex Extended signatures when scanning? 0 = No, 1 = Yes [Default].
- "coex_clamav"
- "coex_custom"
- "coex_mussel"

Check against PDF signatures when scanning? 0 = No, 1 = Yes [Default].
- "pdf_clamav"
- "pdf_custom"
- "pdf_mussel"

Check against Shockwave signatures when scanning? 0 = No, 1 = Yes [Default].
- "swf_clamav"
- "swf_custom"
- "swf_mussel"

Signature matching length limiting options. Only change these if you know what you're doing. SD = Standard signatures. RX = PCRE (Perl Compatible Regular Expressions, or "Regex") signatures. FN = Filename signatures. If you notice php crashing when phpMussel attempts to scan, try lowering these "max" values. If possible and convenient, let me know when this happens and the results of whatever you try.
- "fn_siglen_min"
- "fn_siglen_max"
- "rx_siglen_min"
- "rx_siglen_max"
- "sd_siglen_min"
- "sd_siglen_max"

"fail_silently"
- Should phpMussel report when signatures files are missing or corrupted? If fail_silently is disabled, missing and corrupted files will be reported on scanning, and if fail_silently is enabled, missing and corrupted files will be ignored, with scanning reported for those files that there are no problems. This should generally be left alone unless you're experiencing crashes or similar problems. 0 = Disabled, 1 = Enabled [Default].

####"files" (Categorie)
General configuration for handling of files.

"max_uploads"
- Maximum allowable number of files to scan during files upload scan before aborting the scan and informing the user they are uploading too much at once! Provides protection against a theoretical attack whereby an attacker attempts to DDoS your system or CMS by overloading phpMussel to slow down the php process to a grinding halt. Recommended: 10. You may wish to raise or lower this number depending on the speed of your hardware. Note that this number doesn't account for or include the contents of archives.

"filesize_limit"
- Filesize limit in KB. 65536 = 64MB [Default], 0 = No limit (always greylisted), any (positive) numeric value accepted. This can be useful when your php configuration limits the amount of memory a process can hold or if your php configuration limits filesize of uploads.

"filesize_response"
- What to do with files that exceed the filesize limit (if one exists). 0 - Whitelist, 1 - Blacklist [Default].

"filetype_whitelist", "filetype_blacklist", "filetype_greylist"
- If your system only allows specific types of files to be uploaded, or if your system explicitly denies certain types of files, specifying those filetypes in whitelists, blacklists and greylists can increase the speed at which scanning is performed by allowing the script to skip over certain filetypes. Format is CSV (comma separated values). If you want to scan everything, rather than whitelist, blacklist or greylist, leave the variable(/s) blank; Doing so will disable whitelist/blacklist/greylist.
- Logical order of processing is:
  - If the filetype is whitelisted, don't scan and don't block the file, and don't check the file against the blacklist or the greylist.
  - If the filetype is blacklisted, don't scan the file but block it anyway, and don't check the file against the greylist.
  - If the greylist is empty or if the greylist is not empty and the filetype is greylisted, scan the file as per normal and determine whether to block it based on the results of the scan, but if the greylist is not empty and the filetype is not greylisted, treat the file as blacklisted, therefore not scanning it but blocking it anyway.

"check_archives"
- Attempt to check the contents of archives? 0 - No (do not check), 1 - Yes (check) [Default].
- Currently, only checking of BZ, GZ, LZF and ZIP files is supported (checking of RAR, CAB, 7z and etcetera not currently supported).
- This is not foolproof! While I highly recommend keeping this turned on, I can't guarantee it'll always find everything.
- Also be aware that archive checking currently is not recursive for ZIPs.

"filesize_archives"
- Carry over filesize blacklisting/whitelisting to the contents of archives? 0 - No (just greylist everything), 1 - Yes [Default].

"filetype_archives"
- Carry over filetype blacklisting/whitelisting to the contents of archives? 0 - No (just greylist everything) [Default], 1 - Yes.

"max_recursion"
- Maximum recursion depth limit for archives. Default = 10.

"block_encrypted_archives"
- Detect and block encrypted archives? Because phpMussel isn't able to scan the contents of encrypted archives, it's possible that archive encryption may be employed by an attacker as a means of attempting to bypass phpMussel, anti-virus scanners and other such protections. Instructing phpMussel to block any archives that it discovers to be encrypted could potentially help reduce any risk associated with these such possibilities. 0 - No, 1 - Yes [Default].

####"attack_specific" (Categorie)
Configuration for specific attack detections (not based on CVDs).

Chameleon attack detection: 0 = Off, 1 = On.

"chameleon_from_php"
- Search for php header in files that are neither php files nor recognised archives.

"chameleon_from_exe"
- Search for executable headers in files that are neither executables nor recognised archives and for executables whose headers are incorrect.

"chameleon_to_archive"
- Search for archives whose headers are incorrect (Supported: BZ, GZ, RAR, ZIP, RAR, GZ).

"chameleon_to_doc"
- Search for office documents whose headers are incorrect (Supported: DOC, DOT, PPS, PPT, XLA, XLS, WIZ).

"chameleon_to_img"
- Search for images whose headers are incorrect (Supported: BMP, DIB, PNG, GIF, JPEG, JPG, XCF, PSD, PDD).

"chameleon_to_pdf"
- Search for PDF files whose headers are incorrect.

"archive_file_extensions" and "archive_file_extensions_wc"
- Recognised archive file extensions (format is CSV; should only add or remove when problems occur; unnecessarily removing may cause false-positives to appear for archive files, whereas unnecessarily adding will essentially whitelist what you are adding from attack specific detection; modify with caution; also note that this has no effect on what archives can and can't be analysed at content-level). The list, as is at default, lists those formats used most commonly across the majority of systems and CMS, but intentionally isn't necessarily comprehensive.

"general_commands"
- Search content of files for general commands such as eval(), exec() and include()? 0 - No (do not check) [Default], 1 - Yes (check). Disable this option if you intend to upload any of the following to your system or CMS via your browser: php, JavaScript, HTML, python, perl files and etcetera. Enable this option if you don't have any additional protections on your system and do not intend to upload such files. If you use additional security in conjunction with phpMussel such as ZB Block, there is no need to turn this option on, because most of what phpMussel will look for (in the context of this option) are duplications of protections that are already provided.

"block_control_characters"
- Block any files containing any control characters (other than newlines)? (`[\x00-\x08\x0b\x0c\x0e\x1f\x7f]`) If you are _**ONLY**_ uploading plain-text, then you can turn this option on to provide some additional protection to your system. However, if you upload anything other than plain-text, turning this on may result in false positives. 0 - Don't block [Default], 1 - Block.

"corrupted_exe"
- Corrupted files and parse errors. 0 = Ignore, 1 = Block [Default]. Detect and block potentially corrupted PE (Portable Executable) files? Often (but not always), when certain aspects of a PE file are corrupted or can't be parsed correctly, it can be indicative of a viral infection. The processes used by most anti-virus programs to detect viruses in PE files require parsing those files in certain ways, which, if the programmer of a virus is aware of, will specifically try to prevent, in order to allow their virus to remain undetected.

"decode_threshold"
- Optional limitation or threshold to the length of raw data within which decode commands should be detected (in case there are any noticeable performance issues whilst scanning). Value is an integer representing filesize in KB. Default = 512 (512KB). Zero or null value disables the threshold (removing any such limitation based on filesize).

"scannable_threshold"
- Optional limitation or threshold to the length of raw data that phpMussel is permitted to read and scan (in case there are any noticeable performance issues whilst scanning). Value is an integer representing filesize in KB. Default = 32768 (32MB). Zero or null value disables the threshold. Generally, this value shouldn't be less than the average filesize of file uploads that you want and expect to receive to your server or website, shouldn't be more than the filesize_limit directive, and shouldn't be more than roughly one fifth of the total allowable memory allocation granted to php via the php.ini configuration file. This directive exists to try to prevent phpMussel from using up too much memory (that'd prevent it from being able to successfully scan files above a certain filesize).

####"compatibility" (Categorie)
Compatibility directives for phpMussel.

"ignore_upload_errors"
- This directive should generally be disabled unless it's required for correct functionality of phpMussel on your specific system. Normally, when disabled, when phpMussel detects the presence of elements in the `$_FILES` array(), it'll attempt to initiate a scan of the files that those elements represent, and, if those elements are blank or empty, phpMussel will return an error message. This is proper behaviour for phpMussel. However, for some CMS, empty elements in `$_FILES` can occur as a result of the natural behaviour of those CMS, or errors may be reported when there aren't any, in which case, the normal behaviour for phpMussel will be interfering with the normal behaviour of those CMS. If such a situation occurs for you, enabling this option will instruct phpMussel to not attempt to initiate scans for such empty elements, ignore them when found and to not return any related error messages, thus allowing continuation of the page request. 0 - OFF, 1 - ON.

"only_allow_images"
- If you only expect or only intend to allow images to be uploaded to your system or CMS, and if you absolutely don't require any files other than images to be uploaded to your system or CMS, this directive should be enabled, but should otherwise be disabled. If this directive is enabled, it'll instruct phpMussel to indiscriminately block any uploads identified as non-image files, without scanning them. This may reduce processing time and memory usage for attempted uploads of non-image files. 0 - OFF, 1 - ON.

####"heuristic" (Categorie)
Heuristic directives for phpMussel.

"threshold"
- There are certain signatures of phpMussel that are intended to identify suspicious and potentially malicious qualities of files being uploaded without in themselves identifying those files being uploaded specifically as being malicious. This "threshold" value tells phpMussel what the maximum total weight of suspicious and potentially malicious qualities of files being uploaded that's allowable is before those files are to be flagged as malicious. The definition of weight in this context is the total number of suspicious and potentially malicious qualities identified. By default, this value will be set to 3. A lower value generally will result in a higher occurrence of false positives but a higher number of malicious files being flagged, whereas a higher value generally will result in a lower occurrence of false positives but a lower number of malicious files being flagged. It's generally best to leave this value at its default unless you're experiencing problems related to it.

####"virustotal" (Categorie)
Configuration for Virus Total integration.

"vt_public_api_key"
- Optionally, phpMussel is able to scan files using the Virus Total API as a way to provide a greatly enhanced level of protection against viruses, trojans, malware and other threats. By default, scanning files using the Virus Total API is disabled. To enable it, an API key from Virus Total is required. Due to the significant benefit that this could provide to you, it's something that I highly recommend enabling. Please be aware, however, that to use the Virus Total API, you _**MUST**_ agree to their Terms of Service and you _**MUST**_ adhere to all guidelines as per described by the Virus Total documentation! You are NOT permitted to use this integration feature UNLESS:
  - You have read and agree to the Terms of Service of Virus Total and its API. The Terms of Service of Virus Total and its API can be found [Here](https://www.virustotal.com/en/about/terms-of-service/).
  - You have read and you understand, at a minimum, the preamble of the Virus Total Public API documentation (everything after "VirusTotal Public API v2.0" but before "Contents"). The Virus Total Public API documentation can be found [Here](https://www.virustotal.com/en/documentation/public-api/).

Note: If scanning files using the Virus Total API is disabled, you won't need to review any of the directives in this category (`virustotal`), because none of them will do anything if this is disabled. To acquire a Virus Total API key, from anywhere on their website, click the "Join our Community" link located towards the top-right of the page, enter in the information requested, and click "Sign up" when done. Follow all instructions supplied, and when you've got your public API key, copy/paste that public API key to the `vt_public_api_key` directive of the `phpmussel.ini` configuration file.

"vt_suspicion_level"
- By default, phpMussel will restrict which files it scans using the Virus Total API to those files that it considers "suspicious". You can optionally adjust this restriction by changing the value of the `vt_suspicion_level` directive.
- `0`: Files are only considered suspicious if, upon being scanned by phpMussel using its own signatures, they are deemed to carry a heuristic weight. This would effectively mean that use of the Virus Total API would be for a second opinion for when phpMussel suspects that a file may potentially be malicious, but can't entirely rule out that it may also potentially be benign (non-malicious) and therefore would otherwise normally not block it or flag it as being malicious.
- `1`: Files are considered suspicious if they're known to be executable (PE files, Mach-O files, ELF/Linux files, etc) or if they're known to be of a format that could potentially contain executable data (such as executable macros, DOC/DOCX files, archive files such as RARs, ZIPS and etc). This is the default and recommended suspicion level to apply, effectively meaning that use of the Virus Total API would be for a second opinion for when phpMussel doesn't initially find anything malicious or wrong with a file that it considers to be suspicious and therefore would otherwise normally not block it or flag it as being malicious.
- `2`: All files are considered suspicious and should be scanned using the Virus Total API. I don't generally recommend applying this suspicion level, due to the risk of reaching your API quota much quicker than would otherwise be the case, but there are certain circumstances (such as when the webmaster or hostmaster has very little faith or trust whatsoever in any of the uploaded content of their users) where this suspicion level could be appropriate. With this suspicion level, all files not normally blocked or flagged as being malicious would be scanned using the Virus Total API. Note, however, that phpMussel will cease using the Virus Total API when your API quota has been reached (regardless of suspicion level), and that your quota will likely be reached much faster when using this suspicion level.

Note: Regardless of suspicion level, any files that are either blacklisted or whitelisted by phpMussel won't be scanned using the Virus Total API, because those such files would've already been declared as either malicious or benign by phpMussel by the time that they would've otherwise been scanned by the Virus Total API, and therefore, additional scanning wouldn't be required. The ability of phpMussel to scan files using the Virus Total API is intended to build further confidence for whether a file is malicious or benign in those circumstances where phpMussel itself isn't entirely certain as to whether a file is malicious or benign.

"vt_weighting"
- Should phpMussel apply the results of scanning using the Virus Total API as detections or as detection weighting? This directive exists, because, although scanning a file using multiple engines (as Virus Total does) should result in an increased detection rate (and therefore in a higher number of malicious files being caught), it can also result in a higher number of false positives, and therefore, in some circumstances, the results of scanning may be better utilised as a confidence score rather than as a definitive conclusion. If a value of 0 is used, the results of scanning using the Virus Total API will be applied as detections, and therefore, if any engine used by Virus Total flags the file being scanned as being malicious, phpMussel will consider the file to be malicious. If any other value is used, the results of scanning using the Virus Total API will be applied as detection weighting, and therefore, the number of engines used by Virus Total that flag the file being scanned as being malicious will serve as a confidence score (or detection weighting) for whether or not the file being scanned should be considered malicious by phpMussel (the value used will represent the minimum confidence score or weight required in order to be considered malicious). A value of 0 is used by default.

"vt_quota_rate" and "vt_quota_time"
- According to the Virus Total API documentation, "it is limited to at most 4 requests of any nature in any given 1 minute time frame. If you run a honeyclient, honeypot or any other automation that is going to provide resources to VirusTotal and not only retrieve reports you are entitled to a higher request rate quota". By default, phpMussel will strictly adhere to these limitations, but due to the possibility of these rate quotas being increased, these two directives are provided as a means for you to instruct phpMussel as to what limit it should adhere to. Unless you've been instructed to do so, it's not recommended for you to increase these values, but, if you've encountered problems relating to reaching your rate quota, decreasing these values _**MAY**_ sometimes help you in dealing with these problems. Your rate limit determined as `vt_quota_rate` requests of any nature in any given `vt_quota_time` minute time frame.

---


###7. <a name="SECTION7"></a>HANDTEKENINGFORMAAT

####*FILENAME SIGNATURES*
All filename signatures follow the format:

`NAME:FNRX`

Where NAME is the name to cite for that signature and FNRX is the regex pattern to match filenames (unencoded) against.

####*MD5 SIGNATURES*
All MD5 signatures follow the format:

`HASH:FILESIZE:NAME`

Where HASH is the MD5 hash of an entire file, FILESIZE is the total size of that file and NAME is the name to cite for that signature.

####*ARCHIVE METADATA SIGNATURES*
All archive metadata signatures follow the format:

`NAME:FILESIZE:CRC32`

Where NAME is the name to cite for that signature, FILESIZE is the total size (uncompressed) of a file contained within the archive and CRC32 is the crc32 checksum of that contained file.

####*PE SECTIONAL SIGNATURES*
All PE Sectional signatures follow the format:

`SIZE:HASH:NAME`

Where HASH is the MD5 hash of a section of a PE file, SIZE is the total size of that section and NAME is the name to cite for that signature.

####*WHITELIST SIGNATURES*
All Whitelist signatures follow the format:

`HASH:FILESIZE:TYPE`

Where HASH is the MD5 hash of an entire file, FILESIZE is the total size of that file and TYPE is the type of signatures the whitelisted file is to be immune against.

####*COMPLEX EXTENDED SIGNATURES*
Complex Extended signatures are rather different to the other types of signatures possible with phpMussel, in that what they are matching against is specified by the signatures themselves and they can match against multiple criteria. The match criterias are delimited by ";" and the match type and match data of each match criteria is delimited by ":" as so that format for these signatures tends to look a bit like:

`$variable1:SOMEDATA;$variable2:SOMEDATA;SignatureName`

####*EVERYTHING ELSE*
All other signatures follow the format:

`NAME:HEX:FROM:TO`

Where NAME is the name to cite for that signature and HEX is a hexadecimal-encoded segment of the file intended to be matched by the given signature. FROM and TO are optional parameters, indicting from which and to which positions in the source data to check against (not supported by the mail function).

####*REGEX*
Any form of regex understood and correctly processed by php should also be correctly understood and processed by phpMussel and its signatures. However, I'd suggest taking extreme caution when writing new regex based signatures, because, if you're not entirely sure what you're doing, there can be highly irregular and/or unexpected results. Take a look at the phpMussel source-code if you're not entirely sure about the context in which regex statements are parsed. Also, remember that all patterns (with exception to filename, archive metadata and MD5 patterns) must be hexadecimally encoded (foregoing pattern syntax, of course)!

####*WHERE TO PUT CUSTOM SIGNATURES?*
Only put custom signatures in those files intended for custom signatures. Those files should contain "_custom" in their filenames. You should also avoid editing the default signature files, unless you know exactly what you're doing, because, aside from being good practise in general and aside from helping you distinguish between your own signatures and the default signatures included with phpMussel, it's good to stick to editing only the files intended for editing, because tampering with the default signature files can cause them to stop working correctly, due to the "maps" files: The maps files tell phpMussel where in the signature files to look for signatures required by phpMussel as per when required, and these maps can become out-of-sync with their associated signature files if those signature files are tampered with. You can put pretty much whatever you want into your custom signatures, so long as you follow the correct syntax. However, be careful to test new signatures for false-positives beforehand if you intend to share them or use them in a live environment.

####*SIGNATURE BREAKDOWN*
The following is a breakdown of the types of signatures used by phpMussel:
- "Normalised ASCII Signatures" (ascii_*). Checked against the contents of every non-whitelisted file targeted for scanning.
- "Complex Extended Signatures" (coex_*). Mixed signature type matching.
- "ELF Signatures" (elf_*). Checked against the contents of every non-whitelisted file targeted for scanning and matched to the ELF format.
- "Portable Executable Signatures" (exe_*). Checked against the contents of every non-whitelisted targeted for scanning and matched to the PE format.
- "Filename Signatures" (filenames_*). Checked against the filenames of files targeted for scanning.
- "General Signatures" (general_*). Checked against the contents of every non-whitelisted file targeted for scanning.
- "Graphics Signatures" (graphics_*). Checked against the contents of every non-whitelisted file targeted for scanning and matched to a known graphical file format.
- "General Commands" (hex_general_commands.csv). Checked against the contents of every non-whitelisted file targeted for scanning.
- "Normalised HTML Signatures" (html_*). Checked against the contents of every non-whitelisted HTML file targeted for scanning.
- "Mach-O Signatures" (macho_*). Checked against the contents of every non-whitelisted file targeted for scanning and matched to the Mach-O format.
- "Email Signatures" (mail_*). Checked against the $body variable parsed to the phpMussel_mail() function, which is intended to be the body of email messages or similar entities (potentially forum posts and etcetera).
- "MD5 Signatures" (md5_*). Checked against the MD5 hash of the contents and the filesize of every non-whitelisted file targeted for scanning.
- "Archive Metadata Signatures" (metadata_*). Checked against the CRC32 hash and filesize of the initial file contained inside of any non-whitelisted archive targeted for scanning.
- "OLE Signatures" (ole_*). Checked against the contents of every non-whitelisted OLE object targeted for scanning.
- "PDF Signatures" (pdf_*). Checked against the contents of every non-whitelisted PDF file targeted for scanning.
- "Portable Executable Sectional Signatures" (pe_*). Checked against the MD5 hash and the size of each PE section of every non-whitelisted file targeted for scanning and matched to the PE format.
- "SWF Signatures" (swf_*). Checked against the contents of every non-whitelisted Shockwave file targeted for scanning.
- "Whitelist Signatures" (whitelist_*). Checked against the MD5 hash of the contents and the filesize of every file targeted for scanning. Matched files will be immune to being matched by the type of signature mentioned in their whitelist entry.
- "XML/XDP-Chunk Signatures" (xmlxdp_*). Checked against any XML/XDP chunks found within any non-whitelisted files targeted for scanning.
(Note that any of these signatures may be easily disabled via `phpmussel.ini`).

---


###8. <a name="SECTION8"></a>BEKENDE COMPATIBILITEITSPROBLEMEN

####PHP en PCRE
- PHP en PCRE is vereist voor phpMussel te kunnen functioneren juist. Zonder PHP, of zonder de PCRE extensie van PHP, phpMussel zullen niet worden uitgevoerd of functioneren juist. Je moet er zeker van uw systeem heeft zowel PHP en PCRE geïnstalleerd en beschikbaar voordat downloaden en installeren phpMussel.

####ANTI-VIRUS SOFTWARECOMPATIBILITEIT

Voor het grootste deel, phpMussel is algemeen compatibel met de meeste andere anti-virus software. Echter, conflictions geweest beschreven door een aantal gebruikers in het verleden. Deze informatie hieronder is afkomstig van VirusTotal.com, het beschrijven van een aantal fout-positieven gemeld door anti-virus programma's tegen phpMussel. Hoewel deze informatie is geen absolute garantie van wel of niet je zult compatibiliteitsproblemen ondervindt tussen phpMussel en uw anti-virus software, als uw anti-virus software wordt gemarkeerd tegen phpMussel, moet u ofwel overwegen uit te schakelen voorafgaand aan het werken met phpMussel of moeten overwegen alternatieve opties om ofwel uw anti-virus software of phpMussel.

Deze informatie is voor het laatst bijgewerkt 28 Mei 2015 en is op de hoogte voor alle phpMussel publicaties van de twee meest recente mineur versies (v0.5-v0.6i) op het moment van schrijven dit.

| Scanner              |  Resultaten                          |
|----------------------|--------------------------------------|
| Ad-Aware             |  Geen bekend problemen               |
| Agnitum              |  Geen bekend problemen               |
| AhnLab-V3            |  Geen bekend problemen               |
| AntiVir              |  Geen bekend problemen               |
| Antiy-AVL            |  Geen bekend problemen               |
| Avast                |  Berichten "JS:ScriptSH-inf [Trj]"   |
| AVG                  |  Geen bekend problemen               |
| Baidu-International  |  Geen bekend problemen               |
| BitDefender          |  Geen bekend problemen               |
| Bkav                 |  Berichten "VEXDAD2.Webshell"        |
| ByteHero             |  Geen bekend problemen               |
| CAT-QuickHeal        |  Geen bekend problemen               |
| ClamAV               |  Geen bekend problemen               |
| CMC                  |  Geen bekend problemen               |
| Commtouch            |  Geen bekend problemen               |
| Comodo               |  Geen bekend problemen               |
| DrWeb                |  Geen bekend problemen               |
| Emsisoft             |  Geen bekend problemen               |
| ESET-NOD32           |  Geen bekend problemen               |
| F-Prot               |  Geen bekend problemen               |
| F-Secure             |  Geen bekend problemen               |
| Fortinet             |  Geen bekend problemen               |
| GData                |  Geen bekend problemen               |
| Ikarus               |  Geen bekend problemen               |
| Jiangmin             |  Geen bekend problemen               |
| K7AntiVirus          |  Geen bekend problemen               |
| K7GW                 |  Geen bekend problemen               |
| Kaspersky            |  Geen bekend problemen               |
| Kingsoft             |  Geen bekend problemen               |
| Malwarebytes         |  Geen bekend problemen               |
| McAfee               |  Berichten "New Script.c"            |
| McAfee-GW-Edition    |  Berichten "New Script.c"            |
| Microsoft            |  Geen bekend problemen               |
| MicroWorld-eScan     |  Geen bekend problemen               |
| NANO-Antivirus       |  Geen bekend problemen               |
| Norman               |  Geen bekend problemen               |
| nProtect             |  Geen bekend problemen               |
| Panda                |  Geen bekend problemen               |
| Qihoo-360            |  Geen bekend problemen               |
| Rising               |  Geen bekend problemen               |
| Sophos               |  Geen bekend problemen               |
| SUPERAntiSpyware     |  Geen bekend problemen               |
| Symantec             |  Berichten "WS.Reputation.1"         |
| TheHacker            |  Geen bekend problemen               |
| TotalDefense         |  Geen bekend problemen               |
| TrendMicro           |  Geen bekend problemen               |
| TrendMicro-HouseCall |  Geen bekend problemen               |
| VBA32                |  Geen bekend problemen               |
| VIPRE                |  Geen bekend problemen               |
| ViRobot              |  Geen bekend problemen               |


---


Laatste Bijgewerkt: 29 Juni 2015 (2015.06.29).