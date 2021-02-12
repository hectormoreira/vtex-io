# Forms

Add store-form app to your theme's dependencies in the `manifest.json`, for example:

```sh
vtex install vtex.store-form
```

```json
dependencies: {
  "vtex.store-form": "0.x"
}
```

Then, declare the `form` block. Bear in mind to specify which `entity` and `schema` from Master Data should be fetched to build the block.

```json
{
  "flex-layout.row#form": {
    "children": ["flex-layout.col#form"]
  },
  "flex-layout.col#form": {
    "children": ["form"]
  },
  "form": {
    "props": {
      "entity": "clients",
      "schema": "person"
    }
  }
}
```

If desired, complete the `form` block by adding and configuring an array of children blocks. You can use the blocks listed in the first table stated above. For example:

```json
"form": {
  "props": {
    "entity": "clients",
    "schema": "person"
  },
  "children": [
    "rich-text#formTitle",
    "form-input.text#firstName",
    "form-input.text#lastName",
    "form-field-group#address",
    "form-input.checkbox#agreement",
    "form-submit"
  ],
  "blocks": ["form-success"]
},
"form-success": {
  "children": [
    "rich-text#successSubmit"
  ]
},
"rich-text#successSubmit": {
  "props": {
    "text": "Succesfully submitted the data!",
    "textAlignment": "CENTER",
    "textPosition": "CENTER"
  }
},
"form-input.text#firstName": {
  "props": {
    "pointer": "#/properties/firstName"
  }
},
"form-input.text#lastName": {
  "props": {
    "pointer": "#/properties/lastName"
  }
},
"form-input.checkbox#agreement": {
  "props": {
    "pointer": "#/properties/agreement",
    "label": "Do you agree that this is the best form component in the whole wide world?"
  }
},
"form-field-group#address": {
  "props": {
    "pointer": "#/properties/address"
  }
},
"form-submit": {
  "props": {
    "label": "Submit"
  }
}
```
