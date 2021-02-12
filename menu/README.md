# Create category menu

For the first time, install dependency `vtex.category-menu`

```sh
vtex install vtex.category-menu
```

Add the app to your theme's dependencies on the manifest.json

```json
dependencies: {
    "vtex.category-menu": "2.x"
  }
```

Add the category-menu block into your theme.

```json
{
  "category-menu": {
    "props": {
      "showAllDepartments": true,
      "showSubcategories": true,
      "menuDisposition": "center",
      "departments": []
    }
  }
}
```

> All dependency installed into folder theme

Ref: [Category menu - VTEX IO](https://developers.vtex.com/vtex-developer-docs/docs/vtex-category-menu)
