.. _account:

PCT Account
===========

Percona Cloud Tools (PCT) is a cloud-based service used by many different people.
Each person registers an account that uniquely identifies the user.

The user account is automatically added to a default organization.
You can add other users to your organization or be added to other organizations.
Users within an organization are assigned various roles,
based on the required level of access: *Owner*, *Admin*, *Member*, and *Guest*.

Every organization has a unique API key,
which is used by Percona Agent to identify the data that it collects.
Only members of the organization can view the data collected by this agent.

Creating PCT Account
--------------------

To create a PCT account:

1. Go to `cloud.percona.com <https://cloud.percona.com>`_
#. Enter you first name, last name, e-mail, and password.
#. Select the check box to agree with the *Terms of Service*
   and *Privacy Policy*.
#. Click **Sign Up**.

Your e-mail will be used as your account name.

Managing PCT Account
--------------------

When you log in, click your account name in the top right and select **Manage**.
The following tabs are available:

:Account: In this tab you can set your first name, last name, and time zone.
  You can also delete your account.
:Security: In this tab you can change your account password.
:Organizations: In this tab you can see the organizations
  to which your account is assigned and add other organizations.

.. note:: Every organization has a unique API key.
   You specify it when installing :ref:`agent`.
