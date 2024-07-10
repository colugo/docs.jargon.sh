# Data Definitions 

---

Without a good defintion, it's hard for people to really understand what the Properties in your Domain mean. 

## Using the Data Definitions Sidebar

To write or view Data Definitions:

1. Click the Data Definitions button in the Toolbar
2. Use the Right and Left arrows in the Sidebar to scroll through Definitions. As you scroll, the cursor position in the text editor of the Domain will move to the Property you're looking at
3. Alternatively, click the line of the Property you want to edit in the text Editor.
4. Write your definition here
5. Definitions will be saved when you save the Domain

## Key - Value pairs

Definitions can also contain key-value pairs of informaion.

Any line that starts with '[' and matches the pattern [key]=value will be stored as a key-value.

You can mix them with the textual-definition, but it's probably a good idea to group them all at the end.

Here's an example:

>
> [key]=value
>
> [key.with.hierarchy]=value
> 

## Jargon recognised Key - Value pairs

Jargon recognises some specific Key - Value pairs that impact different parts of your Domain, or your artefacts.

Recognised keys are highlighted in yellow.

Here is a list, and what they do:
- **[jargon.aggregation]=true** - When used on a property that is a Class, aggregate up all the type's properties to the parent 
- **[jargon.required]=true** - Makes this property required. Also adds the 'required=true' to this property in an OpenAPI specification
- **[jargon.reference]=true** - Treats a child property, which is a class (or an array of classes) as a reference pointer to that class, using the child's class ID
- **[jargon.deprecated]=true** - Marks this property as deprecatd, flagging that it may be removed in the future
- **[jargon.extraEnums]=x,y,z** - Adds extra enumeration values to this usage of a CodeTable. Useful when you are using an imported CodeTable, and you need to add some mechanical values, such as 'None', or 'n/a'
- **[oas.codeColumn]=name** - if this property uses a Code Table, this allows you to select the name of the column that is used 
- **[jargon.maxLength]=5** - adds 'maxLength=5' to this property in an OpenAPI specification, and other outputs
- **[jargon.minLength]=5** - adds 'minLength=5' to this property in an OpenAPI specification, and other outputs
- **[jargon.maximum]=5** - adds 'maximum=5' to this property in an OpenAPI specification, and other outputs
- **[jargon.minimum]=5** - adds 'minimum=5' to this property in an OpenAPI specification, and other outputs
- **[jargon.maxItems]=5** - adds 'maxItems=5' to this property in an OpenAPI specification, and other outputs
- **[jargon.minItems]=5** - adds 'minItems=5' to this property in an OpenAPI specification, and other outputs
- **[jargon.example]=5** - adds 'example=5' to this property in an OpenAPI specification, and other outputs
- **[jargon.pattern]=^(\\([0-9]{3}\\))?[0-9]{3}-[0-9]{4}$** - adds a pattern value to this property in an OpenAPI specification, and other outputs
- **[jargon.abstract]=true** - If this is a super class, replaces the schema content with oneOf for each of the subClasses
- **[jargon.jsonSchemaRoot]=true** - Exports this Class, and all its dependencies, into a JSONSchema file
- **[jargon.hideRoute]=true** - Removes the route from the diagram, when used on a property
- **[jargon.routeX]=100** - Moves the routing for the property left and right
- **[jargon.routeY]=-100** - Moves the routing for the property up and down
- **[jargon.showImportedClass]=true** - Adds the imported class from this property to the diagram
- **[jargon.stateTransitions]=true** - Generate state transition API paths based on the lifecycle for this property
- **[jargon.extension]=true** - This is an extension point. No JSONSchema or similar rules will be added to this Class. Implementers can add their own content and it will still pass validation 


- **[oas.additionalProperties]=true** - adds additionalProperties:true to this class in the API / JSONSchema
- **[oas.mediaType]=multipart/form-data** - changes the media type for this class, when it's in the body of a request
- **[oas.exclusiveMaximum]=5** - adds 'exclusiveMaximum=5' to this property in an OpenAPI specification
- **[oas.exclusiveMinimium]=5** - adds 'exclusiveMinimium=5' to this property in an OpenAPI specification
- **[oas.pathName]=newPathChunk** - changes the name of this resource in API paths to the verbatim value provided 
- **[oas.readOnly]=true** - adds the 'readOnly=true' to this property in an OpenAPI specification
- **[oas.writeOnly]=true** - adds the 'writeOnly=true' to this property in an OpenAPI specification
- **[oas.queryParamName]=x** - sets the name of this property, when used as an API query parameter
- **[oas.compoundKeyName]=x** - changes the name of the compound key, if this class has multiple identifiers
- **[oas.securityScopeAcronym]=xx** - Creates a security scope for this resource, using the provided acronym
- **[oas.x-enum-descriptions]=name** - if this property uses a Code Table, this allows you to select the column name to use in OpenAPI specifications for the x-enum-descriptions property
- **[oas.includeClass]=true** - Force this class to be included in the OpenAPI specification 


- **[sql.type]=varchar** - Force the generated SQL column type for this property


- **[jsonld.contextOmit]=true** - Do not include this property in the @Context file 
- **[jsonld.contextPrefix]=prefix** Force a prefix in @Context file
- **[jsonld.contextURI]=https://..** Force URI in @Context file
- **[jsonld.contextLocalName]=Name** Force local name in @Context file



## Writing Data Definitions

Every Class's Property in your Domain can have precise Definitions written to explain what it is, what it's for, how to use it, and guidance on how to correctly populate it.


## Define in the singular

**Example:** Article Number

**Not so good definition** | Reference number identifying articles

**Better** | A reference number that describes an article

?> The 'not so good' definition uses the plural word "articles". This makes it ambiguous since it could imply that article numbers can apply to more than one article


## Don't negate

**Example:** Freight Cost Amount


**Not so good definition** | Costs which are not related to packing, documentation, loading, unloading and insurance

**Better** | The cost incurred by a shipper moving goods from one place to another

?> The 'not so good' definition doesn't specify what is actually in the definition

## Use phrases

**Example:** Agent Name


**Not so good definition** | Representative

**Better** |  The name of a party authorised to act on behalf of another party

?>  'Representative' is a near-synonym of the item's name. It doesn't actually explain anything.

**Example:** Country Name


**Not so good definition** | Name of a country

**Better** |  The commonly known, short name that identifies a country

?>  Simply restating the name in sentence form doesn't describe the concept that is a short name, vs. an expanded or long Name

**Example:** Mailing Address Country


**Not so good definition** | The mailing address country name is the name of the country where the mail piece is delivered.

**Better** |  The name of the country where a mail piece is delivered

?>  Repeating the item's name in a sentence doesn't add anything that clarifies the item's intent. There is also no reason to use more words than needed.


## Only use commonly understood abbreviations

**Example:** Tide Height


**Not so good definition** | The vertical distance from MSL to a specific tide level

**Better** |  The vertical distance from mean sea level (MSL) to a specific tide level

?>  MSL may not be a commonly understood abbreviation and some members may need to refer to other sources to determine what it represents


## Don't embed other definitions

**Example:** Sample Type Code


**Not so good definition** | The code identifying the kind of sample collected. A sample is a small specimen taken for testing. It can either be an actual sample for testing, or a quality control surrogate sample. A quality control sample is a surrogate sample taken to verify results of actual samples

**Better** |  The code identifying the kind of sample

?>  "quality control surrogate sample" should be defined as a separate item

## Stick to the essentials

**Example:** Invoice Amount


**Not so good definition** | The total sum of all chargeable items mentioned on an invoice, taking into account deductions on one hand, such as allowances and discounts, and additions on the other hand, such as charges for insurance, transport, handling, etc

**Better** |  The total sum charged on an invoice

?> There is a lot on extra information that isn't relevant

## Don't overprescribe

**Example:** Consignment Loading Sequence Number


**Not so good definition** | The number indicating the sequence in which consignments are loaded in a truck

**Better** |  The number indicating the sequence in which consignments are loaded for transport

?> Consignments can be transported by more than trucks.

## Be precise

**Example:** Country Code


**Not so good definition** | The code that represents a country

**Better** |  The  alphabetic code assigned by the International Standards Organisation (ISO) 3166-1 to represent a country

?>  Country Codes are assigned by various standards and organisations. Without specifying which standard is being used, interoperability issues are likely to occur

## Be concise

**Example:** Character Set Name


**Not so good definition** | The name given to the set of phonetic or ideographic symbols in which data is encoded, for the purpose of this metadata registry, or, as used elsewhere, the capability of systems hardware and software to process data encoded in one or more scripts

**Better** |  The name given to the set of phonetic or ideographic symbols in which data is encoded

?>  Don't include unnecessary information that doesn't actually describe what the item is

## Stand alone

**Example:** School Location City Name


**Not so good definition** | See "school site"

**Better** |  The name of the city where a school is situated

?>  Don't rely on other definitions to understand the meaning of items

## Don't be restrictive

**Example:** Income Tax Gross Amount


**Not so good definition** | The amount of income tax payable on the company's annual return before the allowance of any rebates/tax offsets or credits

**Better** |  The amount of income tax payable before the allowance of any rebates/tax offsets or credits

?>  By being overly restrictive the item can only be used in one context, forcing other similar items to be created

## Avoid circular reasoning

**Example:** Employee and Employee ID Number


**Employee definition** | The number assigned to an Employee

**Employee ID Number definition** | The person corresponding to the an employee ID number

?>  Each definition refers to the other for it's meaning. Neither definition actually provides any meaning.
