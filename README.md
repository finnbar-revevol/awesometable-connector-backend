# Awesome Table Connector Backend

TODO : 
* describe structure
* why servlet for oauth
* annotations
* why authenticator and why admin
* filter

## Build with Maven

### Adding the project ID to the sample API code

You must add the project ID obtained when you created your project to the
sample's `pom.xml` before you can deploy the code.

To add the project ID:

0. Edit the file `pom.xml`.

0. For `<endpoints.project.id>`, replace the value `YOUR_PROJECT_ID` with
your project ID.

0. Edit the file `src/main/java/com/example/echo/Echo.java` and
   `src/main/java/com/example/echo/EchoEndpointModule.java`.

0. Replace the value `YOUR-PROJECT-ID` with your project ID.

0. Save your changes.

### Building the sample project

To build the project:

    mvn clean package

### Generating the openapi.json file

To generate the required configuration file `openapi.json`:

    mvn endpoints-framework:openApiDocs

### Deploying the sample API to App Engine

To deploy the sample API:

0. Invoke the `gcloud` command to deploy the API configuration file:

         gcloud endpoints services deploy target/openapi-docs/openapi.json

0. Deploy the API implementation code by invoking:

         mvn clean package appengine:deploy

    The first time you upload a sample app, you may be prompted to authorize the
    deployment. Follow the prompts: when you are presented with a browser window
    containing a code, copy it to the terminal window.

0. Wait for the upload to finish.

### Sending a request to the sample API

After you deploy the API and its configuration file, you can send requests
to the API.

To send a request to the API, from a command line, invoke the following `cURL`
command:

     curl \
         -H "Content-Type: application/json" \
         -X POST \
         -d '{"message":"echo"}' \
         https://$PROJECT_ID.appspot.com/_ah/api/echo/v1/echo

You will get a 200 response with the following data:

    {
     "message": "echo"
    }
