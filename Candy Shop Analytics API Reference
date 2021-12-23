### Intro

Freddy loves Halloween. He loves it so much that he decided to open his own online artisanal Halloween candy shop last year. The shop was a huge success, thanks to the unique and exclusive candy stock list. Now Freddy needs a simple web app to manage his candy orders. You’ve been hired to document the API of that shop!

### Tasks

-   Document the following views
    -   **Login**: Login using the API at `https://freddy.codesubmit.io/login` with POST `{ username: 'freddy', password: 'ElmStreet2019' }`. The login endpoint will return a JWT `access_token` that is valid for 15 minutes and a `refresh_token` which is valid for 30 days. Make sure to also provide documentation on how to handle wrong credentials properly
    -   **Dashboard**: Retrieve the necessary data for the dashboard at `https://freddy.codesubmit.io/dashboard`. This endpoint requires a `Authorization: Bearer access_token` header. Use the access token that you retrieved from Login. Keep in mind that access tokens expire after 15 minutes. You may request a fresh access token by sending a POST request to `https://freddy.codesubmit.io/refresh` with the `Authorization: Bearer refresh_token` header. 
    -   **Orders**: Fetch the orders at `https://freddy.codesubmit.io/orders?page=1&q=search_term`. This endpoint requires a `Authorization: Bearer access_token` header. Make sure to document search and pagination