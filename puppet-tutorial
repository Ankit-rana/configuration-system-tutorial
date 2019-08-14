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
    1. Stop the Puppet agent service. On *nix nodes, run 
    ```
                           sudo puppet resource service puppet ensure=stopped. 
    ```
    2. Locate Puppet’s SSL directory and delete everything in it.
    The SSL directory should be at /etc/puppetlabs/puppet/ssl or C:\ProgramData\PuppetLabs\puppet\etc\ssl.

    3. Re-start the Puppet agent service. On *nix nodes, run 
    ```
                           sudo puppet resource service puppet ensure=running.
    ```
    4. Once the Puppet agent starts, it will automatically generate keys and request a new certificate from the CA Puppet   master.
    5. If you are not using autosigning, you will need to sign each agent node’s certificate request. You can do this by        logging into the CA Puppet master server, running 
    ```
                           sudo puppet cert list 
    ```
    to see pending requests, and run 
    ```
                           sudo puppet cert sign <NAME> 
    ```
    to sign requests.
