% The Zest of gist
% Peter Winstanley
%

# gist

gist is a minimalist upper ontology created by [Semantic Arts](https://semanticarts.com).  Is is described in [https://semanticarts.com/gist](https://semanticarts.com) adn development is handled in the repo at [https://github.com/semanticarts/gist](https://github.com/semanticarts/gist).

### gist Metrics

This is a set of metrics from the [Protege](https://protege.stanford.edu/) readout that users may find useful in understanding the recognising the simplicity of the gist ontology.  A key point to note is that there are generally under 150 classes and around 100 object properties in any version of the gist ontology, and this small scale makes it easier for users to develop familiarity with the ontology.  It is also useful to recognise that there are a large number of axioms in ths ontology, and this reflects the specificity of the classes and properties.

| Metric | value | Class Axioms | count |Object Property Axioms | count |Data Property Axioms | count |Individual Axioms | count |Annotation Axioms | count |
|--------|-------|--------|-------|--------|-------|--------|-------|--------|-------|--------|-------|
|Axiom| 1444|SubClassOf| 67|SubObjectPropertyOf| 30|SubDataPropertyOf| 2|ClassAssertion| 31|AnnotationAssertion| 656|
|Logical axiom count| 493|EquivalentClasses| 90|EquivalentObjectProperties| 0|EquivalentDataProperties| 0|ObjectPropertyAssertion| 16|AnnotationPropertyDomain| 0|
|Declaration axioms count| 293|DisjointClasses| 100|InverseObjectProperties| 20|DisjointDataProperties| 0|DataPropertyAssertion| 17|AnnotationPropertyRangeOf| 0|
|Class count| 142|GCI count| 0|DisjointObjectProperties| 1|FunctionalDataProperty| 1|NegativeObjectPropertyAssertion| 0|||
|Object property count| 109|Hidden GCI Count| 7|FunctionalObjectProperty| 4|NegativeDataPropertyAssertion| 0|||
|Data property count| 23|||InverseFunctionalObjectProperty| 2|DataPropertyDomain| 15|SameIndividual| 0|||
|Individual count| 17|||TransitiveObjectProperty| 8|DataPropertyRange| 17|DifferentIndividuals| 1|||
|Annotation Property count| 10|||SymmetricObjectProperty| 0|||||||
|||||AsymmetricObjectProperty| 0|||||||
|||||ReflexiveObjectProperty| 0|||||||
|||||IrrefexiveObjectProperty| 0|||||||
|||||ObjectPropertyDomain| 25|||||||
|||||ObjectPropertyRange| 46|||||||
|||||SubPropertyChainOf| 0|||||||



# Constellations of gist Classes and Properties: v 10.0.0

gist used to be provided in a modular form, and the gathering together of descriptions of classes and properties in this document is based on the modular structure used at that time.



# Address

## Address
A reference to a place (real or virtual) that can be located by some routing algorithm, and where messages or things can be sent to or retrieved from. E.g. PO Box or URL to a PDF file.

**subClassOf** gist:Content

## BuildingAddress
An address to which you can send mail, or that you could find in the physical world.

**subClassOf:**  gist:streetAddressOf some gist:Building

**subClassOf:**  Address		

## ElectronicMessageAddress
Any place an electronic message (email, fax, etc.) can be sent.

**subClassOf:**  Address	

## EmailAddress
An email address is a unique identifier for an email account. It is used to both send and receive email messages over the Internet.

**subClassOf:**  ElectronicMessageAddress	

## PostalAddress
A set of codes the postal authorities can use to deliver physical mail.

**subClassOf:**  Address	

## TelephoneNumber
A numeric code a telephonic device uses for contacting another telephonic device.	

**subClassOf:**  Address

| Property|Label|Type|Definition|subPropertyOf|Domain|Range|Inverse|
| --------|-----|----|----------|-------------|------|------|------|
| communicationAddressOf  | communication address of  | ObjectProperty | Whose address is this                                        |               |        |                      |                        |
| hasCommunicationAddress | has communication address | ObjectProperty | Points to a general class of places you can send messages including  postal addresses, fax numbers, phone numbers, email, web site, etc. |               |        | gist:Address         | communicationAddressOf |
| hasStreetAddress        | has street address        | ObjectProperty | A place that can be found on a map, has geo coordinates; you could live  or work there. |               |        | gist:BuildingAddress |                        |
| streetAddressOf         | street address of         | ObjectProperty | Whose street address is this                                 |               |        |                      | hasStreetAddress       |


# Agreement

## Account
An agreement having a balance, as in a bank account, or credit card account, or Accounts Receivable account.	

**EquivalentClass** gist:Agreement  and (gist:hasMagnitude some gist:Balance)

## Agreement
Something which two or more People or Organizations mutually commit to do.	

**EquivalentClass** gist:Commitment  and (gist:hasParty some (gist:Organization  or gist:Person))  and (gist:hasDirectPart min 2 gist:Obligation)

## Balance
An amount decremented or incremented by a series of transactions.	

**EquivalentClass** gist:Magnitude  and (gist:affectedBy some gist:Transaction)

## Commitment
An obligation (possibly unilateral).	

**EquivalentClass** (gist:Requirement  or gist:Restriction)  and (gist:categorizedBy some gist:DegreeOfCommitment)  and (gist:hasGiver some (gist:Organization  or gist:Person))

## ContingentObligation
An obligation that is not yet firm.  There is some contingent event, the occurrence of which will cause the obligation to become firm.	

**EquivalentClass** gist:Commitment  and (gist:hasGiver some (gist:Organization  or gist:Person))  and (gist:triggeredBy some gist:Event)

## Contract
An Agreement which can be enforced by law	

**EquivalentClass** gist:Agreement  and (gist:hasJurisdiction some gist:GovernmentOrganization)

## ContractTerm
A specification of some aspect of a contract.	

**subClassOf:**  Specification

## DegreeOfCommitment
The difficulty of reversing a commitment.

**subClassOf:**  Category

## Obligation
A future commitment from one organization or person to another. Contracts are sets of obligations to do or forbear, or to indemnify or warrant.	

**EquivalentClass** gist:Commitment  and (gist:hasGetter some (gist:Organization  or gist:Person))  and (gist:hasGiver some (gist:Organization  or gist:Person))


## Offer
A commitment to buy or sell a described or identified part or service.	

**EquivalentClass** gist:ContingentObligation  and (gist:hasGiver some (gist:Organization  or gist:Person))  and (gist:hasDirectPart some gist:CatalogItem)  and (gist:hasMagnitude some gist:Monetary)  and (gist:plannedEnd some gist:TimeInstant)  and (gist:start some gist:TimeInstant)

## Transaction
An event which has an effect on at least one accumulator.	

**subClassOf:**  Event

| Property        | Label            | Type           | Definition                                                   | subPropertyOf       | Domain | Range                            | Inverse    |
| --------------- | ---------------- | -------------- | ------------------------------------------------------------ | ------------------- | ------ | -------------------------------- | ---------- |
| affectedBy      | affected by      | ObjectProperty | Where the effect came from                                   |                     |        |                                  |            |
| affects         | affects          | ObjectProperty | The subject has or had or will have an effect on the object  |                     |        |                                  | affectedBy |
| hasGetter       | has getter       | ObjectProperty | The recipient                                                | gist:hasParticipant |        |                                  |            |
| hasGiver        | has giver        | ObjectProperty | The active party, the one with the obligation or the one initiating the  transfer | gist:hasParticipant |        |                                  |            |
| hasJurisdiction | has jurisdiction | ObjectProperty | When laws and contracts are meted out                        |                     |        |                                  |            |
| hasParty        | has party        | ObjectProperty | The people or organizations participating in an event, agreement or  obligation | gist:hasParticipant |        | gist:Organization or gist:Person |            |
| hasParticipant  | has participant  | ObjectProperty | Relates something (e.g. an agreement) to things that play a role, or take  part or are otherwise involved in some way. |                     |        |                                  |            |

# Category

## ControlledVocabulary
A collection of terms approved and managed by some organization or person.	

**EquivalentClass** gist:Collection  and (gist:governedBy some (gist:Organization  or gist:Person))  and (gist:hasMember some gist:Category)


## Tag
This is for folksonomy type terms, which can be made up on the fly by users.	

**EquivalentClass** gist:Category  and (gist:hasTag some xsd:string)


## Taxonomy
A controlled vocabulary arranged as a hierarchy of concepts.	

**EquivalentClass** gist:ControlledVocabulary  and (gist:hasMember some (gist:Category  and ((gist:hasSubCategory some gist:Category)  or (gist:hasSuperCategory some gist:Category))))


| Property                    | Label                          | Type             | Definition                                                   | subPropertyOf              | Domain | Range | Inverse              |
| --------------------------- | ------------------------------ | ---------------- | ------------------------------------------------------------ | -------------------------- | ------ | ----- | -------------------- |
| hasNavigationalChild        | has navigational child         | ObjectProperty   | Used for informal hierarchical taxonomies. Supports polyhierarchies |                            |        |       |                      |
| hasNavigationalParent       | has navigational parent        | ObjectProperty   | Used for informal hierarchical taxonomies. Supports polyhierarchies |                            |        |       | hasNavigationalChild |
| hasUniqueNavigationalParent | has unique navigational parent | ObjectProperty   | Used for taxos that must have single parents                 | gist:hasNavigationalParent |        |       |                      |
| hasSuperCategory            | has supercategory              | ObjectProperty   | The subject category is included by, or narrower than, the object  category. Everything categorized by the subcategory can be inferred to be  categorized by the supercategory. |                            |        |       | hasSubCategory       |
| hasUniqueSuperCategory      | has unique supercategory       | ObjectProperty   | Used for taxos that must have single parents                 | gist:hasSuperCategory      |        |       |                      |
| hasDirectSuperCategory      | has direct supercategory       | ObjectProperty   | The subject category is a subcategory of the object category. This  property defines the direct links in a category hierarchy; no intermediate  categories can exist between the direct links. | gist:hasSuperCategory      |        |       |                      |
| hasSubCategory              | has subcategory                | ObjectProperty   | The subject category is inclusive of, or broader than, the object  category. Everything categorized by the subcategory can be inferred to be  categorized by the supercategory. |                            |        |       |                      |
| hasDirectSubCategory        | has direct subcategory         | ObjectProperty   | The subject category is a supercategory of the object category. This  property defines the direct links in a category hierarchy; no intermediate  categories can exist between the direct links. | gist:hasSubCategory        |        |       |                      |
| hasTag                      | has tag                        | DatatypeProperty | Used for folksonomy style categories (non controlled vocabulary) |                            |        |       |                      |

# Content

## ContentExpression
Intellectual Property reduced to text, audio etc.  If it contains text (written or spoken), it may be in a language.

**subClassOf:**  Content

**subClassOf:**  gist:categorizedBy some gist:GeneralMediaType	

**subClassOf:**  gist:expressedIn some gist:Language

## FormattedContent
Content which is in a particular format. (E.g., HTML, PDF, JPG.)	

**EquivalentClass** gist:ContentExpression  and (gist:expressedIn some gist:MediaType)


## MediaType
A digitized type that computer applications can recognize.

**subClassOf:**  Category	

## Medium
A physicality on which a work could be implemented or exposed. E.g., paper, clay, or a computer monitor.

**subClassOf:**  Category	

## Message
A specific instance of content sent from an Organization, Person, or Application to at least one other Organization, Person, or Application.	

**EquivalentClass** gist:ContentExpression  and (gist:fromAgent some (gist:Person  or gist:Organization))  and (gist:toAgent some (gist:Person  or gist:Organization))

## RenderedContent
Content which has been expressed, either to print, or through speakers, or on a monitor.	

**EquivalentClass** gist:ContentExpression  and (gist:expressedIn some gist:MediaType)  and (gist:renderedOn some gist:Medium)

## Text
Content expressed as words and numbers (not graphics).	

**EquivalentClass** gist:Content  and (gist:expressedIn some gist:Language)  and (gist:containedText some xsd:string)

### about
Subject matter of a document.	

**Domain:**  Content	

| Property      | Label          | Type             | Definition                                                   | subPropertyOf       | Domain       | Range                            | Inverse |
| ------------- | -------------- | ---------------- | ------------------------------------------------------------ | ------------------- | ------------ | -------------------------------- | ------- |
| about         | about          | ObjectProperty   | Subject matter of a document.                                |                     | gist:Content |                                  |         |
| containedText | contained text | DatatypeProperty | Links to the string corresponding to Text                    |                     |              | xsd:string                       |         |
| describedIn   | described in   | ObjectProperty   | Document the subject matter appeared in                      |                     |              |                                  | about   |
| encryptedText | encrypted text | DatatypeProperty | Links to the string corresponding to EncryptedText           | gist:containedText  |              | xsd:string                       |         |
| expressedIn   | expressed in   | ObjectProperty   | The language something was expressed in                      |                     |              |                                  |         |
| fromAgent     | from agent     | ObjectProperty   | The party that is the source of something (e.g. a message, shipment,  etc.) | gist:hasParticipant |              | gist:Organization or gist:Person |         |
| toAgent       | to agent       | ObjectProperty   | The party that is the recipient of something (e.g. a message, shipment,  etc.) | gist:hasParticipant |              | gist:Organization or gist:Person |         |
| renderedOn    | rendered on    | ObjectProperty   | What media something was rendered On                         |                     |              |                                  |         |

# Event

## ContemporaneousEvent
An event that actually started after the present time.  When we record an end time it ceases to be contemporaneous	

**EquivalentClass** gist:Event  and (gist:actualStart some gist:TimeInstant)  and (gist:actualEnd max 0 gist:TimeInstant)

## ContingentEvent
An event with a probability of happening in the future, and usually dependent upon some other event or condition.	

**EquivalentClass** gist:Event  and (gist:hasMagnitude some gist:Percentage)  and (gist:plannedEnd some gist:TimeInstant)  and (gist:plannedStart some gist:TimeInstant)


## HistoricalEvent
An event which occurred in time, with an actual end earlier than the present moment.	

**EquivalentClass** gist:Event  and (gist:actualEnd some gist:TimeInstant)  and (gist:actualStart some gist:TimeInstant)


## PhysicalEvent
An event that can be said to have occurred at some place in space.	

**EquivalentClass** gist:Event  and (gist:occursAt some gist:Place)

## PlannedEvent
An event which, at the time it is created, is to occur in the future.	

**EquivalentClass** gist:Event  and (gist:plannedEnd some gist:TimeInstant)  and (gist:plannedStart some gist:TimeInstant)


## Project
A project is a task (usually a longer duration task) made up of other tasks.	

**EquivalentClass** gist:Task  and (gist:hasSubTask some gist:Task)


## ScheduledTask
A task planned to occur.  When it was scheduled, it would have been in the future, but now might be in the past.	

**EquivalentClass** gist:PlannedEvent  and gist:Task


## Task
A task which has been defined and either scheduled or accomplished, or both.	

**EquivalentClass** gist:Event  and (gist:hasGoal some gist:Intention)

## TaskTemplate
An outline of a task of a particular type, that will, when instantiated, generate an actual (unscheduled) task.	

**EquivalentClass** gist:Template  and (gist:hasGoal some gist:Intention)

| Property         | Label               | Type           | Definition                                                   | subPropertyOf            | Domain    | Range            | Inverse         |
| ---------------- | ------------------- | -------------- | ------------------------------------------------------------ | ------------------------ | --------- | ---------------- | --------------- |
| directSubTaskOf  | direct subtask of   | ObjectProperty | Immediate parent task                                        |                          |           |                  |                 |
| hasSubTask       | has subtask         | ObjectProperty | A task that is part of a larger task. The time frame of the subtasks may  overlap but may not extend beyond the time frame of the parent task. A  subtask may be part of more than one parent task. |                          | gist:Task | gist:Task        |                 |
| subTaskOf        | subtask of          | ObjectProperty | All the upper tasks this task belongs to                     |                          |           |                  | hasSubTask      |
| hasDirectSubTask | has direct sub task | ObjectProperty | Immediate child task                                         | gist:hasSubTask          | gist:Task | gist:Task        | directSubTaskOf |
| hasGoal          | has goal            | ObjectProperty | The reason for doing something                               |                          |           |                  |                 |
| lastModifiedOn   | last modified on    | ObjectProperty | Date that something was modified.                            | gist:actual              |           | gist:TimeInstant |                 |
| occursAt         | occurs at           | ObjectProperty | The geospatial place where something happened or will happen |                          |           |                  |                 |
| planned          | planned             | ObjectProperty | Dates that were in the future at the time they were made.    |                          |           | gist:TimeInstant |                 |
| plannedStart     | planned start       | ObjectProperty | A date/time that was at least at some point in time in the future. It may  be in the past now, but when we planned it, it was in the future. | gist:start, gist:planned |           | gist:TimeInstant |                 |
| plannedEnd       | planned end         | ObjectProperty | A date/time that was at least at some point in time in the future. It may  be in the past now, but when we planned it, it was in the future. | gist:end, gist:planned   |           | gist:TimeInstant |                 |
| recordedOn       | recorded on         | ObjectProperty | Date that something was posted, not necessarily the date it occurred.  Must be after the occurred date, but could be before or after the planned  date. (Unusual, but I could record today that I expected to be paid last  week.) | gist:actual              |           | gist:TimeInstant |                 |

# Intention

## BundledCatalogItem
Any combination of descriptions of things offered together.  Could be a kit (several parts offered together), but could also be a product plus a warranty.	

**EquivalentClass** gist:CatalogItem  and (gist:hasDirectPart some gist:CatalogItem)


## CatalogItem
A description of a product or service to be delivered, given in a sufficient level of detail that a receiver could determine whether delivery constituted discharge of the obligation to deliver.	

**subClassOf:**  Specification

## Goal
A specific intentional endpoint.  One can tell whether it has been achieved, as opposed to an intention, which may not have an evaluation function.

**subClassOf:**  Intention	

## Permission
A description of things one is permitted to do. This could be broad, such as free speech, but more often is very specific, such as the right of egress through a particular property.

**EquivalentClass** gist:Intention  and (gist:allows some gist:Behavior)



## ProductCategory
Any of many ways of categorizing products, including models, NATO product codes, and the like.

**subClassOf:**  Category	

## ProductSpecification
Offering something which could be physically warehoused or digitally stored.	

**EquivalentClass** gist:CatalogItem  and (gist:categorizedBy some gist:ProductCategory)


## Requirement
A documented physical or functional need that a particular design, product, or process must be able to perform.  Alternately, the obligation of a person or organization to behave in a certain way (i.e., drive on the right side of the road).	

**subClassOf:**  Intention

## Restriction
A description of things one is prevented from doing.  Most laws are restrictions.	

**EquivalentClass** gist:Intention  and (gist:prevents some gist:Behavior)


## ServiceSpecification
A description of something that can be done for a person or organization (which produces some form of an act).	

**EquivalentClass** gist:CatalogItem  and (gist:basisFor some gist:Event)


## Specification
A set of requirements to be satisfied by a material, design, product, or service.	

**subClassOf:**  Requirement

| Property   | Label       | Type           | Definition                                                   | subPropertyOf | Domain         | Range          | Inverse |
| ---------- | ----------- | -------------- | ------------------------------------------------------------ | ------------- | -------------- | -------------- | ------- |
| allows     | allows      | ObjectProperty | The intention (say a grant) allows a particular kind of activity (for  instance egress) |               | gist:Intention | gist:Behavior  |         |
| basedOn    | based on    | ObjectProperty | The Object is a foundation for, a starting point for, gave rise to or  justifies the Subject |               |                |                |         |
| basisFor   | basis for   | ObjectProperty | The Subject is a foundation for, a starting point for, gave rise to or  justifies the Object |               |                |                | basedOn |
| conformsTo | conforms to | ObjectProperty | The subject conforms to the Object, e.g. meet an obligation, meet terms  of an offer, adhere to a specification |               |                | gist:Intention |         |
| prevents   | prevents    | ObjectProperty | The intention (say a law) is intended to prevent this kind of behavior  (say jay-walking) |               | gist:Intention | gist:Behavior  |         |
| requires   | requires    | ObjectProperty | An intention that sets out a state of satisfaction (you are required to  drive on right side of the road) |               | gist:Intention | gist:Behavior  |         |


# IoT

## Actuator
A device that can affect the real world via a message interface

**subClassOf:**  Equipment	

## Controller
A device that takes messages or signals from a sensor and decides through algorithms whether and which actuator to fire via messages	

**EquivalentClass** gist:Equipment  and (gist:categorizedBy some gist:ControllerType)  and (gist:directs some gist:Actuator)  and (gist:respondsTo some gist:Sensor)


## ControllerType
A kind of controller.

**subClassOf:**  Category	

## MessageDefinition
Each pulse from a Sensor is reflected in a message, as well as each instruction to an Actuator

**subClassOf:**  SchemaMetaData	

## PhenomenaType
The things that a sensor can sense, such as light, heat, current, moisture, etc.

**subClassOf:**  Category	

## PhysicalActionType
The effects to be realized in the real world, such as lifting a garage door, turning off a valve, dropping cadmium rods, etc.	

**subClassOf:**  Category

## Sensor
A device that can detect something and report it. Light sensors, temperature sensors,	

**subClassOf:**  Equipment

| Property    | Label        | Type           | Definition                                                   | subPropertyOf | Domain | Range | Inverse |
| ----------- | ------------ | -------------- | ------------------------------------------------------------ | ------------- | ------ | ----- | ------- |
| accepts     | accepts      | ObjectProperty | The types of input messages that will be allowed             |               |        |       |         |
| directs     | directs      | ObjectProperty | The set of actuators that a controller can affect            |               |        |       |         |
| respondsTo  | responds to  | ObjectProperty | The set of sensors that a controller is attached to          |               |        |       |         |
| viableRange | viable range | ObjectProperty | The area over which the sensor can sense (might be a small geospatial  area or a specific wire in a circuit) |               |        |       |         |


# Magnitude
Base class for units which can be converted.  The primitive units can be converted from one measurement system to another; the complex units (ratio or product) have to decompose to their primitives.

**EquivalentClass** (gist:hasPrecision some gist:Magnitude)  and (gist:hasUoM some gist:UnitOfMeasure)  and (gist:decimalValue some xsd:double)

**EquivalentClass** (gist:hasPrecision some gist:Magnitude)  and (gist:hasUoM some gist:UnitOfMeasure)  and (gist:decimalValue some xsd:double)

**EquivalentClass** (gist:hasPrecision some gist:Magnitude)  and (gist:hasUoM some gist:UnitOfMeasure)  and (gist:decimalValue some xsd:double)

**disjointWith** gist:TimeInstant, gist:Organization, gist:UnitOfMeasure



## Count
A measure that involves countable amounts (?eaches? as well as cases, etc.). Can be decimal.

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:CountingUnit)


## ElectricCurrent
A flow of electric charge.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:ElectricalCurrentUnit)


## InformationQuantity
An amount of data, such as 6 petabytes, or 640KB.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:DataSizeUnit)


## LuminousIntensity
A measure of the wavelength-weighted power emitted by a light source in a particular direction per unit solid angle.  This is based on the luminosity function, a standardized model of the sensitivity of the human eye.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:LuminousIntensityUnit)


## Mass
Magnitude of mass.

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:MassUnit)

## MolarQuantity
Amount of a substance, as counted molecules.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:MoleUnit)

## Monetary
A special type of magnitude, due to the way rounding is handled in math and the temporal aspect of conversion.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:CurrencyUnit)

## Percentage
A ratio where the numerator and denominator are of the same unit of measure.	

**subClassOf:**  RatioMagnitude

## ProductMagnitude
A magnitude expressed as a product of primitives.  (E.g., Force = M **A).	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:ProductUnit)


## RatioMagnitude
This is a number whose unit of measure is a ratio.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:RatioUnit)

## Temperature
The degree or intensity of heat present in a substance or object, especially as expressed according to a comparative scale.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:TemperatureUnit)


| Property | Label               | Type           | Definition                                                   | subPropertyOf | Domain         | Range              | Inverse |
| -------- | ------------------- | -------------- | ------------------------------------------------------------ | ------------- | -------------- | ------------------ | ------- |
| hasUoM   | has unit of measure | ObjectProperty | Which unit of measure you are using. All measures are expressed in some  unit of measure, even if we don't know what it is initially. |               | gist:Magnitude | gist:UnitOfMeasure |         |


# Measure

## Aspect
A very general term for the characteristic of something that is being measured.  E.g., property (height) or a process (cycle time) or a behavior (loyalty).

**subClassOf:**  Category	

## OrderedCollection
A collection where the members are in a fixed sequence.

**subClassOf:**  Collection	

## OrdinalCollection
An Ordered Collection where no item can be of the same rank as any other item.  In mathematical terms, this is a ?strict total order?.

**subClassOf:**  OrderedCollection

**subClassOf:**  Category

**subClassOf:**  gist:hasOrderedMember only gist:OrdinalMember		

## OrdinalMember
A member of an Ordinal Collection.  It necessarily precedes or is preceded by another Ordinal Member in the same collection. (This last condition cannot be formally stated in OWL).	
**EquivalentClass** gist:orderedMemberOf some gist:OrdinalCollection

**subClassOf:**  gist:Category

**subClassOf:**  (gist:directlyPrecededBy some gist:OrdinalMember)  or (gist:directlyPrecedes some gist:OrdinalMember)

## ReferenceValue
A measure that was neither measured nor estimated but set by fiat. For instance, a goal. There is no Measurement associated with a ReferenceValue.	

**subClassOf:**  Magnitude

| Property           | Label                | Type           | Definition                                                   | subPropertyOf  | Domain | Range | Inverse            |
| ------------------ | -------------------- | -------------- | ------------------------------------------------------------ | -------------- | ------ | ----- | ------------------ |
| aspectOf           | aspect of            | ObjectProperty | What this aspect is referring to                             |                |        |       |                    |
| directlyPrecedes   | directly precedes    | ObjectProperty | A generic ordering relation indicating that the Subject comes immediately  before the Object. | gist:precedes  |        |       | directlyPrecededBy |
| directlyPrecededBy | directly preceded by | ObjectProperty | Inverse of directly precedes                                 |                |        |       |                    |
| hasOrderedMember   | has ordered member   | ObjectProperty | An inverse functional version of hasMember to ensure that no  OrderedMember can be in more than one OrderedCollection., which can quickly  lead to problems. | gist:hasMember |        |       |                    |
| orderedMemberOf    | ordered member of    | ObjectProperty | An inverse of hasOrderedMember                               |                |        |       | hasOrderedMember   |
| precedes           | precedes             | ObjectProperty | A generic ordering relation indicating that the Subject has the same  order as or comes before the Object. The 'greater than or equal to' symbol is  often used for this relation. |                |        |       |                    |


# Network

## Artifact
An intentional, person-made thing, which could be physical or content	

**subClassOf:**  gist:hasGoal some gist:Function


## Component
A component is an artifact that contributes to a system.  Could be a simple mechanical component, such as the float contributing to the toilet tank maintaining a constant level, or much more complex as in the internet of things.	

**EquivalentClass** gist:Artifact  and (gist:contributesTo some gist:System)


## Equipment
Tangible property other than land or buildings.  Any kind of equipment, could be machine, router, car etc.	

**EquivalentClass** gist:Artifact  and gist:PhysicalIdentifiableItem  and (gist:categorizedBy some gist:EquipmentType)

## EquipmentType
Categories of equipment

**subClassOf:**  Category	

## Function
A function is what a specific made item is intended to do.  For instance: transmit electricity, provide ballast, control ambient temperature.	

**subClassOf:**  Intention

## Network
A network is a connected set of links and nodes	

**EquivalentClass** gist:Artifact  and (gist:hasMember some (gist:NetworkLink  or gist:NetworkNode))

## NetworkLink
A link in a network.  This is the abstraction of the network.  The physical instantiation couple be pipes, or wire  but may also be non physical such as wireless networks or organization structures	

## NetworkNode
A node in a network.  Note the network is the abstract representation of the network.  It is physically instantiated with equipment, or in some cases People.	

## System
A system is an artifact with component parts where the parts contribute to the goal of the system	

**EquivalentClass** gist:Artifact  and (gist:hasDirectPart some gist:Component)


| Property          | Label              | Type           | Definition                                                   | subPropertyOf          | Domain | Range | Inverse |
| ----------------- | ------------------ | -------------- | ------------------------------------------------------------ | ---------------------- | ------ | ----- | ------- |
| contributesTo     | contributes to     | ObjectProperty | The parts of a system contribute to the goal/ function of the whole  system |                        |        |       |         |
| hasFromNode       | has from node      | ObjectProperty | The connections at the abstract level of a network. Note this is directed but the parent is the  undirected version | gist:networkConnection |        |       |         |
| hasToNode         | has to node        | ObjectProperty | The connections at the abstract level of a network. Note this is directed  but the parent is the undirected version | gist:networkConnection |        |       |         |
| networkConnection | network connection | ObjectProperty | Abstract connection for when connections are undirected      |                        |        |       |         |


# Organization

## CountryGovernment
The geopolitical body that governs a geopolitical region recognized as a country.	

**EquivalentClass** gist:GovernmentOrganization  and (gist:governs some gist:GeoRegion)  and (gist:recognizedBy some gist:Organization)


## GeoPoliticalRegion
A collection of GeoRegions that are being administered by a Government Organization	

**EquivalentClass** gist:Collection  and (gist:governedBy some gist:GovernmentOrganization)  and (gist:hasMember some gist:GeoRegion)

## GovernmentOrganization
An organization established either by fiat (as a conquering army overtakes a land and declares a government) or by delegation from a fiat government, such as a state or local government or a specific agency. Differs from a corporation in that it cannot be owned.	

**EquivalentClass** gist:Organization  and (gist:recognizedBy some gist:CountryGovernment)


## Group
A collection of People. The group may or may not be an Organization.  Many organizations consist of groups of people, but that is not a defining characteristic.	

**EquivalentClass** gist:Collection  and (gist:hasMember some gist:Person)


| Property             | Label                  | Type           | Definition                                                   | subPropertyOf     | Domain | Range                            | Inverse      |
| -------------------- | ---------------------- | -------------- | ------------------------------------------------------------ | ----------------- | ------ | -------------------------------- | ------------ |
| recognizes           | recognizes             | ObjectProperty | Recognizes                                                   |                   |        |                                  | recognizedBy |
| recognizedBy         | recognized by          | ObjectProperty | The entity that formally acknowledges the existence of, as the State  recognizes the existence of a particular company |                   |        | gist:Organization or gist:Person |              |
| directlyRecognizedBy | directly recognized by | ObjectProperty | The party doing the recognition                              | gist:recognizedBy |        |                                  |              |


# Place

## Building
A man-made structure for dwelling or working.	

**subClassOf:**  Artifact

**subClassOf:**  Landmark

## GeoRoute
An ordered set of GeoPoints that defines a path from starting point to ending point.	

**EquivalentClass** gist:OrderedCollection  and gist:Place  and (gist:hasDirectPart some gist:GeoSegment)

## GeoSegment
A single portion of a GeoRegion which has been divided (i.e., segmented).	

**EquivalentClass** (gist:fromPlace exactly 1 gist:GeoPoint)  and (gist:toPlace exactly 1 gist:GeoPoint)

**subClassOf:**  Place

## GeoVolume
A three-dimensional space on or near the surface of the Earth, such as an oil reservoir, the body of a lake, or an airspace.	

**EquivalentClass** (gist:geoContains some gist:GeoPoint)  and (gist:hasMagnitude some gist:Volume)

**subClassOf:**  Place

## Landmark
Something permanently attached to the Earth.	

**EquivalentClass** gist:PhysicalIdentifiableItem  and (gist:permanentGeoOccupies some (gist:GeoRegion  or gist:GeoVolume))

**subClassOf:**  Place

## Place
Union of all the geo classes	

| Property               | Label                     | Type           | Definition                                                   | subPropertyOf    | Domain                                                   | Range      | Inverse                |
| ---------------------- | ------------------------- | -------------- | ------------------------------------------------------------ | ---------------- | -------------------------------------------------------- | ---------- | ---------------------- |
| fromPlace              | from place                | ObjectProperty | Origin                                                       |                  |                                                          | gist:Place |                        |
| toPlace                | to place                  | ObjectProperty | Destination                                                  |                  |                                                          | gist:Place |                        |
| geoContains            | geo contains              | ObjectProperty | Relate one place to another place that is contained within the first. |                  | gist:Place                                               | gist:Place | geoContainedIn         |
| geoContainedIn         | geo contained in          | ObjectProperty | Relates one place to another place that contains the first.  |                  |                                                          |            |                        |
| geoOccupies            | geo occupies              | ObjectProperty | A thing occupies are region                                  |                  | gist:PhysicalIdentifiableItem or  gist:PhysicalSubstance | gist:Place | geoOccupiedBy          |
| geoOccupiedBy          | geo occupied by           | ObjectProperty | What is in the location                                      |                  |                                                          |            |                        |
| hasPhysicalLocation    | has physical location     | ObjectProperty | Where something is located                                   |                  |                                                          | gist:Place |                        |
| permanentGeoOccupies   | permanent geo occupies    | ObjectProperty | To be in a fixed position on the earth                       | gist:geoOccupies |                                                          |            | permanentGeoOccupiedBy |
| permanentGeoOccupiedBy | permanent geo occupied by | ObjectProperty | What is in the fixed location                                |                  |                                                          |            |                        |


# TemporalRelation

## TemporalRelation
A relationship existing for a period of time.	

**subClassOf:**  gist:start some gist:TimeInstant

**subClassOf:**  gist:end some gist:TimeInstant	

**subClassOf:**  gist:connectedTo min 2

| Property    | Label        | Type           | Definition                                                   | subPropertyOf | Domain | Range | Inverse |
| ----------- | ------------ | -------------- | ------------------------------------------------------------ | ------------- | ------ | ----- | ------- |
| connectedTo | connected to | ObjectProperty | A non-owning, non-causal, non-subordinate (i.e., peer-to-peer)  relationship. |               |        |       |         |


# Time

## DateInstant
A point in time known only to the accuracy of one day.  Say the signing of the declaration of independence on 7/4/1776	

**EquivalentClass** gist:TimeInstant  and (gist:hasPrecision value gist:_one_day)


## GreenwichInstant
By default time instants are expressed in Greenwich, if you need to be explicit (to calculate offset for instance)	

**EquivalentClass** gist:TimeInstant  and (gist:timeZoneStandardUsed value gist:_greenwichTimeZone)

## HumanInstant
A point in time known only to the accuracy of one minute.  For things like calendar appointments and time reporting	

**EquivalentClass** gist:TimeInstant  and (gist:hasPrecision value gist:_one_minute)


## LocalInstant
A point in time expressed relative to a local time zone. Can be converted to Universal Time using the time zone offset. The precision is used to state how precise this instant is.  Typical values would be day, hour, minute or second.	

**EquivalentClass** gist:TimeInstant  and (gist:sameTimeAs some gist:TimeInstant)  and (gist:timeZoneStandardUsed some gist:TimeZoneStandard)


## SystemInstant
A point in time known to the accuracy of a millisecond.  For posting transaction recorded on times	

**EquivalentClass** gist:TimeInstant  and (gist:hasPrecision value gist:_one_millisecond)

## TimeZone
A region that observes a uniform standard time for legal, commercial, and social purposes.  A typical time zone averages 15? of longitude in width and typically observes a clock time one hour earlier than the zone immediately to the east.	

**EquivalentClass** gist:GeoRegion  and (gist:offsetToUniversal some gist:Duration)

## TimeZoneStandard
The algorithm for getting from Greenwich Mean Time to local time, which includes the time zone offset and rules about daylight savings time.	

**EquivalentClass** gist:Specification  and (gist:basedOn some gist:TimeZone)


#### _day

#### _greenwichTimeZone

#### _millisecond

#### _minute

#### _one_day

#### _one_millisecond

#### _one_minute

#### _second

| Property             | Label                   | Type           | Definition                                                   | subPropertyOf | Domain           | Range                 | Inverse |
| -------------------- | ----------------------- | -------------- | ------------------------------------------------------------ | ------------- | ---------------- | --------------------- | ------- |
| offsetToUniversal    | offset to universal     | ObjectProperty | How many hours the time zone is off GMT                      |               | gist:TimeZone    | gist:Duration         |         |
| sameTimeAs           | same time as            | ObjectProperty | We can have two local time instants refer to the same time, the same  universal time. |               | gist:TimeInstant | gist:TimeInstant      |         |
| timeZoneStandardUsed | time zone standard used | ObjectProperty | the "time zone" with Daylight Savings adjust                 |               | gist:TimeInstant | gist:TimeZoneStandard |         |


# Top

## Area
A measurement of two-dimensional space.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:AreaUnit)

## AreaUnit
A unit of two-dimensional area, such as square inches or hectares.	

**EquivalentClass** gist:ProductUnit  and (gist:multiplicand exactly 1 gist:DistanceUnit)  and (gist:multiplier exactly 1 gist:DistanceUnit)


## BaseUnit
A primitive unit that cannot be decomposed into other units. It can be converted from one measurement system to another.  The base units in gist are the seven primitive units from the System Internationale (SI): (meter, second, kilogram, ampere, kelvin, mole, candela), plus three convenience ones: each. bit and usDollar.	

**EquivalentClass** {gist:_USDollar , gist:_ampere , gist:_bit , gist:_candela , gist:_each , gist:_kelvin , gist:_kilogram , gist:_meter , gist:_mole , gist:_second}

**subClassOf:**  SimpleUnitOfMeasure

## Behavior
A way of categorizing events.  E.g., differentiating drilling versus cutting.	

**subClassOf:**  Category

## Category
A concept or label used to categorize other instances informally. Things that can be thought of as types are usually Categories.	

## Collection
Any identifiable grouping of instances.  For instance, a jury is a collection of people.

**subClassOf:**  gist:hasMember some owl:Thing

## Content
A document, program, image, etc.  (Categories are not content until they are written down.)

**disjointWith** gist:UnitOfMeasure; gist:Organization; gist:TimeInstant; gist:PhysicalIdentifiableItem; gist:GeoPoint; gist:GeoRegion; gist:PhysicalSubstance

**subClassOf:**  Artifact	

## DistanceUnit
A unit to measure linear distance, such as feet or kilometers.	

**EquivalentClass** gist:SimpleUnitOfMeasure  and (gist:hasBaseUnit value gist:_meter)

**disjointWith** gist:MoleUnit; gist:TemperatureUnit; gist:ElectricalCurrentUnit; gist:MassUnit; gist:LuminousIntensityUnit; gist:DurationUnit


## Duration
Time, but not on a timeline.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:DurationUnit)

## DurationUnit
A unit to measure passage of time: hours, days, years.	

**EquivalentClass** gist:SimpleUnitOfMeasure  and (gist:hasBaseUnit value gist:_second)

**disjointWith** gist:TemperatureUnit; gist:MoleUnit; gist:MassUnit; gist:LuminousIntensityUnit; gist:ElectricalCurrentUnit


## Event
Something happening over some period of time, often characterized as some kind of activity being carried out by some person, organization, or software application.	

**EquivalentClass** (gist:characterizedAs some gist:Behavior)  and (gist:end some gist:TimeInstant)  and (gist:start some gist:TimeInstant)

## Extent
A measure of distance, which could be distances over the Earth, and could also be height, width, length, depth, girth, etc.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:DistanceUnit)


## GeoPoint
An individual point on the Earth's surface, identified by latitude, longitude and altitude. If altitude is missing, it is assumed to be at the Earth's surface.  However, altitude is measured from sea level.  these points are to the WGS-84 coordinate system using the GPS decimal lat/long	

**EquivalentClass** (gist:hasAltitude some gist:Extent)  and (gist:latitude some xsd:double)  and (gist:longitude some xsd:double)

**disjointWith** gist:Intention; gist:PhysicalIdentifiableItem; gist:Magnitude; gist:PhysicalSubstance; gist:IntellectualProperty; gist:UnitOfMeasure; gist:Language; gist:TimeInstant; gist:Organization

**subClassOf:**  Place

## GeoRegion
A bounded region (or set of regions) on the surface of the Earth.	

**EquivalentClass** (gist:hasMagnitude some gist:Area)

**subClassOf:**  Place

**disjointWith** gist:PhysicalIdentifiableItem; gist:Language; gist:UnitOfMeasure; gist:TimeInstant; gist:Magnitude; gist:PhysicalSubstance; gist:Intention; gist:IntellectualProperty; gist:Organization; gist:Template
	

## ID
Content that is used to uniquely identify something or someone.	

**EquivalentClass** gist:Content  and (gist:allocatedBy some (gist:IntellectualProperty  or gist:Organization  or gist:Person))  and (gist:uniqueText some xsd:string)

## IntellectualProperty
A work, invention or concept, independent of its being expressed in text, audio, video, image, or live performance.  IP can also be tacit knowledge, know-how, or skill. Also includes Brands.

**subClassOf:**  Artifact	

**disjointWith** gist:UnitOfMeasure; gist:PhysicalSubstance; gist:Magnitude; gist:TimeInstant; gist:Intention; gist:Organization; gist:PhysicalIdentifiableItem
                   

## Intention

Goal, desire, aspiration. This is the teleologic aspect of the system that indicates things are done with a purpose.	

**disjointWith** gist:UnitOfMeasure; gist:TimeInstant; gist:PhysicalSubstance; gist:PhysicalIdentifiableItem; gist:Organization; gist:Magnitude


## Language
A recognized, organized set of symbols and grammar.	

**disjointWith** gist:Magnitude; gist:UnitOfMeasure; gist:PhysicalSubstance; gist:PhysicalIdentifiableItem; gist:Organization; gist:TimeInstant
	               

## LivingThing
Something that is now, or at some point in time was, alive and growing.	

**EquivalentClass** gist:PhysicalIdentifiableItem  and (gist:hasBirthDate some gist:TimeInstant)  and (gist:offspringOf some gist:LivingThing)


## Magnitude
Base class for units which can be converted.  The primitive units can be converted from one measurement system to another; the complex units (ratio or product) have to decompose to their primitives.

**EquivalentClass** (gist:hasPrecision some gist:Magnitude)  and (gist:hasUoM some gist:UnitOfMeasure)  and (gist:decimalValue some xsd:double)


**disjointWith** gist:PhysicalIdentifiableItem; gist:PhysicalSubstance
      

## MassUnit
A unit representing the amount of matter in a particle or object.  The SI unit of mass is the kilogram.	

**EquivalentClass** gist:SimpleUnitOfMeasure  and (gist:hasBaseUnit value gist:_kilogram)

**disjointWith** gist:TemperatureUnit; gist:MoleUnit


## Organization
A generic organization that can be formal or informal, legal or non-legal. It can have members, or not.	

**disjointWith** gist:TimeInstant; gist:PhysicalSubstance; gist:UnitOfMeasure; gist:SchemaMetaData; gist:PhysicalIdentifiableItem


## Person
A human being that may or may not still be alive.	

**EquivalentClass** gist:LivingThing  and (gist:offspringOf some gist:Person)  and (gist:name some xsd:string)


## PhysicalIdentifiableItem
You could, at least in principle, put an RFID tag on members of this class. Physical things are made of something.  E.g., statues are made of bronze.	

**subClassOf**  gist:hasMagnitude some gist:Volume

**subClassOf**  gist:hasMagnitude some gist:Mass	

**subClassOf**  gist:madeUpOf some gist:PhysicalSubstance	

**subClassOf**  gist:identifiedBy some gist:ID	

**disjointWith** gist:TimeInstant; gist:SchemaMetaData; gist:UnitOfMeasure
 

## PhysicalSubstance
Non corporeal material, i.e. 'stuff' which can be divided into parts where each part retains its essence.	

**subClassOf**  owl:intersectionOf[gist:hasMagnitude some gist:Mass,  gist:hasMagnitude some gist:Volume]	

**disjointWith** gist:UnitOfMeasure; gist:TimeInstant


## ProductUnit
A unit of measure that is the product of two simpler ones.	

**EquivalentClass** gist:UnitOfMeasure  and (gist:multiplicand some gist:UnitOfMeasure)  and (gist:multiplier some gist:UnitOfMeasure)  and (gist:convertToBase min 0 xsd:double)


## SchemaMetaData
Superclass for all types of metadata, including owl concepts (such as class) and relational (tables, elements) and tool related (queries, R2RML maps etc etc)	

**disjointWith** gist:UnitOfMeasure


## SimpleUnitOfMeasure
Each simple unit has a base unit and a conversion factor to the base. The bases are from the System International (SI). The conversion factor is the number which one multiplies a Unit by to get to base, or divides by to get from base.  E.g., the convertToBase for inch is 0.0254 to get to the base unit (meter).	

**EquivalentClass** gist:UnitOfMeasure  and (gist:hasBaseUnit exactly 1 gist:BaseUnit)  and (gist:convertToBase some xsd:double)


## Template
Something used to make instances in its own image.  In manufacturing this would be specialized as a die to make stamped parts, cookie cutters are templates for cookies, and forms are templates for data.	

**disjointWith** gist:UnitOfMeasure; gist:TimeInstant
    

## TimeInstant
All time instants are Greenwich and the local equal universal.

**disjointWith** gist:UnitOfMeasure

**subClassOf**  gist:localTime some xsd:string	

**subClassOf**  gist:universalTime some xsd:string

**subClassOf**  gist:localDate some xsd:string

**subClassOf**  gist:localDateTime some xsd:dateTime	

**subClassOf**  gist:universalDate some xsd:string

**subClassOf**  gist:universalDateTime some xsd:dateTime	

**subClassOf**  gist:epoch some xsd:double	

**subClassOf**  gist:hasPrecision some gist:Duration		

## UnitOfMeasure
Standard unit by which we measure things


## Volume
Three-dimensional space, or equivalent fluid measurement.	

**EquivalentClass** gist:Magnitude  and (gist:hasUoM some gist:VolumeUnit)

## VolumeUnit
Units of three-dimensional space, expressed here as an area times a distance.	

gist:ProductUnit  and (gist:multiplicand exactly 1 gist:AreaUnit)  and (gist:multiplier exactly 1 gist:DistanceUnit)

#### _USDollar

#### _ampere

#### _bit
A bit (short for binary digit) is the smallest unit of data in a computer. A bit has a single binary value, either 0 or 1.	

#### _candela

#### _each

#### _kelvin

#### _kilogram

#### _meter

#### _mole

#### _second

| Property          | Label             | Type               | Definition                                                   | subPropertyOf           | Domain                                                       | Range                                                        | Inverse      |
| ----------------- | ----------------- | ------------------ | ------------------------------------------------------------ | ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------ |
| actual            | actual            | ObjectProperty     | When something did occur, therefore noting an historical event. |                         |                                                              | gist:TimeInstant                                             |              |
| actualStart       | actual start      | ObjectProperty     | When something did start, therefore noting an historical event. | gist:actual, gist:start |                                                              |                                                              |              |
| actualEnd         | actual end        | ObjectProperty     | When something did end, therefore noting an historical event. | gist:actual, gist:end   |                                                              |                                                              |              |
| allocatedBy       | allocated by      | ObjectProperty     | Connection between an ID and the thing that minted the ID. It may be a person or organization, or  could be an algorithm (next available or random number generator) |                         |                                                              | gist:IntellectualProperty or  gist:Organization or gist:Person |              |
| basedOn           | based on          | ObjectProperty     | The Object is a foundation for, a starting point for, gave rise to or  justifies the Subject |                         |                                                              |                                                              |              |
| categorizedBy     | categorized by    | ObjectProperty     | Points to a taxonomy item or other less formally defined class. |                         |                                                              |                                                              |              |
| characterizedAs   | characterized as  | ObjectProperty     | A way to categorize a behavior.                              |                         | gist:Event                                                   | gist:Behavior                                                |              |
| conversionOffset  | conversion offset | DatatypeProperty   | Add this number to get to the zero point.   On the Celsius scale, the conversionOffset is -273.15 degrees C. On  the Fahrenheit scale it is -459.67 degrees.   Is equal to 0 when the unit has the same zero point as the base unit.  e.g. inch, meter. |                         | gist:UnitOfMeasure                                           | xsd:double                                                   |              |
| convertToBase     | convert to base   | DatatypeProperty   | The conversion factor used to get to the base unit. E.g., multiplying by 0.0254 gets you from  inches to meters. Divide by this number to go the other way. Used in  conjunction with conversionOffset to convert from one unit to another.  Degrees K = (Degrees F -  conversionOffset) * convertToBase. Or K = (F-(-469.67)) * (5/9. To go the other way: F = (K * 9/5) -469.67. Try it on Google. |                         | gist:UnitOfMeasure                                           | xsd:double                                                   |              |
| decimalValue      | decimal value     | DatatypeProperty   | The actual value of a magnitude.                             |                         | gist:Magnitude                                               | xsd:double                                                   |              |
| description       | description       | DatatypeProperty   | A statement about someone or something's attributes or characteristics. |                         |                                                              |                                                              |              |
| directPartOf      | direct part of    | ObjectProperty     | The relationship between a part and a whole where the part has  independent existence. |                         |                                                              |                                                              |              |
| end               | end               | ObjectProperty     | Connects the subject to its end time.                        |                         |                                                              | gist:TimeInstant                                             |              |
| epoch             | epoch             | DatatypeProperty   | Seconds since 1/1/1970 UTC (unix time )                      |                         | gist:TimeInstant                                             | xsd:double                                                   |              |
| governs           | governs           | ObjectProperty     | The subject controls or inhibits the object in some way      |                         | gist:Intention or  gist:Organization or gist:Person or gist:Template | gist:Category or gist:Content or gist:GeoRegion or gist:IntellectualProperty or gist:Intention or gist:Organization or gist:Person or gist:PhysicalIdentifiableItem or gist:PhysicalSubstance | governedBy   |
| governedBy        | governed by       | ObjectProperty     | A reference from the thing being governed to the governor    |                         |                                                              |                                                              |              |
| hasAltitude       | has altitude      | ObjectProperty     | Distance above sea level                                     |                         | gist:GeoPoint                                                | gist:Extent                                                  |              |
| hasBirthDate      | has birthdate     | ObjectProperty     | Date a living thing is or will be born.                      | gist:actualStart        | gist:LivingThing                                             | gist:TimeInstant                                             |              |
| hasDeathDate      | has death date    | ObjectProperty     | Date a living thing died                                     | gist:actualEnd          | gist:LivingThing                                             | gist:TimeInstant                                             |              |
| hasDirectPart     | has direct part   | ObjectProperty     | The relationship between a whole and a part where the part has  independent existence. | gist:hasPart            |                                                              |                                                              | directPartOf |
| hasMagnitude      | has magnitude     | ObjectProperty     | To have a comparable numerical value. Each magnitude has a unit. |                         |                                                              | gist:Magnitude                                               |              |
| hasMember         | has member        | ObjectProperty     | Relates a Collection to its member individuals.              |                         |                                                              |                                                              |              |
| hasPart           | has part          | ObjectProperty     | The transitive version of hasDirectPart                      |                         |                                                              |                                                              |              |
| hasPrecision      | has precision     | ObjectProperty     | Links a Magnitude to the degree of accuracy of the numeric value.  This allows for fuzzy numbers. All magnitudes have a precision. Usually we don't record them. When we do this, it will be a value whose  extent covers 2 standard deviations around the stated magnitude |                         |                                                              | gist:Magnitude                                               |              |
| identifies        | identifies        | ObjectProperty     | The thing the identifier refers to.                          |                         |                                                              |                                                              | identifiedBy |
| identifiedBy      | identified by     | ObjectProperty     | This is like a URI: a thing can have more than one ID, but each of the  IDs must refer to a unique thing. |                         |                                                              | gist:ID                                                      |              |
| latitude          | latitude          | DatatypeProperty   | Degrees above or below equator                               |                         | gist:GeoPoint                                                | xsd:double                                                   |              |
| license           | license           | AnnotationProperty | An annotation for providing the licensing on this or derivative  ontologies |                         |                                                              |                                                              |              |
| localDate         | local date        | DatatypeProperty   | Relates a TimeInstant to a string indicating what the local date is. |                         | gist:TimeInstant                                             |                                                              |              |
| localDateTime     | local date time   | DatatypeProperty   | Relates a TimeInstant to an xsd:dateTime literal representing the local  date and time. |                         | gist:TimeInstant                                             | xsd:dateTime                                                 |              |
| localTime         | local time        | DatatypeProperty   | Relates a TimeInstant to a string indicating what the local time is. |                         |                                                              |                                                              |              |
| longitude         | longitude         | DatatypeProperty   | Degrees from GM                                              |                         | gist:GeoPoint                                                | xsd:double                                                   |              |
| madeUpOf          | made up of        | ObjectProperty     | Relates something to the the substance that it is made up of. |                         |                                                              | gist:PhysicalSubstance                                       |              |
| memberOf          | member of         | ObjectProperty     | What group the member is in                                  |                         |                                                              |                                                              | hasMember    |
| multiplicand      | multiplicand      | ObjectProperty     | Relates a ProductUnit such as square mile to the second of two units  multiplied together (e.g. mile). |                         | gist:ProductUnit                                             | gist:UnitOfMeasure                                           |              |
| multiplier        | multiplier        | ObjectProperty     | Relates a ProductUnit such as square mile to the first of two units  multiplied together (e.g. mile) |                         | gist:ProductUnit                                             | gist:UnitOfMeasure                                           |              |
| name              | name              | DatatypeProperty   | Relates an individual to a casual name.                      |                         |                                                              | xsd:string                                                   |              |
| offspringOf       | offspring of      | ObjectProperty     | Biological offspring                                         |                         | gist:LivingThing                                             | gist:LivingThing                                             |              |
| owns              | owns              | ObjectProperty     | Possessing and controlling.   Ultimate form of ownership is the right to destroy. Long list of potential Range classes |                         | gist:Organization or gist:Person                             |                                                              |              |
| parentOf          | parent of         | ObjectProperty     | Biological Parent                                            |                         |                                                              |                                                              |              |
| partOf            | part of           | ObjectProperty     | The transitive version of directPartOf                       |                         |                                                              |                                                              | hasPart      |
| produces          | produces          | ObjectProperty     | The subject creates the object.                              |                         |                                                              |                                                              |              |
| sequence          | sequence          | DatatypeProperty   | For ordering ordered lists.                                  |                         |                                                              | xsd:integer                                                  |              |
| start             | start             | ObjectProperty     | Connects the subject to its start time.                      |                         |                                                              | gist:TimeInstant                                             |              |
| triggeredBy       | triggered by      | ObjectProperty     | General causal relation. For  obligations a property that describes what would happen to trigger the  contingent obligation. In most cases,  before the Contingent becomes an Obligation, the triggered by event is a  planned event (that is it hasn't happened yet -- if it had happened the  contingency would no longer be contingent.   In most cases it will be a  ContingentEvent . Other uses include  controls, processes etc |                         |                                                              |                                                              |              |
| uniqueText        | unique text       | DatatypeProperty   | This is used for the actual value of a key or ID where you don't want the  possibility of having more than one. |                         |                                                              | xsd:string                                                   |              |
| universalDate     | UTC date          | DatatypeProperty   | Relates a TimeInstant to a string indicating what the universal date is. |                         | gist:TimeInstant                                             |                                                              |              |
| universalDateTime | UTC date time     | DatatypeProperty   | Relates a TimeInstant to an xsd:dateTime literal representing the  universal time. |                         | gist:TimeInstant                                             | xsd:dateTime                                                 |              |
| universalTime     | UTC time          | DatatypeProperty   | Relates a TimeInstant to a string indicating what the universal time is. |                         | gist:TimeInstant                                             |                                                              |              |


# Unit

## CountingUnit
A unit of counting, especially ?each?, but also units such as dozens.	

**EquivalentClass** gist:SimpleUnitOfMeasure  and (gist:hasBaseUnit value gist:_each)


## CurrencyUnit
A unit of money. Note: this is the only unit whose conversion factors include time (i.e., the conversion rates change on a daily basis).	

**EquivalentClass** gist:SimpleUnitOfMeasure  and (gist:hasBaseUnit value gist:_USDollar)

**disjointWith** gist:DataSizeUnit; gist:MassUnit; gist:TemperatureUnit; gist:ElectricalCurrentUnit; gist:DistanceUnit; gist:LuminousIntensityUnit; gist:DurationUnit; gist:MoleUnit



## DataSizeUnit
A unit to measure amounts of digital information.	

**EquivalentClass** gist:SimpleUnitOfMeasure  and (gist:hasBaseUnit value gist:_bit)

**disjointWith** gist:DurationUnit; gist:MoleUnit; gist:LuminousIntensityUnit; gist:MassUnit; gist:TemperatureUnit; gist:DistanceUnit; gist:ElectricalCurrentUnit


## ElectricalCurrentUnit
Unit of electrical current, which is charge per unit time.  The SI unit is the ampere.  (Note that electrical current is a composed unit.)	

**EquivalentClass** gist:SimpleUnitOfMeasure  and (gist:hasBaseUnit value gist:_ampere)

**disjointWith** gist:TemperatureUnit; gist:MoleUnit; gist:MassUnit; gist:LuminousIntensityUnit

## LuminousIntensityUnit
The measure of brightness. The SI unit is the candela.	

**EquivalentClass** gist:SimpleUnitOfMeasure  and (gist:hasBaseUnit value gist:_candela)

**disjointWith** gist:TemperatureUnit; gist:MoleUnit; gist:MassUnit
	  

## MoleUnit
Amount of chemical material.  Measured in Avogadro units (moles) of 6.02 x 10^23 molecules.	

**EquivalentClass** gist:SimpleUnitOfMeasure  and (gist:hasBaseUnit value gist:_mole)    

**disjointWith** gist:TemperatureUnit


## RatioUnit
A UnitOfMeasure composed of a numerator unit and a denominator unit.	

**EquivalentClass** gist:UnitOfMeasure  and (gist:denominator some gist:UnitOfMeasure)  and (gist:numerator some gist:UnitOfMeasure)


## TemperatureUnit
Unit of measurement for expressing temperature.  Per SI, the base of temperature is in Kelvin, to allow for all units to be expressed relative to a real (in this case absolute) zero.	

**EquivalentClass** gist:SimpleUnitOfMeasure  and (gist:hasBaseUnit value gist:_kelvin)  and (gist:conversionOffset some xsd:double)



| Property          | Label               | Type             | Definition                                                   | subPropertyOf | Domain             | Range              | Inverse |
| ----------------- | ------------------- | ---------------- | ------------------------------------------------------------ | ------------- | ------------------ | ------------------ | ------- |
| denominator       | denominator         | ObjectProperty   | Relates a RatioUnit such as meters/second to the denominator Unit (e.g.  second). |               | gist:RatioUnit     | gist:UnitOfMeasure |         |
| numerator         | numerator           | ObjectProperty   | Relates a RatioUnit such as meter(s)/second to the numerator Unit (e.g.  meter). |               | gist:RatioUnit     | gist:UnitOfMeasure |         |
| unitSymbol        | unit symbol         | DatatypeProperty | The standard symbol for the unit NOT using any special characters. E.g. square meter would be m^2 rather than  m?. |               | gist:UnitOfMeasure | xsd:string         |         |
| unitSymbolHTML    | unit symbol HTML    | DatatypeProperty | The standard symbol for the unit in HTML format for pretty printing, may use special  characters. E.g. to show square meter  as m? rather than m^2, the value of  this property would be "m&sup2;" This is for when Unicode not  supported and the display will be HTML format. |               | gist:UnitOfMeasure | xsd:string         |         |
| unitSymbolUnicode | unit symbol Unicode | DatatypeProperty | The standard symbol for the unit preferred for pretty printing, may use  special characters. E.g. square meter  would be m? rather than m^2. |               | gist:UnitOfMeasure | xsd:string         |         |


# UnitDim

## CoherentProductUnit
A ratio unit whose numerator and denominator reduce to 1	

**EquivalentClass** gist:ProductUnit  and (gist:multiplicand only (gist:BaseUnit  or gist:CoherentProductUnit  or gist:CoherentRatioUnit))  and (gist:multiplier only (gist:BaseUnit  or gist:CoherentProductUnit  or gist:CoherentRatioUnit))


## CoherentRatioUnit
A ratio unit whose numerator and denominator reduce to 1	

**EquivalentClass** gist:RatioUnit  and (gist:denominator only (gist:BaseUnit  or gist:CoherentProductUnit  or gist:CoherentRatioUnit))  and (gist:numerator only (gist:BaseUnit  or gist:CoherentProductUnit  or gist:CoherentRatioUnit))


## CoherentUnit
A unit that is expressed in units that have no conversions.  It may be a simple unit.  It may also be a product or ratio unit that bottoms out in simple units.	

**EquivalentClass** gist:BaseUnit  or gist:CoherentProductUnit  or gist:CoherentRatioUnit


| Property          | Label               | Type             | Definition                                                   | subPropertyOf        | Domain             | Range             | Inverse |
| ----------------- | ------------------- | ---------------- | ------------------------------------------------------------ | -------------------- | ------------------ | ----------------- | ------- |
| convertToStandard | convert to standard | DatatypeProperty | Note this kind of conversion will only work with temperatures if they are  in Kelvin or Rankine (with a true 0).   You multiply to get to the base, divide to go from the base. mph to  mps is .44704. The multiple from kph  to mps is .277778 . To convert 60 mph  to kph is (60 * .44704 / .277778 or 96.56056 kph | gist:convertToBase   | gist:UnitOfMeasure | xsd:double        |         |
| hasBaseUnit       | has base unit       | ObjectProperty   | Relates a UnitOfMeasure to its BaseUnit.   This indicates what kind of Unit something is. | gist:hasStandardUnit | gist:UnitOfMeasure | gist:BaseUnit     |         |
| hasStandardUnit   | has standard unit   | ObjectProperty   | For a complex unit refers to a unit that has all the component parts in  SI |                      | gist:UnitOfMeasure | gist:CoherentUnit |         |