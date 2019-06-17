# video_to_bvh
Convert human motion from video to .bvh with Google Colab

<img alt="" src="https://i.imgur.com/QxML83b.gif" /><img alt="" src="https://i.imgur.com/vfge7DS.gif" />

<img alt="" src=https://i.imgur.com/UvBM1gv.gif />

## Usage
### 1. Open video_to_bvh.ipynb in Google Colab
1. Go to https://colab.research.google.com
2. **```File```** > **```Upload notebook...```** > **```GitHub```** > **```Paste this link:``` https://github.com/Dene33/video_to_bvh/blob/master/video_to_bvh.ipynb**
3. Ensure that **```Runtime```** > **```Change runtime type```** is ```Python 3``` with ```GPU```
### 2. Initial imports, install, initializations
Second step is to install all the required dependencies. Select the first code cell and push ```shift+enter```. You'll see running lines of executing code. Wait until it's done (1-2 minutes).
### 3. Upload video
1. Select the code cell and push ```shift+enter```
2. Push **```select files```** button
3. Select the video you want to process (it should contain only one person, all body parts in frame, long videos will take a lot of time to process)
### 4. Process the video
1. Specify desired ```fps``` rate at which you want to convert video to images. Lower fps = faster processing
2. Select the code cell and push ```shift+enter``` 

This step does all the job: 
1. Convertion of video to images (images are required for pose estimation to work)
2. 2d pose estimation. For each image creates corresponding .json file with 2djoints with format similar to output .json format of original [openpose](https://github.com/CMU-Perceptual-Computing-Lab/openpose/blob/master/doc/output.md). [Fork](https://github.com/Dene33/keras_Realtime_Multi-Person_Pose_Estimation) of [keras_Realtime_Multi-Person_Pose_Estimation](https://github.com/michalfaber/keras_Realtime_Multi-Person_Pose_Estimation) is used.
3. 3d pose estimation. Creates .csv file of all the frames of video with 3d joints coordinates. [Fork](https://github.com/Dene33/hmr) of [End-to-end Recovery of Human Shape and Pose](https://github.com/akanazawa/hmr)
4. Convertion of estimated .csv files to .bvh with help of [custom script](https://github.com/Dene33/hmr/blob/master/csv_to_bvh.py) with [.blend file](https://github.com/Dene33/hmr/blob/master/csv_to_bvh.blend).

### 5. Download .bvh
1. Select the code cell and push ```shift+enter``` .bvh will be saved to your PC.
2. If you want preview it, run [Blender](https://www.blender.org/) on your PC. **```File```** > **```Import```** > **```Motion Capture (.bvh)```** > **```alt+a```**

### 6. Clear all the generated data if you want to process new video
1. Select the code cell and push ```shift+enter```. 
