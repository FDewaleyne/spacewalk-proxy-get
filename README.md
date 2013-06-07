spacewalk-proxy-get
===================

*populate spacewalk-proxy bypassing squid for a given package or an entire channel.Search on package is case insensitive*

####Basic usage:
~~~
spacewalk-proxy-get -u admin -p passwd -C your_channel -H 192.168.16.2
 
spacewalk-proxy-get -u admin -p passwd -C your_channel -H 192.168.16.2 -P your_package
~~~ 

wget can also be specified as download helper with `-W`

use -V to check packages before downloading them :

~~~
spacewalk-proxy-get -u admin -p passwd -C a_channel -H 192.168.16.2 -V
~~~

all options can be seen through the -h option

####The spacewalk-clean-customchannel script

*this script is meant to make sure that, in the mesure of the possible, only one source of signature is used for the packages in that channel.*

~~~
Usage: spacewalk-clean-customchannel [options]

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -u USER, --user=USER  User to connect to satellite
  -p PASSWORD, --password=PASSWORD
                        Password to connect to satellite
  -c CHANNEL, --channel=CHANNEL
                        Label of the Channel to parse. Required for most
                        operations
  -H HOST, --host=HOST  Satellite hostname or ip - defaults to 127.0.0.1
  -v, --verbose         Turns up the verbosity
  -l, --list            List all the packages affected
  -a, --auto            Attempts to automatically fix the packages found
  -P PROVIDER, --provider=PROVIDER
                        Name of the provider of the package that we want to
                        find. Required for fixing the content.
  --listproviders       Make the script list the providers defined and exit.
                        only the base org admin can list the providers
~~~

####The spacewalk-add-by-date script

~~~
Usage: spacewalk-add-by-date [options]

Usage: spacewalk-add-by-date [options] This program will clone all erratas and
packages from the source to the destination as long as they are not already
present in the destiation, depending on which settings are used

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -u SATURL, --url=SATURL
                        url or hostname of the satellite to use e.g.
                        http://satellite.example.com/rpc/api
  -l SATUSER, --login=SATUSER
                        User to connect to satellite
  -p SATPWD, --password=SATPWD
                        Password to connect to satellite
  -c DESTCHANNEL, --destChannel=DESTCHANNEL
                        Label of the destination channel to parse. Will be
                        created if doesn't exist
  -s SOURCECHANNEL, --sourceChannel=SOURCECHANNEL
                        Label of the source channel to clone from
  -v, --verbose         Turns up the verbosity by one for each v
  --listChannels        List all the channels
  --listErratas         Lists all the erratas of the source.
  --errataType=ERRATATYPE
                        The type of errata to display - one of 'Security
                        Advisory', 'Product Enhancement Advisory', 'Bug Fix
                        Advisory'
  --maxIssueDate=MAXISSUEDATE
                        Maximum issue date for the erratas and packages to be
                        included (YYYY-MM-DD HH24:MI:SS)
  --maxUpdateDate=MAXUPDATEDATE
                        Maximum update date for the erratas and packages to be
                        included (YYYY-MM-DD H24:MI:SS)
  --onlyErratas         only process erratas
  --onlyPackages        only process packages
  -C, --clean-channel   clean the destination channel before starting
~~~

