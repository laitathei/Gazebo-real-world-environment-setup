# Setup Hong Kong height map in Gazebo environment with free
### First, use Tangram heightmapper or terrain party to retrive grayscale picture
1. https://terrain.party/
1. https://tangrams.github.io/heightmapper/
#### Usually, the required size in Gazebo is 2*n+1 which n=1,2,3,4....... (For example 257x257,513x513,1025x1025)
#### Please use GIMP or Paint to trim into suitable size
#### Thank for Sarath18 work. We can just gitclone https://github.com/Sarath18/terrain_generator to download Terrain Generator and others things
### Second, change sdf version to 1.5 for different files in terrain_generator package and the desired size with your heightmap in wizard.py line 73 hm_resize = cv2.resize(hm,(129,129)) and size.text in model_gen.py line 53 and 128
#### You can customize your texture file path or autogen_terrain destination path in wizard.py
### Third, type the following command to build your real world environment
```XML
sudo python wizard.py
```
### Next, you should see the following command
```XML
1. Insert Heightmap from disk
2. Insert Heightmap from URL
3. Use Earth's Terrain
Enter your choice:
```
#### According to your requirement to choose 1 , 2 , 3. For me I just try choice 1.
### If you successfully to change into correct path and correct size, you should see the following command
```XML
Enter the location of the heightmap:
```
