
<head>
    <title>FCM Client</title>
    <script src="https://www.gstatic.com/firebasejs/8.6.8/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.6.8/firebase-messaging.js"></script>
</head>
<body>
    <h1>FCM Client</h1>
    <script>
    // Your web app's Firebase configuration
    var firebaseConfig = {
        apiKey: "AIzaSyDHHsoD_oWlBCY0k_3nHVUCD931gTbsD0k",
        authDomain: "notificationmicroservice-c84aa.firebaseapp.com",
        projectId: "notificationmicroservice-c84aa",
        storageBucket: "notificationmicroservice-c84aa.appspot.com",
        messagingSenderId: "141418498850",
        appId: "1:141418498850:web:06ba1f8e0fd4317b80b37b",
        measurementId: "G-1HQW7S1S0X"
    };

    // Initialize Firebase
    firebase.initializeApp(firebaseConfig);

    const messaging = firebase.messaging();

    messaging.requestPermission()
    .then(function() {
        console.log('Notification permission granted.');
        return messaging.getToken();
    })
    .then(function(token) {
        console.log('Token: ', token); // log the token to the console
        // you can now use this token to test push notifications
    })
    .catch(function(err) {
        console.log('Unable to get permission to notify.', err);
    });

    messaging.onMessage(function(payload) {
        console.log('Message received. ', payload);
        // process the payload here
    });
    </script>
</body>


