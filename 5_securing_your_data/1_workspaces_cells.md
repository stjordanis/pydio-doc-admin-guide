If you went through the [Quick Admin Tour](./quick-admin-tour), you should already be familiar with the Workspaces concept. Basically a pointer to anywhere in the global tree aggregated by all Data Sources, they define the basic units to grant or restrict permissions, but also customize actions in the interface. These feature will be described in the next sections.

This section will go through the advanced features of Workspaces and explain the difference with 'Cells'.

### Workspaces as a way to organize your data

Workspaces provide a very flexible way to organize your data, depending on who will access to it. It is important to spend some time to define them properly. This is generally a good opportunity for looking at the existing datasets and clean/reorganize them. 

#### Typical layouts

In a typical company setup workspaces will often be organized by business units : 

[:image:5_securing_your_data/workspaces-layouts.png]

Other will define a per-region organization

- America
- Europe - Middle East
- Asia
- Africa
- etc... 

Up to you. 

#### Multiple Paths workspace

To define a workspace, one must point to at least one location in the DataSources tree. It is interesting to note that you can also compose a workspace from multiple locations. You can that way aggregate various data from various datasources into one unique workspace.

### Cells : sandboxed workspaces for the users

As described in the [Sharing Features](./sharing-features) section, Cells are a simple way for users to share data with other users, either by opening them partial access to their personal data, or by creating cells from scratch to start collaborating in a fresh folder. 

In fact, Cells are more or less "just workspaces" that can be managed by users, whereas only administrators can manage workspaces. They have the same abilities for aggregating data with multiple paths. Users can create cells based on an existing folders and later on share more data into that same Cells. 

Difference is subtle but important. Workspaces are created by administrators, they are fixed and come with a set of predefined authorizations or restrictions : these rules are always inherited by the Cells created inside those workspaces. As such, Cells provide the flexibility and power of workspaces, empowering your users, while still keeping the data secure and under control.

------
_See Also_

- [Creating a simple workspace in the Quick Admin Tour](./quick-admin-tour)
- [Datasources overview](./datasources-overview)
- [Assigning workspaces accesses via Users, Groups and Roles](./users-roles-and-groups)