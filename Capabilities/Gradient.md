# Gradient property
The gradient property is special property that cannot be set as usual property. Instead, you need to set special rule for substitution of color picker property (fill type). See the example below.

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```
Please, pay attention to `"fill"` and `"fillRule"` properties. The first is color picker, the second is substitution rule for gradient that will substitute "fill" property `visually` when the rule conditions will be reached.

This link between fill property and substitution rule is set in `"rule"`->`"output"` section of `"fillRule"` property.

`"Rule"`->`"InputRole"` sets which data role triggers the rule (condition). In tis example, if data role `"Gradient"` contains data then the rule will be applied for `"fill"` property.

The example of data role that triggers the fill rule you can see below (`the last item`).

```json
"dataRoles": [
        {
            "name": "Category",
            "kind": "Grouping",
            "displayName": "Details",
            "displayNameKey": "Role_DisplayName_Details"
        },
        {
            "name": "Series",
            "kind": "Grouping",
            "displayName": "Legend",
            "displayNameKey": "Role_DisplayName_Legend"
        },
        {
            "name": "Gradient",
            "kind": "Measure",
            "displayName": "Color saturation",
            "displayNameKey": "Role_DisplayName_Gradient"
        }
]
```