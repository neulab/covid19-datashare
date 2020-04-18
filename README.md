# covid19-datashare
A repo for sharing language resources related to the outbreak (in machine readable format)

## Directory Organization
This is the suggested organization. Hopefully some content will move from one bucket to another, as we keep refining it.
Additional information (eg. metadata) can be added through xml tags (see below).

```
Parallel 
- TMs (homogeneous)
- Terminologies (homogeneous)
- Documents (homogeneous)
- Sentences (sparse)
- Terms (sparse)

Comparable 
- Documents (not translations, wiki pages)
- Sentences (as above)

Back-translated (xml defines original and MT and engine)
- documents 
- sentences

Monolingual
- Documents (pages, docs) 
- Sentences ( e.g tweets) 
```

Some of the data are not available under a CC-0 license (which is the default license for this repository) 
For the data that we reproduce/share under a different license (e.g. CC BY-SA 3.0 or others), this is denoted by the name of the directory and a corresponding README.

## Data file format

The industry standard for sharing parallel data is TMX. TAUS and other translators can easily share their data in this format.

For other scraped/collected/filtered data (e.g. monolingual news articles) we suggest a very simple xml format, as it is important to add some metadata information, where available. This can/should include: 

* 'lang': the language of the document (please use ISO-3, three-letter codes)
* 'source': (e.g. url or other dataset) 
* 'type': to denote the type of data e.g. mono, parallel, comparable, terminology, translation memory, and others. 
* 'docid': can be used to match parallel docs across languages, or to map filtered/aligned docs to their original dumped version.

Also, optionally you can add: 
* a 'term' field: to be used if we have other information, e.g. some monolingual texts that were filtered based on some term (e.g. COVID, SARS, Ebola).
* a 'original_lang' field: in the case of translated data, it'd be good to define the source
* a 'translation_mode': in the case of (back-)translated data, please denote if this was "auto" (for MT) or "manual" (for human-generated translations).

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

If you can't or don't want to convert your data into this xml, you could also share plain text files, but also add a README that will provide information on the source of the data, the type, etc etc

For sharing large files, you can also upload a compressed archive. The current repo tracks `.zip` and `.tar.gz` files and stores them using [git-lfs](https://git-lfs.github.com/).

## Sources we have already scraped/collected

Parallel:
* The [Zhejiang handbook](https://covid-19.alibabacloud.com/) (10 languages)
* International SOS Need-to-know slides [vietnamese example](https://pandemic.internationalsos.com/-/media/pandemic/files/pan-comms-new-corona-virus/intlsos_coronavirus_disease_2019_talk_simplified_v3_vi_vn.pptx) (6 languages)
* [Canadian Government Public Service Announcements](https://www.sac-isc.gc.ca/eng/1583781906998/1583781926813) (21 languages)
* [King County (WA) fact sheet](https://welcoming.seattle.gov/covid-19/?utm_source=WASCLA+Members&utm_campaign=f9ef53ee9b-EMAIL_CAMPAIGN_2020_03_04_10_45&utm_medium=email&utm_term=0_ec7c02e82f-f9ef53ee9b-47852315&mc_cid=f9ef53ee9b&mc_eid=6e5511a48a#top) (12 languages)
* Crowd Sourced Translations from [source 1](https://drive.google.com/file/d/12KBKTLwHcBDIO5zV7nuOk2MtuaQ9FNPy/view?fbclid=IwAR01nqJu6DN_RIsoJSfCSCCR-vxPkmzLN8UKmeyIB_ORdWX6rTK795i6Pi8) and [source 2](https://docs.google.com/document/d/1JiBETtDgl1Y2defcjAALBB9-bCSKOMSFUC_0P_G9mAM/edit#) for the languages of the Philippines (13 and 8 languages) 

Monolingual/Comparable:
* Wikipedia
* BBC World Service (22 languages)
* Voice of America (31 languages)
* [Deutsche Welle](https://www.dw.com/) (29 languages)
* [El Diario](diario.aw) (Papiamento language)
* Data from previous Medical Health Exercise (English)

Other Collections:
* [TAUS](https://www.taus.net/) has compiled a corpus of COVID-19-related parallel sentences. Available [here](https://md.taus.net/corona). Note that these corpora are published under the CC BY-NC 4.0 license which means the data can be shared and modified only for non-commercial purposes.  
