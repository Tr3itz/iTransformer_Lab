# iTransformer Lab
Repository for Statistical Learning laboratory on **iTransformer**. This is a shortened version of the [original repository](https://github.com/thuml/iTransformer) focusing only on the implementation of the iTransformer architecture.

# Dataset
In the folder `dataset` you can find 4 `.csv` files, which are 4 variants of the of the **Electricity Transformer Temperature** dataset (**ETT**).

## Description
Datasets contain observations of two Electricity Transformers at two different stations in China. Depending on the variant, you will find two different granularities of observations:
* _hourly_ observations for `ETTh1.csv` and `ETTh2.csv`
* _minute by minute_ observations for `ETTm1.csv` and `ETTm2.csv`

For hourly-level files there are a total of 17,420 observations, while for minute by minute files thre are 69,680 observations.

# Setup
1. Install [miniconda](https://www.anaconda.com/docs/getting-started/miniconda/install#quickstart-install-instructions)
2. Create and activate a conda environment:
   ```console
   conda create -n itransformer python==3.11 -y
   conda activate itransformer
   ```
3. Install requirements:
   ```console
   pip install -r requirements.txt
   ```

# Experiments
In the folder `./scripts` you can find a series of bash scripts for performing experiments. 

## Launch bash scripts
In order to launch an experiment, run the following commands from the terminal in the main direcory:
```console
chmod +x scripts/<script_to_launch>.sh # you may need to give permissions to the file for being executed
bash scripts/<script_to_launch>.sh
```

For example, suppose you want to run an experiment on the variant `h1` of the `ETT` dataset:
```console
chmod +x scripts/iTransformers_ETTh1.sh
bash ./scripts/iTransformers_ETTh1.sh
```

## Launch with Python
If you want to run one single experiment on a dataset, you can also run directly the python script `run.py` tuning the configurations to pass as arguments. For example, in order to run the same epxperiment as above:
```console
python -u run.py \
  --is_training 1 \
  --root_path ./dataset/ \
  --data_path ETTh1.csv \
  --model_id ETTh1_96_96 \
  --model iTransformer \
  --data ETTh1 \
  --features M \
  --seq_len 192 \
  --pred_len 96 \
  --e_layers 2 \
  --enc_in 7 \
  --dec_in 7 \
  --c_out 7 \
  --des 'Exp' \
  --d_model 256 \
  --d_ff 256 \
  --itr 1
```

The list of all the arguments and their meanings can be found within the script `run.py`.