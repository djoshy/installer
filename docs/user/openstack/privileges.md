# Required Privileges

In order to succesfully deploy an OpenShift cluster on OpenStack, the user passed to the installer needs a particular set of permissions in a given project. Our recommendation is to create a user in the project that you intend to install your cluster onto with the role *member*. In the event that you want to customize the permissions for a more restricted install, the following use cases can accomodate them.

## Bring Your Own Networks

Using the [bring your own networks feature](https://github.com/openshift/installer/blob/master/docs/user/openstack/customization.md#custom-subnets) will allow you to use already prepared networking infrastructure. As long as you are not using Kuryr, using this feature enables the user to not need permission to create/delete networks, subnets, routers, and router interfaces. However, it will still need to be able to read them, tag them, and create/read/modify/delete ports on a given network and subnet. Note that if you are using Kuryr, you will still need the full set of permissions of the *member* role.

## Floating IP Free Installs

By leaving the `externalNetwork`, `ingressFloatingIP`, and `appsFloatingIP` fields empty, you can run the installer without creating, deleting, or modifying any floating IPs. Running the installer this way does not require you to have any Floating IP Privileges. Once again, this does not apply for Kuryr, and if you are using it you will need the full set of permissions of a typical *member* role.