# Listing management

**API endpoint**: `/listings`

## Get listing list

`GET /listings.json`

Return the list of all listings.

## Get specific listing details

`GET /listings/{url_key}.json`

Return the details for a specific listing.

Example response:

```json
{
    "listing": {
        "url_key": "kgdt7r",
        "sku": "",
        "order_type_id": 23,
        "user_id": 1,
        "status_id": 1,
        "title": "Paquet de Pringles vide",
        "slug": "paquet-de-pringles-vide",
        "description": "C'est un paquet de pringles  que j'ai mangé.\r\nIls étaient très bon, au paprika au passage.",
        "price": 100,
        "original_price": 0,
        "is_online": true,
        "on_homepage": true,
        "category_id": 32,
        "location": "Paname",
        "date_online": "2019-03-12T16:02:48+00:00",
        "currency": "EUR"
    }
}
```

## Create listing

`POST /listings.json`

Create a new listing. 
Data must be passed as raw JSON body content.

Required fields are : 

- `order_type_url_token` (string), obtained by calling `/listings/order_types.json`
- `category_id` (integer), obtained by calling `/listings/categories.json`
- `user_id` (integer). The user id the listing will be attributed to. Obtained by calling `/users.json`
- `title` (string). The listing title.
- `description` (string). The listing description.
- `price` (float). The listing price.
- `is_online` (boolean). Whether the listing should be online or not.
- `on_homepage` (boolean). Whether the listing should be displayed on homepage or not.
- `location` (string). Location field.

Optional fields :

- `images` (JSON array). An array of up to 3 image URLs for the listing pictures. 
- `attributes` (JSON object), to pass an array of attributes to the listing. Available attribute list showed when calling `/listings/attributes.json`.

E.g:

```json
{
    "order_type_url_token": "tcu3yxwbyb", 
    "category_id": 33,
    "user_id": 1,
    "title": "Yamaha YZF M1", 
    "description": "Elite motorcycle used in MotoGP.",
    "price": 1500,
    "is_online": true,
    "on_homepage": true, 
    "location": "France",
    "attributes": {
      "couleur": [638,639]
    }
}
```

## Update listing data

`POST|PUT|PATCH /listings/{url_key}.json`

Update the listing with given `url_key`. 

New data passed as raw JSON body content. E.g:

```json
{
    "listing": {
        "title": "MacBook Pro - New !",
        "description": "This is the latest updated version.",
        "price": 3500,
        "is_online": true,
        "on_homepage": true,
        "category_id": 33,
        "location": "France",
        "images": [
            "https://assets.pcmag.com/media/images/419372-apple-macbook-2016.jpg'"
            "https://cnet2.cbsistatic.com/img/r55D9EFCaaNpPVUay88jTv5-gZ4=/830x467/2017/06/27/13484418-bfd9-41e2-8f2d-9b4afb072da8/apple-macbook-pro-15-inch-2017-14.jpg"
        ]
    }
}
```

Note that if the key `images` is present, all the listing images will be replaced by the new values.


Example response:

```json
{
    "success": true,
    "message": "Listing updated"
}
```

## Delete listing

`DELETE /listings/{url_key}.json`

Delete the listing with given `url_key`. 


Example response:

```json
{
   "success": true,
   "message": "Listing deleted"
}
```
