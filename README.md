A very quick personal fork to use the firebase-admin package instead of the normal firebase and support authenticating with a service account, because leaving the entire thing open read/write is kind of bad. __remember to be careful where I commit the service account json file to because it contains a powerful private key__

# botkit-storage-firebase

A Firebase storage module for Botkit.

## Usage

Just require `botkit-storage-firebase` and pass it a config with a `firebase_uri` option.
Then pass the returned storage when creating your Botkit controller. Botkit will do the rest.

Make sure everything you store has an `id` property, that's what you'll use to look it up later.

```
var Botkit = require('botkit'),
    firebaseStorage = require('botkit-storage-firebase')({databaseURL: '...'}),
    controller = Botkit.slackbot({
        storage: firebaseStorage
    });
```

```
// then you can use the Botkit storage api, make sure you have an id property
var beans = {id: 'cool', beans: ['pinto', 'garbanzo']};
controller.storage.teams.save(beans);
beans = controller.storage.teams.get('cool');

```
