# aac-objects_folded_cleaned.json

## Add Column

## Add Node/Literal
#### Literal Node: `http://vocab.getty.edu/aat/300312355`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300404670`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300080091`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300179869`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300026687`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300263534`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300266036`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`


## PyTransforms
#### _ObjectID_
From column: _data / id_
``` python
return "object/id/"+getValue("id")
```

#### _objectURL_
From column: _data / link_
``` python
return getValue("link")
```

#### _titleLabel_
From column: _data / title_
``` python
return getValue("title")
```

#### _TitleURI_
From column: _data / ObjectID_
``` python
return getValue("ObjectID")+"/title"
```

#### _accessionLabel_
From column: _data / accession_number_
``` python
return getValue("accession_number")
```

#### _AccessionNumberURI_
From column: _data / TitleURI_
``` python
return getValue("ObjectID")+"/accessionnumber"
```

#### _creation_place_
From column: _data / Glue_1 / data_creation_city_values_
``` python
c = str(getValue("data_creation_city_values"))
s = str(getValue("data_creation_state_values"))
if c == "" and s == "":
    return ""
elif c == "":
    return s
elif s == "":
    return c
else:
    return c+', '+s
```

#### _ProductionURI_
From column: _data / TitleURI_
``` python
return getValue("ObjectID")+"/production"
```

#### _CreationLocationClassURI_
From column: _data / ProductionURI_
``` python
return getValue("ObjectID")+"/production/creationlocation"
```

#### _FirstImageURL_
From column: _data / imageconcated_
``` python
url = getValue("imageconcated")
if url == "":
    return url
else:
    return url[:url.index(',')]
```

#### _RightsURI_
From column: _data / AccessionNumberURI_
``` python
return getValue("ObjectID")+"/rights"
```

#### _DescriptionValue_
From column: _data / description_
``` python
return getValue("description")
```

#### _DescriptionURI_
From column: _data / RightsURI_
``` python
return getValue("ObjectID")+"/description"
```

#### _ClassificationURI_
From column: _data / DescriptionURI_
``` python
return getValue("ObjectID")+"/type"
```

#### _ClassificationLabelURI_
From column: _data / object_types / values_
``` python
if getValue('values') != "":
    return getValue('ObjectID')+'/type/'+getValue("values")
else:
    return ""
```

#### _MaterialURI_
From column: _data / ClassificationURI_
``` python
return getValue("ObjectID")+"/material"
```

#### _TechniqueURI_
From column: _data / ClassificationURI_
``` python
return getValue("ObjectID")+"/technique"
```

#### _TechniqueLabelURI_
From column: _data / technique_
``` python
if getValue('technique') != "":
    return getValue('ObjectID')+'/technique/'+getValue("technique")
else:
    return ""
```

#### _CreditLineURI_
From column: _data / TechniqueLabelURI_
``` python
return getValue('ObjectID')+'/creditline'
```

#### _CollectionURI_
From column: _data / CreditLineURI_
``` python
return getValue('ObjectID')+'/collection'
```

#### _DepartmentURI_
From column: _data / CollectionURI_
``` python
return getValue('ObjectID')+'/collection/department'
```

#### _InformationObjectURI_
From column: _data / DepartmentURI_
``` python
return getValue('ObjectID')+'/information'
```

#### _ConceptURI_
From column: _data / InformationObjectURI_
``` python
return getValue('ObjectID')+'/information/concept'
```

#### _CreationDateURI_
From column: _data / ObjectID_
``` python
return getValue("ObjectID")+'/creationdate'
```

#### _CreationDateTimeSpanURI_
From column: _data / CreationDateURI_
``` python
return getValue("ObjectID")+'/creationdate/timespan'
```

#### _CreatorURI_
From column: _data / actors / id_
``` python
return 'actor/id/'+getValue("id")
```

#### _ProductionCreatorURI_
From column: _data / ConceptURI_
``` python
return getValue('ObjectID')+'/productioncreator/'
```

#### _DimensionDepthURI_
From column: _data / dimensions / PhyType_tab_
``` python
return UM.uri_from_fields(getValue("ObjectID")+'/depth/',getValue('PhyType_tab'))
```

#### _DimensionDiameterURI_
From column: _data / dimensions / PhyType_tab_
``` python
return UM.uri_from_fields(getValue("ObjectID")+'/diameter/',getValue('PhyType_tab'))
```

#### _DimensionHeightURI_
From column: _data / dimensions / PhyType_tab_
``` python
return UM.uri_from_fields(getValue("ObjectID")+'/height/',getValue('PhyType_tab'))
```

#### _DimensionWidthURI_
From column: _data / dimensions / PhyType_tab_
``` python
return UM.uri_from_fields(getValue("ObjectID")+'/width/',getValue('PhyType_tab'))
```

#### _DimensionDepthUnit_
From column: _data / dimensions / PhyUnitLength_tab_
``` python
v = getValue("PhyUnitLength_tab").replace('.','')
if "." in v:
    v = v.replace('.','')
return v
```

#### _DimensionWidthUnit_
From column: _data / dimensions / DimensionDepthUnit_
``` python
v = getValue("PhyUnitLength_tab").replace('.','')
if "." in v:
    v = v.replace('.','')
return v
```

#### _DimensionHeightUnit_
From column: _data / dimensions / DimensionWidthUnit_
``` python
v = getValue("PhyUnitLength_tab").replace('.','')
if "." in v:
    v = v.replace('.','')
return v
```

#### _DimensionDiameterUnit_
From column: _data / dimensions / DimensionHeightUnit_
``` python
v = getValue("PhyUnitLength_tab").replace('.','')
if "." in v:
    v = v.replace('.','')
return v
```

#### _DimensionsTextURI_
From column: _data / dimensions / DimensionWidthURI_
``` python
return getValue("ObjectID")+'/dimensiontext'
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _AccessionNumberURI_ | `uri` | `crm:E42_Identifier1`|
| _ClassificationLabelURI_ | `uri` | `crm:E55_Type1`|
| _ClassificationURI_ | `uri` | `crm:E17_Type_Assignment1`|
| _CollectionURI_ | `uri` | `crm:E19_Physical_Object1`|
| _ConceptURI_ | `uri` | `owl:Thing1`|
| _CreationDateTimeSpanURI_ | `uri` | `crm:E52_Time-Span1`|
| _CreationDateURI_ | `uri` | `crm:E12_Production3`|
| _CreationLocationClassURI_ | `uri` | `crm:E53_Place1`|
| _CreatorURI_ | `uri` | `crm:E39_Actor1`|
| _CreditLineURI_ | `uri` | `crm:E33_Linguistic_Object2`|
| _DepartmentURI_ | `uri` | `crm:E74_Group1`|
| _DescriptionURI_ | `uri` | `crm:E33_Linguistic_Object1`|
| _DescriptionValue_ | `rdf:value` | `crm:E33_Linguistic_Object1`|
| _DimensionDepthURI_ | `uri` | `crm:E54_Dimension4`|
| _DimensionDepthUnit_ | `crm:P91_has_unit` | `crm:E54_Dimension4`|
| _DimensionDiameterURI_ | `uri` | `crm:E54_Dimension3`|
| _DimensionDiameterUnit_ | `crm:P91_has_unit` | `crm:E54_Dimension3`|
| _DimensionHeightURI_ | `uri` | `crm:E54_Dimension2`|
| _DimensionHeightUnit_ | `crm:P91_has_unit` | `crm:E54_Dimension2`|
| _DimensionWidthURI_ | `uri` | `crm:E54_Dimension1`|
| _DimensionWidthUnit_ | `crm:P91_has_unit` | `crm:E54_Dimension1`|
| _DimensionsTextURI_ | `uri` | `crm:E33_Linguistic_Object3`|
| _FirstImageURL_ | `uri` | `crm:E38_Image1`|
| _InformationObjectURI_ | `uri` | `crm:E73_Information_Object1`|
| _MaterialURI_ | `uri` | `crm:E57_Material1`|
| _ObjectID_ | `uri` | `crm:E22_Man-Made_Object1`|
| _ProductionCreatorURI_ | `uri` | `crm:E12_Production4`|
| _ProductionURI_ | `uri` | `crm:E12_Production1`|
| _RightsURI_ | `uri` | `crm:E30_Right1`|
| _TechniqueLabelURI_ | `uri` | `crm:E55_Type2`|
| _TechniqueURI_ | `uri` | `crm:E12_Production2`|
| _TitleURI_ | `uri` | `crm:E35_Title1`|
| _accessionLabel_ | `rdfs:label` | `crm:E42_Identifier1`|
| _accession_number_ | `rdf:value` | `crm:E42_Identifier1`|
| _creation_place_ | `rdfs:label` | `crm:E53_Place1`|
| _description_ | `dc:description` | `crm:E22_Man-Made_Object1`|
| _link_ | `uri` | `foaf:Document1`|
| _objectURL_ | `rdfs:label` | `foaf:Document1`|
| _technique_ | `rdfs:label` | `crm:E55_Type2`|
| _title_ | `rdf:value` | `crm:E35_Title1`|
| _titleLabel_ | `rdfs:label` | `crm:E22_Man-Made_Object1`|
| _values_ | `rdfs:label` | `crm:E55_Type1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `crm:E12_Production1` | `crm:P7_took_place_at` | `crm:E53_Place1`|
| `crm:E12_Production2` | `crm:P32_used_general_technique` | `crm:E55_Type2`|
| `crm:E12_Production3` | `crm:P4_has_time-span` | `crm:E52_Time-Span1`|
| `crm:E12_Production4` | `crm:P14_carried_out_by` | `crm:E39_Actor1`|
| `crm:E17_Type_Assignment1` | `crm:P42_assigned` | `crm:E55_Type1`|
| `crm:E19_Physical_Object1` | `crm:P49_has_former_or_current_keeper` | `crm:E74_Group1`|
| `crm:E22_Man-Made_Object1` | `crm:P108i_was_produced_by` | `crm:E12_Production1`|
| `crm:E22_Man-Made_Object1` | `crm:P108i_was_produced_by` | `crm:E12_Production2`|
| `crm:E22_Man-Made_Object1` | `crm:P108i_was_produced_by` | `crm:E12_Production3`|
| `crm:E22_Man-Made_Object1` | `crm:P108i_was_produced_by` | `crm:E12_Production4`|
| `crm:E22_Man-Made_Object1` | `crm:P41i_was_classified_by` | `crm:E17_Type_Assignment1`|
| `crm:E22_Man-Made_Object1` | `crm:P46i_forms_part_of` | `crm:E19_Physical_Object1`|
| `crm:E22_Man-Made_Object1` | `crm:P104_is_subject_to` | `crm:E30_Right1`|
| `crm:E22_Man-Made_Object1` | `crm:P129i_is_subject_of` | `crm:E33_Linguistic_Object1`|
| `crm:E22_Man-Made_Object1` | `crm:P67i_is_referred_to_by` | `crm:E33_Linguistic_Object2`|
| `crm:E22_Man-Made_Object1` | `crm:P67i_is_referred_to_by` | `crm:E33_Linguistic_Object3`|
| `crm:E22_Man-Made_Object1` | `crm:P102_has_title` | `crm:E35_Title1`|
| `crm:E22_Man-Made_Object1` | `crm:P138i_has_representation` | `crm:E38_Image1`|
| `crm:E22_Man-Made_Object1` | `crm:P1_is_identified_by` | `crm:E42_Identifier1`|
| `crm:E22_Man-Made_Object1` | `crm:P43_has_dimension` | `crm:E54_Dimension1`|
| `crm:E22_Man-Made_Object1` | `crm:P43_has_dimension` | `crm:E54_Dimension2`|
| `crm:E22_Man-Made_Object1` | `crm:P43_has_dimension` | `crm:E54_Dimension3`|
| `crm:E22_Man-Made_Object1` | `crm:P43_has_dimension` | `crm:E54_Dimension4`|
| `crm:E22_Man-Made_Object1` | `crm:P45_consists_of` | `crm:E57_Material1`|
| `crm:E22_Man-Made_Object1` | `crm:P128_carries` | `crm:E73_Information_Object1`|
| `crm:E22_Man-Made_Object1` | `foaf:homepage` | `foaf:Document1`|
| `crm:E22_Man-Made_Object1` | `crm:P2_has_type` | `crm:E55_Type1`|
| `crm:E33_Linguistic_Object1` | `crm:P2_has_type` | `xsd:http://vocab.getty.edu/aat/300404670`|
| `crm:E33_Linguistic_Object1` | `crm:P2_has_type` | `xsd:http://vocab.getty.edu/aat/300080091`|
| `crm:E33_Linguistic_Object2` | `crm:P2_has_type` | `xsd:http://vocab.getty.edu/aat/300026687`|
| `crm:E33_Linguistic_Object3` | `crm:P2_has_type` | `xsd:http://vocab.getty.edu/aat/300266036`|
| `crm:E42_Identifier1` | `crm:P2_has_type` | `xsd:http://vocab.getty.edu/aat/300312355`|
| `crm:E55_Type1` | `crm:P21_had_general_purpose` | `xsd:http://vocab.getty.edu/aat/300179869`|
| `crm:E73_Information_Object1` | `crm:P129_is_about` | `owl:Thing1`|
| `crm:E74_Group1` | `crm:P2_has_type` | `xsd:http://vocab.getty.edu/aat/300263534`|