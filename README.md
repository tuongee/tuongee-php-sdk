# tuongee-php-sdk
Tuongee PHP sdk

### An example script 

``` php
<?php 

require './sdk/tuongee.class.php';

// Set the application credentials. Grab from your application dashboard 
$api_key = "API_KEY";
$api_secret = "API SECRET";

// Initialize my application 
$tuongee = new Tuongee( $api_key, $api_secret );

// To get payload details for the customer request,
$phone_no = @$_POST["phone"]; 	// the customer phone number 
$message = @$_POST["message"]; 	// the message send by the customer 
$name = @$_POST["name"];		// the customer name

// 
// Process the request according to your needs
// 

// Set response header message 
$tuongee->setHeaderMessage( "Welcome customer to our service. Choose from the menus below");

// Provide a nice menu back to the customer - optional
$menu = array(
	array( "code"=> 1, "message"=> "My account history"),
	array( "code"=> 2, "message"=> "Check order status")
);
$tuongee->setMenu( $menu );

// Send the reply back to the customer 
$tuongee->display();

// Prevent any further processing otherwise the content type might be different 
// from the required application/xml
// NB: Always make sure the response content-type is application/xml 
// otherwise your customer won't receive the response
exit();
?>
```

When you run this code, the following is the response which is forwarded back to your customer via whatsapp 
``` json 
Welcome customer to our service. Choose from the menus below
1: My account history
2: Check order status
```
