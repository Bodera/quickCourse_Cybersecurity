## Communications
So much of our technology usage nowadays has been communicating with other people.

There's the traditional email and SMS, of course.

But there's also instant messaging like Hangouts, social chat systems like Discord and Slack, and more modern SMS platforms like Signal and WhatsApp.

Aside from using TLS and SSL to ensure a secure connection between the client and the server, you should also consider including end-to-end encryption and forward secrecy.

Let's talk a bit about how that would work.

In traditional cryptography discussions, you'll usually encounter two users, Alice and Bob. We'll stick with those.

So Alice and Bob are both using Treehouse Messenger.

When they signed up, the service created for each of them a private and public key pair.

Now when Alice tries to send a message to Bob, her client sends a handshake to Bob's client, a message that says hey, I'd like to connect to you, here's who I am.

Bob's client checks the signature on the handshake against Alice's public key, and sends his own handshake back to her, which she validates.

Now that they've verified each other's identity, they agree together on a Shared Secret Key.

They'll both use that same key to encrypt the messages they send to each other.

At this point, we have a potential issue though.

If someone gains access to either Alice's or Bob's private keys, they can impersonate them for future handshake.

If they gained access to the shared secret key, they could decrypt the messages each has sent with that key.

To prevent both of these, and to provide something known as forward secrecy, the messaging system should switch the shared secret key often.

Sometimes this is as often as with every message.

Our system could take Alice's and Bob's message encryption a bit further too.

We can use the other party's public key to encrypt the message before or after it's encrypted with the secret key.

Decryption would then require both the shared key and their own private key.

If you're interested in exploring this further, Open Whisper system have made signal protocol available as an open source library for C, Java, and JavaScript.

I've included links to them in the Teachers' Notes.

Before we move on, let's talk a bit more about this forward secrecy thing I brought up.

If Alice and Bob always used the same key to encrypt their communications, if a new player, Carol, gained access to that key, she could read all of Alice's and Bob's past and future communications.

In a system with forward secrecy though, Alice and Bob agree on a new shared secret key for every time they talk to each other.

Now, if Carol gains access to a shared secret, she can only decrypt messages sent using that key.

Any messages sent in the future conversations will be encrypted with a new shared secret, so they're safe.

And messages from previous conversations are also encrypted with a different secret, so they're also safe.

Encryption and hashing are all well and good.

But what about keeping people out of the system to begin with?

In the next video, we'll talk about ACLs, and no, that's not a shoulder injury.