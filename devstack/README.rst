==========================
Devstack plugin for Calico
==========================

1. Download devstack

2. Add to your devstack local.conf file::

     enable_plugin calico https://github.com/Metaswitch/calico routed

3. Run ``stack.sh``

4. Create a shared, routed network with an IPv4 subnet::

    . openrc admin admin
    neutron net-create --shared --provider:network_type routed calico
    neutron subnet-create --gateway 10.65.0.1 --enable-dhcp --ip-version 4 --name calico-v4 calico 10.65.0/24

5. Launch instances attached to the 'calico' network.

6. Use ``ip route`` to observe per-instance routes created by the Calico agent.

7. Log into each instance (e.g. through Horizon console) and verify
   that it can ping the others.
