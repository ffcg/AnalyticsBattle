# Analytics PUB den 13 april -16

## Användning av detta subrepot

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