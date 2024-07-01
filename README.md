# Plaid_Guide_Code
This Repository is created to help guide the users to edit the quickstart app and integrate with Plaid.

You can create your authorization profile to obtain an access token and use it to complete integration for authorization.

1. Select Custom.

2. Click Select Authorization.
    
3. Select Create New.
    
4. Select the type of authorization mechanism.

i. Select oAuth v2.
  	
ii. Name the Authorization profile under the label “Identity Provider Name” and navigate to https://dashboard.plaid.com/overview and log in.
	
iii. On the left menu, go to “developers” and “keys” and copy the ClientId from the page and paste it into the ClientId field to the Kore.ai platform.

iv. Similarly, Copy the Client secret according to the environment and paste it into the Client Secret field to the Kore.ai platform.

v. On the left menu, navigate to “API” under the same “Developers” list and click “Configure” beside the “Allowed redirect URI’s” label.

vi. Copy the callback URL from the authorization page and click “add new URI” and paste it into the text field on the Plaid platform and save the changes.

vii. Then on the left menu, go to “Docs” and then procced to “Quickstart” or click https://plaid.com/docs/quickstart/#introduction. Follow the detailed Youtube video to set up the quickstart app on your local machine.

viii. Go to the repository - “https://github.com/NikithaPa-Kore/Plaid_Guide_Code” and replace the ‘/quickstart/frontend/src/Components/Link/index.tsx’ file’s content with the one from the repo. Also check if the Callback URL on line 44 in the file is set to the one from the Auth Profile.

ix. Go to the repository - “https://github.com/NikithaPa-Kore/Plaid_Guide_Code” and replace the ‘/quickstart/node/index.js’ file’s content with the one from the repo.

x. Make sure to set your .env file with the appropriate clientId, Secret, env, products, country codes, and app port.

NOTE: The following must be set - 

PLAID_PRODUCTS=auth,transactions,identity,investments,liabilities

PLAID_REDIRECT_URI=https://idp.kore.com/workflows/callback OR "The Callback URL from the AUTH profile".

5. The Authorization URL in the auth profile must be set to the frontend host URL of the quickstart app.

6. Then in the “Subdomain (aka Tenanancy URL) ” field, select YES and enter the base URL as “https://{tenant}.plaid.com”.
7. The “Token request URL” and the “Refresh Token URL” must be set to the backend host URL of the quickstart app with the following endpoint - /api/send_the_access_token_AUTH.

EX: https://example.com/api/send_the_access_token_AUTH

8. In the “Authorization Field(s) ” label, edit the existing field by clicking on the edit icon and set the following-

Field Type = payload
Field Key = access_token
Field Value = {{accessToken}}

9. Then proceed to “Add Authorization Fields” and set the following two fields.

Field Type = header
Field Key = PLAID-CLIENT-ID
Field Value = YOUR_CLIENT_ID

Field Type = header
Field Key = PLAID-SECRET
Field Value = YOUR_CLIENT_SECRET

10. Make sure to follow all the above steps in order to Authorize with Plaid Properly. Then save the Authorization Profile.

11. Select the created Authorization Profile to complete integration. Click Authorize. It will redirect you to the Plaid Quickstart login page.

12. Complete the login process by giving corresponding App permissions and you’ll be succesfully authorized to Plaid.
