.. |PCT| replace:: :abbr:`PCT (Percona Cloud Tools)`

===========
PCT Account
===========

A :term:`PCT Account` uniquely identifies the :term:`user`.
The following types of accounts are available:

* *Percona Cloud Tools* account is registered as described in
  `Creating PCT Account`_
* `Percona Customer Portal <https://customers.percona.com>`_
  account can be used by current Percona customers
* Your personal or business Google account can also be used

When you sign up for |PCT|,
an :term:`organization` with your name is automatically created.
You can use this default organization to get started,
or you can be added to an existing organization
(for example, your company).

Users within an organization are assigned various roles,
based on the required level of access:

:Owner: The user that created the organization.
  Has full access to all settings,
  can add and remove other users, etc.
:Admin: User with the same level of access as the owner.
:Member: Can add and remove dashboards and charts,
  review queries, configure settings.
  Cannot add or remove users, or change user roles.
:Guest: Can view everything, but cannot change anything.

Every organization has a unique :term:`API key`,
which is used to authenticate and authorize :term:`Percona Agent`.
All members of the organization can view the data collected by the agent
authenticated using the corresponding API key.
No one outside of your organization can view this data.

Creating PCT Account
--------------------

To create a *PCT account*:

1. Go to `cloud.percona.com <https://cloud.percona.com>`_
#. Enter your first name, last name, e-mail, and password.
#. Select the check box to agree with the *Terms of Service*
   and *Privacy Policy*.
#. Click **Sign Up**.

Your e-mail will be used as your account name.
Your first and last name will be used for the default organization.

Managing PCT Account
--------------------

When you log in, click your account name in the top right and select **Manage**.
The following tabs are available:

:Account: In this tab, you can set your first name, last name, and time zone.
  You can also delete your account.
:Security: In this tab, you can change your account password.
:Organizations: In this tab, you can see the organizations
  to which your account is assigned, add and manage other organizations.

.. note:: Every organization has a unique API key.
   You specify it when installing *Percona Agent*.
