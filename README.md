# Utveksling av metadata om offentlige ressurser på nett

NB! **UNDER UTVIKLING - PÅGÅENDE ARBEID**

HIDA-teamet, Digitaliseringsdirektoratet, januar 2024

Denne siden forvaltes på GitHub: [https://github.com/rockphotog/hida](https://github.com/rockphotog/hida)

Se også åpen [gjøremålsliste](todo.md) og [issues](https://github.com/rockphotog/hida/issues).

---

## Mål

Innholdet beskriver et minimumssett av metadata som kan implementeres som et enkleste brukbare produkt (*MVP*[^1] ) og utprøves ved hjelp av smidig metode.  

*Mål på kort sikt:* Metadatasettet skal testes ut i livshendelsen [Alvorlig sykt barn](https://alvorligsyktbarn.no/) i prosjektet [Enklere tilgang til informasjon](https://alvorligsyktbarn.no/enklere-tilgang-til-informasjon) (ETI) i 2024.  

*Mål på lengre sikt:* Dette **ikke-normerende** dokumentet har som formål å utvikles til en veileder, eller vedlegg til en veileder, som normeres av Digitaliseringsdirektoratet.  

## Behov

### Bakgrunn

Veilederen er utviklet som en del av *Helhetlig informasjon for digital assistanse* (HIDA) hos Digitaliseringsdirektoratet.

Målet er å skape et helheltlig og brukervennlig informasjonstilbud for ulike brukergrupper og på tvers av offentlige tjenester. Det er i dag spesielt tidkrevende og komplekt for brukerne å finne relevant informasjon. En av grunnene er fraværet av felles regler og retningslinjer. Denne veilederen skal bidra til å bøte på det siste.

Les mer på Digitaliseringsbloggen: [Frå silo til samanheng](https://www.digdir.no/sammenhengende-tjenester/fra-silo-til-samanheng/5240).

### Anvendelse

>*Som produsent av offentlig informasjon,*
>
>*ønsker jeg at innhold publisert på internett er tilstrekkelig merket med metadata,*
>
>*slik at innholdet bedre kan tolkes av konsumenter.*

### Begrep brukt i veilederen

**Produsent** er her en offentlig etat som produserer og publiserer offentlig ressurser (innhold, informasjon) beregnet på innbyggere og næringsliv. Innhold publiseres typisk ved hjelp av et publiseringssystem[^2].

**Konsument** er her programvare brukt av andre offentlige etater, innbyggere og næringsliv, slik som programvare-roboter (digitale assistenter, indekseringstjenester/søkemotorer, kunstig intelligens) og systemer for videre publisering.

**Metadata** - Data om data, informasjon som beskriver annen informasjon, gjerne en elektronisk fil som et tekstdokument, bilde eller film.[^3]

**Offentlige ressurser på nett** - ressurser som offentlige virksomheter forvalter som er adresserte med HTTP eller HTTPS-protokollen[^4]. Eksempelvis artikler og informasjon til innbyggere og næringsliv.

## Juridisk samhandlingsevne

Det er ingen juridiske føringer for anvendelsen. Det kan vurderes å gjøre normere hele eller deler av denne veilederen ved å gjøre den til en anbefalt eller obligatorisk standard i Referansekatalogen for IT-standarder[^5].

## Organisatorisk samhandlingsevne

<img width="60%" src="diagrams/usecase-a.png" alt="UML use case diagram" />

***Figur 1** Use case-diagram for organisatorisk samhandlingsevne (UML)*

En *produsent* sørger for å publisere informasjon på internett. Produsenten kan også oppdatere eller trekke tilbake informasjonen. Informasjonen som publiseres må beskrives (metadata).

En *konsument* vil kunne lese informasjonen publisert av produsenten, inkludert metadata. En konsument kan bearbeide informasjonen og dele den videre, ved så å innta rollen som produsent.  

<!-- <img width="90%" src="diagrams/organizational-alt-1.png" /> -->
<!-- Må bruke HTML for størrelse på bilder -->

<img width="60%" src="diagrams/organizational.png" alt="archimate business diagram" />

***Figur 2** Organisatorisk samhandlingsevne (ArchiMate)*

## Semantisk samhandlingsevne

Under følger beskrivelse av felles informasjonsmodell, kodeverk/terminologi og syntaks/format for utveksling av metadata.  

<img width="50%" src="diagrams/semantic-eira.png" alt="UML klassediagram for metadata" />

***Figur 3** Semantisk innhold i henhold til EIRA 6.0.0 (konseptuelt utkast, ArchiMate)*

### Informasjonsmodell

Dette er et subsett baseret på funn i HIDA og ETI våren 2023. Minimumskrav er hentet fra [CDV-NO - Spesifikasjon for innholdsbeskrivelser](https://informasjonsforvaltning.github.io/cdvno/). Disse to dokumentene er overlappende og kan vurderes slått sammen.  

<img width="50%" src="diagrams/klassediagram.png" alt="UML klassediagram for metadata" />

***Figur 4** Klassediagram for metadata (UML)*

| **Metadata-felt**       | **Type** | **Krav**                     | **Beskrivelse**                                                  |
|-------------------------|----------|------------------------------|------------------------------------------------------------------|
| **Utgiver**             | enhet    | Obligatorisk                 | Organisasjonen som publiserer teksten på eget nettsted           |
| **Produsent**           | enhet    | Frivillig, flere er mulig    | Organisasjonen som forfatter teksten                             |
| **Beskrivelse**         | tekst    | Frivillig                    | Kort beskrivelse av tekstens innhold og kontekst                 |
| **Hovedspråk**          | kodet    | Obligatorisk                 | Språket størstedelen av teksten er på, se *Kodeverk/terminologi* |
| **Identifikator**       | tekst    | Obligatorisk                 | Unik identifikator i form av URI                                 |
| **Tema**                | kodet    | Obligatorisk, flere er mulig | Tekstens hovedtema basert på Los, se *Kodeverk/terminologi*.     |
| **Tittel**              | tekst    | Obligatorisk                 | Artikkelens tittel                                               |
| **Dato opprettet**      | dato     | Frivillig                    | Dato for publisering                                             |
| **Dato sist oppdatert** | dato     | Frivillig                    | Dato for oppdatering                                             |

### Kodeverk/terminologi

#### Tema

Los benyttes for kor koding av attributtet *tema*.

Los er et felles vokabular som er temainndelt for å kategorisere og beskrive offentlige tjenester og ressurser[^6]. Los brukes her primært for å kategorisere og beskrive offentlige sluttbrukertjenester og ressurser, samt å optimalisere søk på nettsider.

Det kan oppgis tre koder: [NB, se Gjøremålsliste]

1. Det skal som minimum kodes med **hovedtema** - [temastruktur](https://psi.norge.no/los/struktur.html)
2. Det er sterkt anbefalt å kode med **undertema** - [tema](https://psi.norge.no/los/ontologi/tema.html)
3. Det er anbefalt å kode med ett eller flere **emneord** - [ord](https://psi.norge.no/los/ontologi/ord.html)

Se dokumentasjon for Los på data.norge.no: [Los (norge.no)](https://data.norge.no/docs/los-dokumentasjon)

#### Hovedspråk

| ISO 639-1 | ISO 639-3 | Språk |
| --- | --- | --- |
| nb | nob | norsk (bokmål) |
| nn | nno | norsk (nynorsk) |
| no | nor | norsk |
| | smi | samisk |
| se | sme | nordsamisk |
| | smj | lulesamisk |
| | sma | sørsamisk |
| | fkv | kvensk |

Listen er ikke uttømmende.  

### Syntaks/format

Det anbefales å uttrykke metadata på ett eller flere format som kan benyttes med CMS. Det finnes ingen dominerende standard. Mye brukte formater er JSON Linked Data (JSON-LD), RDFa og Microdata. 

Under vises det bruk med felt og datatyper basert på henholdsvis [CDV-NO](https://informasjonsforvaltning.github.io/cdvno/) og [Schema.org](https://schema.org/).

Det finnes andre syntaks/format også, som f.eks. [OpenGraph](https://ogp.me). I prinsippet bør man forvalte og vedlikeholde en guide for mapping mot de til enhver mest aktuelle formatene.

#### Kobling mellom informasjonsmodell og CDV-NO og Schema.org

| **Metadata-felt**       | **[CDV-NO](https://informasjonsforvaltning.github.io/cdvno/)**      | *datatype*           | | **[Schema.org](https://schema.org/)** | *datatype*                           |
|-------------------------|-----------------|----------------------|-|----------------|--------------------------------------|
| **Utgiver**             | dct:publisher   | org:Organization     | | publisher      | Organization (legalName, identifier) |
| **Produsent**           | dct:creator     | org:Organization     | | author         | Organization (legalName, identifier) |
| **Beskrivelse**         | dct:description | rdf:langString       | | description    | Text                                 |
| **Hovedspråk**          | dct:language    | dct:LinguisticSystem | | inLanguage     | Text [eller Language]                |
| **Identifikator**       | dct:identifier  | xsd:anyURI           | | identifier     | Text                                 |
| **Tema**                | dcat:theme      | skos:Concept         | | about          | Thing (name, additionalType) **NB!** |
| **Tittel**              | dct:title       | rdf:langString       | | headline       | Text                                 |
| **Dato opprettet**      | dct:issued      | xsd:date             | | datePublished  | Date / DateTime                      |
| **Dato sist oppdatert** | dct:modified    | xsd:date             | | dateModified   | Date / DateTime                      |

#### Namespace

| **Prefiks** | **Namespace** | Dokumentasjon |
| --- | --- | --- |
| dcat | http://www.w3.org/ns/dcat# | [Data Catalog Vocabulary (DCAT) - Version 2](https://www.w3.org/TR/vocab-dcat-2/) |
| dct | [http://purl.org/dc/terms/](http://purl.org/dc/terms/) | [DCMI Metadata Terms (Dublin Core)](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/) |
| org | http://www.w3.org/ns/org# | [The Organization Ontology](https://www.w3.org/TR/vocab-org/) |
| skos | [http://www.w3.org/2004/02/skos/core#](https://www.w3.org/2009/08/skos-reference/skos.html) |[SKOS Simple Knowledge Organization System Reference](https://www.w3.org/TR/skos-reference/) |
| rdf | http://www.w3.org/1999/02/22-rdf-syntax-ns# | [RDF 1.1 XML Syntax](https://www.w3.org/TR/rdf-syntax-grammar/) |
| xsd | http://www.w3.org/2001/XMLSchema# | [XML Schema Part 2: Datatypes Second Edition](https://www.w3.org/TR/xmlschema-2/) |

Eksempel på bruk finnes i Appendiks 1 – Eksempel på JSON-LD.

**NB!** Det er ikke mulig å følge kravene til beskrivelse av tema i feltet "about" alene. Inntil videre foreslås det å kode med **undertema** (nivå 2). Se problembeskrivelse i [issue 2](https://github.com/rockphotog/hida/issues/2)

## Teknisk samhandlingsevne

<!-- <img src="diagrams/technical.png" width="90%" alt="ArchiMate-diagram" /> -->

![ArchiMate-diagram](diagrams/technical.png)

***Figur 5** Teknisk samhandlingsevne (ArchiMate)*

En *produsent* må ha et publiseringssystem som støtter ett eller flere format. Denne veilederen presiserer støtte for JSON-LD bygd opp med vokabular fra Schema.org på artikkelnivå (web-side) som minimumskrav. Ytterligere formater f.eks. RDFa på artikkel- og blokknivå kan prøves ut.

Innholdet skal publiseres på internett fritt tilgjengelig og uten hinder.

En *konsument* må ha programvare som kan lese og behandle informasjon, inkludert metadata, fra produsentenes publiseringssystem. Det er et minimumskrav å kunne lese og behandle JSON-LD bygd opp med vokabular fra Schema.org.

## Oppfølging

[Anbefaling om videre oppfølging av veilederen for å ferdigstille den hvis det er mangler (les: Los), anbefaling om prosess for utprøving (les: ETI, +), normering/forvaltning (f.eks. publisering via GitHub)]

---

## Appendiks A – Eksempler

### JSON-LD

<img width="90%" src="diagrams/example-json-ld-1.png" alt="diagram" />

***Figur 6** Et lesbart eksempel på metadata som JSON-LD*

```json
<script type="application/ld+json"\>
{
    "@context": "https://schema.org",
    "@type": "CreativeWork",
    "publisher": {
        "@type" : "Organization",
        "legalname" : "Digitaliseringsdirektoratet",
        "identifier" : "991 825 827"
    },
    "author": {
        "@type" : "Organization",
        "legalname" : "Digitaliseringsdirektoratet",
        "identifier" : "991 825 827"
    },
    "description" : "Et eksempel på en beskrivelse av innholdet",
    "inLanguage" : "nb",
    "identifier" : "https://www.digdir.no/eksempel/artikkel/123456789",
    "about" : {
        "name" : "Bålbrenning",
        "additionalType" : "https://psi.norge.no/los/ord/balbrenning"
    },
    "headline" : "Regler for bålbrenning ved Økern Portal",
    "datePublished" : "2023-12-07"
}
</script\>
```

### html/meta, RDFa og JSON-LD

Eksempel med kombinasjon meta-tags, JSON-LD og RDFa fra en ordinær SEO-plugin.  

[Eksempel - Tatt fra undertegnedes hjemmeside](examples/seland.org.html)

RDFa er i prinsippet "property"-attributtene som utvider "meta.

```html
<meta property="og:title" content="Regler for bålbrenning ved Økern Portal" />
```

Namespacet *og* betyr [Open Graph](https://ogp.me/).

## Appendix B - Notasjon og verktøy

- [PlantUML](https://plantuml.com/) for [UML](https://www.omg.org/spec/UML/2.5.1/About-UML/)
- [PlantText Editor](https://www.planttext.com/) - Online redigeringsverktøy for PlantUML
- [Archi](https://www.archimatetool.com/) - Åpent verktøy for [ArchiMate](https://www.opengroup.org/archimate-forum/archimate-overview)
- [Validator for Schema.org](https://validator.schema.org/) - testing av JSON-LD mot Schema.org-krav

---

[^1]: Minimum viable product, et så enkelt produkt som mulig, men som faktisk gir verdi for brukerne og nyttig tilbakemelding til videreutvikling

[^2]: Engelsk: Content management system (CMS)

[^3]: [metadata - Felles begrepskatalog](https://www.termportalen.no/FBK/bkg/20b2e2a5-9fe1-11e5-a9f8-e4115b280940)

[^4]: [Peikarar til offentlege ressursar på nett - Digdir](https://www.digdir.no/standarder/peikarar-til-offentlege-ressursar-pa-nett/1492)

[^5]: [Referansekatalogen for IT-standardar - Digdir](https://www.digdir.no/standarder/referansekatalogen-it-standardar/1480)

[^6]: [Los - felles vokabular for klassifisering av offentlige tjenester og ressurser - Digdir](https://www.digdir.no/informasjonsforvaltning/los-felles-vokabular-klassifisering-av-offentlige-tjenester-og-ressurser/2434)