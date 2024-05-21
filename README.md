```markdown
# MuleSoft Intelligent Document Processing (IDP)

Welcome to MuleSoft IDP! This application enables you to capture images using your device's camera, process them, and interact with a WebSocket server for intelligent document processing.

## Table of Contents
- [Features](#features)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Buttons and Their Functions](#buttons-and-their-functions)
- [UI Components](#ui-components)
- [Technical Details](#technical-details)

## Features
- Capture images using the device's camera.
- Send captured images to a WebSocket server.
- Display received messages from the WebSocket server.
- Clear message history.

## Getting Started

To start using the MuleSoft IDP application, follow these steps:

1. **Open Connection:** Establish a WebSocket connection.
2. **Capture Image:** Capture an image using your device's camera.
3. **Send Image:** Send the captured image to the WebSocket server.
4. **Close Connection:** Close the WebSocket connection when done.

## Usage

### Opening the Connection
1. Click the **"Open Connection"** button. This initializes and opens a WebSocket connection to the server.

### Capturing an Image
1. Click the **"Capture Image"** button. This will capture an image from your device's camera and display a thumbnail of the captured image.

### Sending the Image
1. After capturing an image, click the **"Send Image"** button. This will send the captured image to the WebSocket server.

### Closing the Connection
1. Click the **"Close Connection"** button to close the WebSocket connection.

### Clearing Messages
1. Click the **"Clear Messages"** button to clear the message history displayed on the page.

## Buttons and Their Functions

- **Open Connection:** Opens the WebSocket connection.
- **Capture Image:** Captures an image from the camera feed.
- **Send Image:** Sends the captured image to the WebSocket server.
- **Close Connection:** Closes the WebSocket connection.
- **Clear Messages:** Clears all messages from the message display area.

## UI Components

### Logo and Title
- **Logo:** Displays the MuleSoft logo.
- **Title:** "Try MuleSoft Intelligent Document Processing".

### Camera and Capture Area
- **Video Feed:** Displays the live video feed from the device's camera.
- **Overlay:** An overlay for capturing the image.
- **Canvas:** A hidden canvas used for image processing.

### Message Display
- **Message Container:** Displays the captured image as a thumbnail.
- **Timestamp:** Shows the timestamp of the captured image.
- **Received Messages Container:** Displays messages received from the WebSocket server.

### Popup
- **Popup Window:** Displays the full-size image when a thumbnail is clicked.
- **Close Button:** Closes the popup window.

### WebSocket Status Icon
- **Socket Icon:** Indicates the status of the WebSocket connection (green for open, grey for closed).

## Technical Details

- The application uses the device's camera to capture images, which are then displayed and can be sent to a WebSocket server.
- WebSocket connection management is handled through buttons that enable and disable functionalities based on the connection status.
- The WebSocket server URL is dynamically determined based on the protocol (http or https).

### Scripts and Event Listeners
- **Access Camera:** Automatically accesses the camera when the page loads.
- **Capture Image:** Captures an image from the video feed and displays a thumbnail.
- **Send Image:** Sends the captured image data to the WebSocket server.
- **WebSocket Management:** Handles opening, closing, and managing the WebSocket connection.
- **Clear Messages:** Clears the message display area.
- **Popup Management:** Manages the display and closure of the image popup.

### Styling
- The application uses a responsive layout with a centered logo and title, vertically aligned buttons, and flexbox containers for the video feed and message display areas.

### Server Configuration (MuleSoft)
- The application is packaged as a MuleSoft .jar , prior to usage make sure to change config.yaml to change all idp and mulesoft key values with your own. You will need an anypoint org with IDP enabled and one action published.
- The application was developed for Mule 4 and tested on cloudhub 2
- The Mule app is self containing, it contains both the webpage frontend as the backend components
- The application uses the object store to store the active sockets and another one to store the IDP executionids (keys) and the socketid as values.
- Multiple concurrent socket web clients ( = multiple demoes) are supported though not tested

## Notes
- Ensure your browser has permissions to access the camera.
- The application is designed to use the back camera if available, ideal for document capture.
- WebSocket communication requires a server endpoint to connect and process the captured images.

Enjoy using MuleSoft IDP for intelligent document processing!
```

