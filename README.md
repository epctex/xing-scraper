# Actor - XING Scraper

## XING scraper

Since XING doesn't provide a good and free API, this actor should help you to retrieve data from it. This actor can provide you very detailed

The XING data scraper supports the following features:

-   Search any keyword - You can search for any keyword and find the jobs according to your needs.

-   Filter your search - Filter your search results by any location name or any specific radius.

-   Scrape job - Fetch any job detail that has been published on XING.

-   Scrape profile - You can any person's profile on XING. It is structured and provides all the detail information.

-   Scrape community or group - You can scrape a specific community or group that people are included on.

-   Scrape company - You can scrape all the detailed information from the company profiles.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/xing-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on XING that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on XING.

- `startUrls`: (Optional) (Array) List of XING URLs. You should only provide profile, job, community, company, group or job search URLs.

- `location`: (Optional) (String) Location that you want to filter your search on XING.

- `radius`: (Optional) (Number) Radius that you want to filter your search on XING.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as argument and returns object with data.

- `customMapFunction`: (Optional) (String) Function that takes each objects handle as argument and returns object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific item URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape many as items as possible. Therefore, it forefronts all item detail requests. If actor doesn't block very often it'll scrape 100 items in 1 minute with ~0.04-0.08 compute units.

### XING Scraper Input example

```json
{
  "startUrls":[
    "https://www.xing.com/gruppen/freelance",
    "https://www.xing.com/communities/groups/it-projekte-punkt-de-1004120",
    "https://www.xing.com/pages/spectrumag",
    "https://www.xing.com/profile/Marko_RoeperGrewe",
    "https://www.xing.com/jobs/muenchen-hello-senior-it-consultant-73093508?paging_context=search&search_query%5Bkeywords%5D=hello&search_query%5Blimit%5D=20&search_query%5Boffset%5D=80&ijt=jb_18",
    "https://www.xing.com/search/in/jobs?facets%5B%5D=discipline&keywords=product&location=berlin&nrs=1&page=2&radius=10&section=jobs"
  ],
  "search": "product",
  "location":"berlin",
  "radius":100,
  "proxy":{
    "useApifyProxy": true
  },
  "maxItems": 50,
  "endPage": 2
}


```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## XING Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this XING actor.

## Scraped XING Output

The structure of each item in XING looks like this:

### Profile Detail

```json
{
  "url": "https://www.xing.com/profile/Marko_RoeperGrewe",
  "profilePicture": "https://profile-images.xing.com/images/22a7df06597a426a43a45b16bfc94b9e-5/marko-röper-grewe.1024x1024.jpg",
  "name": "Marko Röper-Grewe",
  "isPremium": true,
  "occupation": "Selbstständig, Freiberuflicher TYPO3 Spezialist, MR-SEO Web-Dienstleistungen",
  "location": "Porst, Deutschland",
  "tags": [
    "TYPO3",
    "Extbase",
    "Fluid",
    "... außer einem frohen Wesen noch",
    "Contentmanagement",
    "CMS",
    "TYPO3 Extensions",
    "Typoscript",
    "TYPO3 Programmierung",
    "Suchmaschinenoptimierung",
    "SEO",
    "XML",
    "Javascript",
    "jquery",
    "MySQL",
    "Datenbank",
    "Optimierung",
    "Performance",
    "Webdeveloper",
    "Code Review",
    "Debugging",
    "Frontend",
    "Qualitätsarbeit",
    "Qualität",
    "Qualitätsprüfung",
    "less",
    "VBA Programmierung",
    "Visual Basic for Applications",
    "Excel Programmierung",
    "Schnittstellenprogrammierung",
    "Search Engine Optimization (SEO)",
    "Git",
    "HTML",
    "PHP",
    "Ajax",
    "Webentwicklung",
    "Responsive Webdesign",
    "CSS",
    "Solr"
  ],
  "timeline": [
    {
      "time": "Bis heute 9 Monate, seit Sep. 2021",
      "occupation": "Vorsitzender",
      "organizationName": "Die PARTEI Ortsverband Köthen"
    },
    {
      "time": "Bis heute 2 Jahre und 5 Monate, seit Jan. 2020",
      "occupation": "Backend-Entwickler TYPO3",
      "organizationName": "brandung GmbH",
      "organizationUrl": "https://www.xing.com/pages/brandung"
    },
    {
      "time": "Bis heute 13 Jahre und 9 Monate, seit Sep. 2008",
      "occupation": "Freiberuflicher TYPO3 Spezialist",
      "organizationName": "MR-SEO Web-Dienstleistungen",
      "organizationUrl": "https://www.xing.com/pages/mr-seoweb-dienstleistungen"
    },
    {
      "time": "5 Monate, Jan. 2021 - Mai 2021",
      "occupation": "Senior TYPO3 Developer",
      "organizationName": "CBE DIGIDEN AG",
      "organizationUrl": "https://www.xing.com/pages/cbedigidenag"
    },
    {
      "time": "4 Monate, Jan. 2021 - Apr. 2021",
      "occupation": "Senior TYPO3 Developer",
      "organizationName": "THE BRETTINGHAMS GmbH",
      "organizationUrl": "https://www.xing.com/pages/thebrettinghamsgmbh"
    },
    {
      "time": "1 Jahr und 6 Monate, März 2019 - Aug. 2020",
      "occupation": "Vorsitzender",
      "organizationName": "DiePARTEI Ortsverband Teltow-Kleinmachnow-Stahnsdorf"
    },
    {
      "time": "6 Jahre und 7 Monate, Aug. 2013 - Feb. 2020",
      "occupation": "Senior Web Developer",
      "organizationName": "wilhelm innovative medien GmbH",
      "organizationUrl": "https://www.xing.com/companies"
    },
    {
      "time": "1 Jahr und 7 Monate, Mai 2018 - Nov. 2019",
      "occupation": "Senior Backend Developer (TYPO3)",
      "organizationName": "Berufsverband der Deutschen Dermatologen"
    },
    {
      "time": "6 Jahre und 9 Monate, Dez. 2012 - Aug. 2019",
      "occupation": "Senior Web Developer",
      "organizationName": "RESMEDIA - Anwälte für IT-IP-Medien"
    },
    {
      "time": "3 Jahre und 2 Monate, Juni 2016 - Juli 2019",
      "occupation": "Senior Web Developer",
      "organizationName": "media consulta Corporate Publishing GmbH"
    },
    {
      "time": "9 Monate, Jan. 2018 - Sep. 2018",
      "occupation": "Backend-Entwickler",
      "organizationName": "brandung GmbH",
      "organizationUrl": "https://www.xing.com/pages/brandung"
    },
    {
      "time": "9 Jahre und 5 Monate, Feb. 2009 - Juni 2018",
      "occupation": "Senior Web Developer",
      "organizationName": "Planwerk"
    },
    {
      "time": "9 Monate, Jan. 2017 - Sep. 2017",
      "occupation": "VBA Programmierer",
      "organizationName": "Ingenieurgesellschaft Nordwest mbH",
      "organizationUrl": "https://www.xing.com/pages/ingenieurgesellschaftnordwestmbh"
    },
    {
      "time": "6 Jahre und 11 Monate, März 2010 - Jan. 2017",
      "occupation": "Webentwickler",
      "organizationName": "Normamed Deutschland AG"
    },
    {
      "time": "6 Jahre und 10 Monate, Nov. 2009 - Aug. 2016",
      "occupation": "Webentwickler",
      "organizationName": "Weisser-Wertheim"
    },
    {
      "time": "7 Jahre und 3 Monate, Juni 2009 - Aug. 2016",
      "occupation": "Webentwickler",
      "organizationName": "internetwarriors gmbh",
      "organizationUrl": "https://www.xing.com/pages/internetwarriorsgmbh"
    },
    {
      "time": "3 Jahre und 11 Monate, Juli 2012 - Mai 2016",
      "occupation": "Webentwickler",
      "organizationName": "IMK Institut für Marketing und Kommunikation",
      "organizationUrl": "https://www.xing.com/companies"
    },
    {
      "time": "1 Jahr und 5 Monate, Nov. 2014 - März 2016",
      "occupation": "Webentwickler",
      "organizationName": "ressourcenmangel GmbH"
    },
    {
      "time": "5 Jahre und 9 Monate, Sep. 2009 - Mai 2015",
      "occupation": "Webentwickler",
      "organizationName": "art core Werbeagentur GmbH"
    },
    {
      "time": "2 Jahre und 1 Monat, Jan. 2011 - Jan. 2013",
      "occupation": "Webentwickler",
      "organizationName": "form4 GmbH & Co. KG",
      "organizationUrl": "https://www.xing.com/pages/form4gmbh-co-kg"
    }
  ],
  "education": [
    {
      "title": "Wirtschaftsinformatik",
      "school": "5 Jahre, Okt. 1998 - Sep. 2003Hochschule Anhalt (FH)"
    }
  ],
  "languages": [
    {
      "name": "Deutsch",
      "level": "Muttersprache"
    },
    {
      "name": "Englisch",
      "level": "Gut"
    }
  ],
  "wants": [
    "den 4. Such-Punkt",
    "damit der Xing Algorithmus endlich Ruhe gibt :-D",
    "Freie Posten in Landkreis- oder Stadtverwaltung",
    "Gleichgesinnte Freiberufler (PHP HTML CSS TYPO3) zum Netzwerken",
    "Die richtigen Zahlen für nächsten Samstag."
  ],
  "interests": [
    "Familie",
    "TYPO3",
    "Wassersport (motorbetrieben)",
    "iPhone",
    "iPad",
    "Siedler von Catan",
    "Science Fiction",
    "Simpsons",
    "Star Gate",
    "Apple",
    "Angeln",
    "ab und zu mal Langweilen",
    "Schlaaaand anfeuern!",
    "Holzbearbeitung",
    "Heimwerken",
    "Dart",
    "Aquaristik",
    "Politik",
    "Grillen"
  ],
  "groups": [
    {
      "name": "Freelance",
      "link": "https://www.xing.com/gruppen/freelance/posts"
    },
    {
      "name": "IT-Projekte.de",
      "link": "https://www.xing.com/communities/groups/it-projekte-punkt-de-1004120/posts"
    },
    {
      "name": "TYPO3 Enterprise Content Management System",
      "link": "https://www.xing.com/communities/groups/typo3-enterprise-content-management-system-1069498/posts"
    },
    {
      "name": "TYPO3",
      "link": "https://www.xing.com/communities/groups/typo3-1099313/posts"
    },
    {
      "name": "Webdesign mit CSS",
      "link": "https://www.xing.com/communities/groups/webdesign-mit-css-1068694/posts"
    }
  ]
}
```

### Community Detail

```json
{
  "url": "https://www.xing.com/communities/groups/it-projekte-punkt-de-1004120",
  "name": "IT-Projekte.de",
  "description": "Finden Sie die richtigen Köpfe, Projekte & Infos. Eine Win-Win Lösung für Unternehmen, Dienstleister, Freelancer, Agenturen.",
  "image": "https://www.xing.com/img/custom/communities/communities_files/c/3/1/3121/size96/IT-Projekte.de-freelancer-1.png?1438784564",
  "hostedBy": "Atasoy Altinci",
  "isPublic": true,
  "moderators": [
    {
      "name": "Atasoy Altinci",
      "url": "https://www.xing.com/profile/Atasoy_Altinci?sc_o=groups_moderator_click"
    },
    {
      "name": "Gökcen Altinci",
      "url": "https://www.xing.com/profile/Goekcen_Altinci2?sc_o=groups_moderator_click"
    },
    {
      "name": "Steffen Sauerbier",
      "url": "https://www.xing.com/profile/Steffen_Sauerbier?sc_o=groups_moderator_click"
    },
    {
      "name": "Olaf Jürgens",
      "url": "https://www.xing.com/profile/Olaf_Juergens6?sc_o=groups_moderator_click"
    },
    {
      "name": "",
      "url": "https://www.xing.comundefined"
    }
  ]
}
```

### Job Detail

```json
{
  "datePosted": "2021-06-30T00:45:15Z",
  "validThrough": "2022-06-30T00:45:15Z",
  "url": "https://www.xing.com/jobs/muenchen-hello-senior-it-consultant-73093508?paging_context=search&search_query%5Bkeywords%5D=hello&search_query%5Blimit%5D=20&search_query%5Boffset%5D=80&ijt=jb_18",
  "title": "Hello, Senior IT Consultant (m/w/d)",
  "location": "München",
  "industry": "Internet und Informationstechnologie",
  "type": "Vollzeit",
  "description": "<div>\n<header><div><div><div><div><div><ul><li>\n                        Karriere\n                      </li></ul></div></div></div></div></div></header><div><main><div><div><div><div><div>\n<div><div>\n                           Zurück\n                        <h1>\n                          Hello, Senior IT Consultant (m/w/d)!\n                        </h1>\n<div> \n                             Vollzeit\n                            \n                            \nMünchen\n\n      \n                            \nMünchen\n\n                           </div>\n</div></div>\n<div>\n<div><h2>\n                          Deine Karriere\n                        </h2></div>\n<div><div>\n<div>\n<h2><strong>\n                                5 Dinge, die Du in diesem Job erleben wirst\n                              </strong></h2>\n<ul>\n<li>\n                                Wie Du unsere Kunden (Mittelstand bis Konzern) fit machst für die nächsten 10 Jahre, indem Du innovative Technologien gezielt einsetzt. Du wirst Dich immer wieder mit neuen IT-Trends beschäftigen und diese zum Teil auch prägen.\n                              </li>\n<li>\n                                Dass der direkte Kontakt zum Kunden durch nichts zu ersetzen ist.\n                              </li>\n<li>\n                                Wie befriedigend es ist, Deine eigenen IT-Projekte von der Konzeption bis hin zur Umsetzung zu realisieren.\n                              </li>\n<li>\n                                Dass aus Deiner Arbeit viele wunderbare Dinge entstehen: elegante IT-Infrastrukturen, schlanke IT-Prozesse und begeisterte Kunden. Für den optimalen Mehrwert vernetzt Du dabei IT und Business.\n                              </li>\n<li>\n                                Beratung, wie sie sein sollte: mit flachen Hierarchien, hohem Anspruch und einem vertrauensvollen zwischenmenschlichen Umgang\n                              </li>\n</ul>\n</div>\n<div>\n<h2><strong>\n                                Dies ist Deine Traumstelle, wenn\n                              </strong></h2>\n<ul>\n<li>\n                                Du was IT-Beratung angeht, kein unbeschriebenes Blatt mehr bist. Du verstehst das Gesamtkonstrukt und weißt, wie man Konzepte für IT Servicemanagement erstellt und bei Kunden auf den Weg bringt.\n                              </li>\n<li>\n                                Du für Deine schnellen und pragmatischen, aber auch fundierten und nachhaltigen IT-Lösungen bekannt bist.\n                              </li>\n<li>\n                                Du Dich in der Welt von ITIL, ISO/IEC, COBIT, MaRisk, BAIT zu Hause fühlst.\n                              </li>\n<li>\n                                Wenn es Dich langweilt, jeden Tag dasselbe zu tun. Bei uns findest Du stets neue Themengebiete und Abwechslung, die Dich nicht nur fachlich, sondern auch persönlich wachsen lässt.\n                              </li>\n<li>\n                                Wenn Du technikverrückt und gleichzeitig sozial kompatibel bist.\n                              </li>\n</ul>\n</div>\n</div></div>\n<div>\n<h3>\n                          Deine Ansprechpartnerin\n                        </h3>\n<div><p>\n                              karriere@ventum.de\n                            </p></div>\n</div>\n</div>\n<div>\n<div><h2>\n                          Deine Benefits\n                        </h2></div>\n<div>\n<h3>\n                          Das gibt es on top\n                        </h3>\n<ul><li>\n                            Ein Fellow (oder wie wir es nennen: Vellow), der Dir in Deinen ersten Wochen bei uns zur Seite steht. \n                          </li></ul>\n<ul><li>\n                            Einen erfahrenen Counselor aus unserem Team, der Dich danach langfristig bei Deiner Karriere- und Lebensplanung berät.\n                          </li></ul>\n<ul><li>\n                            Einen Kisten-Pack-Bonus, wenn Du für uns umziehst. \n                          </li></ul>\n<ul><li>\n                            Wenn Du möchtest: Einen Arbeitsplatz in unserem loftartigen Basislager in München mit Fairtrade Kaffee und Co. Wir sind aber auch offen für alternative Arbeitsmodelle wie Remote-Work. \n                          </li></ul>\n<ul><li>\n                            Arbeitszeiten auf Vertrauensbasis. Wir zählen darauf, dass Du da bist, wenn es nötig ist. Dafür sind wir flexibel, wenn Du mal nachmittags wegmusst. Generell gilt: Ergebnisse vor Stunden.\n                          </li></ul>\n<ul><li>\n                            Deine Karriere unterstützen wir mit 4.000 € Fortbildungsbudget, Fortbildungstagen, Coaching und dem Programm \n                            Career@Ventum.\n                          </li></ul>\n<ul><li>\n                            Viel, viel Gestaltungsspielraum für Deine eigenen Ideen und Visionen. Oder auch mal ein Sabbatical. Schließlich bist Du dann am kreativsten und produktivsten, wenn Du glücklich bist.\n                          </li></ul>\n</div>\n<div><h3>\n                          Alle Insights:\n                        </h3></div>\n</div>\n<div>\n<div><h2>\n                          Das Unternehmen\n                        </h2></div>\n<div>\n<b>\n                          Das Wichtigste über uns\n                        </b><ul><li>\n                            Als mittelständische Beratung mit 6 Standorten in München und der Welt helfen wir unseren Kunden dabei, digital, agil und vernetzt zu arbeiten.\n                          </li></ul>\n<ul><li>\n                            Unsere Arbeitsphilosophie in vier Worten? Freude, Fairness und fantastische Ergebnisse. Unser Anspruch ist Exzellenz ohne Kompromisse, dafür mit einem wertschätzenden Miteinander.\n                          </li></ul>\n<ul><li>\n                            150 Kolleg:innen mit internationalem Background sorgen für frischen Wind und ein vielschichtiges Umfeld. Charakterköpfe willkommen!\n                          </li></ul>\n</div>\n</div>\n<div>\n<div><h2>\n                          Bewerben\n                        </h2></div>\n<div>\n<h3>\n                          Wie geht’s weiter?\n                        </h3>\n<ul><li>\n                            Du hast noch Fragen? Wir stehen Dir gerne Rede und Antwort. Schreib uns einfach eine Mail an \n                            work@ventum.de\n                            !\n                          </li></ul>\n<ul><li>\n                            Du bist bereit für die Bewerbung? Dafür musst Du Dir bei uns kein Bein ausreißen: Lebenslauf hochladen oder Xing-Profil angeben. Relevante Zeugnisse und Gehaltsvorstellung mitschicken. Fertig. Das Anschreiben sparen wir uns!\n                          </li></ul>\n<br>\n</div>\n</div>\n</div></div></div></div></div></main></div>\n</div>\n<span data-version=\"1.2.0-x106\"></span>",
  "employer": {
    "name": "Ventum Consulting GmbH & Co. KG",
    "url": "https://www.xing.com/companies"
  },
  "similarJobs": [
    {
      "title": "Hello, Senior IT Consultant (m/w/d)!",
      "url": "https://www.xing.com/jobs/muenchen-hello-senior-it-consultant-84563955?ijt=jb_20&paging_context=similar_postings"
    },
    {
      "title": "Senior IT Consultant (w|m|d)",
      "url": "https://www.xing.com/jobs/muenchen-senior-it-consultant-85123987?ijt=jb_20&paging_context=similar_postings"
    },
    {
      "title": "Hello, Senior Consultant Projektmanagement im Bereich Komponentenentwicklung (m/w/d)",
      "url": "https://www.xing.com/jobs/muenchen-hello-senior-consultant-projektmanagement-bereich-komponentenentwicklung-82888696?ijt=jb_20&paging_context=similar_postings"
    },
    {
      "title": "Hello, Senior Consultant Business Process Management (m/w/d)",
      "url": "https://www.xing.com/jobs/muenchen-hello-senior-consultant-business-process-management-84811130?ijt=jb_20&paging_context=similar_postings"
    },
    {
      "title": "Senior IT Consultant - Streaming & Messaging / Java / Kanban (m/w/d)",
      "url": "https://www.xing.com/jobs/muenchen-senior-it-consultant-streaming-messaging-java-kanban-84885011?ijt=jb_20&paging_context=similar_postings"
    },
    {
      "title": "Senior IT Consultant - UML / Datenbank (m/w/d)",
      "url": "https://www.xing.com/jobs/muenchen-senior-it-consultant-uml-datenbank-84947610?ijt=jb_20&paging_context=similar_postings"
    },
    {
      "title": "Senior IT Consultant IT M&A / Corporate IT (m/w/d)",
      "url": "https://www.xing.com/jobs/muenchen-senior-it-consultant-it-corporate-it-85036508?ijt=jb_20&paging_context=similar_postings"
    },
    {
      "title": "Senior IT Consultant (m/w/d) Requirements Engineering / Business Analytic",
      "url": "https://www.xing.com/jobs/muenchen-senior-it-consultant-requirements-engineering-business-analytic-83201062?ijt=jb_20&paging_context=similar_postings"
    },
    {
      "title": "Senior IT Consultant & Process Manager (m|w|d)",
      "url": "https://www.xing.com/jobs/muenchen-senior-it-consultant-process-manager-82813400?ijt=jb_20&paging_context=similar_postings"
    }
  ]
}
```

### Company Detail

```json
{
  "url": "https://www.xing.com/pages/spectrumag",
  "profilePicture": "https://www.xing.com/imagecache/public/scaled_original_image/eyJ1dWlkIjoiZTM5ZjM0ZDItMzViMy00ZWZmLThmNDYtODkyZGI1MWIwN2Y2IiwiYXBwX2NvbnRleHQiOiJlbnRpdHktcGFnZXMiLCJtYXhfd2lkdGgiOjMyMCwibWF4X2hlaWdodCI6MzIwfQ?signature=d867802c9cbd0d5fdec92f884f3f9bbf53a420e783b6fd81717662ab833a6fda",
  "name": "NeuigkeitenÜber unsAuszeichnungenJobsBewertungen & KulturZitate von MitarbeitendenVorteile für MitarbeitendeMitarbeitendeAnsprechpersonenStandort",
  "kununuRating": "4,3/5",
  "recommendRate": "",
  "jobs": [
    {
      "name": "Trainee Projektmanager (m/w/d)",
      "link": "https://www.xing.com/jobs/duesseldorf-trainee-projektmanager-84924207?ijt=jb_40",
      "location": "Düsseldorf, Deutschland"
    },
    {
      "name": "Trainee SCRUM Master (m/w/d)",
      "link": "https://www.xing.com/jobs/muenchen-trainee-scrum-master-84924233?ijt=jb_40",
      "location": "München, Deutschland"
    },
    {
      "name": "Junior Business Analyst (m/w/d)",
      "link": "https://www.xing.com/jobs/muenchen-junior-business-analyst-84720800?ijt=jb_40",
      "location": "München, Deutschland"
    },
    {
      "name": "Trainee (m/w/d) IT-Consultant Risikomanagement",
      "link": "https://www.xing.com/jobs/heidelberg-trainee-it-consultant-risikomanagement-84112581?ijt=jb_40",
      "location": "Heidelberg, Deutschland"
    },
    {
      "name": "Trainee Data Analyst (m/w/d)",
      "link": "https://www.xing.com/jobs/frankfurt-main-trainee-data-analyst-83910443?ijt=jb_40",
      "location": "Frankfurt am Main, Deutschland"
    },
    {
      "name": "Trainee Account Manager (m/w/d)",
      "link": "https://www.xing.com/jobs/frankfurt-main-trainee-account-manager-83910142?ijt=jb_40",
      "location": "Frankfurt am Main, Deutschland"
    },
    {
      "name": "Trainee (m/w/d) Java - Entwickler",
      "link": "https://www.xing.com/jobs/koeln-trainee-java-entwickler-83867952?ijt=jb_40",
      "location": "Köln, Deutschland"
    }
  ],
  "employeeReviews": [
    {
      "rating": "5.0",
      "currentStatus": "Arbeitet hier",
      "date": "Mär 22",
      "message": "An employer that respects you and your time"
    },
    {
      "rating": "5.0",
      "currentStatus": "Arbeitet hier",
      "date": "Feb 22",
      "message": "Best place to work."
    },
    {
      "rating": "5.0",
      "currentStatus": "Arbeitet hier",
      "date": "Jan 22",
      "message": "Very knowledgeable and Helpful Staff"
    },
    {
      "rating": "5.0",
      "currentStatus": "Arbeitet hier",
      "date": "Dez 21",
      "message": "Guter Arbeitgeber!"
    },
    {
      "rating": "5.0",
      "currentStatus": "Arbeitet hier",
      "date": "Nov 21",
      "message": "Ein Unternehmen das Spass macht"
    },
    {
      "rating": "4.8",
      "currentStatus": "Hat hier gearbeitet",
      "date": "Nov 21",
      "message": "Viele Möglichkeiten, wenn man gewillt ist sich einzubringen und auch in schwierigen Zeiten bereit ist mitzuziehen"
    },
    {
      "rating": "4.6",
      "currentStatus": "Hat hier gearbeitet",
      "date": "Nov 21",
      "message": "Für den Einstieg gut."
    },
    {
      "rating": "2.5",
      "currentStatus": "Hat hier gearbeitet",
      "date": "Nov 21",
      "message": "Gutes Konzept, mangelhafte Umsetzung"
    },
    {
      "rating": "2.1",
      "currentStatus": "Hat hier gearbeitet",
      "date": "Nov 21",
      "message": "Kann ich nicht empfehlen"
    },
    {
      "rating": "2.1",
      "currentStatus": "Hat hier gearbeitet",
      "date": "Nov 21",
      "message": "Gutes Konzept mangelhaft geführt"
    },
    {
      "rating": "4.8",
      "currentStatus": "Arbeitet hier",
      "date": "Apr 21",
      "message": "Angenehme Zusammenarbeit auch in der Corona-Zeit"
    },
    {
      "rating": "4.6",
      "currentStatus": "Arbeitet hier",
      "date": "Mär 21",
      "message": "Alles andere nur kein kleines Unternehmen mit viel Engagement"
    }
  ],
  "benefits": [
    {
      "rate": "55%",
      "name": "Flexible Arbeitszeiten"
    },
    {
      "rate": "54%",
      "name": "Veranstaltungen"
    },
    {
      "rate": "40%",
      "name": "40%Günstige Anbindung"
    }
  ],
  "employees": [
    {
      "name": "Cham Almatar",
      "url": "/profile/Cham_Almatar?sc_o=entity_page_profile_other_visit_main_employees"
    },
    {
      "name": "Gemma Baillie",
      "url": "/profile/Gemma_Baillie?sc_o=entity_page_profile_other_visit_main_employees"
    },
    {
      "name": "Aaron Baur",
      "url": "/profile/Aaron_Baur?sc_o=entity_page_profile_other_visit_main_employees"
    },
    {
      "name": "Franziska Fink",
      "url": "/profile/Franziska_Fink14?sc_o=entity_page_profile_other_visit_main_employees"
    }
  ],
  "contactPeople": [],
  "contact": {
    "headline": "Stuttgart",
    "address": "Schulze-Delitzsch-Straße 41, 70565 Stuttgart, Deutschland",
    "phone": "Telefon: +49 711 7819420",
    "websiteLink": "https://www.spectrum-ag.de"
  },
  "description": {
    "html": "<h2 class=\"headlinestyles__Headline-sc-1gpssxl-0 bDwiDk Description-Description-headerText-e30a9498\">SPECTRUM AG</h2><div class=\"ReadMore-ReadMore-textArea-ba1c6451\" style=\"max-height:330px\"><div class=\"ReadMore-ReadMore-textAreaInner-ae570bdb\"><div class=\"content-editor-core-viewer-viewer-viewer-e66f7512\"><h3 class=\"content-editor-plugin-heading-Heading-heading-f58e97f8 content-editor-plugin-heading-Heading-heading3-a4a0f230\" data-editor-plugin=\"h3\">Wir machen aus Talenten Experten.</h3><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\"><strong>FÜR BERUFSEINSTEIGER</strong> finden wir einzigartige Einstiegsjobs, auch ohne Berufserfahrung.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\"><strong>FÜR UNTERNEHMEN</strong> bieten wir qualifizierte Nachwuchskräfte und erfahrene IT-Experten im Rundum-Sorglos-Paket. Mit unseren Upskilling Services helfen wir zudem bei der Weiterentwicklung ihrer Fach- und Führungskräfte.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\"><strong>Keine Berufserfahrung und auf der Suche nach einem Berufseinstieg?</strong></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">· Dann bewirb Dich für unser außergewöhnliches Traineeprogramm.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">· Gemeinsam qualifizieren wir Dich für Deinen Traumjob.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">· Wir schließen die Lücke zwischen dem, was Du im Studium gelernt hast und dem, was die Berufspraxis von Dir verlangen wird.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">· Extra auf Dich abgestimmte Schulungsprogramme fungieren als Ergänzung zur Praxis.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">· Deine Vorteile: unbefristeter Arbeitsvertrag, fairer Ausgleich zwischen Beruf und Freizeit, intensive Betreuung durch Deinen persönlichen Mentor, kollegiales und vertrauensvolles Miteinander, u.v.m.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\"><strong>FOLGE UNSEREM BLOG!</strong> Studium, Bewerbung und Berufseinstieg. Hier abonnieren und jeden Monat interessante und informative Beiträge für Junge Talente erhalten: </p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\"><a rel=\"nofollow\" class=\"content-editor-plugin-link-Link-link-fe1bcbc5\" href=\"https://newsroom.spectrum-ag.de/newsletter/\" target=\"_blank\">https://newsroom.spectrum-ag.de/newsletter/</a></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\"><strong>Auf der Suche nach qualifizierten Talenten?</strong></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">· Egal ob aufgrund von Fachkräftemangel, Digitalisierung, demographischem Wandel oder anderen Herausforderungen: Wir haben, finden oder bilden die richtigen Talente für Ihr Unternehmen aus.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">· Unsere Services:</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\"><strong>CAREER SOLUTIONS</strong>: Nachwuchsprogramm für Ihre individuellen Vakanzen.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\"><strong>EXPERT RECRUITING+</strong>: Rekrutierung und Qualifizierung erfahrener Experten maßgeschneidert für Ihr Unternehmen.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\"><strong>UPSKILLING SERVICES</strong>: Individuelle Weiterentwicklung der digitalen Kompetenz Ihrer Fach- und Führungskräfte.</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\"><strong>MEHR ERFAHREN</strong></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">Fragen, Feedback, mehr erfahren? Ganz einfach über:</p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">Homepage:&nbsp;<a rel=\"nofollow\" class=\"content-editor-plugin-link-Link-link-fe1bcbc5\" href=\"http://www.spectrum-ag.de/de/\" target=\"_blank\">https://www.spectrum-ag.de/de/</a></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">Jobs: <a rel=\"nofollow\" class=\"content-editor-plugin-link-Link-link-fe1bcbc5\" href=\"https://jobs.spectrum-ag.de/Jobs\" target=\"_blank\">https://jobs.spectrum-ag.de/Jobs</a></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">Facebook:&nbsp;<a rel=\"nofollow\" class=\"content-editor-plugin-link-Link-link-fe1bcbc5\" href=\"https://www.facebook.com/spectrumag/\" target=\"_blank\">https://www.facebook.com/spectrumag/</a></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">Twitter:&nbsp;<a rel=\"nofollow\" class=\"content-editor-plugin-link-Link-link-fe1bcbc5\" href=\"https://twitter.com/spectrum_ag\" target=\"_blank\">https://twitter.com/spectrum ag</a></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">Instagram: <a rel=\"nofollow\" class=\"content-editor-plugin-link-Link-link-fe1bcbc5\" href=\"https://www.instagram.com/spectrum_ag/\" target=\"_blank\">https://www.instagram.com/spectrum ag/</a></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">LinkedIn:&nbsp;<a rel=\"nofollow\" class=\"content-editor-plugin-link-Link-link-fe1bcbc5\" href=\"https://www.linkedin.com/company/spectrum-ag\" target=\"_blank\">https://www.linkedin.com/company/spectrum-ag</a></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">YouTube:&nbsp;<a rel=\"nofollow\" class=\"content-editor-plugin-link-Link-link-fe1bcbc5\" href=\"https://www.youtube.com/channel/UCv-xR0JV0yx3iL0JMlkcYeQ\" target=\"_blank\">https://www.youtube.com/channel/UCv-xR0JV0yx3iL0JMlkcYeQ</a></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">Pinterest: <a rel=\"nofollow\" class=\"content-editor-plugin-link-Link-link-fe1bcbc5\" href=\"https://www.pinterest.de/spectrum_ag/_created/\" target=\"_blank\">https://www.pinterest.de/spectrum_ag/_created/</a></p><p class=\"content-editor-plugin-paragraph-Paragraph-paragraph-b59ad9d8 Description-Description-paragraph-e0037d80\">Impressum:&nbsp;<a rel=\"nofollow\" class=\"content-editor-plugin-link-Link-link-fe1bcbc5\" href=\"https://www.spectrum-ag.de/de/impressum/\" target=\"_blank\">https://www.spectrum-ag.de/de/impressum/</a></p></div></div></div>",
    "text": "SPECTRUM AGWir machen aus Talenten Experten.FÜR BERUFSEINSTEIGER finden wir einzigartige Einstiegsjobs, auch ohne Berufserfahrung.FÜR UNTERNEHMEN bieten wir qualifizierte Nachwuchskräfte und erfahrene IT-Experten im Rundum-Sorglos-Paket. Mit unseren Upskilling Services helfen wir zudem bei der Weiterentwicklung ihrer Fach- und Führungskräfte.Keine Berufserfahrung und auf der Suche nach einem Berufseinstieg?· Dann bewirb Dich für unser außergewöhnliches Traineeprogramm.· Gemeinsam qualifizieren wir Dich für Deinen Traumjob.· Wir schließen die Lücke zwischen dem, was Du im Studium gelernt hast und dem, was die Berufspraxis von Dir verlangen wird.· Extra auf Dich abgestimmte Schulungsprogramme fungieren als Ergänzung zur Praxis.· Deine Vorteile: unbefristeter Arbeitsvertrag, fairer Ausgleich zwischen Beruf und Freizeit, intensive Betreuung durch Deinen persönlichen Mentor, kollegiales und vertrauensvolles Miteinander, u.v.m.FOLGE UNSEREM BLOG! Studium, Bewerbung und Berufseinstieg. Hier abonnieren und jeden Monat interessante und informative Beiträge für Junge Talente erhalten: https://newsroom.spectrum-ag.de/newsletter/Auf der Suche nach qualifizierten Talenten?· Egal ob aufgrund von Fachkräftemangel, Digitalisierung, demographischem Wandel oder anderen Herausforderungen: Wir haben, finden oder bilden die richtigen Talente für Ihr Unternehmen aus.· Unsere Services:CAREER SOLUTIONS: Nachwuchsprogramm für Ihre individuellen Vakanzen.EXPERT RECRUITING+: Rekrutierung und Qualifizierung erfahrener Experten maßgeschneidert für Ihr Unternehmen.UPSKILLING SERVICES: Individuelle Weiterentwicklung der digitalen Kompetenz Ihrer Fach- und Führungskräfte.MEHR ERFAHRENFragen, Feedback, mehr erfahren? Ganz einfach über:Homepage: https://www.spectrum-ag.de/de/Jobs: https://jobs.spectrum-ag.de/JobsFacebook: https://www.facebook.com/spectrumag/Twitter: https://twitter.com/spectrum agInstagram: https://www.instagram.com/spectrum ag/LinkedIn: https://www.linkedin.com/company/spectrum-agYouTube: https://www.youtube.com/channel/UCv-xR0JV0yx3iL0JMlkcYeQPinterest: https://www.pinterest.de/spectrum_ag/_created/Impressum: https://www.spectrum-ag.de/de/impressum/"
  },
  "foundedYear": "1986 gegründet",
  "legalNotice": "https://www.spectrum-ag.de/de/impressum/",
  "industries": [
    "Internet und Informationstechnologie"
  ],
  "website": "https://www.spectrum-ag.de",
  "affiliates": [
    {
      "name": "W&W-GruppeW&W-Gruppe Follower",
      "url": "https://www.xing.com/pages/wwgruppe?sc_o=entity_page_about_us_affiliate_visit"
    },
    {
      "name": "ADACADAC Follower",
      "url": "https://www.xing.com/pages/adac?sc_o=entity_page_about_us_affiliate_visit"
    },
    {
      "name": "SV SparkassenVersicherungSV SparkassenVersicherung Follower",
      "url": "https://www.xing.com/pages/svsparkassenversicherung?sc_o=entity_page_about_us_affiliate_visit"
    },
    {
      "name": "VR Smart FinanzVR Smart Finanz Follower",
      "url": "https://www.xing.com/pages/vrsmartfinanz?sc_o=entity_page_about_us_affiliate_visit"
    },
    {
      "name": "SPIRIT/21 GmbHSPIRIT/21 GmbH Follower",
      "url": "https://www.xing.com/pages/spirit21?sc_o=entity_page_about_us_affiliate_visit"
    },
    {
      "name": "Preh GmbHPreh GmbH Follower",
      "url": "https://www.xing.com/pages/prehgmbh?sc_o=entity_page_about_us_affiliate_visit"
    },
    {
      "name": "Xylem Water Solutions Deutschland GmbHXylem Water Solutions Deutschland GmbH Follower",
      "url": "https://www.xing.com/pages/xylem?sc_o=entity_page_about_us_affiliate_visit"
    },
    {
      "name": "Lebensversicherung von 1871 a.G. MünchenLebensversicherung von 1871 a.G. München Follower",
      "url": "https://www.xing.com/pages/lebensversicherungvon1871a-g?sc_o=entity_page_about_us_affiliate_visit"
    },
    {
      "name": "ALH GruppeALH Gruppe Follower",
      "url": "https://www.xing.com/pages/alteleipziger-halleschekonzern?sc_o=entity_page_about_us_affiliate_visit"
    },
    {
      "name": "Mecklenburgische VersicherungsgruppeMecklenburgische Versicherungsgruppe Follower",
      "url": "https://www.xing.com/pages/mecklenburgischeversicherungsgruppe?sc_o=entity_page_about_us_affiliate_visit"
    }
  ]
}
```
