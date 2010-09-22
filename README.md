# Development MacPorts

MacPorts makes it easy for me to keep the mac boxes in my office in sync - more ore less pain free.
You're welcome to give my Portfiles a try. But remember that these are unofficial. 
I won't update Portfiles that made it into the offical Portfile trunk (unless there's a really good reason for it).

## Some Quickies on MacPorts

Original Ports: /opt/local/var/macports/sources/rsync.macports.org/release/ports/
Portfile-Documentation: http://guide.macports.org/#development.creating-portfile

## Local Portfile Repository

### Register

1. open /opt/local/etc/macports/sources.conf
2. add file:///path/to/your/ports [nosync]
3. save

### Update

1. cd /path/to/your/ports
2. sudo portindex

## Go Sphinx Go

So you're interested in Sphinx but can't get it up and running? 
Given you already have git and MacPorts (with at least php5) installed, you could try this:

<pre><code>
# switch to superuser (for convinience only)
sudo -i

# specify the directory for the ports
PORTS_REPO=/opt/ports/rodneyrehm/

# get this repo
git clone git://github.com/rodneyrehm/MacPorts.git $PORTS_REPO

# prepend the PORTS_REPO path to macport sources
echo "\nfile://$PORTS_REPO [nosync]\n" > /tmp/sources.conf
cat /opt/local/etc/macports/sources.conf >> /tmp/sources.conf
mv /opt/local/etc/macports/sources.conf /opt/local/etc/macports/sources.conf.bak
mv /tmp/sources.conf /opt/local/etc/macports/sources.conf

# switch to the new Portfile repository
cd $PORTS_REPO

# run Portfile indexer
portindex

# switch back to actual user
exit

# install sphinx, libsphinxclient and pecl sphinx via MacPorts 
sudo port install sphinx sphinx-client php5-sphinx  
</code></pre>