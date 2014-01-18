This guide with allow you to complete the following on Ubuntu 13.

----------------------------------------------------------------------


- Install Deluged 1.3.6
- Install Deluge-web 1.3.6
- Install LibTorrent 0.16.13.0 with Proxy UDP fix included


----------------------------------------------------------------------
----------------------------------------------------------------------
Step 1. Install required dependencies for the above applications.


apt-get install python-libtorrent python-libtorrent libboost-dev libboost-test-dev libboost-program-options-dev libevent-dev automake libtool flex bison pkg-config g++ libssl-dev


----------------------------------------------------------------------
Step 2. Download the LibTorrent-rasterbar files from the following Google Code location.

https://libtorrent.googlecode.com/files/

Note: For me this was libtorrent-rasterbar-0.16.13.tar.gz as it was the latest version.


----------------------------------------------------------------------
Step 3. Extract the LibTorrent-rasterbar files.

tar xfv libtorrent-rasterbar-0.16.13.tar.gz


----------------------------------------------------------------------
Step 4. Move into the directory and start the configuration process on the source files.

cd libtorrent-rasterbar-0.16.13/
./configure --enable-python-binding


----------------------------------------------------------------------
Step 5. Make the package, and complete the installation.

make
make install


----------------------------------------------------------------------
Step 6. Build and install the Python files.

cd bindings/python/
python setup.py build
python setup.py install


----------------------------------------------------------------------
Step 7. UpdateDB and locate the libtorrent-rasterbar install location.

updatedb
locate libtorrent-rasterbar.so.*


----------------------------------------------------------------------
Step 8. Update the export location to allow Python to install it.

export LD_LIBRARY_PATH=/<path_to_directory>/ <-- This is found with the above locate command.

For me it was the below.

export LD_LIBRARY_PATH=/usr/local/lib/


----------------------------------------------------------------------
Step 9. Start Python and import libtorrent

python
>> import libtorrent


----------------------------------------------------------------------
Step 10. Check if its now installed and available.

python -c "import libtorrent as lt; print lt.version"


----------------------------------------------------------------------
Step 11. Install deluged and deluge-web

apt get deluged deluge-web


----------------------------------------------------------------------
Step 12. Check its detecting the correct version of LibTorrent

deluge-web --version
deluged --version


----------------------------------------------------------------------

You are now done, try and visit your deluge front end and enable proxy and test the download of the torrent files.
