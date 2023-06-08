# FCM Client

## Description

This is a simple Firebase Cloud Messaging (FCM) client written in JavaScript. The FCM client allows your web application to receive push notifications from a Firebase backend. The code establishes a connection to a Firebase backend using a project-specific Firebase configuration and requests the user's permission to receive notifications. Once the permission is granted, it retrieves a token which can be used to send push notifications to the client. It also logs any received messages to the console.

## Setup

1. Clone this repository or copy the provided HTML code into an HTML file in your project.
2. Open the file with your favorite text editor.
3. Replace the `firebaseConfig` object values with your Firebase project's specific values. The configuration object is defined as follows:

```javascript
    var firebaseConfig = {
        apiKey: "YOUR_API_KEY",
        authDomain: "YOUR_AUTH_DOMAIN",
        projectId: "YOUR_PROJECT_ID",
        storageBucket: "YOUR_STORAGE_BUCKET",
        messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
        appId: "YOUR_APP_ID",
        measurementId: "YOUR_MEASUREMENT_ID"
    };
```

4. Save the file.
5. Run the HTML file in a browser. If permission to send notifications is granted, the FCM client will print a token to the console, which you can use to send push notifications.

## Usage

When you run the HTML file, the script automatically attempts to obtain permission from the user to display notifications. If permission is granted, the Firebase messaging token is logged to the console. You can use this token to send push notifications to the client.

When a message is received, it is logged to the console. To handle these messages in your own way, replace or extend the `messaging.onMessage` function:

```javascript
    messaging.onMessage(function(payload) {
        console.log('Message received. ', payload);
        // process the payload here
    });
```
