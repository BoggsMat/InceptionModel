Requires Tensorflow installed from source using bazel 
	
Trained model is included in the Graphs folder with the name output_graph.pb

Trained model can be tested using classifyInception.py
	Prints probabilites that each class is in the given image

Running the model: 
- python inceptionModel.py
- File paths must be changed in inceptionModel.py if any changes are made to data locations

Re-Training model:
- Go to root of tensorflow source folder 
- bazel build tensorflow/examples/image_retraining:retrain
- bazel-bin/tensorflow/examples/image_retraining/retrain --image_dir ~/ARL/InceptionModel/DroneData  --output_graph ~/ARL/InceptionModel/Graph/output_graph.pb --output_labels ~/ARL/InceptionModel/Labels/output_labels.txt --bottleneck_dir ~/ARL/InceptionModel/bottleneck
