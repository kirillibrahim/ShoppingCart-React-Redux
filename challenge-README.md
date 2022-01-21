Geektastic Javascript / React / Redux Code Challenge
This challenge involves creating a simple shopping basket interface that interacts with a JSON API endpoint running on your local machine. The endpoints are provided as a Node.js based HTTP server and a JS/TS API file which you can integrate with your React/Redux code to interact with the endpoints. Your task is to implement the two views of the application using the specifications outlined below.

There is no specific visual design requirement for the two views. Given the time constraint you should aim to implement functional views using any third party styling libraries or basic styling structures you are comfortable with, adding extra visual styling only if time permits.

You should build the interface components using React and the state solution using Redux. Your code will be reviewed against the specifications outlined below. The two views are:

Product List view. Retrieve a list of available products from the API using the function provided, create a practical set of React components that display that list and allow users to add and remove products to/from a shopping basket state implemented in Redux.

Basket Checkout view. Manage the contents of the basket, including credit card validity checks and complete a rudimentary checkout process.

The data foundation for the app is the list of products provided by the server. You can retrieve this list by calling getProducts, a function exported from the basket_server_api.js file (or basket_server_api.ts for TypeScript developers) under the client_utils/js (or client_utils/ts) folder. The (JSON) format of the product list data can be seen in the example file client_utils/sample_json/products_sample.json.

Product List View Requirements
The view should have a header which contains:

The total number of items in the basket
The total cost of those items (sum of product quantity \* product price for all products in the basket)
Clicking on either of those items should navigate the user to the Basket Checkout View
The body of the view should contain a list of the products retrieved from the API. Each list item should have:

The product name
The product description
The product price
An Add to Basket button which increments the number of items of that product sku in the basket
A Remove Basket button which decrements the number of items of that product sku in the basket
The user should not be able to add more than the ‘basketLimit’ limit amount per product sku.

A Proceed to Checkout button should navigate the user to the Basket Checkout View.

Basket Checkout View Requirements
The view should have a header which contains:

The total number of items in the basket
The body of the view should list the products in the basket. Each item in the list should have:

The product name
The current quantity. This should be implemented as a numeric select field allowing the users to change the quantity of that product. The valid numbers are 1 to ‘basketLimit’ for that product sku.
The product price
The total price for this product (product quantity _ product price)
A Remove All button should remove this product entirely from the basket
The total cost of all items (sum of product quantity _ product price for all products in the basket) should be shown beneath the list in (2).

There should a text field for the user to enter a credit card number. This number should be checked using the included luhn_check.js (or luhn_check.ts file for TypeScript) file which is in the client_utils folder.

If the number is valid the user should be able to checkout
If the number is invalid then there should be some sort of visual indication to the user of this state (you may implement your choice of solution for this aspect)
Example card numbers you can test with: 4539456463019519 (valid) / 1234567812345678 (invalid)
A Continue Shopping link should navigate back to the Product List view.

A Checkout button should submit the relevant data to the server API using the checkout function from basket_server_api.js (or basket_server_api.ts). That function will JSON.stringify the submitted JS object - you will need to ensure that this will result in JSON data in the same format as the example in client_utils/sample_json/basket_sample.json. If the basket is empty the user should not be able to click the Checkout button.

Bonus Items
If you have completed all of the requirements noted above, the requirements below (in no particular order) represent some additional items that you can attempt:

Improve the visual design of the pages
Instead of using the getProducts function to retrieve the product list from the API, use the getUnreliableProducts version. This API endpoint will randomly result in either a delayed response, or an error response, which you would need to gracefully handle (e.g. this might require some sort of visual loading indication, or a way of displaying an error message to the user)
Installing and running the Node server
As specified in the prerequisites, current versions of NodeJS and npm should be installed on your machine. The code for the node server is available to download as a ZIP file. After extracting the contents of the zip archive, navigate into created folder and run the file server.js: node server.js

By default the Node HTTP server will run on port 9001. You can easily change this by editing the value of the PORT variable near the top of the server.js file.
