Requires Tensorflow installed from source using bazel 
	
Trained model is included in the Graphs folder with the name output_graph.pb

Trained model can be tested using classifyInception.py
	Prints probabilites that each class is in the given image

The retraining script works by removing the top layer off of the pre-trained inception model and training a new layer on specific classes. More classes can be added by placing training images for a class in a folder within the DroneData folder. When classifyInception.py is run, the trained inception model is loaded and a test image is run through the model. The probability for each class is printed to the terminal (between 0 and 1). 

A high certainty for one class will show a high probability for one class and low for the others: 
	class 1: 0.9
	class 2: 0.07
	class 3: 0.03
	
A low certainty for all classes will show as an equal probability for each class
	class 1: 0.45
	class 2: 0.3
	class 3: 0.25
	
Running the model: 
- python classifyInception.py
- File paths must be changed in inceptionModel.py if any changes are made to data locations

Re-Training model:
- Go to root of tensorflow source folder 
- To add a class to train on, add a folder with the name of the new class to the DroneData directory and place all images inside of that new folder
- Building retrainer: bazel build tensorflow/examples/image_retraining:retrain
- Training: bazel-bin/tensorflow/examples/image_retraining/retrain --image_dir ~/ARL/InceptionModel/DroneData  --output_graph ~/ARL/InceptionModel/Graph/output_graph.pb --output_labels ~/ARL/InceptionModel/Labels/output_labels.txt --bottleneck_dir ~/ARL/InceptionModel/bottleneck

