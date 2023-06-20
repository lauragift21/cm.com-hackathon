Frontend
===================================================

.. toctree::
   :maxdepth: 2

   frontend.rst
   backend.rst

## Tasks:
- Create & deploy a NextJS project using npm cloudflare create
- Go to dash and explore, then attach a custom domain. You can use any URL in the form of <YOUR-SUBDOMAIN>.cf-workshop.eu
- Get local dev running by running npm run dev
- Edit Home page to have a file-upload form
- Deploy your changes to Pages using previews (see https://developers.cloudflare.com/pages/platform/direct-upload/#publish-your-assets); note that you'll have to install next-on-pages first using npm and use the following command to deploy npx wrangler pages deploy .vercel/output/static 
- Protect the preview deployments using Cloudflare Access, so that only authorised members can access the previews (see https://developers.cloudflare.com/pages/platform/preview-deployments/#customizing-preview-deployments-access)
- On submit, the file should be sent to an API endpoint using formData in a POST request
  - At the end, the backend team will provide an endpoint
  - Meanwhile during development use webhook.site as a mock endpoint
  - Enable CORS Headers for webhook site
  - Edit the response to return "example.com"
  - Important the data needs to be included as formData:
    const formData = new FormData();
    formData.append("file", file);
- The submit button should be disabled during upload and display "Uploading..."
- The API endpoint will return a link to the shared file in the response body, display said link after successful upload

## Stretch goals:
- Add a button to copy the link to the clipboard
- Handle failure cases in the frontend to give the user feedback
- Add a selector to the form with 1h, 24h or 7d options and add the respective value in seconds as "expire" header to the POST request.