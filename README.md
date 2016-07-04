# ansible-swarmkit

Provision Swarmkit clusters with Machine.

1. Source your EC2 credentials (<a href="https://github.com/docker/machine/blob/master/docs/drivers/aws.md">see here</a>)

2. Create a Swarmkit master:

        ansible-playbook aws_provision_master.yml

3. Create any number of other Swarmkit nodes, i.e.:

        for i in `seq 0 5`; do ansible-playbook aws_provision_master.yml; done

4. Use `swarmctl` to ensure that nodes joined the cluster:

        eval $(docker-machine env swarmkit-master)
        docker exec -ti c0946f034c1e swarmctl -s /swarmkitstate/swarmd.sock node ls

Where ***c0946f034c1e*** is the swarmkit container.

5. Enjoy


TODO
====

* Add an overlay network
* Handle AWS docker-machine security group
