## How to add user to OpenStack 


###### **List all users in openstack**
List all users under domain default

```openstack user list --domain default```

###### **Create user in Openstack**
Create user with name bala under default domain

```openstack user create --domain default --password-prompt bala```

###### **Show recently created user**
Show created user

```openstack user show bala```

###### **Add role to user**
Add role "admin" to user "bala"

```openstack role add admin --project default --user bala```

###### **Add role to project**
Add role "admin" to project "default"

```openstack role add --project default --user bala admin```


Source: http://docs.openstack.org/mitaka/install-guide-obs/keystone-users.html
