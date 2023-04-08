# GDL-Project-Network
TransUNet code adapted for the GDL project including code to generate different embedding methods. Also added early stopping to the training and a training resume function as well as a naming option for the experiments.

The code to change between the different embedding methods is found in the networks/vit_seg_modeling.py file in the embeddings section.

### 1. Get the pretrained weights by doing:

* [Get models in this link](https://console.cloud.google.com/storage/vit_models/): R50-ViT-B_16, ViT-B_16, ViT-L_16...
```bash
wget https://storage.googleapis.com/vit_models/imagenet21k/{MODEL_NAME}.npz &&
mkdir ../model/vit_checkpoint/imagenet21k &&
mv {MODEL_NAME}.npz ../model/vit_checkpoint/imagenet21k/{MODEL_NAME}.npz
```

### 2. Prepare data:

Please go to ["./datasets/README.md"](datasets/README.md) for details

### 3. Environment

python=3.7, and then use "pip install -r requirements.txt"

### 4. Train/Test

- Run the train script on synapse dataset. Add the '--resume' flag to continue training from best weights

```bash
CUDA_VISIBLE_DEVICES=0 python train.py --dataset Synapse --vit_name R50-ViT-B_16 --name 'experiment_name'
```

- Run the test script on synapse dataset

```bash
python test.py --dataset Synapse --vit_name R50-ViT-B_16 --name 'experiment_name'
```
