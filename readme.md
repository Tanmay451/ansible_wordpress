# INSTALL WORDPRESS WITH ANSIBLE
## Simple demo to install wordpress in a Debian/ubuntu vm using ansible

If you're getting started with Ansible you need first to read the documentation at the following link: 
http://docs.ansible.com/ansible/intro_getting_started.html

Once you're ready to go there are just a few things to configure:

- In the file *ssh.cfg* modify <SERVER USER> and <PATH TO KEY FILE> with your host configurations,

        Host *
            User ubuntu
            IdentityFile ~/.ssh/my-key.pem
            ControlMaster auto
            ControlPath ~/.ssh/ansible-%r@%h:%p
            ControlPersist 30m
            StrictHostKeyChecking no
      
- In the file *mysql.cfg* choose your db password and use th same in *wpconfig.cfg*, 

        #mysql.cfg
        mySqlRootPassword: 'MY_complex.Pa$$w0rd'
    
        #wpconfig.cfg
        wpConfigDB: define('DB_NAME', 'wordpress');
        wpCondfigUSER: define('DB_USER', 'root');
        wpConfigPassword: define('DB_PASSWORD', 'MY_complex.Pa$$w0rd');
    
- In the *host.ini* modify <YOU HOST IP>,

        [wp-group]
        instance1   ansible_host=54.23.124.76
    
You can go further in editing by creating another user for the DB instead of using 'root' and securing more the installation, 
but this is not the purpose of this simple demo.

###THE PLAYBOOK WAS MADE FOR DEMO PURPOSE ONLY