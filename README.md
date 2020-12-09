# Node.js Launcher Code Examples

### Github repo: https://github.com/docusign/code-examples-node

This GitHub repo includes code examples for both the DocuSign eSignature REST API and the DocuSign Rooms API. 

To use the Rooms API code examples, modify the `exampleAPI` setting at the end of the config/appsettings.json file to `rooms`.

**Note:** To use the Rooms API, you must also [create your DocuSign developer account for Rooms](https://developers.docusign.com/docs/rooms-api/rooms101/create-account). 


## Introduction

This repo is a Node.js application that supports the following authentication workflows:

* Authentication with DocuSign via [Authorization Code Grant](https://developers.docusign.com/platform/auth/authcode).
When the token expires, the user is asked to re-authenticate. The refresh token is not used.

* Authentication with DocuSign via [JSON Web Token (JWT) Grant](https://developers.docusign.com/platform/auth/jwt/).
When the token expires, it updates automatically.


## eSignature API

For more information about the scopes used for obtaining authorization to use the eSignature API, see the [Required Scopes section](https://developers.docusign.com/docs/esign-rest-api/esign101/auth).

1. **Use embedded signing.** [Source](./eg001EmbeddedSigning.js)<br />
   Sends an envelope, then uses embedded signing for the first signer. With embedded signing, DocuSign signing is initiated from your website.
1. **Send an envelope with a remote (email) signer and cc recipient.** [Source](./lib/eSignature/eg002SigningViaEmail.js)<br />
   The envelope includes a PDF, Word, and HTML document. [Anchor text](https://support.docusign.com/en/guides/AutoPlace-New-DocuSign-Experience) is used to position the signing fields in the documents.
1. **List envelopes in the user's account.** [Source](./lib/eSignature/eg003ListEnvelopes.js)<br />
   The envelopes' current status is included.
1. **Get an envelope's basic information.** [Source](./lib/eSignature/eg004EnvelopeInfo.js)<br />
   Lists basic information about an envelope, including its overall status.
1. **List an envelope's recipients** [Source](./lib/eSignature/eg005EnvelopeRecipients.js)<br />
   Includes current recipient status.
1. **List an envelope's documents.** [Source](./lib/eSignature/eg006EnvelopeDocs.js)<br />
   Includes current recipient status.
1. **Download an envelope's documents.** [Source](./lib/eSignature/eg007EnvelopeGetDoc.js)<br />
   Downloads individual documents, the documents concatenated together, or a ZIP file of the documents.
1. **Programmatically create a template.** [Source](./lib/eSignature/eg008CreateTemplate.js)
1. **Send an envelope using a template.** [Source](./lib/eSignature/eg009UseTemplate.js)
1. **Send an envelope and upload its documents with multipart binary transfer.** [Source](./lib/eSignature/eg010SendBinaryDocs.js)<br />
   Binary transfer is 33% more efficient than using Base64 encoding.
1. **Use embedded sending.** [Source](./lib/eSignature/eg011EmbeddedSending.js)<br />
   Embeds the DocuSign UI in your web app to finalize or update the envelope and documents before they are sent.
1. **Embed the DocuSign UI in your app.** [Source](./lib/eSignature/eg012EmbeddedConsole.js)<br />
1. **Use embedded signing from a template with an added document.** [Source](./lib/eSignature/eg013AddDocToTemplate.js)<br />
   Sends an envelope based on a template. In addition to the template's document(s), this example adds an
   additional document to the envelope by using the [Templates](https://developers.docusign.com/esign-rest-api/guides/features/templates#composite-templates) feature.
1. **Accept payments.** [Source](./lib/eSignature/eg014CollectPayment.js)<br />
   Sends an order form with online payment by credit card.
1. **Get envelope tab data.** [Source](./lib/eSignature/eg015EnvelopeTabData.js)<br />
   Retrieves the tab (field) values for all of the envelope's recipients.   
1. **Set envelope tab values.** [Source](./lib/eSignature/eg016SetTabValues.js)<br />
   Creates an envelope and sets the initial values for its tabs (fields). Some of the tabs
   are set to be read-only, others can be updated by the recipient. This example also stores
   metadata with the envelope.
1. **Set template tab values.** [Source](./lib/eSignature/eg017SetTemplateTabValues.js)<br />
   Creates an envelope using a template and sets the initial values for its tabs (fields). This example also stores metadata with the envelope.
1. **Get the envelope custom field data (metadata).** [Source](./lib/eSignature/eg018EnvelopeCustomFieldData.js)<br />
   Retrieves the custom metadata (custom data fields) stored with the envelope.
1. **Require an access code for a recipient.** [Source](./lib/eSignature/eg019AccessCodeAuthentication.js)<br />
   Sends an envelope that requires entering an access code for the purpose of multifactor authentication.
1. **Require SMS authentication for a recipient.** [Source](./lib/eSignature/eg020SmsAuthentication.js)<br />
   Sends an envelope that requires entering a six-digit code from an text message for the purpose of multifactor authentication.
1. **Require phone authentication for a recipient.** [Source](./lib/eSignature/eg021PhoneAuthentication.js)<br />
   Sends an envelope that requires entering a voice-based response code for the purpose of multifactor authentication.
1. **Require knowledge-based authentication (KBA) for a recipient.** [Source](./lib/eSignature/eg022KbaAuthentication.js)<br />
   Sends an envelope that requires passing a public records check to validate identity for the purpose of multifactor authentication.
1. **Require ID Verification (IDV) for a recipient.** [Source](./lib/eSignature/eg023IdvAuthentication.js)<br />
   Sends an envelope that requires the recipient to upload a government issued ID for the purpose of multifactor authentication. 
1. **Create a permission profile.** [Source](./lib/eSignature/eg024CreatePermission.js)<br />
1. **Set a permission profile.** [Source](./lib/eSignature/eg025PermissionSetUserGroup.js)<br />
   Demonstrates how to set a user group's permission profile. You must have already created a permission profile and a group of users.
1. **Update individual permission settings.** [Source](./lib/eSignature/eg026PermissionChangeSingleSetting.js)<br />
   Demonstrates how to edit individual permission settings on a permission profile.
1. **Delete a permission profile.** [Source](./lib/eSignature/eg027DeletePermission.js)<br />
1. **Create a brand.** [Source](./lib/eSignature/eg028CreateBrand.js)<br />
   Creates a brand profile for an account.
1. **Apply a brand to an envelope.** [Source](./lib/eSignature/eg029ApplyBrandToEnvelope.js)<br />
   Demonstrates how to apply a brand you've created to an envelope. First, this example creates the envelope, then applies the brand to it. [Anchor text](https://support.docusign.com/en/guides/AutoPlace-New-DocuSign-Experience) is used to position the signing fields in the documents.
1. **Apply a brand to a template.** [Source](./lib/eSignature/eg030ApplyBrandToTemplate.js)<br />
   Demonstrates how to apply a brand you've created to a template. You must have at least one created template and brand. [Anchor text](https://support.docusign.com/en/guides/AutoPlace-New-DocuSign-Experience) is used to position the signing fields in the documents.
1. **Bulk-send envelopes to multiple recipients.** [Source](./lib/eSignature/eg031BulkSendEnvelopes.js)<br />
   Demonstrates how to send envelopes in bulk to multiple recipients. First, this example creates a bulk-send recipients list, then creates an envelope.  After that, it initiates bulk envelope sending.


## Rooms API 

For more information about the scopes used for obtaining authorization to use the Rooms API, see the [Required Scopes section](https://developers.docusign.com/docs/rooms-api/rooms101/auth/).

**Note:** To use the Rooms API you must also [create your DocuSign Developer Account for Rooms](https://developers.docusign.com/docs/rooms-api/rooms101/create-account). Examples 4 and 6 require that you have the DocuSign Forms feature enabled in your Rooms for Real Estate account.

1. **Create a room with data.** [Source](./lib/rooms/eg001CreateRoomWithData.js)<br />
   Creates a new room in your DocuSign Rooms account to be used for a transaction.
1. **Create a room from a template.** [Source](./lib/rooms/eg002CreateRoomFromTemplate.js)<br />
   Creates a new room using a template.
1. **Export data from a room.** [Source.](./lib/rooms/eg003ExportDataFromRoom.js)<br />
   Exports all the available data from a specific room in your DocuSign Rooms account.
1. **Add a form to a room.** [Source.](./lib/rooms/eg004AddingFormToRoom.js)<br />
   Adds a standard real estate-related form to a specific room in your DocuSign Rooms account.
1. **Search for a room with a filter.** [Source](./lib/rooms/eg005GetRoomsWithFilters.js)<br />
   Searches for rooms in your DocuSign Rooms account using a specific filter. 
1. **Create an external form fillable session.** [Source](./lib/rooms/eg006CreateExternalFormFillSession.js)<br />
   Creates an external form that can be filled using DocuSign for a specific room in your DocuSign Rooms account.


## Installation

### Prerequisites
**Note: If you downloaded this code using [Quickstart](https://developers.docusign.com/docs/esign-rest-api/quickstart/) from the DocuSign Developer Center, skip items 1 and 2 below as they're automatically performed for you.**

1. [Create a DocuSign developer account](https://go.docusign.com/o/sandbox/) if you don't already have one.
1. A DocuSign integration key (client ID) that is configured for authentication to use either [Authorization Code Grant](https://developers.docusign.com/platform/auth/authcode/) or [JWT Grant](https://developers.docusign.com/platform/auth/jwt/).

   To use [Authorization Code Grant](https://developers.docusign.com/platform/auth/authcode/), you will need an integration key and its secret key. 

   To use [JWT Grant](https://developers.docusign.com/platform/auth/jwt/), you will need an integration key, an RSA key pair, and the **API Username** (GUID) of the impersonated user. See [Configure JWT](#configure-jwt) below for detailed steps.

   For both authentication flows:
   
   If you use this launcher on your own workstation, the integration key must include a redirect URI of http://localhost:5000/ds/callback

   If you will not be running the example on your own workstation, use the appropriate DNS name and port instead of localhost.

1. [Node.js version 8.10 or later with NPM version 5 or later](https://nodejs.org/en/download/).
1. A name and email for a signer, and a name and email for a cc recipient.


### Installation steps
**Note: If you downloaded this code using [Quickstart](https://developers.docusign.com/docs/esign-rest-api/quickstart/) from the DocuSign Developer Center, skip steps 1 and 4 below as they're automatically performed for you.**

1. Download or clone the [code-examples-node](https://github.com/docusign/code-examples-node) repository.
1. Switch to the folder: `cd <Quickstart_folder_name>` or `cd code-examples-node`
1. Run `npm install`   
1. Create a new file config/appsettings.json by using config/appsettings.example.json as your template and *either:*
   * Update config/appsettings.json in the project's root directory with the integration key and other settings, *or*
   * Create and export environment variables for the settings. See config/appsettings.json for the names of the environment variables.
   **Note:** Protect your integration key and secret and/or RSA private key pair; ensure that config/appsettings.json will not be stored in your source code repository.
1. `npm start`
1. Open a browser to http://localhost:5000


### Configure JWT
1. [Create a DocuSign developer account](https://go.docusign.com/o/sandbox/) if you don't already have one.
1. Create a new integration key on the [Apps and Keys](https://admindemo.docusign.com/api-integrator-key) page and save the GUID to a secure location for step 6 below.
1. Set a redirect URI of http://localhost:5000/ds/callback as mentioned in the [Installation Prerequisites](#prerequisites) item 2 above.
1. Generate an RSA key pair. Under **Apps and Integration Keys**, choose the integration key to use, then select **Actions**, then **Edit**. In the **Authentication** section, select **ADD RSA KEYPAIR**. Save the private key to a secure location for the next step.
1. Create a new file config/private.key, then paste and save your RSA private key in it.
1. Update the file config/appsettings.json with your integration key GUID from step 2 as your `dsJWTClientId` and your **API Username** from the [Apps and Keys](https://admindemo.docusign.com/api-integrator-key) page as your `impersonatedUserGuid`.
1. Run the launcher using `npm start`, then select **JSON Web Token** when authenticating your account.


## Payments code example
To use the payments example, create a test payments gateway for your DocuSign developer account. See the 
[PAYMENTS_INSTALLATION.md](./PAYMENTS_INSTALLATION.md)
file for instructions.
   
Then add the payment **Gateway Account ID** to the config/appsettings.json file.


## Unit Testing

1. Before running the unit tests you will need to [obtain an access token](https://developers.docusign.com/platform/auth/authcode/authcode-get-token/)
and you will need an API Account ID.

2. *Either:*

   * Update the file test/testHelpers.js in the project's root folder with the access token, **API Account ID**, signer and cc information *or*
   * Create and export this information as the environment variables named in that file.

3. Run `npm test`


## License and additional information

### License
This repository uses the MIT License. See the LICENSE file for more information.

### Pull Requests
Pull requests are welcomed. Pull requests will only be considered if their content
uses the MIT License.
