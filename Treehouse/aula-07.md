## Services
One of the biggest challenges of data today is just how much of it is out there.

Data breaches are unfortunately a given.

Your data as a user or consumer is going to get out there.

Your data as a business is highly sought after.

We give out a lot of data.

Phone numbers, government ID numbers, dates of birth, not to mention payment info like credit card and bank account numbers.

As a service provider, you can help to minimize the damage done by data breaches, by just not collecting and storing data.

## Não caia em devaneios
Let's start with the easiest part, don't collect data that you don't need.

It's really tempting to ask users for anything you think you might ever need.

For example, your service might in the future, implement automatic phone calls for suspicious account behavior.

That's a great feature.

But you don't have it yet, and I certainly haven't opted into it yet, so don't ask me for my phone number.

The less data you store, the less can be lost in a successful hacking attempt.

Okay, but that's obvious, right?

What about things you have to have the data?

Like user accounts, you can't really get around storing passwords, right?

Actually you can. There are few common modern ways of avoiding storing user passwords that could get leaked.

The first is social media accounts.

Instead of requiring your users to create a new account on your service and you having to store their password and other account details, you let them sign up with their Facebook, Twitter, GitHub or whatever else account.

You'll store a token that the service provides you instead of a password.

You can usually request other information from the third party service too like email addresses and legal names.

Sometimes you can even ask for that on demand.

This technique is known as OAuth, and it's quickly becoming a common
feature throughout the industry.

Check the teacher's notes on for links to treehouse content on how to take advantage of OAuth for your own projects.

Another alternative is the OpenID technology.

This bit of tech allows people to use their logins from other systems, much like with OAuth.

OpenID relies, as you should have come to expect by now, on a shared secret between the requesting system, your site or service, and the authentication provider.

It's not quite as popular as OAuth, but it's a secure, reliable system.

Isn't that data still vulnerable to a breach though?

I mean if Facebook gets hacked that data is still gonna be out there right?

Sure.

But companies like Facebook have massive teams and massive bank accounts aimed squarely at preventing these breaches.

While they won't always have more protection and security than you do, it's often a good assumption.

There's a theory in the industry too.

That one of the reasons users stick with bad or repeated passwords is because we require them to create so many of them.

It's possible that users will use better passwords if they have to have a few of them.

Services like OAuth and OpenID might lead to this.

The next option is a newer type of service that's been appearing the last few years.

Much like using social media sites for login, services like Octa and Certify let you register and authenticate users without having to
store their details on your own servers.

Again, you're relying on a much more focused company for the security instead of having to divide up your own attention.

Lastly, what about payment details?

I know in the early days of buying things on the Internet it wasn't uncommon to find a service provider or e-commerce shop that would store their customers payment details in their own database.

Often these were stored in plain, unencrypted text too.

The headaches caused by any breach in those databases.

Luckily, now though, services like Stripe, PayPal and Authorize.net all exist and allow you to safely and securely charge people money for your products and services.

Without having to store the the payment details yourself.

In fact, if you did want to store those major credit card details yourself, you must implement PCIDSS, or the Payment Card Industry Data Security Standard.

PCI represents American Express, Discover, JCB, MasterCard and Visa.

There aren't many cards out there that aren't issued by one of those.

Depending on the size of your operation, you may or may not have to have your compliance verified.

I put some information in the teacher's notes about all of these services.

Be sure to read through them if they apply to your projects.

And look for places where you can avoid storing user data.

Now, let's take a look at a feature that's quickly becoming a requirement for messaging software, end-to-end encryption.