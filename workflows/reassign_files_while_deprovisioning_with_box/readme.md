# Workflows Template: Reassign Files while Deprovisioning with Box

## Overview

This page outlines a workflows template that contains two workflows:

An **Okta Box User - Provision Flow** - starts the flow when user was added to a specific okta group:
- Verify okta group match to an expected one.
- Create an account in Box for user, and create folder for them.
- Send a notification email to the user`s manager.

An **Okta Box User - Deprovision Flow** - starts the flow when user was removed from a specific okta group:
- Verify user was removed from an expected okta group.
- Depending on Remove Box User flag value will remove or deactivate current user and transfer user`s folder and files to their manager.
- Send a notification email to the user`s manager.


## Before you get Started / Prerequisites

For ths template to work you will need:

* An Okta Workflow connector in to your Okta tenant that has Workflows enabled.

* A [Box](http://Box.com) Workflow connector in Workflows.

* An Office 365 Mail connector in Workflows.

* An existing user (that will represent the manager user) in Okta and [Box](http://Box.com) where the username in Okta and in Box are the same (the user`s email address). The manager user's email address needs to point to a valid email address so that the manager can get the email notifications as part of the flow.

* An exiting user (that will represent the target user) in Okta where the manager attribute in Okta Universal Directory is the username of the Okta user that represents the manager.

* An Okta Group that will be used to trigger this Workflow.

* [Optionally]: Federate your [Box](http://Box.com) tenant with your Okta tenant that has Okta Workflows enabled.

* If you do not choose to federate your [Box](http://Box.com) tenant with Okta, you will need to configure a [Box](http://Box.com) application in your Okta tenant that has Okta Workflows enabled configured as Secure Web Authentication.

* DO NOT enable provisioning for the [Box](http://Box.com) application in Okta.

* Add the [Box](http://Box.com) application to the Okta Group that will be used to trigger this Workflow.


## Setup Steps

1. In Workflows find [Templates] button at the top of the page an click on it.

2. Find and select: "Reassign Files while Deprovisioning with Box" flow.

3. Find and click on [Add template] button > and click on  [Add Template] in the  appeared pop-up. A "Reassign Files while Deprovisioning with Box" folder is automatically added and the user is navigated there, once the flow is built.

4. If you have not already done so, authorize the connections to Box, Office 365 Mail, and Okta.

5. Select the Okta Box User - Deprovision Flow Flow from the folder.

6. Change the name of the [Box](http://Box.com) Assignment Group variable to match the Okta group you created in the prerequisites section.

7. If you do not wish to have the target user automatically deleted from your [Box](http://Box.com) tenant, set the Remove Box User variable to False.

8. Save the Okta Box User - Deprovision Flow.

9. Navigate back to the flows in the flow pack.

10. Select the Okta Box User - Provision Flow.

11. Change the name of the [Box](http://Box.com) Assignment Group variable to match the Okta group you created in the prerequisites section.

12. Save the Okta Box User - Provision Flow.

13. Navigate back to the flows in the flow pack.

14. Turn on the following flows:

    *   Okta Box User - Provision Flow
    *   Okta Box User - Deprovision Flow
    *   [UTIL] Send Manager Email Message



## Testing this Flow

To test this template:

[Box](http://Box.com) User Onboarding:

1. Start by adding an existing Okta user to the Okta group that you created as part of the prerequisites section as well as defined in the [Box](http://Box.com) Assignment Group variable in the Okta Box User - Provision Flow.

2. 	Go into your Box tenant and view the users in your Box tenant. You should see the user you added to the Okta group in step 1 added to your [Box](http://Box.com) tenant.

3. 	If you login to Okta as the user that you added to the Okta group specified in step 1 you should see the [Box](http://Box.com) application assigned to them. If you have federated [Box](http://Box.com) to the Okta tenant you should be able to click on the [Box](http://Box.com) chicklet and the user will have Single Sign On into Box.

4. 	The user in [Box](http://Box.com) will have a folder created with their name in [Box](http://Box.com) as well.

5. 	For testing go ahead and put a test text file into the personal folder created for the target user (the one just created) in Box.

6. 	Check the email box for the manager user assigned to the target user. There should be an email message about the box user being created.

[Box](http://Box.com) User Off-boarding:

1. Start by removing the existing Okta target user from the Okta group that you created as part of the prerequisites section as well as defined in the [Box](http://Box.com) Assignment Group variable in the Okta Box User - Deprovision Flow.

2. 	Go to the user's manager email box. You should see an email about the target users files and folders being transferred to the manager user.

3. 	Login to [Box](http://Box.com) as the manager if [Box](http://Box.com) is not federated to Okta,
    If [Box](http://Box.com) is federated to Okta, login to Okta as the manager and click on the [Box](http://Box.com) chicklet to Single Sign On into Box.

4. 	You should see a new folder in that user's manager [Box](http://Box.com) with a format of: [Box](http://Box.com) username of target user full names Files and Folders

5. 	If you selected to have the target users [Box](http://Box.com) account removed, when you view the [Box](http://Box.com) users you should also see that the target user is no longer in the [Box](http://Box.com) tenant.


## Limitations & Known Issues

None