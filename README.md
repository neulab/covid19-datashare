# covid19-datashare
A repo for sharing language resources related to the outbreak (in machine readable format)

## Sources we have already scraped/collected

Parallel Terminologies:
* Translations of covid19-related terms in dozens of languages and locales, provided by Facebook and Google.

Parallel:
* Coronavirus advice from the [Doctors of the World](https://www.doctorsoftheworld.org.uk/coronavirus-information/) (47 languages; last updated May 10th)
* Data from the [COVID-19 Myth Busters in World Languages](https://covid-no-mb.org/) project (28 languages; last updated May 9th)
* The [Zhejiang handbook](https://covid-19.alibabacloud.com/) (10 languages)
* International SOS Need-to-know slides [vietnamese example](https://pandemic.internationalsos.com/-/media/pandemic/files/pan-comms-new-corona-virus/intlsos_coronavirus_disease_2019_talk_simplified_v3_vi_vn.pptx) (6 languages)
* [Canadian Government Public Service Announcements](https://www.sac-isc.gc.ca/eng/1583781906998/1583781926813) (21 languages)
* [King County (WA) fact sheet](https://welcoming.seattle.gov/covid-19/?utm_source=WASCLA+Members&utm_campaign=f9ef53ee9b-EMAIL_CAMPAIGN_2020_03_04_10_45&utm_medium=email&utm_term=0_ec7c02e82f-f9ef53ee9b-47852315&mc_cid=f9ef53ee9b&mc_eid=6e5511a48a#top) (12 languages)
* Crowd Sourced Translations from [source 1](https://drive.google.com/file/d/12KBKTLwHcBDIO5zV7nuOk2MtuaQ9FNPy/view?fbclid=IwAR01nqJu6DN_RIsoJSfCSCCR-vxPkmzLN8UKmeyIB_ORdWX6rTK795i6Pi8) and [source 2](https://docs.google.com/document/d/1JiBETtDgl1Y2defcjAALBB9-bCSKOMSFUC_0P_G9mAM/edit#) for the languages of the Philippines (13 and 8 languages) 
* Translations related to COVID-19 originally created by [https://translatorswithoutborders.org/covid-19](https://translatorswithoutborders.org/covid-19) and [https://better.sg/migrantworkertranslations/](https://better.sg/migrantworkertranslations/). Taken from [this Kaggle Dataset](https://www.kaggle.com/alvations/covid19-translations/) created and shared by [Liling Tang](http://alvations.com).

Monolingual/Comparable:
* Wikipedia -- last updated March 25th 2020.
* BBC World Service (22 languages) -- last updated May 8th 2020.
* Voice of America (31 languages) -- last updated March 26th 2020.
* [Deutsche Welle](https://www.dw.com/) (29 languages) -- last updated May 9th 2020.
* [El Diario](diario.aw) (Papiamento language) -- last updated April 6th 2020.


Other Collections from our friends:
* The [Translators Without Borders](https://translatorswithoutborders.org/) have compiled [glossaries](https://translatorswithoutborders.org/twb-glossary-for-covid-19/) and are starting to provide [translations](https://translatorswithoutborders.org/translations-covid-19/).
* [TAUS](https://www.taus.net/) has compiled a corpus of COVID-19-related parallel sentences. Available [here](https://md.taus.net/corona). Note that these corpora are published under the CC BY-NC 4.0 license which means the data can be shared and modified only for non-commercial purposes.  
* Microsoft has collected covid19-related bing search logs (desktop users only) over the period of Jan 1st, 2020 – April 18th, 2020. They are [here](https://github.com/microsoft/BingCoronavirusQuerySet)
* An international team of scientists that tries to estimate the number of cases with COVID-19 symptoms in different countries have put out [surveys](https://github.com/GCGImdea/coronasurveys/blob/master/surveys.md) in 57 languages. (HT: @juliakreutzer)
* The [COVID-19 Myth Busters in World Languages](https://covid-no-mb.org/) has information in 31+ languages.
* The [EMEA corpus](http://opus.nlpl.eu/EMEA.php) provides pdf conversions of documents from the European Medicines Agency (22 languages, 231 bitexts).
* SketchEngine has collected an [English in-domain corpus](https://www.sketchengine.eu/covid19/).


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


## Contact/Contributors

Here is who has contributed content so far:
* Facebook terminologies: Facebook. Contact: [Francisco (Paco) Guzman](http://guzmanhe.github.io/)
* Google terminologies: Google. Contact: Mengmeng Niu (mniu [at] google [dot] com) and Ian Hill (ihill [at] google [dot] com)
* The Zhejiang handbook: [Alp Öktem](https://alpoktem.github.io/) from TWB.
* The Kaggle dataset was originally compiled by [Liling Tang](http://alvations.com)
* Everything else was scraped by Neulab members: [Junjie Hu](http://www.cs.cmu.edu/~junjieh/), [Zi-Yi Dou](https://scholar.google.com/citations?user=RWogNsEAAAAJ&hl=en), and [Antonis Anastasopoulos](http://www.cs.cmu.edu/~aanastas/). Contact: Antonis.
* Microsoft shared their URL list from past disaster responses. Contact: [Will Lewis](https://www.microsoft.com/en-us/research/people/wilewis/)
* [Hady Elsahar](https://www.hadyelsahar.io/) did an initial scraping of covid19 wikipedia domains: It's [here](https://github.com/hadyelsahar/covid-domains).
