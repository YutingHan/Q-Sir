# Q-Sir
Weblink: https://yutinghan.github.io/Q-Sir/

Video: [Presentation](Q-Sir/Presentation.mp4)


## Project Overview

Q-SIR is a Question answering Service Improvement and Redesign project that provides a tool to answer questions using Artificial Intelligence to achieve human-level accuracy in rapid progress. According to the comprehensive dataset we choose, SQuAD, Q-SIR could answer most of the questions in diverse fields, and we could see it as an advanced automatic encyclopedic. 
Based on its powerful functions, it not only could be set as a chatbot in social media but also could be embedded in existing domestic robots, contributing to smart living home. 
In this project, in order to do some research, we compare the results of two models, which are BERT and XLNET.


## Dataset Description

The SQuAD is a reading comprehension dataset consisting of questions posted by crowdworkers on a set of Wikipedia articles. The reason why we use SQuAD is that it’s in diverse fields. The answer to every question is a segment of text, or span, from the corresponding reading passage, or the question might be unanswerable. 
 
SQuAD2.0 combines the 100,000 questions in SQuAD1.1 with over 50,000 unanswerable questions written adversarially by crowdworkers to look similar to answerable ones. 
 
The format of the data is a json format. 

## HomePage
![HomePage](/media/homePage.png)


## ResultPage
![ResultPage](/media/resultPage.gif)


## Model 

BERT relies on transformers. A basic Transformer consists of an encoder that reads text input and a decoder that predicts the task. Since the goal of BERT is to generate language representation models, only the encoder part is needed. The transformer encoder reads the entire word sequence at once. This is the opposite of the previous work, which is to view the text sequence from left to right or from left to right and right to left.

![BERT](/media/BERT.png)

XLNet is an automatic regression language model based on recursive converter architecture, which outputs the joint probability of token sequences. Its training target calculates the probability of word tags. This condition depends on all permutations of word tags in a sentence, which is the opposite of tags that are only on the left or right of the target tag.

![XLNet](/media/XLNet.png)


Dependency
------
```shell
pip install 'tensorflow-gpu >= 1.11.0'
```


Procedure
------
```shell
python run_squad.py \
  --vocab_file=$BERT_LARGE_DIR/vocab.txt \
  --bert_config_file=$BERT_LARGE_DIR/bert_config.json \
  --init_checkpoint=$BERT_LARGE_DIR/bert_model.ckpt \
  --do_train=True \
  --train_file=$SQUAD_DIR/train-v2.0.json \
  --do_predict=True \
  --predict_file=$SQUAD_DIR/dev-v2.0.json \
  --train_batch_size=24 \
  --learning_rate=3e-5 \
  --num_train_epochs=2.0 \
  --max_seq_length=384 \
  --doc_stride=128 \
  --version_2_with_negative=True
  --output_dir=gs://some_bucket/squad_large/ \
```


Model Result
------
- [BERT](model_result/BERT_result.json)
- [XLNet](model_result/XLNet_result.json)


Reference
------
- Data: https://rajpurkar.github.io/SQuAD-explorer/
- Model - Bert: https://github.com/google-research/bert
- Model - XLNet: https://github.com/zihangdai/xlnet
