# ![LOGO](logo.png) Voodoo Manufacturing 3D Print **flow**ground Connector

## Description

A generated **flow**ground connector for the Voodoo Manufacturing 3D Print API (version 2.0.0).

Generated from: https://api.apis.guru/v2/specs/voodoomfg.com/2.0.0/swagger.json<br/>
Generated at: 2019-05-07T17:44:46+03:00

## API Description

Welcome to the Voodoo Manufacturing API docs!

Your Voodoo Manufacturing API key must be included with each request to the API. The API will look for the key in the "api_key" header of the request. <a href="https://voodoomfg.com/3d-print-api#get-access" target="_blank">You can request a key here.</a>

This API provides a programmatic interface for submitting printing orders to Voodoo Manufacturing. The general process for creating an order is as follows:
  - Get a list of the available materials with the /materials endpoint
  - Upload models to the API with the /models endpoint
  - Get quotes for shipping methods with the /order/shipping endpoint
  - Get a quote for an order with the /order/create endpoint
  - Confirm the order with the /order/confirm endpoint

Uploaded models and orders can be retrieved either in bulk or by id at the /model and /order endpoints, respectively.

In some cases, you may wish to get a quote for a specific model without the context of an order. In this case, you may use the /model/quote (if you've already uploaded the model to the API) or the /model/quote_attrs (lets you quote based on calculated model attributes) endpoints.


## Authorization

Supported authorization schemes:
- API Key
## Actions

### Voodoo Manufacturing offers printing in a number of different materials, with different color options for each. Your organization can expose as many or as few material options as you want to your end-customer.

> The Materials endpoint returns a list of materials that are currently available for production for your account.<br/>
> The responses include display details about each material, along with the unique id required to request a print in a specific material.

*Tags:* `materials`

### Retrieve the models you've created.

> Lists all of the models you've created.

*Tags:* `model`

### Models represent 3D design files that you'd like to produce. Creating models is generally the first step in creating an order.

> Downloads the model data from the URL specified by file_url and saves it as a model. As a part of the model upload process, the file is run through a program that repairs the mesh (closing holes, flipping inverted normals, etc). In some cases, this may alter the geometry of your model. If you're noticing bad results for your created models, you might consider repairing your files before submitting them.

*Tags:* `model`

### Get a quote a given model id.

> Calculates a quote for the given model in the given material and quantity. This endpoint required that you've already uploaded the model to our servers -- to get a quote for a model you haven't yet uploaded, you can try /model/quote_attrs.

*Tags:* `model`

#### Input Parameters
* `model_id` - _required_ - The unique id of the model you'd like to quote.
* `material_id` - _required_ - The unique id of the desired material.
* `quantity` - _required_ - The number of units in this quote.
* `units` - _required_ - The units of the model file. Either "mm", "cm", or "in". The correct value to pass here depends on which design program you're using. Defaults to "mm".
* `options[orientation]` - _optional_ - Indicates whether or not this model needs to be oriented prior to printing. If your model is already oriented for 3D printing, you can omit this flag (or set it to false) and it will not be re-oriented prior to printing. If true, it will be re-oriented prior to printing. If you're not sure if your model is oriented, you should set this flag to true. There is an additional charge for orientation.

### Get a quote for a model with the given attributes.

> This endpoint will provide a quote for a model matching the submitted parameters. Note that this quote may be different than the quote provided by /model/quote in the case that your attribute calculations differ from the ones used by Voodoo Manufacturing.

*Tags:* `model`

#### Input Parameters
* `x` - _required_ - The calculated unitless x dimension of this model's bounding box.
* `y` - _required_ - The calculated unitless y dimension of this model's bounding box.
* `z` - _required_ - The calculated unitless z dimension of this model's bounding box.
* `volume` - _required_ - The calculated unitless volume of the model.
* `surface_area` - _required_ - The calculated unitless surface area of the model.
* `material_id` - _required_ - The unique id of the desired material.
* `quantity` - _required_ - The number of units in this quote.
* `units` - _required_ - The units of the model file. Either "mm", "cm", or "in". The correct value to pass here depends on which design program you're using. Defaults to "mm".
* `options[orientation]` - _optional_ - Indicates whether or not this model needs to be oriented prior to printing. If your model is already oriented for 3D printing, you can omit this flag (or set it to false) and it will not be re-oriented prior to printing. If true, it will be re-oriented prior to printing. If you're not sure if your model is oriented, you should set this flag to true. There is an additional charge for orientation.

### Retrieve a previously created model by its id.

> In cases where you're ordering models you've created previously, you can fetch a specific model by its id.

*Tags:* `model`

#### Input Parameters
* `model_id` - _required_

### Lists all orders.

> Gets all of orders that you've confirmed.

*Tags:* `order`

### Confirms an order from a quote_id and submits it to the Voodoo factory.

> After generating a quote for an order, you can choose to confirm the order for manufacturing by hitting this endpoint with the quote_id returned by the /order/quote endpoint. Returns the order with a unique order_id in place of the quote_id.

*Tags:* `order`

### Quotes an order and returns a quote_id that is used to confirm the order.

> Creates an order for the requested items, shipping address, and shipping method. This method returns the order along with a quote_id, which needs to be confirmed with /order/confirm prior to the order actually being started. quote_ids are only valid for 15 minutes.

*Tags:* `order`

### List shipping options and prices for a given shipment.

> Get quotes for shipping your order to the given shipping address. Because shipping quotes depend on the items being shipped, you should use the same array of print descriptions here that you do to create the order.<br/>
> <br/>
> This endpoint should allow you to select the appropriate shipping method using the "service" field of the desired shipping method.

*Tags:* `order`

### Retrieve a previously created model by its id.

> In cases where you're ordering models you've created previously, you can fetch a specific model by its id.

*Tags:* `order`

#### Input Parameters
* `order_id` - _required_

## License

**flow**ground :- Telekom iPaaS / voodoomfg-com-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
