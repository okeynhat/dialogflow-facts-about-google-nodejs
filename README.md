# Actions on Google: Facts about Google

This sample demonstrates Actions on Google features for use on Google Assistant
including custom entities, contexts, deep links, and rich responses -- using
the [Node.js client library](https://github.com/actions-on-google/actions-on-google-nodejs)
and deployed on [Cloud Functions for Firebase](https://firebase.google.com/docs/functions/).

## Setup Instructions
### Prerequisites
1. Node.js and NPM
    + We recommend installing using [NVM](https://github.com/creationix/nvm)
1. Install the [Firebase CLI](https://developers.google.com/assistant/actions/dialogflow/deploy-fulfillment)
    + We recommend using version 6.5.0, `npm install -g firebase-tools@6.5.0`
    + Run `firebase login` with your Google account

### Configuration
#### Actions Console
1. From the [Actions on Google Console](https://console.actions.google.com/), New project (this will be your *Project ID*) > **Create project** > under **More options** > **Conversational**
1. From the top menu under **Develop** > **Actions** (left nav) > **Add your first action** > **BUILD** (this will bring you to the Dialogflow console) > Select language and time zone > **CREATE**.
1. In the Dialogflow console, go to **Settings** ⚙ > **Export and Import** > **Restore from zip** using the `agent.zip` in this sample's directory.

#### Firebase Deployment
1. In the `functions` directory, run `npm install`
1. Run `firebase deploy --project {PROJECT_ID}` to deploy the function
    + To find your **Project ID**: In [Dialogflow console](https://console.dialogflow.com/) under **Settings** ⚙ > **General** tab > **Project ID**.

#### Dialogflow Console
1. Return to the [Dialogflow Console](https://console.dialogflow.com) > select **Fulfillment** > **Enable** Webhook > Set **URL** to the **Function URL** that was returned after the deploy command > **SAVE**.
    ```
    Function URL (dialogflowFirebaseFulfillment): https://${REGION}-${PROJECT_ID}.cloudfunctions.net/dialogflowFirebaseFulfillment
    ```
1. Add Deep Links:
    + Select **Integrations** from the left navigation menu > **Google Assistant** > **Integration Settings** > **Implicit invocation** > add `choose_cats` & `choose_fact` intents.
1. From the left navigation menu, click **Integrations** > **Integration Settings** under Google Assistant > Enable **Auto-preview changes** >  **Test** to open the Actions on Google simulator then say or type `Talk to my test app`.

### Running this Sample
+ You can test your Action on any Google Assistant-enabled device. Make sure the Assistant is signed into the same account used to create the Actions project, and just say “OK Google, talk to my test app”.
+ You can also use the Actions on Google Console simulator to test most features and preview on-device behavior.

### Automated Testing
Unit and integration tests are located in the `functions/test/`. In each of the JavaScript files, change `projectId` and `pathToServiceAccount` to your GCP project id and the path to the JSON file for your service account - please follow the [following instructions](https://cloud.google.com/iam/docs/creating-managing-service-accounts) on how to create a service account.

1. `npm install` from the `functions/` directory
1. `npm test`

Notes:
1. One of the configuration variables you'll need to set in the code is `fulfillUrl`, which is the url of the fulfillment. Ideally, this should be a locally run cloud function. We recommend using `firebase serve`.
1. To use Dialogflow API, you will need to have service account that has the "Dialogflow API client" role. You can set this in the GCP IAM page (see https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

## References & Issues
+ Questions? Go to [StackOverflow](https://stackoverflow.com/questions/tagged/actions-on-google), [Assistant Developer Community on Reddit](https://www.reddit.com/r/GoogleAssistantDev/) or [Support](https://developers.google.com/assistant/support).
+ For bugs, please report an issue on Github.
+ Actions on Google [Documentation](https://developers.google.com/assistant)
+ Actions on Google [Codelabs](https://codelabs.developers.google.com/?cat=Assistant).
+ [Webhook Boilerplate Template](https://github.com/actions-on-google/dialogflow-webhook-boilerplate-nodejs) for Actions on Google.

## Make Contributions
Please read and follow the steps in the [CONTRIBUTING.md](CONTRIBUTING.md).

## License
See [LICENSE](LICENSE).

## Terms
Your use of this sample is subject to, and by using or downloading the sample files you agree to comply with, the [Google APIs Terms of Service](https://developers.google.com/terms/).
