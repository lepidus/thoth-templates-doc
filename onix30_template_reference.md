# ONIX 3.0 Template Reference

- [ONIXMessage](#onixmessage)
  - [Header](#header)
    - [Sender](#sender)
    - [SentDateTime](#sentdatetime)
  - [Product](#product)
    - [RecordReference](#recordreference)
    - [NotificationType](#notificationtype)
    - [RecordSourceType](#recordsourcetype)
    - [ProductIdentifier](#productidentifier)
    - [DescriptiveDetail](#descriptivedetail)
      - [ProductComposition](#productcomposition)
      - [ProductForm](#productform)
      - [ProductFormDetail](#productformdetail)
      - [PrimaryContentType](#primarycontenttype)
      - [Collection](#collection)
        - [CollectionType](#collectiontype)
        - [CollectionIdentifier](#collectionidentifier)
        - [CollectionSequence](#collectionsequence)
        - [TitleDetail](#titledetail)
          - [TitleType](#titletype)
          - [TitleElement](#titleelement)
      - [Measure](#measure)
      - [EpubLicense](#epublicense)
        - [EpubLicenseName](#epublicensename)
        - [EpubLicenseExpression](#epublicenseexpression)
      - [TitleDetail](#titledetail-1)
        - [TitleType](#titletype-1)
        - [TitleElement](#titleelement-1)
      - [Contributor](#contributor)
        - [SequenceNumber](#sequencenumber)
        - [ContributorRole](#contributorrole)
        - [NameIdentifier](#nameidentifier)
        - [PersonName](#personname)
        - [NamesBeforeKey](#namesbeforekey)
        - [KeyNames](#keynames)
        - [ProfessionalAffiliation](#professionalaffiliation)
          - [ProfessionalPosition](#professionalposition)
          - [Affiliation](#affiliation)
        - [BiographicalNote](#biographicalnote)
        - [Website](#website)
      - [EditionNumber](#editionnumber)
      - [Language](#language)
      - [Extent](#extent)
      - [IllustrationsNote](#illustrationsnote)
      - [AncillaryContent](#ancillarycontent)
      - [Subject](#subject)
      - [Audience](#audience)
    - [CollateralDetail](#collateraldetail)
      - [TextContent](#textcontent)
      - [SupportingResource](#supportingresource)
        - [ResourceContentType](#resourcecontenttype)
        - [ContentAudience](#contentaudience)
        - [ResourceMode](#resourcemode)
        - [ResourceFeature](#resourcefeature)
        - [ResourceVersion](#resourceversion)
    - [ContentDetail](#contentdetail)
      - [ContentItem](#contentitem)
        - [LevelSequenceNumber](#levelsequencenumber)
        - [TextItem](#textitem)
          - [TextItemType](#textitemtype)
          - [TextItemIdentifier](#textitemidentifier)
          - [PageRun](#pagerun)
          - [NumberOfPages](#numberofpages)
        - [ComponentTypeName](#componenttypename)
    - [PublishingDetail](#publishingdetail)
      - [Imprint](#imprint)
        - [ImprintIdentifier](#imprintidentifier)
        - [ImprintName](#imprintname)
      - [Publisher](#publisher)
        - [PublishingRole](#publishingrole)
        - [PublisherIdentifier](#publisheridentifier)
        - [PublisherName](#publishername)
        - [Funding](#funding)
          - [FundingIdentifier](#fundingidentifier)
        - [Website](#website-1)
      - [CityOfPublication](#cityofpublication)
      - [PublishingStatus](#publishingstatus)
      - [PublishingDate](#publishingdate)
      - [CopyrightStatement](#copyrightstatement)
      - [SalesRights](#salesrights)
    - [RelatedMaterial](#relatedmaterial)
      - [RelatedWork](#relatedwork)
        - [ProductRelationCode](#productrelationcode)
        - [ProductIdentifier](#productidentifier-1)
      - [RelatedProduct](#relatedproduct)
        - [ProductRelationCode](#productrelationcode-1)
        - [ProductIdentifier](#productidentifier-2)
    - [ProductSupply](#productsupply)
      - [Market](#market)
      - [SupplyDetail](#supplydetail)
        - [Supplier](#supplier)
          - [SupplierRole](#supplierrole)
          - [SupplierName](#suppliername)
          - [Website](#website-2)
        - [ProductAvailability](#productavailability)
        - [SupplyDate](#supplydate)
        - [Price](#price)
          - [PriceType](#pricetype)
          - [PriceAmount](#priceamount)
          - [CurrencyCode](#currencycode)
          - [Territory](#territory)

## ONIXMessage
`Mandatory`

The root element that contains all ONIX data.

The ONIX 3.0 XML file follows a specific structure:

```xml
<?xml version="1.0" encoding="utf-8"?>
<ONIXMessage release="3.0" xmlns="http://ns.editeur.org/onix/3.0/reference">
  <Header>
    <!-- Header information -->
  </Header>
  <Product>
    <!-- Product information -->
  </Product>
</ONIXMessage>
```

**Attributes:**
- `release="3.0"` - ONIX version
- `xmlns="http://ns.editeur.org/onix/3.0/reference"` - XML namespace

## Header
`Mandatory`

Contains information about the file.

```xml
<Header>
  <Sender>
    <!-- Sender information -->
  </Sender>
  <SentDateTime>...</SentDateTime>
</Header>
```

### Sender
`Mandatory`

Information about the entity sending the file.

```xml
<Sender>
  <SenderName>My Publisher</SenderName>
  <EmailAddress>contact@publisher.com</EmailAddress>
</Sender>
```

**Sub-elements:**
- `SenderName` - Sender entity name
- `EmailAddress` - Sender entity contact e-mail

### SentDateTime

Specifies the date and time when the file is being sent.

```xml
<SentDateTime>20240101T120000</SentDateTime>
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

Indicates the type of notification or update which you are sending. Default 03 (Notification confirmed on publication).

```xml
<NotificationType>03</NotificationType>
```

### RecordSourceType
`Mandatory`

Indicates the type of source which has issued the record. Default 01 (Publisher).

```xml
<RecordSourceType>01</RecordSourceType>
```

### ProductIdentifier
`Optional, Repeatable`

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
  - `05`: DOI
  - `13`: LCCN
  - `15`: ISBN-13
  - `23`: OCLC
- `IDValue` - The identifier value of the type specified in the `ProductIDType` element.

### DescriptiveDetail
`Mandatory`

Describes the product form and metadata such as title, content description, and authorship.

#### ProductComposition
`Mandatory`

Indicates if the product is a single-item product, a multi-item collection, or a trade-only product. Default `00` (Single-item retail product).

```xml
<ProductComposition>00</ProductComposition>
```

#### ProductForm
`Mandatory`

Indicates the primary form of the product.

| ONIX Code | Description |
| :--- | :--- |
| BB | Hardback |
| BC | Paperback / softback |
| EB | Digital download and online |
| AN | Downloadable and online audio file |

```xml
<ProductForm>BC</ProductForm>
```

#### ProductFormDetail
`Optional, Repeatable`

Provides more specific detail about the product form. Mandatory for `EB` and `AN` `ProductForm`

| ONIX Code | Publication Type |
| :--- | :--- |
| E107 | PDF |
| E105 | HTML |
| E113 | XHTML |
| E101 | EPUB |
| E127 | Mobipocket |
| E116 | Amazon Kindle |
| E104 | DOCX |
| E100 | Other (for Fiction Book) |
| A103 | MP3 format |
| A104 | WAV format |

```xml
<ProductFormDetail>E107</ProductFormDetail>
```

#### PrimaryContentType
`Mandatory`

An ONIX code which indicates the primary content type of the product. Default `10` (Text (eye-readable)).

```xml
<PrimaryContentType>10</PrimaryContentType>
```

#### Collection
`Optional, Repeatable`

A group of related products.

```xml
<Collection>
    <CollectionType>10</CollectionType>
    <CollectionIdentifier>
      <!-- Series Identifier -->
    </CollectionIdentifier>
    <CollectionSequence>
      <!-- Issue number information -->
    </CollectionSequence>
    <TitleDetail>
      <!-- Series Name -->
    </TitleDetail>
</Collection>
```

##### CollectionType
`Mandatory`

An ONIX code indicating the type of collection. Default `10` (Publisher collection).

```xml
<CollectionType>10</CollectionType>
```

##### CollectionIdentifier
`Optional, Repeatable`

A unique identifier for the collection.

**Sub-elements**:
- `CollectionIDType` - ONIX code specifying the Collection Identifier type provided.
  - `01`: Proprietary
  - `02`: ISSN
- `IDTypeName` - A name for the proprietary identifier.
  - Series ID
  - Series URL
  - Series Call for Proposals URL
- `IDValue` - The identifier value.

```xml
<CollectionIdentifier>
    <CollectionIDType>01</CollectionIDType>
    <IDTypeName>Series ID</IDTypeName>
    <IDValue>574e57ec-c039-4ab2-b8b9-87376c0235fc</IDValue>
</CollectionIdentifier>
```

##### CollectionSequence
`Optional`

Identifies the sequence of the product within the collection.

**Sub-elements**:
- `CollectionSequenceType` - An ONIX code for the type of sequence.
  - `03` - Issue number
- `CollectionSequenceNumber` - The number of the product in the sequence.

```xml
<CollectionSequence>
    <CollectionSequenceType>03</CollectionSequenceType>
    <CollectionSequenceNumber>1</CollectionSequenceNumber>
</CollectionSequence>
```

##### TitleDetail
`Mandatory`

Contains the title of the collection.

```xml
<TitleDetail>
    <TitleType>01</TitleType>
    <TitleElement>
        <TitleElementLevel>02</TitleElementLevel>
        <PartNumber>1</PartNumber>
        <TitleText>My Series Name</TitleText>
    </TitleElement>
</TitleDetail>
```

###### TitleType
`Mandatory`

An ONIX code for the type of title. Default `01` (Distinctive title (book)).

```xml
<TitleType>01</TitleType>
```

###### TitleElement
`Mandatory`

Contains the elements of the title.

**Sub-elements**:
- `TitleElementLevel` - An ONIX code indicating the level of the title element.
  - `02`: Collection level
- `PartNumber` - The number of the part.
- `TitleText` - The text of the title.

```xml
<TitleElement>
    <TitleElementLevel>02</TitleElementLevel>
    <PartNumber>1</PartNumber>
    <TitleText>My Series Name</TitleText>
</TitleElement>
```

#### Measure
`Optional, Repeatable`

Specifies the measurements of the product.

```xml
<Measure>
    <MeasureType>01</MeasureType>
    <Measurement>229</Measurement>
    <MeasureUnitCode>mm</MeasureUnitCode>
</Measure>
```

**Sub-elements**:
- `MeasureType` - An ONIX code for the type of measurement.
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

#### EpubLicense
`Optional`

Contains the license information for a digital product.

```xml
<EpubLicense>
    <EpubLicenseName>Creative Commons Attribution 4.0 International license (CC BY 4.0).</EpubLicenseName>
    <EpubLicenseExpression>
        <EpubLicenseExpressionType>02</EpubLicenseExpressionType>
        <EpubLicenseExpressionLink>https://creativecommons.org/licenses/by/4.0</EpubLicenseExpressionLink>
    </EpubLicenseExpression>
</EpubLicense>
```

##### EpubLicenseName
`Optional`

The name of the license.

```xml
<EpubLicenseName>Creative Commons Attribution 4.0 International license (CC BY 4.0).</EpubLicenseName>
```

##### EpubLicenseExpression
`Optional`

A structured representation of the license.

```xml
<EpubLicenseExpression>
    <EpubLicenseExpressionType>02</EpubLicenseExpressionType>
    <EpubLicenseExpressionLink>https://creativecommons.org/licenses/by/4.0</EpubLicenseExpressionLink>
</EpubLicenseExpression>
```

**Sub-elements**:
- `EpubLicenseExpressionType` - An ONIX code for the type of license expression.
  - `02`: Human-readable URL
- `EpubLicenseExpressionLink` - The URL of the license.

#### TitleDetail
`Mandatory, Repeatable`

Contains the title of the product.

```xml
<TitleDetail>
    <TitleType>01</TitleType>
    <TitleElement>
        <TitleElementLevel>01</TitleElementLevel>
        <TitleText>My Book Title</TitleText>
        <Subtitle>My Book Subtitle</Subtitle>
    </TitleElement>
</TitleDetail>
```

##### TitleType
`Mandatory`

An ONIX code for the type of title. Default `01` (Distinctive title (book)).

```xml
<TitleType>01</TitleType>
```

##### TitleElement
`Mandatory, Repeatable`

Contains the elements of the title.

**Sub-elements**:
- `TitleElementLevel` - An ONIX code indicating the level of the title element.
  - `01`: Product level
- `TitleText` - The text of the title.
- `Subtitle` - The subtitle of the product.

```xml
<TitleElement>
    <TitleElementLevel>01</TitleElementLevel>
    <TitleText>My Book Title</TitleText>
    <Subtitle>My Book Subtitle</Subtitle>
</TitleElement>
```

#### Contributor
`Optional, Repeatable`

Contains information about the authors and other contributors to the product.

```xml
<Contributor>
    <SequenceNumber>1</SequenceNumber>
    <ContributorRole>A01</ContributorRole>
    <NameIdentifier>
        <NameIDType>21</NameIDType>
        <IDValue>0000-0001-2345-678X</IDValue>
    </NameIdentifier>
    <PersonName>John Doe</PersonName>
    <NamesBeforeKey>John</NamesBeforeKey>
    <KeyNames>Doe</KeyNames>
    <ProfessionalAffiliation>
        <ProfessionalPosition>Professor</ProfessionalPosition>
        <AffiliationIdentifier>
            <AffiliationIDType>40</AffiliationIDType>
            <IDValue>03vek6s52</IDValue>
        </AffiliationIdentifier>
        <Affiliation>Harvard University</Affiliation>
    </ProfessionalAffiliation>
    <BiographicalNote>John Doe is a Professor at the Harvard University.</BiographicalNote>
    <Website>
        <WebsiteRole>06</WebsiteRole>
        <WebsiteDescription>Own website</WebsiteDescription>
        <WebsiteLink>https://john.doe.org/</WebsiteLink>
    </Website>
</Contributor>
```

##### SequenceNumber
`Optional`

The sequence number of the contributor.

```xml
<SequenceNumber>1</SequenceNumber>
```

##### ContributorRole
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

##### NameIdentifier
`Optional`

A unique identifier for the contributor.

**Sub-elements**:
- `NameIDType` - An ONIX code for the type of identifier.
  - `21`: ORCID
- `IDValue` - The identifier value.

```xml
<NameIdentifier>
    <NameIDType>21</NameIDType>
    <IDValue>0000-0001-2345-678X</IDValue>
</NameIdentifier>
```

##### PersonName
`Optional`

The full name of the contributor.

```xml
<PersonName>John Doe</PersonName>
```

##### NamesBeforeKey
`Optional`

The part of the name before the key name (first name).

```xml
<NamesBeforeKey>John</NamesBeforeKey>
```

##### KeyNames
`Mandatory`

The key name (last name).

```xml
<KeyNames>Doe</KeyNames>
```

##### ProfessionalAffiliation
`Optional, Repeatable`

The professional affiliation of the contributor.

```xml
<ProfessionalAffiliation>
    <ProfessionalPosition>Professor</ProfessionalPosition>
    <AffiliationIdentifier>
        <AffiliationIDType>40</AffiliationIDType>
        <IDValue>03vek6s52</IDValue>
    </AffiliationIdentifier>
    <Affiliation>Harvard University</Affiliation>
</ProfessionalAffiliation>
```

###### ProfessionalPosition
`Optional`

The professional position of the contributor.

```xml
<ProfessionalPosition>Professor</ProfessionalPosition>
```

###### Affiliation
`Optional`

The name of the affiliation.

```xml
<Affiliation>Harvard University</Affiliation>
```

##### BiographicalNote
`Optional`

A biographical note about the contributor.

```xml
<BiographicalNote>John Doe is a Professor at the Harvard University.</BiographicalNote>
```

##### Website
`Optional, Repeatable`

A website associated with the contributor.

**Sub-elements**:
- `WebsiteRole` - An ONIX code for the role of the website.
  - `06`: Personal website
- `WebsiteDescription` - A description of the website.
- `WebsiteLink` - The URL of the website.

```xml
<Website>
    <WebsiteRole>06</WebsiteRole>
    <WebsiteDescription>Own website</WebsiteDescription>
    <WebsiteLink>https://john.doe.org/</WebsiteLink>
</Website>
```

#### EditionNumber
`Optional`

The number of the edition.

```xml
<EditionNumber>2</EditionNumber>
```

#### Language
`Mandatory, Repeatable`

The language of the product.

```xml
<Language>
    <LanguageRole>01</LanguageRole>
    <LanguageCode>eng</LanguageCode>
</Language>
```

**Sub-elements**:
- `LanguageRole` - An ONIX code for the role of the language.
  | ONIX Code | Description |
  | :--- | :--- |
  | 01 | Language of text (Original) |
  | 02 | Original language of a translated text (Translated from) |
- `LanguageCode` - An ISO 639-3 code for the language.

#### Extent
`Optional, Repeatable`

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

#### IllustrationsNote
`Optional`

A note about the illustrations in the product.

```xml
<IllustrationsNote>Includes bibliographical references and index.</IllustrationsNote>
```

#### AncillaryContent
`Optional, Repeatable`

Describes content that is ancillary to the main content of the product.

```xml
<AncillaryContent>
    <AncillaryContentType>09</AncillaryContentType>
    <Number>16</Number>
</AncillaryContent>
```

**Sub-elements**:
- `AncillaryContentType` - An ONIX code for the type of ancillary content.
  - `09`: Illustrations, black and white
  - `11`: Tables, black and white
  - `19`: Audio files
  - `00`: Unspecified, see description
- `AncillaryContentDescription` - A description of the ancillary content. Use for videos.
- `Number` - The number of items of the ancillary content.

#### Subject
`Optional, Repeatable`

A subject of the product.

```xml
<!-- LCC -->
<Subject>
    <MainSubject />
    <SubjectSchemeIdentifier>04</SubjectSchemeIdentifier>
    <SubjectCode>BD183</SubjectCode>
</Subject>
```

```xml
<!-- Keywords -->
<Subject>
    <MainSubject />
    <SubjectSchemeIdentifier>20</SubjectSchemeIdentifier>
    <SubjectHeadingText>Interest-Relative Epistemology</SubjectHeadingText>
</Subject>
```

**Sub-elements**:
- `MainSubject` - Indicates that this is the main subject.
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

#### Audience
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

### CollateralDetail
`Mandatory`

Contains promotional material about the product.

#### TextContent
`Mandatory, Repeatable`

Contains text related to the product, such as a description or abstract.

```xml
<TextContent>
    <TextType>02</TextType>
    <ContentAudience>00</ContentAudience>
    <Text>This is the short abstract of my book.</Text>
</TextContent>
```

**Sub-elements**:
- `TextType` - An ONIX code for the type of text.
  - `02`: Short description/annotation
  - `03`: Description
  - `04`: Table of contents
  - `13`: Promotional headline
  - `20`: Open access statement
  - `30`: Long description
- `ContentAudience` - An ONIX code for the audience of the content. Default `00` (Unrestricted).
- `Text` - The text content.

#### SupportingResource
`Optional`

A resource that supports the product, such as a cover image.

```xml
<SupportingResource>
    <ResourceContentType>01</ResourceContentType>
    <ContentAudience>00</ContentAudience>
    <ResourceMode>03</ResourceMode>
    <ResourceFeature>
        <ResourceFeatureType>02</ResourceFeatureType>
        <FeatureNote>My book cover caption</FeatureNote>
    </ResourceFeature>
    <ResourceVersion>
        <ResourceForm>02</ResourceForm>
        <ResourceLink>https://my.publisher.com/catalog/book/1/cover.jpg</ResourceLink>
    </ResourceVersion>
</SupportingResource>
```

##### ResourceContentType
`Mandatory`

An ONIX code for the type of resource content. Default `01` (Front cover).

```xml
<ResourceContentType>01</ResourceContentType>
```

##### ContentAudience
`Mandatory`

An ONIX code for the audience of the content. Default `00` (Unrestricted).

```xml
<ContentAudience>00</ContentAudience>
```

##### ResourceMode
`Mandatory`

An ONIX code for the mode of the resource. Default `03` (Image).

```xml
<ResourceMode>03</ResourceMode>
```

##### ResourceFeature
`Optional, Repeatable`

A feature of the resource.

**Sub-elements**:
- `ResourceFeatureType` - An ONIX code for the type of feature.
  - `02`: Caption
- `FeatureNote` - A note about the feature.

```xml
<ResourceFeature>
    <ResourceFeatureType>02</ResourceFeatureType>
    <FeatureNote>My book cover caption</FeatureNote>
</ResourceFeature>
```

##### ResourceVersion
`Mandatory, Repeatable`

A version of the resource.

**Sub-elements**:
- `ResourceForm` - An ONIX code for the form of the resource.
  - `02`: Downloadable file
- `ResourceLink` - The URL of the resource.

```xml
<ResourceVersion>
    <ResourceForm>02</ResourceForm>
    <ResourceLink>https://my.publisher.com/catalog/book/1/cover.jpg</ResourceLink>
</ResourceVersion>
```

### ContentDetail
`Optional`

Describes the content of the product in detail, such as chapters.

#### ContentItem
`Mandatory, Repeatable`

An item of content in the product.

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
        <NumberOfPages>20</NumberOfPages>
    </TextItem>
    <ComponentTypeName>Chapter</ComponentTypeName>
</ContentItem>
```

##### LevelSequenceNumber
`Optional`

The sequence number of the content item at its level.

```xml
<LevelSequenceNumber>1</LevelSequenceNumber>
```

##### TextItem
`Mandatory`

A text item within the content item.

```xml
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
    <NumberOfPages>20</NumberOfPages>
</TextItem>
```

###### TextItemType
`Mandatory`

An ONIX code for the type of text item. Default `03` (Chapter).

```xml
<TextItemType>03</TextItemType>
```

###### TextItemIdentifier
`Optional, Repeatable`

A unique identifier for the text item.

**Sub-elements**:
- `TextItemIDType` - An ONIX code for the type of identifier.
  - `06`: DOI
- `IDValue` - The identifier value.

```xml
<TextItemIdentifier>
    <TextItemIDType>06</TextItemIDType>
    <IDValue>10.12345/00010001</IDValue>
</TextItemIdentifier>
```

###### PageRun
`Optional, Repeatable`

The page range of the text item.

**Sub-elements**:
- `FirstPageNumber` - The first page number.
- `LastPageNumber` - The last page number.

```xml
<PageRun>
    <FirstPageNumber>1</FirstPageNumber>
    <LastPageNumber>21</LastPageNumber>
</PageRun>
```

###### NumberOfPages
`Optional`

The number of pages in the text item.

```xml
<NumberOfPages>20</NumberOfPages>
```

##### ComponentTypeName
`Optional`

The name of the component type.

```xml
<ComponentTypeName>Chapter</ComponentTypeName>
```

### PublishingDetail
`Mandatory`

Contains information about the publishing of the product.

#### Imprint
`Mandatory`

The imprint under which the product is published.

```xml
<Imprint>
    <ImprintIdentifier>
        <ImprintIDType>01</ImprintIDType>
        <IDTypeName>01</IDTypeName>
        <IDValue>https://my.publisher.imprint.com</IDValue>
    </ImprintIdentifier>
    <ImprintName>My Publisher Imprint</ImprintName>
</Imprint>
```

##### ImprintIdentifier
`Optional`

A unique identifier for the imprint. Use for Imprint URL.

```xml
<ImprintIdentifier>
    <ImprintIDType>01</ImprintIDType>
    <IDTypeName>URL</IDTypeName>
    <IDValue>https://my.publisher.imprint.com</IDValue>
</ImprintIdentifier>
```

**Sub-elements**:
- `ImprintIDType` - An ONIX code for the type of identifier.
  - `01`: Proprietary
- `IDTypeName` - A name for the proprietary identifier.
  - `URL`
- `IDValue` - The identifier value.

##### ImprintName
`Mandatory`

The name of the imprint.

```xml
<ImprintName>My Publisher Imprint</ImprintName>
```

#### Publisher
`Mandatory, Repeatable`

The publisher of the product.

```xml
<Publisher>
    <PublishingRole>01</PublishingRole>
    <PublisherName>My Publisher Name</PublisherName>
    <Website>
        <WebsiteRole>01</WebsiteRole>
        <WebsiteDescription>Publisher's website: home page</WebsiteDescription>
        <WebsiteLink>https://my.publisher.com</WebsiteLink>
    </Website>
</Publisher>
```

##### PublishingRole
`Mandatory`

An ONIX code for the role of the publisher. Default `01` (Publisher).

```xml
<PublishingRole>01</PublishingRole>
```

##### PublisherIdentifier
`Optional, Repeatable`

A unique identifier for the publisher.

**Sub-elements**:
- `PublisherIDType` - An ONIX code for the type of identifier.
  - `32`: DOI
  - `40`: ROR
- `IDValue` - The identifier value.

```xml
<PublisherIdentifier>
    <PublisherIDType>40</PublisherIDType>
    <IDValue>0123abc45</IDValue>
</PublisherIdentifier>
```

##### PublisherName
`Optional`

The name of the publisher.

```xml
<PublisherName>My Publisher Name</PublisherName>
```

##### Funding
`Optional, Repeatable`

Information about the funding of the product.

```xml
<Funding>
    <FundingIdentifier>
        <FundingIDType>01</FundingIDType>
        <IDTypeName>programname</IDTypeName>
        <IDValue>My Funding Program Name</IDValue>
    </FundingIdentifier>
</Funding>
```

###### FundingIdentifier
`Optional, Repeatable`

A unique identifier for the funding.

**Sub-elements**:
- `FundingIDType` - An ONIX code for the type of identifier.
  - `01`: Proprietary
- `IDTypeName` - A name for the proprietary identifier.
  - `programname`
  - `projectname`
  - `projectshortname`
  - `grantnumber`
  - `jurisdiction`
- `IDValue` - The identifier value.

```xml
<!-- Program -->
<FundingIdentifier>
    <FundingIDType>01</FundingIDType>
    <IDTypeName>programname</IDTypeName>
    <IDValue>My Funding Program Name</IDValue>
</FundingIdentifier>

<!-- Project Name -->
<FundingIdentifier>
    <FundingIDType>01</FundingIDType>
    <IDTypeName>projectname</IDTypeName>
    <IDValue>My Funding Project Name</IDValue>
</FundingIdentifier>

<!-- Project Short Name -->
<FundingIdentifier>
    <FundingIDType>01</FundingIDType>
    <IDTypeName>projectshortname</IDTypeName>
    <IDValue>My Funding Project Short Name</IDValue>
</FundingIdentifier>

<!-- Grant Number -->
<FundingIdentifier>
    <FundingIDType>01</FundingIDType>
    <IDTypeName>grantnumber</IDTypeName>
    <IDValue>0102-3345</IDValue>
</FundingIdentifier>

<!-- Jurisdiction -->
<FundingIdentifier>
    <FundingIDType>01</FundingIDType>
    <IDTypeName>jurisdiction</IDTypeName>
    <IDValue>My Funding Jurisdiction</IDValue>
</FundingIdentifier>
```

##### Website
`Optional, Repeatable`

A website associated with the publisher.

**Sub-elements**:
- `WebsiteRole` - An ONIX code for the role of the website.
  - `01`: Publisher's corporate website
  - `02`: Publisher's website for a specific work
- `WebsiteDescription` - A description of the website.
- `WebsiteLink` - The URL of the website.

```xml
<Website>
    <WebsiteRole>01</WebsiteRole>
    <WebsiteDescription>Publisher's website: home page</WebsiteDescription>
    <WebsiteLink>https://my.publisher.com</WebsiteLink>
</Website>
```

#### CityOfPublication
`Optional`

The city of publication.

```xml
<CityOfPublication>Vancouver, CA</CityOfPublication>
```

#### PublishingStatus
`Optional`

An ONIX code for the publishing status of the product.

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

#### PublishingDate
`Optional, Repeatable`

A date related to the publishing of the product.

```xml
<PublishingDate>
    <PublishingDateRole>01</PublishingDateRole>
    <Date dateformat="00">20240101</Date>
</PublishingDate>
```

**Sub-elements**:
- `PublishingDateRole` - An ONIX code for the role of the date.
  - `01`: Publication date
  - `13`: Out-of-print date / Withdrawn date
- `Date` - The date in `YYYYMMDD` format.

#### CopyrightStatement
`Optional`

A copyright statement for the product.

```xml
<CopyrightStatement>
    <CopyrightOwner>
        <PersonName>John Doe</PersonName>
    </CopyrightOwner>
</CopyrightStatement>
```

**Sub-elements**:
- `CopyrightOwner` - The owner of the copyright.
- `PersonName` - The name of the person who owns the copyright.

#### SalesRights
`Optional, Repeatable`

The sales rights for the product.

```xml
<SalesRights>
    <SalesRightsType>02</SalesRightsType>
    <Territory>
        <RegionsIncluded>WORLD</RegionsIncluded>
    </Territory>
</SalesRights>
```

**Sub-elements**:
- `SalesRightsType` - An ONIX code for the type of sales rights.
  - `02`: For sale with non-exclusive rights in the specified countries or territories
- `Territory` - The territory for the sales rights.
- `RegionsIncluded` - The regions included in the territory.

### RelatedMaterial
`Optional`

Contains information about material related to the product.

#### RelatedWork
`Optional, Repeatable`

A work that is related to the product.

```xml
<RelatedWork>
    <WorkRelationCode>49</WorkRelationCode>
    <WorkIdentifier>
        <WorkIDType>06</WorkIDType>
        <IDValue>10.12345/01902080</IDValue>
    </WorkIdentifier>
</RelatedWork>
```

**Sub-elements**:
- `WorkRelationCode` - An ONIX code for the relation of the work.
  - `49`: Other work in same collection
- `WorkIdentifier` - A unique identifier for the work.
- `WorkIDType` - An ONIX code for the type of identifier.
  - `06`: DOI
- `IDValue` - The identifier value.

##### ProductRelationCode
`Mandatory, Repeatable`

An ONIX code for the relation of the product.

##### ProductIdentifier
`Mandatory, Repeatable`

A unique identifier for the product.

#### RelatedProduct
`Optional, Repeatable`

A product that is related to the product.

```xml
<RelatedProduct>
    <ProductRelationCode>01</ProductRelationCode>
    <ProductIdentifier>
        <ProductIDType>06</ProductIDType>
        <IDValue>10.12345/01234098</IDValue>
    </ProductIdentifier>
</RelatedProduct>
```

**Sub-elements**:
- `ProductRelationCode` - An ONIX code for the relation of the product.
  - `01`: Includes
  - `06`: Alternative format
  - `34`: Cites
- `ProductIdentifier` - A unique identifier for the product.
- `ProductIDType` - An ONIX code for the type of identifier.
  - `01`: Proprietary
  - `06`: DOI
  - `15`: ISBN-13
- `IDTypeName` - A name for the proprietary identifier.
- `IDValue` - The identifier value.

##### ProductRelationCode
`Mandatory, Repeatable`

An ONIX code for the relation of the product.

##### ProductIdentifier
`Mandatory, Repeatable`

A unique identifier for the product.

### ProductSupply
`Optional, Repeatable`

Contains information about the supply of the product.

#### Market
`Optional, Repeatable`

A market for the product.

```xml
<Market>
    <Territory>
        <RegionsIncluded>WORLD</RegionsIncluded>
    </Territory>
</Market>
```

**Sub-elements**:
- `Territory` - The territory of the market.
- `RegionsIncluded` - The regions included in the territory.

#### SupplyDetail
`Mandatory, Repeatable`

Details of the supply of the product.

```xml
<SupplyDetail>
    <Supplier>
        <SupplierRole>09</SupplierRole>
        <SupplierName>My Publisher Name</SupplierName>
        <Website>
            <WebsiteRole>02</WebsiteRole>
            <WebsiteDescription>Publisher's website: webpage for this product</WebsiteDescription>
            <WebsiteLink>https://my.publisher.com/catalog/book/1</WebsiteLink>
        </Website>
    </Supplier>
    <ProductAvailability>20</ProductAvailability>
    <SupplyDate>
        <SupplyDateRole>08</SupplyDateRole>
        <Date dateformat="00">20240101</Date>
    </SupplyDate>
    <Price>
        <PriceType>02</PriceType>
        <PriceAmount>9.99</PriceAmount>
        <CurrencyCode>USD</CurrencyCode>
        <Territory>
            <RegionsIncluded>WORLD</RegionsIncluded>
        </Territory>
    </Price>
</SupplyDetail>
```

##### Supplier
`Mandatory, Repeatable`

The supplier of the product.

```xml
<Supplier>
    <SupplierRole>09</SupplierRole>
    <SupplierName>My Publisher Name</SupplierName>
    <Website>
        <WebsiteRole>02</WebsiteRole>
        <WebsiteDescription>Publisher's website: webpage for this product</WebsiteDescription>
        <WebsiteLink>https://my.publisher.com/catalog/book/1</WebsiteLink>
    </Website>
</Supplier>
```

###### SupplierRole
`Optional`

An ONIX code for the role of the supplier. Default `09` (Publisher's sales agent).

| ONIX Code | Description |
| :--- | :--- |
| 09 | Publisher to end-customers |
| 11 | Non-exclusive distributor to end-customers |

```xml
<SupplierRole>09</SupplierRole>
```

###### SupplierName
`Optional`

The name of the supplier.

| Supplier Name |
| :--- |
| Project MUSE |
| OAPEN |
| DOAB |
| JSTOR |
| EBSCO Host |
| OCLC KB |
| ProQuest KB |
| ProQuest ExLibris |
| EBSCO KB |
| JISC KB |
| Google Books |
| Internet Archive |
| ScienceOpen |
| SciELO Books |
| Zenodo |

```xml
<SupplierName>My Publisher Name</SupplierName>
```

###### Website
`Optional, Repeatable`

A website associated with the supplier.

**Sub-elements**:
- `WebsiteRole` - An ONIX code for the role of the website.
  - `02`: Publisher's website for a specific work
  - `36`: Supplier’s website for a specified work
  - `29`: URL for full content
- `WebsiteDescription` - A description of the website.
- `WebsiteLink` - The URL of the website.

```xml
<Website>
    <WebsiteRole>02</WebsiteRole>
    <WebsiteDescription>Publisher's website: webpage for this product</WebsiteDescription>
    <WebsiteLink>https://my.publisher.com/catalog/book/1</WebsiteLink>
</Website>
```

##### ProductAvailability
`Optional`

An ONIX code for the availability of the product. Default `20` (Available).

```xml
<ProductAvailability>20</ProductAvailability>
```

##### SupplyDate
`Optional, Repeatable`

A date related to the supply of the product.

**Sub-elements**:
- `SupplyDateRole` - An ONIX code for the role of the date.
  - `08`: Expected availability date
- `Date` - The date in `YYYYMMDD` format.

```xml
<SupplyDate>
    <SupplyDateRole>08</SupplyDateRole>
    <Date dateformat="00">20240101</Date>
</SupplyDate>
```

##### Price
`Optional, Repeatable`

The price of the product.

```xml
<Price>
    <PriceType>02</PriceType>
    <PriceAmount>9.99</PriceAmount>
    <CurrencyCode>USD</CurrencyCode>
    <Territory>
        <RegionsIncluded>WORLD</RegionsIncluded>
    </Territory>
</Price>
```

###### PriceType
`Optional`

An ONIX code for the type of price. Default `02` (RRP excluding tax).

```xml
<PriceType>02</PriceType>
```

###### PriceAmount
`Mandatory`

The amount of the price.

```xml
<PriceAmount>9.99</PriceAmount>
```

###### CurrencyCode
`Mandatory`

An ISO 4217 code for the currency of the price.

```xml
<CurrencyCode>USD</CurrencyCode>
```

###### Territory
`Mandatory`

The territory for the price.

**Sub-elements**:
- `RegionsIncluded` - The regions included in the territory.

```xml
<Territory>
    <RegionsIncluded>WORLD</RegionsIncluded>
</Territory>
```
