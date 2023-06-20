Backend
===================================================

.. toctree::
   :maxdepth: 2

   frontend.rst
   backend.rst

Tasks:
===================================================


* Create & deploy a Workers project using npm cloudflare create
* Go to dash and explore
* Explore the local dev setup by executing wrangler dev
* Get familiar with logging locally as well as using wrangler tail
* Share your endpoint url with Gift/Mark so that we can provide you with a mock-frontend to test your backend
* Handle CORS by setting these response headers
  'Access-Control-Allow-Origin': '*',
  'Access-Control-Allow-Methods': 'POST, OPTIONS',
  'Access-Control-Max-Age': '86400',
* Create conditionals to handle POST, OPTIONS and all other requests
  * On OPTIONS request, return null, and the CORS headers
  * On POST request execute the main code and the CORS headers
  * On all other requests return a 405 and the CORS headers
* Create an R2 bucket and set up a binding to the Worker
* Upload the incoming file to R2 by:
  * Parsing the formData
  * Using the R2.put binding
  * Return 201 on success, 500 otherwise
* Make the file name unguessable and conflict-free, by using a UUID
  * Generate a UUID using the crypto libarary
  * Extract the origin file exentension
  * Use the concat of both as new object key
* Return a pre-signed URL in the response body
  * Follow https://developers.cloudflare.com/r2/api/s3/presigned-urls/ to generate a pre-signed URL for the GET method that is valid for 3600 seconds
  * Return that URL in response body
  
## Stretch goals:
* Parse the "expire" header from the request and use it to set the pre-signed URL expiration; if it is not present or invalid, default to 36000
* Set up Logpush to R2 for the Worker and add meaningful logs
* Use KV to generate "nicer" links. The current links are very long. Store the current link in KV with a random number as key and return a link with the number instead. Then implement a GET method that can parse the link (i.e. extract the path), makes a KV lookup to the original link and then fetches that link and returns the result
* Use R2 bucket lifecycles to delete files automatically after 7 days (https://developers.cloudflare.com/r2/buckets/object-lifecycles/)