# Cone detection using YOLOv2

 > ## Approach
  1) ##### Data collection
  		1) Created a [dataset of ~300](https://drive.google.com/drive/folders/1GKAPXpw4lRAy_a3nn1UtU1FfNdwT2IfR?usp=sharing) manually annotated instances of all the 5 colors of traffic cones
        
  2) ##### Setup my the environment in ubuntu to make ros node 
  		1) Had a lot of trouble with the setup. Thanks for the heads up about the ROS source and Py3   
     2) After trying [yolov3](https://github.com/bsridatta/kthfsdv-Perception-Interview/blob/master/Yolo.py) ,darknet, I decided darkflow was the best way
  
  3) ##### Detection without cones - Getting the basics right
      1) Object detection with darkflow. 
      
      ![output](https://github.com/bsridatta/kthfsdv-Perception-Interview/blob/master/darkflow.png)
      
      Check [output/code](https://github.com/bsridatta/kthfsdv-Perception-Interview/blob/master/py2%20Darkflow.ipynb) here
     
      2) Object detection in video 
     
      ![video]("https://github.com/bsridatta/kthfsdv-Perception-Interview/blob/master/video.avi")

  4) ##### Training the  model on my "CPU" laptop ( Not my first time ) 
  	
    	1) I trained 200 videos on my laptop in windows in couple of hours but in after changing to ubuntu for this training program,  the epoch per hour for these 'image' dataset is so high. 
  		2) Found [pretrained weights](https://github.com/melfm/dukecone) but no config file. Morphed many configs and experimented, no use.
   
   5) ##### Turning to Google colabs  
      	1) Redone the entire setup again [My colab GPU env.](https://drive.google.com/drive/folders/1r6yw32bb-H6Xb52tpjTJ5JJeXERog_dN?usp=sharing) Entire darkflow, dataset, models and configurations in the above link. (Note : Not fully functoning) 
   		2) #### Got struck training in colab due to format/access errors raised by google drive. Still fiddling with it....   
  
  .and so on but unfortunately could not go any further 
  
  > ## Future Work
  1) Ill try to get it to work. Darkflow is meant to work for py3 but i discovered it works well for py2 also. So hopefully it doesnt conflict with ROS
  
  > ## Update after the deadline
  
  1) Editing out all the conflicts Darkflow had with GDrive and hardcoded the classes and model config. It kind of worked. 
      1) model - tiny yolo
      2) training- 300 images
      3) epoch -100,200 - 5k , 10k steps
      4) convergence - ~1
      5) GPU- Tesla 180 - colabs
      6) FPS- 4 on gpu
  and trained on tiny yolo architecture with ~200 epoch- 10k steps for 5 hours on tesla GPU in colab. Checkpoints however werent stored (didnt even prompt an error) after 5000 steps. Testing on the video provided at a speed of 4 FPS on a CPU. And the result looked something like this. 
     ![cones](https://github.com/bsridatta/kthfsdv-Perception-Interview/blob/master/conesDetection.png)
     and whole video is ![here](https://github.com/bsridatta/kthfsdv-Perception-Interview/blob/master/testVideo.avi). It detects blueCones pretty well but not white. Intrestingly I provided more orange samples than the blues
     
     
     
