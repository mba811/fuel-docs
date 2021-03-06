.. _style-notes-fuel-plugins:

Creating documentation for Fuel Plugins
=======================================

Beginning with Fuel 6.0 release, you can create your own plugin
and validate it.
For the validation procedure, you need to provide Mirantis
with the required package of documentation and the plugin itself.

As to the documentation, it is divided into two blocks:

* Provided for the validation procedure and created in pdf:

  #. Plugin Guide

  #. Test Plan

  #. Test Report.

* Kept in plugin's repo and created in rst and md format accordingly:

  #. Developer's specification

  #. README.md file.

The section below contains style recommendations for creating Plugin Guide.

Plugin Guide
------------

Plugin Guide is targeted at those who would like to
enable the plugin to meet their particular needs.
That means, the Guide must explain the following operations:

* install the plugin

* configure it

* use it.

Structure
+++++++++

Plugin Guide is formed according to the template.
In fact, it consists of four basic parts:

#. Introductory - what functionality does the plugin have,
   what technologues are involved, what are the plugin-specific
   terms, what are the use cases.

#. Installation - how to perform configuration of additional components (for example,
   if the plugin is hardware-specific), how to copy the plugin to the Fuel Master node
   and install it.

#. Configuration - how to configure environment using the Fuel UI wizard and the web UI,
   how to set up plugin itself.

#. Usage - how to use the plugin, what are basic scenarios and actions. It is
   recommended that you wrote these instructions in a very detailed manner
   in user story format. See the nice example in
   `Mirantis blog <https://www.mirantis.com/blog/mirantis-openstack-express-vpn-service-vpnaas-step-step/>`_. To sum up, user story must have a target and a result,
   so that the user would be able to repeat and get the same result
   as described.


Terminology
+++++++++++

#. Explain all complex concepts.
   That means, you should put all terms, acronyms and abbreviations
   into a special table giving a definition with a link to
   third-party resource (if present) or with deabbreviating them.

#. Use terms related to Fuel and Mirantis OpenStack correctly:

   +-------------------+----------------------+
   |  Incorrect usage  |  Correct usage       |
   +===================+======================+
   | Openstack         | OpenStack            |
   +-------------------+----------------------+
   | Mirantis Fuel     | Mirantis OpenStack   |
   |                   | Fuel                 |
   +-------------------+----------------------+
   | Fuel UI           | the Fuel web UI      |
   +-------------------+----------------------+
   | plug-in           | plugin               |
   +-------------------+----------------------+
   | wizard            | the Fuel UI wizard   |
   +-------------------+----------------------+
   | the Fuel-node     | the Fuel Master node |
   | the Fuel master   |                      |
   +-------------------+----------------------+


#. Check if your plugin's name has only
   one writing variant along the text and does not change. For example,
   in case of HA fencing plugin, you can write it either HA fencing or
   HA Fencing, but not use both in the same document.

Links
+++++

#. Put links to third-party documentation.
   For example, if the plugin requires backend configuration,
   then please add a reference.

#. Refer to the
   `official Mirantis OpenStack <https://docs.mirantis.com/fuel/fuel-master/>`_
   or `OpenStack community <http://docs.openstack.org>`_
   documentation when describing standard actions since
   not all users are well acquainted with the platform.
   The following actions can be regarded as standard:
   creating an environment, adding nodes, assigning roles to
   the nodes. This is especially useful when writing about
   actions to perform in the Fuel UI wizard or web UI
   and OpenStack Horizon.

Screenshots
+++++++++++

#. All screenshots should meet their initial purpose:
   provide information on how to work with UI elements.
   That means, they must be of high quality and properly cropped.
   **Correct**:

   .. image:: /_images/user_screen_shots/deploy_env.png

   **Incorrect (black frame is present)**:

   .. image:: /_images/user_screen_shots/style-crop-screen-bad.png

   **Incorrect (it is not clear, in what part of Horizon the user is right now
   because the left-side menu is cropped)**:

   .. image:: /_images/user_screen_shots/style-crop-screen-bad2.png

#. If your plugin works only in a specific Fuel configuration
   (for instance, with Neutron as a Networking Setup), please
   provide a screeenshot with the selected option. For example,
   this plugin works in Neutron with VLAN segmentation setup only.
   To demonstrate this, we should provide the following screenshot:

   .. image:: /_images/user_screen_shots/network-services.png

Lists
+++++

#. Use bullet lists for available options
   user can choose from. For example:
   *The plugin will let you use the Mirantis OpenStack with Cisco SDN solution.
   Four installation options are available:*

   * *Generic APIC ML2 driver*
   * *GBP module and Mapping driver*
   * *GBP module and APIC ML2 driver*
   * *GBP module and APIC GBP driver*

#. Use numerated lists for step-by-step instructions when
   the order is important.
   For example, see
   :ref:`HowTo: Create an XFS disk partition <create-the-XFS-partition>` section
   from Operations Guide.

Describing user's actions and UI elements
+++++++++++++++++++++++++++++++++++++++++

#. Each section should start with an introductory sentence.
   This sentence provides the purpose (why the user should do something):
   *To install HA Fencing plugin, follow these steps:*.

#. When describing action to perform with UI elements
   (for example, in Horizon or in the Fuel web UI), provide
   clear instructions on how to get into specific menu/tab
   and what to do. For example:
   *In the left-hand menu shown in the screenshot below,
   click “Projects” under the “Identity” option, then press “+Create project”
   on the upper-right of the screen.*

#. You should describe all plugin-related UI elements in the Fuel
   web UI like checkboxes, fields and radio buttons. Even if they
   are present in the screenshots, the user should understand,
   when to pick up the specific option using those elements.
   If UI elements contain a drop-down list, then please
   provide a short description for every option.


Formatting
++++++++++

#. Use different formatting techniques for specific content pieces:

   * italic, bold - UI elements, messages or warnings that can be displayed;

   * Consolas-like fonts - commands and their output;

   * colored bold - warnings or notes.

Checklist
+++++++++

Please, before sending out the document
for validation,
use this checklist to verify that it
meets all necessary requirements:

+-----------------------------------------------------+-------------------+
|Issue                                                | Tick if done      |
+=====================================================+===================+
| Plugin version is the same as the one               |                   |
| defined in plugin's *metadata.yaml* file.           |                   |
+-----------------------------------------------------+-------------------+
| Plugin's name stays the same and does not           |                   |
| change within the document.                         |                   |
+-----------------------------------------------------+-------------------+
| All external links are clickable and                |                   |
| lead to the existing pages with actual content.     |                   |
+-----------------------------------------------------+-------------------+
| All screenshots are properly cropped, have high     |                   |
| quality and provide the required information. The   |                   |
| plugin-related UI elements are explained.           |                   |
+-----------------------------------------------------+-------------------+
| All terms and complex concepts are put into         |                   |
| *Key terms, acronyms and abbreviations* table,      |                   |
| even if it goes about IP or UI.                     |                   |
+-----------------------------------------------------+-------------------+
| All commands have correct syntax and can be copied  |                   |
| right into the console from the document.           |                   |
+-----------------------------------------------------+-------------------+
| All steps have right order and the numbered lists   |                   |
| are not mixed up. All lists have the same style     |                   |
| that does not change within the document.           |                   |
+-----------------------------------------------------+-------------------+





