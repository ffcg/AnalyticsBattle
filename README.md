# Analytics PUB den 13 april -16 

**Varmt Välkomna till Forefronts nästa kompetensevent!**

<img width="300" height="100" src="https://camo.githubusercontent.com/0b620ce36d82944a4cd0f59cdfea477b36f50964/68747470733a2f2f6c68342e676f6f676c6575736572636f6e74656e742e636f6d2f35786876787379626a73355169344575595a6d6456436558556672636730784d58754a5169326d416f7270642d54704c396f55417537704c6e6f7461584b382d69347a346451" data-canonical-src="https://lh4.googleusercontent.com/35xhvxsybjs5Qi4EuYZmdVCeXUfrcg0xMXuJQi2mAorpd-TpL9oUAu7pLnotaXK8-i4z4dQ" /> <br/>

> Datum: Onsdag den 13 april

> Tid: Klockan 17:30

> Plats: Forefront Consulting Group. Holländargatan 13, våning 5

**Nu** startar vi även upp våra populära kompetenspubar inom området Analytics. Ämnet för kvällen är ”Möjligheter med textanalys”. Vi kommer att belysa vilken nytta man kan uppnå med textanalys samt presentera resultatet av en jämförelse som vi gjort mellan Gavagais, MS och SAS verktyg. Förutom intressanta presentationer bjuder vi på trevligt mingel samt mat och dryck. 

Slutligen blir det ”Battle” mellan dessa leverantörer. De kommer att visa hur textanalys genomförs med hjälp av olika verktyg och vilket resultat man kan få fram. Givetvis finns det utrymme för frågor och vidare diskussioner. 

Detta får ni inte missa!

Vänligen [OSA senast torsdag den 7 april](https://docs.google.com/forms/d/1J_BSyP-ht4a0FXE0Zhta7UlXggg9ymGQZJuht0TzW1Q/viewform?c=0&w=1). 

<img width="250" height="250" src="https://camo.githubusercontent.com/bdfbbb86d57fb2a321b81156f7b3749d44197fc2/68747470733a2f2f6c68362e676f6f676c6575736572636f6e74656e742e636f6d2f576c79794e57693279306632373637764c383738364e5f423061654b57546f67503074744164617a39547a6a375a76443569666b7158717a575566303862642d433753386c51" data-canonical-src="https://lh6.googleusercontent.com/WlyyNWi2y0f2767vL8786N_B0aeKWTogP0ttAdaz9Tzj7ZvD5ifkqXqzWUf08bd-C7S8lQ" />
![Microsoft](https://lh4.googleusercontent.com/6IyGBSy89kzKKRc5gaog8eCY42_47u_-g9eChZVoW398Aswbbtw2VbRIQFxVgfTsWbEgOg)
![SAS](https://lh4.googleusercontent.com/INqn118wdUaCVDhg8fYNioTTuQziqfIAOAZR4x4IuiUqMh9ieyh7XgbQ68L9JEIIxkqxxw)

---

## Användning av detta repot

Se [den här repot](https://github.com/benhamner/hillary-clinton-emails.git) för diverse scripts som använts på email-datan från grunden.

## Strukturen

```
+-- data
¦   +-- original
¦   ¦   +-- Aliases.csv
¦   ¦   +-- EmailReceivers.csv
¦   ¦   +-- Emails.csv
¦   ¦   +-- Persons.csv
¦   ¦   +-- databases.sqlite
¦   ¦   +-- hashes.txt
¦   +-- generated
¦       +-- Candidates.json
¦       +-- US_states.json
+-- scripts
	+-- databases.sqlite.sql
```

## Datan

Från [Kaggle.com/hillary-clinton-emails](https://www.kaggle.com/kaggle/hillary-clinton-emails) kan man få originaldata kring Hillary Clintons emails. Dessa är också upplagda här under `/data`.


### Aliases.csv

```
 - **Id** - unique identifier for internal reference
 - **Alias** - text in the From/To email fields that refers to the person
 - **PersonId** - person that the alias refers to
```
 
### EmailReceivers.csv

```
 - **Id** - unique identifier for internal reference
 - **EmailId** - Id of the email
 - **PersonId** - Id of the person that received the email
```

### Emails.csv
```
 - **Id** - unique identifier for internal reference
 - **DocNumber** - FOIA document number
 - **MetadataSubject** - Email SUBJECT field (from the FOIA metadata)
 - **MetadataTo** - Email TO field (from the FOIA metadata)
 - **MetadataFrom** - Email FROM field (from the FOIA metadata)
 - **SenderPersonId** - PersonId of the email sender (linking to Persons table)
 - **MetadataDateSent** - Date the email was sent (from the FOIA metadata)
 - **MetadataDateReleased** - Date the email was released (from the FOIA metadata)
 - **MetadataPdfLink** - Link to the original PDF document (from the FOIA metadata)
 - **MetadataCaseNumber** - Case number (from the FOIA metadata)
 - **MetadataDocumentClass** - Document class (from the FOIA metadata)
 - **ExtractedSubject** - Email SUBJECT field (extracted from the PDF)
 - **ExtractedTo** - Email TO field (extracted from the PDF)
 - **ExtractedFrom** - Email FROM field (extracted from the PDF)
 - **ExtractedCc** - Email CC field (extracted from the PDF)
 - **ExtractedDateSent** - Date the email was sent (extracted from the PDF)
 - **ExtractedCaseNumber** - Case number (extracted from the PDF)
 - **ExtractedDocNumber** - Doc number (extracted from the PDF)
 - **ExtractedDateReleased** - Date the email was released (extracted from the PDF)
 - **ExtractedReleaseInPartOrFull** - Whether the email was partially censored (extracted from the PDF)
 - **ExtractedBodyText** - Attempt to only pull out the text in the body that the email sender wrote (extracted from the PDF)
 - **RawText** - Raw email text (extracted from the PDF)
```
 
### Persons.csv

```
 - **Id** - unique identifier for internal reference
 - **Name** - person's name
```
 
### database.sqlite

This SQLite database contains all of the above tables (Emails, Persons, Aliases, and EmailReceivers) with their corresponding fields. You can see the schema and ingest code under `scripts/databases.sqlite.sql`

### Candidates.json

This file is a string literal of both the main presidential candidates of the 2016 election and all of the democrats and republicans that have been potential candidates.

### US_states.json

This file is a string literal of all of the American states. Also includes abbreviations in case you want to match with geodata. The written name of the states are also included in Candidates.json as part of each candidate's state belonging. 
