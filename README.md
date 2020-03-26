# covid19-datashare
A repo for sharing language resources related to the outbreak (in machine readable format)

## Data file format

The industry standard for sharing parallel data is TMX. TAUS and other translators can easily share their data in this format.

For other scraped/collected/filtered data (e.g. monolingual news articles) we suggest a very simple xml format, as it is important to add some metadata information, where available. This can/should include: 

* lang: the language of the document (please use ISO-3, three-letter codes)
* source: (e.g. url or other dataset) 
* type: to denote the type of data e.g. mono, parallel, comparable, terminology, translation memory, and others. 
I also added: 
* a 'docid' field: can be used to match parallel docs across languages, or to map filtered/aligned docs to their original dumped version.
* a 'term' field: to be used if we have other information, e.g. some monolingual texts that were filtered based on some term (e.g. COVID, SARS, Ebola).

Example for document level:
```
<doc docid='bbc_51871911' lang='eng' type='mono' source_url='https://www.bbc.co.uk/gahuza/51871911' term='COVID'>
text text text
</doc>
```

If we manage to align documents at the sentence level, we can add 'sent_id' information e.g.
```
<doc docid='bbc_51871911' lang='eng' type='mono' source_url='https://www.bbc.co.uk/gahuza/51871911' term='COVID'>
<s sent_id='1'>text text text</s>
<s sent_id='2'>text text text</s>
...
</doc>
```



