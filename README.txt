Requires Tensorflow installed from source using bazel 
	
Trained model is included in the Graphs folder with the name output_graph.pb

Trained model can be tested using classifyInception.py
	Prints probabilites that each class is in the given image

Running the model: 
- python classifyInception.py
- File paths must be changed in inceptionModel.py if any changes are made to data locations

Re-Training model:
- Go to root of tensorflow source folder 
- To add a class to train on, add a folder with the name of the new class to the DroneData directory and place all images inside of that new folder
- Building retrainer: bazel build tensorflow/examples/image_retraining:retrain
- Training: bazel-bin/tensorflow/examples/image_retraining/retrain --image_dir ~/ARL/InceptionModel/DroneData  --output_graph ~/ARL/InceptionModel/Graph/output_graph.pb --output_labels ~/ARL/InceptionModel/Labels/output_labels.txt --bottleneck_dir ~/ARL/InceptionModel/bottleneck

