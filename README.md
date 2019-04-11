# Image-to-Image-search
* Image-to-Image-search is a reverse image search engine. 
* Search by image: Give it an image and it will return the similar images based on the image captions.
* Uses Deep Learning for Automatic Image Captioning, Elastic search as it's search engine.
* Both Command line as well as Webapp interface provided.

## Demo
[Deep Reverse Image Search Engine - YouTube](https://www.youtube.com/watch?v=xNUL2IHl4tQ)


## Packages Required:
* Anaconda
* Keras with Tensorflow Backend (Python 3.6)
* Elastic Search and elasticsearch-py (Elastic Search 6.0)

## Dataset and Pre-trained models
* [Flickr-8k LSTM weights (flickr8k\_cnn\_lstm\_v1.p)](https://cs.stanford.edu/people/karpathy/neuraltalk/flickr8k_cnn_lstm_v1.zip)
* [Flickr-8k dataset](https://forms.illinois.edu/sec/1713398)

## Output
<img src="webapp.png">

### Files
* `capgen.py` : Takes in the image, produces image captions using LSTM (Long Short Term Memory network) (CLI and Webapp)
* `index.py` : Parses the `static/img/` folder, indexes images and their descriptions in the elastic search server (CLI)
* `query.py` : Given a description, returns nearest description and their image path as JSON response. (CLI)
* `main.py` : Main program, elastic search server must be running before launching this program. (CLI)
* `server.py` : launches the webapp to do the reverse image search (Webapp) 

### Frequently Asked Questions
1. What is dataset.json and how to prepare it?

dataset.json contains information about location of the image as well as caption of the image. As per [custom_index](https://github.com/sethuiyer/Image-to-Image-search/blob/master/custom_index.py), you can index your own image database to the elastic search server by preparing it as follows:

```python
import json
import glob

image_database = glob.glob('/static/img/<your_path_here>') #gets all the image path from the desired folder
dataset_list = []
for image in image_database:
    image.show()
    print 'Enter the description':
    description = input()
    img_data = {}
    img_data['imgurl'] = image
    img_data['description'] = description
    dataset_list.append(img_data)
dataset_json = {}
dataset_json['images'] = dataset_list
json.dump(dataset_json, open('custom_dataset.json','wb')
```

then run `custom_index.py`

2. I am getting Error 404 index not found while uploading the images. 

Before you launch the server.py, make sure the elastic search service is running and index.py is working correctly.

### What you can expect in future versions?
1. Extend the index.py to accomodate custom datasets. :white_check_mark:
2. Make a dashboard through which user can manage their image database.
2. Make a highly scalable REST API which accepts base64 encoding of the image and returns the caption of the image.
3. Make a dashboard through which the training of the captioner could be done on custom datasets.
4. Change the architecture of image captioner in order reduce the memory footprint required by the current pre trained models. 
5. Introduce unit tests and logging to enable smooth debugging.
    
