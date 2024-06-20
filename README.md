# MuleSoft IDP Demo Application

This MuleSoft application provides an interactive demo of MuleSoft's Intelligent Document Processing (IDP) capabilities.   It is a comprehensive package inclusive of a webclient (the MuleSoft IDP HTML page) that allows to take a picture of the document and then submit it for processing. The processing results are displayed on the webclient as well.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Configuration](#configuration)
   - [Configuration Properties](#configuration-properties)
   - [MuleSoft IDP Connector Configuration](#mulesoft-idp-connector-configuration)
3. [Flows](#flows)
   - [Handle WebSocket Open](#handle-websocket-open)
   - [Handle WebSocket Inbound Message](#handle-websocket-inbound-message)
   - [Poll Object Store Execution ID](#poll-object-store-execution-id)
   - [Handle WebSocket Closed](#handle-websocket-closed)
   - [Verify Execution ID Status](#verify-execution-id-status)
   - [Reset All Object Stores](#reset-all-object-stores)
   - [Retrieve Object Store Contents](#retrieve-object-store-contents)
   - [Load Main Page](#load-main-page)
   - [Load Images](#load-images)
4. [Using the MuleSoft IDP HTML Page](#using-the-mulesoft-idp-html-page)
5. [Running the Application](#running-the-application)
6. [License](#license)

## Prerequisites

- MuleSoft Anypoint Platform
- MuleSoft IDP Connector (George Jeffcock)
- WebSocket support in MuleSoft
- An HTTP client for testing (e.g., Postman)

## Configuration

### Configuration Properties

Configuration properties are defined in `config/config.yaml`. Ensure the following properties are set:

- `http.port`: Port for the HTTP listener
- `idp.host`: Host for the IDP service
- `idp.clientId`: Client ID for IDP authentication
- `idp.clientSecret`: Client Secret for IDP authentication
- `idp.accessTokenUrl`: URL to obtain access tokens from IDP
- `mulesoft.orgId`: Organization ID for IDP actions
- `idp.actionId`: IDP action ID for document submission
- `idp.actionVersion`: Version of the IDP action
- `mulesoft.pollingFrequency`: Polling frequency in seconds

### MuleSoft IDP Connector Configuration

The IDP connector configuration includes authentication details for interacting with the IDP service.

## Flows

### Handle WebSocket Open

This flow handles the opening of new WebSocket connections, logs the event, stores the socket ID, and sends a response to the client.

### Handle WebSocket Inbound Message

This flow processes inbound WebSocket messages, submits the document to IDP, and stores the execution ID.

### Poll Object Store Execution ID

This flow periodically checks the execution IDs stored in the object store, polls for results from IDP, and sends the results to the corresponding WebSocket clients.

### Handle WebSocket Closed

This flow handles the closure of WebSocket connections, logs the event, and removes the socket ID from the object store.

### Verify Execution ID Status

This flow verifies the status of an execution ID provided via a URL parameter and sends the result back to the client.

### Reset All Object Stores

This flow resets all the object stores by removing all entries.

### Retrieve Object Store Contents

This flow retrieves the contents of the object stores and returns them in the HTTP response.

### Load Main Page

This flow serves the main HTML page of the application to the client.

### Load Images

This flow serves image resources to the client.

## Using the MuleSoft IDP HTML Page

The MuleSoft IDP HTML page allows users to interact with the WebSocket endpoint for document submission and result retrieval. Follow these steps to use the page:

1. **Access the HTML Page**:
   - Open a web browser and navigate to the main page served by the application. The URL is  `http://host:{http.port}/html/index.html`.

2. **Connect to the WebSocket**:
   - Click the "Connect WebSocket" button on the page to establish a WebSocket connection to the server. 
   - You should see a message indicating that the WebSocket connection has been opened.

2. **Capture a Document**:
   - Position your document so it fits in the red rectangle on the video element
   - Click the "Capture Image" button on the page to capture the image. 
   - You should see a thumbnail with the captured document, clicking on the thumbnail will open a popup with a full size view of the captured image .

3. **Submit a Document**:
   - Enter the text of the document you wish to process in the textarea provided.
   - Click the "Send Document" button to submit the document through the WebSocket connection.
   - You will see a message indicating that the document has been sent.

4. **View Results**:
   - As the server processes the document, any results or updates will be sent back through the WebSocket connection and displayed in the "Messages" section of the page.
   - Look for messages indicating the status of your document processing and the final results.

5. **Disconnect the WebSocket**:
   - Click the "Disconnect WebSocket" button to close the WebSocket connection when you are finished.

## Running the Application

1. Deploy the application on MuleSoft Anypoint Platform.
2. Ensure all configuration properties are correctly set in `config/config.yaml`.
3. Use the provided HTML page to interact with the WebSocket endpoint.
4. Use the HTTP endpoints to manage and monitor object stores.


