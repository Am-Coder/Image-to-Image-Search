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

## Other things which are required
* Flickr-8k LSTM weights (flickr8k\_cnn\_lstm\_v1.p)
* Flickr-8k dataset is required.

## Output
<img src="webapp.png">

### Files
* `capgen.py` : Takes in the image, produces image captions using LSTM (Long Short Term Memory network) (CLI and Webapp)
* `index.py` : Parses the `static/img/` folder, indexes images and their descriptions in the elastic search server (CLI)
* `query.py` : Given a description, returns nearest description and their image path as JSON response. (CLI)
* `main.py` : Main program, elastic search server must be running before launching this program. (CLI)
* `server.py` : launches the webapp to do the reverse image search (Webapp)

### What you can expect in future versions?
1. Extend the index.py to accomodate custom datasets.
2. Make a highly scalable REST API which accepts base64 encoding of the image and returns the caption of the image.
3. Make a dashboard through which the training of the captioner could be done on custom datasets.
4. Change the architecture of image captioner in order reduce the memory footprint required by the current pre trained models. 
5. Introduce unit tests and logging to enable smooth debugging.
