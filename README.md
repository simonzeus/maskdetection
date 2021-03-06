# MaskDetection

## What is MaskDetection?
To further help combat the coronavirus, Didi Chuxing decides to open up its face mask detection technology to the public for free. Developed by DiDi AI team, the mask detection technology is based on DFS face detection algorithm and the face attributes recognition algorithm DiDi employs on its platform. 
The model has overcome several difficulties like complex lighting changes in a day, face pose variety, face scales, etc. It uses weighted loss function and data augmentation methods to deal with different mask types and uneven mask data during the day and the night. 

The system can identify non-mask drivers using their uploaded images with 99.5 per cent accuracy, and achieves 98 per cent accuracy during DiDi’s spot inspection with in-vehicle cameras. The model was trained on a dataset of 200,000 faces to ensure its robustness. 

This quick detection system can be widely used in travel scenes, with mobile phone photos, surveillance images etc., and is able to work round the clock.

## Requirements
- google/protobuf
- openblas or atlas
- opencv
- cuda/cudnn(if GPU is used)
- Caffe

## Installation
- Clone the repository. We'll call the directory that you cloned as MASK_ROOT.
```bash
git clone git@github.com:didi/maskdetection.git
```
- Build Caffe,see:http://caffe.berkeleyvision.org

## Usage
In this part, we assume you are in the directory $MASK_ROOT/

- Install requirements (remember the install path to configure CMakeLists.txt)
- Configure CMakeLists.txt、 test/CMakeLists.txt、 lib/CMakeLists.txt
- Compile
```bash
mkdir build
cd build
cmake ..
make
```
- After compilation, executable files will be generated in directory: build/bin
- Detect the face bounding box, and then expand the bounding box to a certain proportion to get a detected face.
- Run executable files with the detected face to judge if the face is wearing mask.

### Tips：
- The detected face bounding box is expanded to reduce the effect of detection errors.
- Each side of the original face bounding box is expanded by 40% for mask detection. The proportion may be adjusted to the actual scenario/context（e.g., reduced to fit the actual scene in case of a dense crowd).

## Model
- Our model is pretrained by public ResNet50-caffemodel.
- Trained by our collected private data.
- Introduce attention mechanism.

# License

<img alt="Apache-2.0 license" src="https://lucene.apache.org/images/mantle-power.png" width="128">

maskdetection is licensed under the terms of the Apache license. See [LICENSE ](LICENSE)for more information.

## Note
DiDi's mask-recognition service is designed to better protect users from public health risks. An attention-learning mechanism is built in the technology to focus on recognizing the existence of a mask while weakening the recognition of other face areas. The service is subject to various sources of error including brightness, posture or partial image capture. We will continue to improve on the accuracy of the technology. Thank you for your support. 
