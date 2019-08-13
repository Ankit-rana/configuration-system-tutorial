# puppet-tutorial 

# Configuration Management System (CMS)
1. Separate configuration from actual code
2. Enforce desired configuration on hundred’s of system at once.
3. Automatically remediate any unexpected changes or configuration drift

# Puppet
1. Puppet have modules
2. Each module have manifests (which define resources). 
    1. A module is a collection of classes, resource types, files, functions and templates, organized around a particular purpose.
    2.  Details: https://puppet.com/docs/puppet/6.7/type.html
3. Module can also have template, spec, files
4. Each manifests define different kind of resource
    1. Class
    2. files
    3. Package
    4. Service
    5. Exec
    6. Group
    7. Notify
    8. Stage
    9. Tidy
    10. User
5. Tutorial (https://programmaticponderings.com/2014/12/14/installing-puppet-master-and-agents-on-multiple-vm-using-vagrant-and-virtualbox/)
    1. Vagrant up
    2. vagrant ssh puppet.example.com. (puppetmaster)
    3. sudo service puppetmaster status  # test that puppet master was installed
    4. sudo service puppetmaster stop
    5. sudo puppet master --verbose --no-daemonize
    6. \# Ctrl+C to kill puppet master
    7. sudo service puppetmaster start
    8. sudo puppet cert list --all # check for 'puppet' cert
    9. Exit
    10. On each agent node, run following
        1. sudo service puppet status # test that agent was installed
        2. sudo puppet agent --test --waitforcert=60 # initiate certificate signing request (CSR)
    11. On master node
        1. Vagrant \# should see 'node01.example.com' cert waiting for signature
        2. sudo puppet cert sign --all # sign the agent node certs
        3. sudo puppet cert list --all # check for signed certs
6. Starting point is /etc/puppet/manifests/site.pp
7. On Restart, certificate gets regenerated
    1. https://puppet.com/docs/puppet/5.5/ssl_regenerate_certificates.html
    2. https://shapeshed.com/connecting-clients-to-a-puppet-master/
