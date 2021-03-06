What To Do When a Test Fails
----------------------------

If a test fails, there are several ways to investigate the problem. You may
prefer to start in Fuel UI, since its feedback is directly related to the
health of the deployment. To do so, start by checking the following:

* Under the `Health Check` tab
* In the OpenStack Dashboard
* In the test execution logs (in Environment Logs)
* In the individual OpenStack components' logs

Certainly there are many different conditions that can lead to system
breakdowns, but there are some simple items that can be examined before you
start digging deeply. The most common issues include:

* Not all OpenStack services are running
* Some defined quota has been exceeded
* Something has broken in the network configuration
* A general lack of resources (memory/disk space)

The first thing to be done is to ensure all OpenStack services are up and
running. To do this, you can run the sanity test set or execute the following
command on your Controller node::

  nova-manage service list

If any service is off (has “XXX” status), you can restart it using this command::

  service openstack-<service name> restart

If all services are on, but you`re still experiencing some issues, you can
gather information from OpenStack Dashboard (exceeded number of instances,
fixed IPs, etc). You may also read the logs generated by tests which are
stored in Logs -> Fuel Master -> Health Check and check if any operation is
in ERROR status. If it looks like the last item, you may have underprovisioned
our environment and should check your math and your project requirements.

