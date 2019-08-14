# Application Configuration Management System (CMS)
1. Separate configuration from actual code
2. Enforce desired configuration on hundred’s of system at once.
3. Automatically remediate any unexpected changes or configuration drift

| CMS      | Documentation                                      | Tutorial                                                                                             |
|----------|----------------------------------------------------|------------------------------------------------------------------------------------------------------|
| Ansible  | https://docs.ansible.com/ansible/latest/index.html | [ansible]()                                                                                          |
| Puppet   | https://puppet.com/docs                            | [puppet](https://github.com/Ankit-rana/configuration-system-tutorial/blob/master/puppet-tutorial.md) |
| CFENGINE | https://docs.cfengine.com/docs/3.12/               | [cfengine]()                                                                                         |
| Chef     | https://docs.chef.io/                              | [chef]()                                                                                             |

# Architecture
1. agent based pull: Puppet and Chef fall under this. Chef and Puppet install an agent daemon on the hosts to be managed. This daemon is configured to run at specific intervals. There are ways to push to each of these as well but that’s not how they were designed or meant to be used. There’s also masterless mode (at least on Puppet). 
2. agent based push: I wasn’t quite positive how to classify Salt. It’s actually a command executor on a message bus. It is typically ran from the master server with a salt command (state.apply if you have salt/pillar configured with a top.sls file). It’s a bit more flexible than the others because it’s just a command executor on a message bus. It can run masterless as well and comes with a variety of other tools like salt-cloud.
3. non-agent ssh based: For anyone that’s used Ansible, this was obviously Ansible. Ansible connects through SSH and needs no agent. You do have to have a valid login and privileges to perform the commands in your playbook.

![Architecture](http://blog.kwnetapps.com/wp-content/uploads/2017/11/cm-architecture.png)
