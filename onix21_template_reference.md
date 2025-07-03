# ONIX 2.1 Template Reference

- [ONIXMessage](#onixmessage)
  - [Header](#header)
    - [FromCompany](#fromcompany)
    - [FromEmail](#fromemail)
    - [SentDate](#sentdate)
  - [Product](#product)
    - [RecordReference](#recordreference)
    - [NotificationType](#notificationtype)
    - [RecordSourceType](#recordsourcetype)
    - [ProductIdentifier](#productidentifier)
    - [ProductForm](#productform)
    - [EpubType](#epubtype)
    - [Series](#series)
      - [SeriesIdentifier](#seriesidentifier)
      - [TitleOfSeries](#titleofseries)
      - [NumberWithinSeries](#numberwithinseries)
    - [Title](#title)
      - [TitleType](#titletype)
      - [TitleText](#titletext)
      - [Subtitle](#subtitle)
    - [Website](#website)
    - [Contributor](#contributor)
      - [SequenceNumber](#sequencenumber)
      - [ContributorRole](#contributorrole)
      - [NamesBeforeKey](#namesbeforekey)
      - [KeyNames](#keynames)
      - [PersonNameIdentifier](#personnameidentifier)
      - [ProfessionalAffiliation](#professionalaffiliation)
      - [BiographicalNote](#biographicalnote)
    - [EditionNumber](#editionnumber)
    - [Language](#language)
    - [Extent](#extent)
    - [IllustrationsNote](#illustrationsnote)
    - [Illustrations](#illustrations)
    - [Subject](#subject)
    - [Audience](#audience)
    - [OtherText](#othertext)
    - [MediaFile](#mediafile)
    - [ContentItem](#contentitem)
    - [Imprint](#imprint)
    - [Publisher](#publisher)
    - [CityOfPublication](#cityofpublication)
    - [PublishingStatus](#publishingstatus)
    - [PublicationDate](#publicationdate)
    - [CopyrightStatement](#copyrightstatement)
    - [SalesRights](#salesrights)
    - [Measure](#measure)
    - [RelatedProduct](#relatedproduct)
    - [OutOfPrintDate](#outofprintdate)
    - [SupplyDetail](#supplydetail)

## ONIXMessage
`Mandatory`

The root element that contains all ONIX data.

The ONIX 2.1 XML file follows a specific structure:

```xml
<?xml version="1.0" encoding="utf-8"?>
<ONIXMessage xmlns="http://www.editeur.org/onix/2.1/reference">
  <Header>
    <!-- Header information -->
  </Header>
  <Product>
    <!-- Product information -->
  </Product>
</ONIXMessage>
```

**Attributes:**
- `xmlns="http://www.editeur.org/onix/2.1/reference"` - XML namespace

## Header
`Mandatory`

Contains information about the file.

```xml
<Header>
    <FromCompany>My Publisher</FromCompany>
    <FromEmail>contact@publisher.com</FromEmail>
    <SentDate>202401011200</SentDate>
</Header>
```

### FromCompany
`Mandatory`

Information about the entity sending the file.

```xml
<FromCompany>My Publisher</FromCompany>
```

### FromEmail
`Optional`

Sender entity contact e-mail.

```xml
<FromEmail>contact@publisher.com</FromEmail>
```

### SentDate
`Mandatory`

Specifies the date when the file is being sent. Format `YYYYMMDD`.

```xml
<SentDate>20240101</SentDate>
```

## Product
`Mandatory, Repeatable`

Information about each publication.

### RecordReference
`Mandatory`

Unique identifier for the record. ISBN recommended.

```xml
<RecordReference>9789800000001</RecordReference>
```

### NotificationType
`Mandatory`

Indicates the type of notification or update which you are sending. Default `03` (Notification confirmed on publication).

```xml
<NotificationType>03</NotificationType>
```

### RecordSourceType
`Optional`

Indicates the type of source which has issued the record. Default `01` (Publisher).

```xml
<RecordSourceType>01</RecordSourceType>
```

### ProductIdentifier
`Mandatory, Repeatable`

Define an identifier of the organization which is the source of the record.

**ISBN-13**
```xml
<ProductIdentifier>
    <ProductIDType>15</ProductIDType>
    <IDValue>9781800649866</IDValue>
</ProductIdentifier>
```

**DOI**
```xml
<ProductIdentifier>
    <ProductIDType>06</ProductIDType>
    <IDValue>10.12345/12345678</IDValue>
</ProductIdentifier>
```

**LCCN (Library of Congress Control Number)**
```xml
<ProductIdentifier>
    <ProductIDType>13</ProductIDType>
    <IDValue>2017123456</IDValue>
</ProductIdentifier>
```

**OCLC Number**
```xml
<ProductIdentifier>
    <ProductIDType>23</ProductIDType>
    <IDValue>1086123456</IDValue>
</ProductIdentifier>
```

**Sub-elements**:
- `ProductIDType` - ONIX code specifying the Product Identifier type provided.
  - `01`: Proprietary
  - `06`: DOI
  - `13`: LCCN
  - `15`: ISBN-13
  - `23`: OCLC
- `IDTypeName` - A name for the proprietary identifier.
- `IDValue` - The identifier value of the type specified in the `ProductIDType` element.

### ProductForm
`Mandatory`

Indicates the primary form of the product.

| ONIX Code | Description |
| :--- | :--- |
| `BB` | Hardback |
| `BC` | Paperback / softback |
| `DG` | Electronic book text |

```xml
<ProductForm>DG</ProductForm>
```

### EpubType
`Optional`

Provides more specific detail about the product form.

| ONIX Code | Publication Type |
| :--- | :--- |
| `002` | PDF |
| `004` | HTML |
| `010` | EPUB |
| `029` | Mobipocket |

```xml
<EpubType>002</EpubType>
```

### Series
`Optional, Repeatable`

A group of related products.

```xml
<Series>
    <SeriesIdentifier>
      <!-- Series Identifier -->
    </SeriesIdentifier>
    <TitleOfSeries>My Series Name</TitleOfSeries>
    <NumberWithinSeries>1</NumberWithinSeries>
</Series>
```

#### SeriesIdentifier
`Optional, Repeatable`

A unique identifier for the collection.

**Sub-elements**:
- `SeriesIDType` - ONIX code specifying the Series Identifier type provided.
  - `01`: Proprietary
  - `02`: ISSN
- `IDTypeName` - A name for the proprietary identifier.
  - `Series ID`
  - `Series URL`
  - `Series Call for Proposals URL`
- `IDValue` - The identifier value.

```xml
<SeriesIdentifier>
    <SeriesIDType>01</SeriesIDType>
    <IDTypeName>Series ID</IDTypeName>
    <IDValue>574e57ec-c039-4ab2-b8b9-87376c0235fc</IDValue>
</SeriesIdentifier>
```

#### TitleOfSeries
`Mandatory`

Contains the title of the series.

```xml
<TitleOfSeries>My Series Name</TitleOfSeries>
```

#### NumberWithinSeries
`Optional`

The number of the product in the series.

```xml
<NumberWithinSeries>1</NumberWithinSeries>
```

### Title
`Mandatory`

Contains the title of the product.

```xml
<Title>
    <TitleType>01</TitleType>
    <TitleText>My Book Title</TitleText>
    <Subtitle>My Book Subtitle</Subtitle>
</Title>
```

#### TitleType
`Mandatory`

An ONIX code for the type of title. Default `01` (Distinctive title (book)).

```xml
<TitleType>01</TitleType>
```

#### TitleText
`Mandatory`

The text of the title.

```xml
<TitleText>My Book Title</TitleText>
```

#### Subtitle
`Optional`

The subtitle of the product.

```xml
<Subtitle>My Book Subtitle</Subtitle>
```

### Website
`Optional, Repeatable`

A website associated with the product.

**Sub-elements**:
- `WebsiteRole` - An ONIX code for the role of the website.
  - `02`: Publisher’s website for a specified work
  - `36`: Supplier’s website for a specified work
- `WebsiteDescription` - A description of the website.
- `WebsiteLink` - The URL of the website.

```xml
<Website>
    <WebsiteRole>02</WebsiteRole>
    <WebsiteDescription>Publisher's website: webpage for this title</WebsiteDescription>
    <WebsiteLink>https://my.publisher.com/book/my-book</WebsiteLink>
</Website>
```

### Contributor
`Mandatory, Repeatable`

Contains information about the authors and other contributors to the product.

```xml
<Contributor>
    <SequenceNumber>1</SequenceNumber>
    <ContributorRole>A01</ContributorRole>
    <NamesBeforeKey>John</NamesBeforeKey>
    <KeyNames>Doe</KeyNames>
    <PersonNameIdentifier>
        <PersonNameIDType>01</PersonNameIDType>
        <IDTypeName>ORCID</IDTypeName>
        <IDValue>0000-0001-2345-678X</IDValue>
    </PersonNameIdentifier>
    <ProfessionalAffiliation>
        <ProfessionalPosition>Professor</ProfessionalPosition>
        <Affiliation>Harvard University</Affiliation>
    </ProfessionalAffiliation>
    <BiographicalNote>This is the bibliography of the author of my book.</BiographicalNote>
</Contributor>
```

#### SequenceNumber
`Optional`

The sequence number of the contributor.

```xml
<SequenceNumber>1</SequenceNumber>
```

#### ContributorRole
`Mandatory`

An ONIX code for the role of the contributor.

| ONIX Code | Description |
| :--- | :--- |
| A01 | By (author) |
| B01 | Edited by |
| B06 | Translated by |
| A13 | Photographs by |
| A12 | Illustrated by |
| B25 | Arranged by (music) |
| A23 | Foreword by |
| A24 | Introduction by |
| A19 | Afterword by |
| A15 | Preface by |
| A30 | Software written by |
| A51 | Research by |
| A32 | Contributions by |
| A34 | Index by |

```xml
<ContributorRole>A01</ContributorRole>
```

#### NamesBeforeKey
`Optional`

The part of the name before the key name (first name).

```xml
<NamesBeforeKey>John</NamesBeforeKey>
```

#### KeyNames
`Optional`

The key name (last name).

```xml
<KeyNames>Doe</KeyNames>
```

#### PersonNameIdentifier
`Optional`

A unique identifier for the contributor.

**Sub-elements**:
- `PersonNameIDType` - An ONIX code for the type of identifier.
  - `01`: Proprietary
- `IDTypeName` - A name for the proprietary identifier (e.g. ORCID).
- `IDValue` - The identifier value.

```xml
<PersonNameIdentifier>
    <PersonNameIDType>01</PersonNameIDType>
    <IDTypeName>ORCID</IDTypeName>
    <IDValue>0000-0001-2345-678X</IDValue>
</PersonNameIdentifier>
```

#### ProfessionalAffiliation
`Optional, Repeatable`

The professional affiliation of the contributor.

```xml
<ProfessionalAffiliation>
    <ProfessionalPosition>Professor</ProfessionalPosition>
    <Affiliation>Harvard University</Affiliation>
</ProfessionalAffiliation>
```

#### BiographicalNote
`Optional`

A biographical note about the contributor.

```xml
<BiographicalNote>This is the bibliography of the author of my book.</BiographicalNote>
```

### EditionNumber
`Optional`

The number of the edition.

```xml
<EditionNumber>2</EditionNumber>
```

### Language
`Optional, Repeatable`

The language of the product.

```xml
<Language>
    <LanguageRole>01</LanguageRole>
    <LanguageCode>eng</LanguageCode>
</Language>
```

**Sub-elements**:
- `LanguageRole` - An ONIX code for the role of the language.
  - `01`: Language of text
  - `02`: Original language of a translated text
- `LanguageCode` - An ISO 639-2/B code for the language.

### Extent
`Optional`

The extent of the product, such as the number of pages.

```xml
<Extent>
    <ExtentType>00</ExtentType>
    <ExtentValue>284</ExtentValue>
    <ExtentUnit>03</ExtentUnit>
</Extent>
```

**Sub-elements**:
- `ExtentType` - An ONIX code for the type of extent.
  - `00`: Main content page count
- `ExtentValue` - The value of the extent.
- `ExtentUnit` - An ONIX code for the unit of the extent.
  - `03`: Pages

### IllustrationsNote
`Optional`

A note about the illustrations in the product. The text may also include other content items, eg maps, bibliography, tables, index etc.

Use this element for bibliography notes.

```xml
<IllustrationsNote>Includes bibliographical references and index.</IllustrationsNote>
```

### Illustrations
`Optional, Repeatable`

Describes content that is ancillary to the main content of the product.

```xml
<Illustrations>
    <IllustrationType>09</IllustrationType>
    <Number>16</Number>
</Illustrations>
```

**Sub-elements**:
- `IllustrationType` - An ONIX code for the type of ancillary content.
  - `09`: Illustrations, unspecified
  - `11`: Tables, unspecified
  - `19`: Recorded music items
  - `00`: Unspecified, see description
- `IllustrationTypeDescription` - A description of the ancillary content. Use for videos.
- `Number` - The number of items of the ancillary content.

### Subject
`Optional, Repeatable`

A subject of the product.

```xml
<!-- BISAC Subject -->
<Subject>
    <SubjectSchemeIdentifier>10</SubjectSchemeIdentifier>
    <SubjectCode>1.1.2.2.0.0.0</SubjectCode>
</Subject>

<!-- BIC Subject -->
<Subject>
    <SubjectSchemeIdentifier>12</SubjectSchemeIdentifier>
    <SubjectCode>1D</SubjectCode>
</Subject>

<!-- LCC Subject -->
<Subject>
    <SubjectSchemeIdentifier>04</SubjectSchemeIdentifier>
    <SubjectCode>BD183</SubjectCode>
</Subject>

<!-- Keywords Subject-->
<Subject>
    <SubjectSchemeIdentifier>20</SubjectSchemeIdentifier>
    <SubjectHeadingText>Interest-Relative Epistemology</SubjectHeadingText>
</Subject>

<!-- Thema Subject -->
<Subject>
    <SubjectSchemeIdentifier>93</SubjectSchemeIdentifier>
    <SubjectCode>1A</SubjectCode>
</Subject>

<!-- Custom Subject -->
<Subject>
    <SubjectSchemeIdentifier>B2</SubjectSchemeIdentifier> <!-- B2 Keywords (not for display) -->
    <SubjectHeadingText>Philosophy</SubjectHeadingText>
</Subject>
```

**Sub-elements**:
- `SubjectSchemeIdentifier` - An ONIX code for the subject scheme.
  | ONIX Code | Description |
  | :--- | :--- |
  | 04 | LC subject heading |
  | 10 | BISAC Subject Heading |
  | 12 | BIC subject category |
  | 20 | Keywords |
  | 93 | Thema subject category |
  | B2 | Keywords (not for display) |
- `SubjectCode` - The subject code.
- `SubjectHeadingText` - The text of the subject heading. For Keywords

### Audience
`Mandatory`

The target audience of the product.

```xml
<Audience>
    <AudienceCodeType>01</AudienceCodeType>
    <AudienceCodeValue>06</AudienceCodeValue>
</Audience>
```

**Sub-elements**:
- `AudienceCodeType` - An ONIX code for the type of audience code.
  - `01`: ONIX audience codes
- `AudienceCodeValue` - The audience code value.
  - `06`: Professional and scholarly

### OtherText
`Optional, Repeatable`

Contains text related to the product, such as a description or abstract.

```xml
<!-- For open access books -->
<OtherText>
    <TextTypeCode>47</TextTypeCode> <!-- 47 Open access statement -->
    <Text>Open access - no commercial use</Text>
</OtherText>

<!-- License -->
<OtherText>
    <TextTypeCode>46</TextTypeCode> <!-- 46 License -->
    <Text>https://creativecommons.org/licenses/by-nc-nd/4.0/legalcode</Text>
</OtherText>

<!-- Short Abstract -->
<OtherText>
    <TextTypeCode>02</TextTypeCode> <!-- 02 Short description/annotation -->
    <TextFormat>06</TextFormat> <!-- 06 Default text format -->
    <Text>This is the short abstract of my book.</Text>
</OtherText>

<!-- Long Abstract -->
<OtherText>
    <TextTypeCode>03</TextTypeCode> <!-- 03 Long description -->
    <TextFormat>06</TextFormat> <!-- 06 Default text format -->
    <Text>This is the long abstract of my book.</Text>
</OtherText>

<!-- Table of Content -->
<OtherText>
    <TextTypeCode>04</TextTypeCode> <!-- 04 Table of contents -->
    <TextFormat>06</TextFormat> <!-- 06 Default text format -->
    <Text>1. Prologue 2. Chapter 1 3. Chapter 2 4. Chapter 3 5. Epilogue</Text>
</OtherText>

<!-- General Note -->
<OtherText>
    <TextTypeCode>21</TextTypeCode> <!-- 21 Publisher’s notice -->
    <TextFormat>06</TextFormat> <!-- 06 Default text format -->
    <Text>This is a general note of my book.</Text>
</OtherText>
```

**Sub-elements**:
- `TextTypeCode` - An ONIX code for the type of text.
  - `02`: Short description/annotation
  - `03`: Long description
  - `04`: Table of contents
  - `21`: Publisher’s notice
  - `46`: License
  - `47`: Open access statement
- `Text` - The text content.

### MediaFile
`Optional`

A resource that supports the product, such as a cover image.

```xml
<MediaFile>
    <MediaFileTypeCode>04</MediaFileTypeCode>
    <MediaFileLinkTypeCode>01</MediaFileLinkTypeCode>
    <MediaFileLink>https://my.publisher.com/book/my-book/cover.jpg</MediaFileLink>
    <TextWithDownload>This is the cover caption of my book</TextWithDownload>
</MediaFile>
```

**Sub-elements**:
- `MediaFileTypeCode` - An ONIX code for the type of media file.
  - `04`: Image: front cover
- `MediaFileLinkTypeCode` - An ONIX code for the link type.
  - `01`: URL
- `MediaFileLink` - The URL of the resource.
- `TextWithDownload` - A caption for the media file.

### ContentItem
`Optional, Repeatable`

An item of content in the product. Use this element for chapters

```xml
<ContentItem>
    <LevelSequenceNumber>1</LevelSequenceNumber>
    <TextItem>
        <TextItemType>03</TextItemType>
        <TextItemIdentifier>
            <TextItemIDType>06</TextItemIDType>
            <IDValue>10.12345/00010001</IDValue>
        </TextItemIdentifier>
        <PageRun>
            <FirstPageNumber>1</FirstPageNumber>
            <LastPageNumber>21</LastPageNumber>
        </PageRun>
    </TextItem>
    <ComponentTypeName>Chapter</ComponentTypeName>
</ContentItem>
```

### Imprint
`Mandatory`

Contains the imprint name.

```xml
<Imprint>
    <ImprintName>My Publisher Imprint</ImprintName>
</Imprint>
```

### Publisher
`Mandatory`

Contains information about the publisher.

```xml
<Publisher>
    <PublishingRole>01</PublishingRole>
    <PublisherName>My Publisher</PublisherName>
    <Website>
        <WebsiteLink>https://my.publisher.website.com</WebsiteLink>
    </Website>
</Publisher>
```

### CityOfPublication
`Optional`

The city of publication.

```xml
<CityOfPublication>Vancouver, CA</CityOfPublication>
```

### PublishingStatus
`Mandatory`

An ONIX code for the publishing status.

| ONIX Code | Description |
| :--- | :--- |
| 01 | Cancelled |
| 02 | Forthcoming |
| 03 | Postponed Indefinitely |
| 04 | Active |
| 08 | Inactive |
| 11 | Withdrawn from sale |


```xml
<PublishingStatus>04</PublishingStatus>
```

### PublicationDate
`Optional`

The date of publication. Format `YYYYMMDD`.

```xml
<PublicationDate>20240101</PublicationDate>
```

### CopyrightStatement
`Optional`

Copyright information.

```xml
<CopyrightStatement>
    <CopyrightYear>2024</CopyrightYear>
    <CopyrightOwner>
        <PersonName>John Doe</PersonName>
    </CopyrightOwner>
</CopyrightStatement>
```

### SalesRights
`Optional`

Sales rights for the product.

```xml
<SalesRights>
    <SalesRightsType>02</SalesRightsType>
    <RightsTerritory>WORLD</RightsTerritory>
</SalesRights>
```

**Sub-elements**:
- `SalesRightsType` - An ONIX code for the sales rights type.
  - `02`: For sale with non-exclusive rights in the specified countries or territories
- `RightsTerritory` - The territory for the sales rights.

### Measure
`Optional, Repeatable`

Specifies the measurements of the product.

```xml
<Measure>
    <MeasureTypeCode>01</MeasureTypeCode>
    <Measurement>229</Measurement>
    <MeasureUnitCode>mm</MeasureUnitCode>
</Measure>
```

**Sub-elements**:
- `MeasureTypeCode` - An ONIX code for the type of measurement.
  - `01`: Height
  - `02`: Width
  - `03`: Thickness (depth)
  - `08`: Unit weight
- `Measurement` - The value of the measurement.
- `MeasureUnitCode` - An ONIX code for the unit of measurement.
  - `mm`: millimeters
  - `in`: inches
  - `gr`: grams
  - `oz`: ounces

### RelatedProduct
`Optional, Repeatable`

A related product.

```xml
<RelatedProduct>
    <RelationCode>34</RelationCode>
    <ProductIdentifier>
        <ProductIDType>06</ProductIDType>
        <IDValue>10.12345/01020102</IDValue>
    </ProductIdentifier>
</RelatedProduct>
```

**Sub-elements**:
- `RelationCode` - An ONIX code for the relation.
  - `01`: Includes
  - `11`: Is other-language version of 
  - `34`: Cites
- `ProductIdentifier` - The identifier of the related product.

### OutOfPrintDate
`Optional`

The date the product went out of print. Format `YYYYMMDD`.

```xml
<OutOfPrintDate>20250101</OutOfPrintDate>
```

### SupplyDetail
`Mandatory`

Contains information about the supply of the product.

```xml
<SupplyDetail>
    <SupplierName>My Publisher</SupplierName>
    <SupplierRole>09</SupplierRole>
    <ProductAvailability>99</ProductAvailability>
    <Price>
        <PriceTypeCode>02</PriceTypeCode>
        <PriceAmount>0.01</PriceAmount>
        <CurrencyCode>USD</CurrencyCode>
    </Price>
</SupplyDetail>
```
#### SupplierName
`Mandatory`

The name of a supply source from which the product may be ordered by a trade customer

```xml
<SupplierName>My Publisher</SupplierName>
```

#### SupplierRole
`Mandatory`

An ONIX code identifying the role of a supplier in relation to the product. Default `09` (Publisher to end-customers)

```xml
<SupplierRole>09</SupplierRole>
```

#### ProductAvailability
`Mandatory`

An ONIX code indicating the availability of a product from a supplier.

```xml
<ProductAvailability>99</ProductAvailability>
```

#### AudienceRestrictionFlag
`Optional`

Used with `<AudienceRestrictionNote>` where within a particular market there is an additional restriction on sale. Use to indicate open acess books. Default `R` (Restrictions apply, see note)

```xml
<AudienceRestrictionFlag>R</AudienceRestrictionFlag>
```

#### AudienceRestrictionNote
`Optional`

Free text describing a non-territorial restriction on supply. Use to indicate open acess books.

```xml
<AudienceRestrictionNote>Open access</AudienceRestrictionNote>
```

#### UnpricedItemType
`Optional`

An ONIX code which specifies a reason why a price amount is not sent. Default `01` (Free of charge)

```xml
<UnpricedItemType>01</UnpricedItemType>
```

#### Price
`Optional`

```xml
<Price>
  <PriceTypeCode>02</PriceTypeCode>
  <PriceAmount>0.01</PriceAmount>
  <CurrencyCode>USD</CurrencyCode>
</Price>
```

**Sub-elements**:
- `PriceTypeCode` - ONIX code indicating the type of the price.
  - `02`: RRP including tax
- `PriceAmount` - The amount of a price.
- `CurrencyCode` - An ISO standard code identifying the currency in which a price is given.
