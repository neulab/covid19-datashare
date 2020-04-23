File Format
Language and Locale Format
We use BCP-47 (https://tools.ietf.org/html/bcp47) as language and locale code format, conforming to casing specs (https://tools.ietf.org/html/bcp47#section-3.1.4) and will use hyphen to indicate locales or scripts.  

We use two letter language code in most cases except for:

es-419, es-ES
fr-FR, fr-CA
pt-BR, pt-PT
zh-CN, zh-TW, zh-HK

File Format
CSV files with BCP-47 standard with following headers: 
stringID | sourceLang | targetLang | pos | description | sourceString | targetString 

Files are encoded in UTF-8.

pos tags will follow the spelled out pos names in POS Universal tags: https://universaldependencies.org/u/pos/


File Naming Convention
sourceLang_targetLang
The file name should be all lower case. Example: en_af, en_pt-br

Tracking changes
After the initial batch of term commits, we will use the index.csv file to track the following file change status:

Draft (the terms have been translated by professional translators but haven’t been independently reviewed) or Revised
Additional languages are being committed
Additional source terms are being added
Additional translations are being added

index.csv file has headers: file_name | status 

Example: 
en_af.csv | Draft
en_ms.csv | Revised
