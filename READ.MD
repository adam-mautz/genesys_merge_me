This widget will allow a Genesys acd agent the ability to merge ACD calls.

Example use case:

1. Customer calls into support/queue
2. Agent determines a help from an on call person is needed
3. Agent pages the on call person (does not want to call them so as not to disrupt them family time/it may be middle of the night, etc)
4. On call person calls back in and the Agent with Utilization set gets a second ACD call
5. Agent using this widget can now merge those two calls

Setup:

AWS S3 or Similar
1. Store the file in an accessible bucket.  Copy the https file link. You will need that to access the file and configure the Genesys Client app and OAuth



OAuth
1. Create a OAuth Client
2. Add Client --> Select Code Authorization/ PKCE
3. Add the https file link to the Add AUthorized redirect URI's
4. Add conversations, and conversations:readonly scope
5. You will only need the Client ID 

Update Merge.html
1. Find the section that looks like this
const CONFIG = {
  clientId: "REPLACE WITH YOUR CLIENT ID",
  environment: "usw2.pure.cloud",
  scope: "" // optional

2. Place your ClientId value and update the enviroment with your orgs region. (ie. usw2.pure.cloud, mypurecloud.com, etc)
3. Save

Group
1. Add a General Group
2. Add members or associate with a role
3. These members will have visibility to the client app widget

Integration
1. Add Integration
2. Select Genesys Interaction Widget
3. Give it a Integration Name
4. From the Configuration Tab
    1. Paste the link to the file in the Application URL
    2. Assign the group you created to the Group Filtering
    3. Type call for the Communication Type Filtering
    4. Save and Activate





