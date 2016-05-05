---
layout: post
title: Securing CouchDB
categories: 
- tech
- couchdb
- security
description: guide to securing a CouchDB instance
keywords: couchdb,security,securing,howto,guide,database,couch,securing couchdb,couchdb security
---

Most CouchDB instances are run locally, behind the firewall where security is less of an issue

However if you want to allow the public read-only access to the database (or if you've grabbed yourself a hosted account at [Couchio](http://www.couch.io/get)) security settings are far more important

(Instructions here good for CouchDB v 1.0.0)

### Create the first admin account

By default a new instance of CouchDB runs in Admin Party mode - until the first admin account is created, everyone's an admin. Once that first account has been created, anyone who's not logged in will be treated as public and will no longer be able to create users or create and destroy databases

1. Launch Futon, look for the "Welcome to Admin Party!" text down in the bottom right and click on "Fix this"  
  <img src="images/couch-admin-link.gif" alt="screenshot detail showing the 'Fix this' link in Futon" width="215" height="87" />
1. Submit an admin username and password for your server admin account at the prompt

From this point on, all other security settings have to be carried out on a per-database basis

### Secure the users database

Now you have an admin account, you'll want to protect it as much as possible. Although the password is encrypted and safely stored away from prying eyes, until you take action the account name is still visible

1. Go into the _users database and click on the "Security" link at the top of the page
1. In the popup dialog that appears, change the Readers Roles to *["admin"]*  
  <img src="images/couch-security-panel1.gif" alt="screenshot of the CouchDB security dialog" width="443" height="360"/>  
  Now only admin users can access the _users database and, if you were quick enough, you're the only person who knows what your admin account is called

### Making a database read-only

This is a little more tricky - if you ban public users from reading the database, they won't be able to access the data; if you leave it open, there's nothing to stop someone from breaking it

1. Create your new database
1. Go into the new database and click on the "Security" link at the top of the page
1. In the popup dialog, change the Admins Roles to *["admin"]*  
  <img src="images/couch-security-panel2.gif" alt="screenshot of the CouchDB security dialog" width="443" height="360"/>  
  You have now stopped unauthorised users from accessing this security panel or messing with your design documents. At this stage there is still nothing to prevent them from adding, deleting or altering the data itself
1. To control access at a document (read: record in SQL-speak) level, CouchDB uses a special function called validate_doc_update which runs every time a document is altered. To make one, create a new design document and set the <code>_id</code> field to `_design/auth`
1. Add a field called `language` and set the value to `javascript`
1. Add a field called `validate_doc_update` and add the following text:

{% gist 490482 CouchDB%20security%20-%20prevent%20non-admins%20from%20editing %}

And that should be it. Log out and do a few quick tests to make sure everything's working as expected.