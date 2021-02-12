# Product Components

## product-availability

Install `vtex.product-availability`

```sh
vtex install vtex.product-availability
```

To use this app or override the default CSS you need import it in your dependencies on `manifest.json` file.

```json
"dependencies": {
    "vtex.product-availability": "0.x"
  }
```
Then, add product-availability block to your `blocks.json`

Now, you can change the behavior of the product-availability block that is in the minicart. See an example of how to configure:

```json
"product-availability": {
  "props": {
    "threshold": "10",
    "lowStockMessage": "Only {quantity} left!",
    "highStockMessage": "Item in stock!"
  }
}
```

Ref: [Product Availability - VTEX IO](https://developers.vtex.com/vtex-developer-docs/docs/vtex-product-availability)