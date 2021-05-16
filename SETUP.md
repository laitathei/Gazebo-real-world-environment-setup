# Gazebo-real-world-environment-setup

### Create real world DEM environment
#### First, install GDAL libraries which is the only one supported formats in Gazebo
```XML
sudo apt-get install gdal-bin libgdal-dev python-gdal
```
#### Second, download the required materials
```XML
cd ~/Downloads
wget https://github.com/osrf/gazebo_tutorials/raw/master/dem/files/mtsthelens_before.zip
unzip ~/Downloads/mtsthelens_before.zip -d /tmp
mv /tmp/30.1.1.128760.dem /tmp/mtsthelens.dem
mkdir -p /tmp/media/dem/
gdalwarp -ts 129 129 /tmp/mtsthelens.dem /tmp/media/dem/mtsthelens_129.dem
```
#### Third, build up the volcano.world file in /tmp directory
```XML
cd ~/Downloads
wget https://github.com/osrf/gazebo_tutorials/raw/master/dem/files/mtsthelens_before.zip
unzip ~/Downloads/mtsthelens_before.zip -d /tmp
mv /tmp/30.1.1.128760.dem /tmp/mtsthelens.dem
mkdir -p /tmp/media/dem/
gdalwarp -ts 129 129 /tmp/mtsthelens.dem /tmp/media/dem/mtsthelens_129.dem
```
#### Finally, change the source path and simulate the world files
```XML
source /usr/share/gazebo-9/setup.sh
GAZEBO_RESOURCE_PATH="$GAZEBO_RESOURCE_PATH:/tmp" gazebo /tmp/volcano.world
```
#### If if cannot shown the environment and show following error
```XML
gzclient: /build/ogre-1.9-B6QkmW/ogre-1.9-1.9.0+dfsg1/OgreMain/include/OgreAxisAlignedBox.h:252: void Ogre::AxisAlignedBox::setExtents(const Ogre::Vector3&, const Ogre::Vector3&): Assertion (min.x <= max.x && min.y <= max.y && min.z <= max.z) && "The minimum corner of the box must be less than or equal to maximum corner" failed
```
#### The error caused by NO_PUBKEY which means the public key is not available
#### type following command to find out the NO_PUBKEY
```XML
sudo apt-get update
```
#### After find out the NO_PUBKEY, type following command and replace xxx with your NO_PUBKEY
```XML
sudo apt-key adv -- keyserver keyserver.ubuntu.com --recv-keys xxx
sudo apt-get update
sudo apt-get upgrade
```
