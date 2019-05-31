## Access control
Outside of hashing, encryption and general privacy, it's best to think about who has access to what pieces of your data.

It seems like a really easy topic, but it's one that often requires a lot more thought than you might have expected.

Let's start at the beginning, you have users and they have accounts that they can log into, but how do they do that logging in?

This process, known as authentication, can have a lot of different implementations.

It could be done through a standard log in form, where they enter a user name or e-mail address and a password.

They can be logging in through a third-party site, like Facebook or Octa.

Or maybe you authenticate users against an internal service, like LDAP, which allows for an internal collection of user names and passwords, like you might find on a LAN or intranet.

This is a good place to talk about two factor authentication.

You've probably heard of this, and likely even used it.

But if you haven't, here's the general idea.

You log into a service with your username and password.

That service then expects a time sensitive code from you, that you get through either a code generator, like Google's authenticator app, or by SMS.

There's an old adage about authentication that should require three things.

Something you are, something you have and something you know.

Two factor auth covers as you might expect, two of these things.

There's something you know, is your password.

There's something you have, is your phone or device that gives you
the two factor auth code.

If you get your code from your phone and your phone requires a finger print to access it, that could fulfill the third requirement something you are.

There are also modern devices like UB key that uses a bio-metric print like your thumb print to generate a two factor off code, some systems even use other bio-metric items like voice or face recognition too but the security of these systems is still in flex.

Okay, so there are authenticated, logged in.

Now comes the second consideration in this arena, authorization.

Now that you know who the user is, what are they allowed to do and see?

For example, once you log into your Google account, you're only allowed to see the documents you have created in Google Docs or those that have been explicitly shared with you.

Two modern solutions to this are database based access control lists, or ACLs, and role based access control, or RBAC.

These two systems assign users different access levels or roles, and then based on the level or role, determine if the user can access a given object or area.

Roles simply define access in a way that lets you assign one or more roles to a specific user.

This allows you to control access for groups or teams in a more organized way, rather than having to explicitly define every single thing an individual needs to access.

When working with OAuth authentication services, the authorization information that you receive about a particular user is expressed as a set of claims.

A claim can be a role these are belongs to, a resource they can access, or an action they can perform.

Probably the most common ACL that most people encounter is the granting of privileges and a database like Postgrass or MySQL.

You grant read, write, or both accesses to particular user or role on a particular table, tables, or databases, ensuring that your database users only have privileges on tables that they need access to, is one of the first steps you can take on ensuring that data.

Obviously the implementation of such a system is beyond the scope of this course but their common components and many modern day frameworks and CMSs.

Using and enforcing SCL and RBAC systems, helps to minimize the damage that can happen when a single account is compromised.

If the account doesn't have access to all of your data and really what account should?

The damage done should be constrained to just what the compromised account has access to, if you're using such a system, be sure to do an audit

of your user accounts, roles, and what each has access to.

It's rare that any one account should have total and complete access to all of your data.