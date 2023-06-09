# FCM Client

This project demonstrates how to use Firebase Cloud Messaging (FCM) to implement push notifications in a Svelte application. FCM is a cross-platform messaging solution that allows you to send messages at no cost.

## Features
- Request Notification Permission from User
- Initialize Firebase Messaging
- Retrieve FCM Token
- Send FCM Token to Server

## Getting Started

### Prerequisites

Before you begin, ensure you have met the following requirements:

- You have installed the latest version of [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/).
- You have a [Firebase](https://firebase.google.com/) account.
- You have a web server for your client app (for development purposes, you can use [lite-server](https://www.npmjs.com/package/lite-server), [live-server](https://www.npmjs.com/package/live-server), etc.)
- You have a basic understanding of [Svelte](https://svelte.dev/) and [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript).

### Installation

1. Clone the project to your local directory

```bash
git clone https://github.com/your-username/fcm-client.git
```

2. Go into the project directory

```bash
cd fcm-client
```

3. Install the required dependencies

```bash
npm install
```

### Usage

To use FCM Client, follow these steps:

1. Replace the `firebaseConfig` in the script with your own Firebase project credentials.

2. Replace the URL in the `sendTokenToServer` function with your own server URL.

3. Run your local web server. If you're using `lite-server`, you can start it with `npm run start`.

4. Open your web browser and navigate to `http://localhost:8000` (or whatever port your server is running on). The application should request notification permissions.
