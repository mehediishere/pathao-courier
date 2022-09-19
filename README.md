<p align="center">
  <img src="https://pathao.com/wp-content/uploads/2019/02/Pathao-logo.svg">
</p>

<h1 align="center">Pathao Courier Banagladesh</h1>
<p align="center" >
<img src="https://img.shields.io/packagist/dt/codeboxr/pathao-courier">
<img src="https://img.shields.io/packagist/stars/codeboxr/pathao-courier">
</p>


## Requirements

- PHP >=7.4
- Laravel >= 6

## Installation

```bash
composer require codeboxr/pathao-courier
```

### vendor publish (config)
```bash
php artisan vendor:publish --provider="Codeboxr\PathaoCourier\PathaoCourierServiceProvider"
```

After publish config file setup your credential. you can see this in your config directory pathao.php file
```
"sandbox"       => env("PATHAO_SANDBOX", false), // for sandbox mode use true
"client_id"     => env("PATHAO_CLIENT_ID", ""),
"client_secret" => env("PATHAO_CLIENT_SECRET", ""),
"username"      => env("PATHAO_USERNAME", ""),
"password"      => env("PATHAO_PASSWORD", "")
```

### Set .env configuration
```
PATHAO_SANDBOX=true // for production mode use false
PATHAO_CLIENT_ID=""
PATHAO_CLIENT_SECRET=""
PATHAO_USERNAME=""
PATHAO_PASSWORD=""
```


## Usage

### 1. Get pathao delivery city list

```
use Codeboxr\PathaoCourier\Facade\PathaoCourier

return PathaoCourier::area()->city();

```

### 2. To get pathao zone list

```
use Codeboxr\PathaoCourier\Facade\PathaoCourier

return PathaoCourier::area()->zone($cityId); // City ID
```

### 3. To get pathao delivery area list

```
use Codeboxr\PathaoCourier\Facade\PathaoCourier

return PathaoCourier::area()->area($zoneId); // Zone ID
```


### 4. Create new store

```
use Codeboxr\PathaoCourier\Facade\PathaoCourier

return PathaoCourier::store()
                        ->create([
                            "name"              => "", // Store Name
                            "contact_name"      => "", // Store contact person name
                            "contact_number"    => "", // Contact person number
                            "address"           => "", // Store address
                            "secondary_contact" => "", // Contact person secondary number not mandatory
                            "city_id"           => "", // Find in city method
                            "zone_id"           => "", // Find in zone method
                            "area_id"           => "", // Find in Area method
                        ]);
```

### 5. Get Store List

```
use Codeboxr\PathaoCourier\Facade\PathaoCourier

return PathaoCourier::store()->list();
```

### 6. Create new parcel

```
use Codeboxr\PathaoCourier\Facade\PathaoCourier

return PathaoCourier::order()
                        ->create([
                            "store_id"            => "", // Find in store list,
                            "merchant_order_id"   => "", // Unique order id
                            "recipient_name"      => "", // Customer name
                            "recipient_phone"     => "", // Customer phone
                            "recipient_address"   => "", // Customer address
                            "recipient_city"      => "", // Find in city method
                            "recipient_zone"      => "", // Find in zone method
                            "recipient_area"      => "", // Find in Area method
                            "delivery_type"       => "", // 48 for normal delivery or 12 for on demand delivery
                            "item_type"           => "", // 1 for document,
2 for parcel
                            "special_instruction" => "",
                            "item_quantity"       => "", // item quantity
                            "item_weight"         => "", // parcel weight
                            "amount_to_collect"   => "", // amount to collect
                            "item_description"    => "" // product details
                        ]);
```

### 7. Get Order Details

```
use Codeboxr\PathaoCourier\Facade\PathaoCourier

return PathaoCourier::order()->orderDetails($consignmentId); // After successfully create order they given a consignment_id
```




## Contributing

Contributions to the Pathao package are welcome. Please note the following guidelines before submitting your pull request.

- Follow [PSR-4](http://www.php-fig.org/psr/psr-4/) coding standards.
- Read Pathao API documentations first

## License

Pathao package is licensed under the [MIT License](http://opensource.org/licenses/MIT).

Copyright 2022 [Codeboxr](https://codeboxr.com)
