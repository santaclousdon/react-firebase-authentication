# React Firebase Authentication

## Features

* uses:
  * only React (create-react-app)
  * firebase
  * react-router
* features:
  * Sign In
  * Sign Up
  * Sign Out
  * Password Forget
  * Password Change
  * Verification Email
  * Protected Routes with Authorization
  * Roles-based Authorization
  * Social Logins with Google, Facebook and Twitter
  * Linking of Social Logins on Account dashboard
  * Auth Persistence with Local Storage
  * Database with Users and Messages

## Installation

* `git clone git@github.com:the-road-to-react-with-firebase/react-firebase-authentication.git`
* `cd react-firebase-authentication`
* `npm install`
* `npm start`
* visit http://localhost:3000

Get an overview of Firebase, how to create a project, what kind of features Firebase offers, and how to navigate through the Firebase project dashboard in this [visual tutorial for Firebase](https://www.robinwieruch.de/firebase-tutorial/).

### Firebase Configuration

* copy/paste your configuration from your Firebase project's dashboard into one of these files
  * *src/components/Firebase/firebase.js* file
  * *.env* file
  * *.env.development* and *.env.production* files

The *.env* or *.env.development* and *.env.production* files could look like the following then:

```
REACT_APP_API_KEY=AIzaSyBtxZ3phPeXcsZsRTySIXa7n33NtQ
REACT_APP_AUTH_DOMAIN=react-firebase-s2233d64f8.firebaseapp.com
REACT_APP_DATABASE_URL=https://react-firebase-s2233d64f8.firebaseio.com
REACT_APP_PROJECT_ID=react-firebase-s2233d64f8
REACT_APP_STORAGE_BUCKET=react-firebase-s2233d64f8.appspot.com
REACT_APP_MESSAGING_SENDER_ID=701928454501
```

### Activate Sign-In Methods

![firebase-enable-google-social-login_640](https://user-images.githubusercontent.com/2479967/49687774-e0a31e80-fb42-11e8-9d8a-4b4c794134e6.jpg)

* Email/Password
* [Google](https://www.robinwieruch.de/react-firebase-social-login/)
* [Facebook](https://www.robinwieruch.de/firebase-facebook-login/)
* [Twitter](https://www.robinwieruch.de/firebase-twitter-login/)
* [Troubleshoot](https://www.robinwieruch.de/react-firebase-social-login/)

### Activate Verification E-Mail

* add a redirect URL for redirecting a user after an email verification into one of these files
  * *src/components/Firebase/firebase.js* file
  * *.env* file
  * *.env.development* and *.env.production* files

The *.env* or *.env.development* and *.env.production* files could look like the following then (excl. the Firebase configuration).

**Development:**

```
REACT_APP_CONFIRMATION_EMAIL_REDIRECT=http://localhost:3000
```

**Production:**

```
REACT_APP_CONFIRMATION_EMAIL_REDIRECT=https://mydomain.com
```

### Security Rules

```
{
  "rules": {
    ".read": false,
    ".write": false,
    "users": {
      "$uid": {
        ".read": "$uid === auth.uid || root.child('users/'+auth.uid).child('roles').hasChildren(['ADMIN'])",
        ".write": "$uid === auth.uid || root.child('users/'+auth.uid).child('roles').hasChildren(['ADMIN'])"
      },
      ".read": "root.child('users/'+auth.uid).child('roles').hasChildren(['ADMIN'])",
      ".write": "root.child('users/'+auth.uid).child('roles').hasChildren(['ADMIN'])"
    },
    "messages": {
      ".indexOn": ["createdAt"],
      "$uid": {
        ".write": "data.exists() ? data.child('userId').val() === auth.uid : newData.child('userId').val() === auth.uid"
      },
      ".read": "auth != null",
      ".write": "auth != null",
    },
  }
}
```

### Contacts


![Gmail](https://github.com/santaclous112/MonilP-Portfolio/blob/master/src/components/Icon/svg/mailto.svg)               
        santaclous112@gmail.com

![Skype](https://github.com/santaclous112/MonilP-Portfolio/blob/master/src/components/Icon/svg/skype.svg)               
        live:.cid.772f958a47f37977

![Telegram](https://github.com/santaclous112/MonilP-Portfolio/blob/master/src/components/Icon/svg/telegram.svg)               
        PeaceStar01
