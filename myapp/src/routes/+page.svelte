<script>
  import { onMount } from 'svelte';
  import { initializeApp } from "firebase/app";
  import { getMessaging, getToken } from "firebase/messaging";

  function requestNotificationPermission() {
    Notification.requestPermission().then(permission => {
      if (permission === 'granted') {
        console.log('Notification permission granted');
        // You can handle the permission being granted here
      } else {
        console.warn('Notification permission denied');
        // You can handle the permission being denied here
      }
    });
  }

  /**
	 * @param {string} token
	 */
  function sendTokenToServer(token) {
    fetch('http://localhost:8000/api/save-token', {  // Replace this with your FastAPI server URL
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            token: token
        })
    })
    .then(response => {
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        return response.json();
    })
    .then(data => {
        console.log('Response from server:', data);
    })
    .catch(error => {
        console.error('Error:', error);
    });
  }

  function initMessaging() {
      // Your web app's Firebase configuration
      const firebaseConfig = {
          apiKey: "AIzaSyDHHsoD_oWlBCY0k_3nHVUCD931gTbsD0k",
          authDomain: "notificationmicroservice-c84aa.firebaseapp.com",
          projectId: "notificationmicroservice-c84aa",
          storageBucket: "notificationmicroservice-c84aa.appspot.com",
          messagingSenderId: "141418498850",
          appId: "1:141418498850:web:06ba1f8e0fd4317b80b37b",
          measurementId: "G-1HQW7S1S0X"
      };
      const firebaseApp = initializeApp(firebaseConfig);
      const messaging = getMessaging(firebaseApp);
      getToken(messaging, { vapidKey: 'BNmM9Kp8SI2D4ClvAFw34ba1jo3eMfYJDV35mJ5uQrmbw0uz984DDzEmX8-BOp3FrVZ-daUPMcmjnklUosqyGes' }).then((currentToken) => {
      console.log('Hello')
      if (currentToken) {
          console.log('currentToken', currentToken)
          sendTokenToServer(currentToken);
      } else {
          // Show permission request UI
          console.log('No registration token available. Request permission to generate one.');
      }
      }).catch((err) => {
      console.log('An error occurred while retrieving token. ', err);
      });
  }

  onMount(() => {
    requestNotificationPermission();
    initMessaging();
  });
</script>
<head>
  <title>FCM Client</title>
</head>
<body>
  <h1>FCM Client</h1>
</body>
