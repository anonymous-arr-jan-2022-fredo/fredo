# Few-Shot Document-Level Relation Extraction

Preliminary[^1] code for FREDo benchmark (review). 
Documentation will be expanded for final publication.

## Environment Setup
```
python3 -m venv venv
source venv/bin/activate
pip install wheel
pip install -U setuptools
pip install torch==1.8.0+cu111 -f https://download.pytorch.org/whl/torch_stable.html
pip install transformers tqdm wandb
```

## Relevant Code per Section in Paper

### Section 4.3 Test Episode Sampling

Covered by parse_test() in src/data.py (lines 138-324)

Parameters for test sets are found in train.py (lines 72-73)

### Section 5.1.1 Baseline

Covered in src/models/base_model.py
Covered in src/models/dlmnav_sbn.py

Run using:
```
python train.py --query_docs_train 3 --query_docs_eval 3 --support_docs_train 1 --support_docs_eval 1 --model dlmnav+sie+sbn --num_epochs 0
```
### Section 5.1.2 DLMNAV

Covered in src/models/base_model.py
Covered in src/models/dlmnav_sbn.py

Run using:
```
python train.py --query_docs_train 3 --query_docs_eval 3 --support_docs_train 1 --support_docs_eval 1 --model dlmnav
```
### Section 5.1.3 SIE

Covered in src/models/base_model.py
Covered in src/models/dlmnav_sie.py

Run using:
```
python train.py --query_docs_train 3 --query_docs_eval 3 --support_docs_train 1 --support_docs_eval 1 --model dlmnav+sie
```
### Section 5.1.4 SBN

Covered in src/models/base_model.py
Covered in src/models/dlmnav_sbn.py

Run using:
```
python train.py --query_docs_train 3 --query_docs_eval 3 --support_docs_train 1 --support_docs_eval 1 --model dlmnav+sie+sbn
```
### Section 5.2 Sampling Training & Development Episodes

Covered by parse_episodes() in src/data.py (lines 144-324)

Parameters for test sets are found in train.py (lines 70-71)

[^1]: In an effort to improve reproducibility and readability, we have removed code not relevant to the experiments described in the paper. We have further renamed and reorganized code related to models to fit the naming chosen in the paper. While we did perform some tests and did not encounter any problems, we can not say with absolute certainty that we haven't missed something that was broken during this clean up. There will be more tests before the final publication.
