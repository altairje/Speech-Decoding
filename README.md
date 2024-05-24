# Brain-to-Text  
***This repository was created for DL course in skoltech 2024***

## Team 1
1. Adithya Shetty
2. Aibek Akhmetkazy
3. Altair Toleugazinov
4. Daniyal Asif
5. Sergey Smetankin


![Screenshot of a comment on a GitHub issue showing an image, added in the Markdown, of an Octocat smiling and raising a tentacle.](https://legendary-digital-network-assets.s3.amazonaws.com/wp-content/uploads/2022/05/09122423/Patrick-Stewart-as-Professor-X-.jpeg)



# Project description

![proj description](https://raw.githubusercontent.com/fwillett/speechBCI/main/SystemDiagram.png)

Our project is related to Kaggle challenge ["Brain-to-Text Benchmark '24"](https://eval.ai/web/challenges/challenge-page/2099/overview)

Link for [dataset](https://datadryad.org/stash/dataset/doi:10.5061/dryad.x69p8czpq)

This competition asks participants to solve a problem that borders on the fantastic -- to teach a computer to translate human thoughts into text. More specifically, the challenge is to train a neural network to decode the data coming from the EEG and convert it into sentences.

## Data structure 
During neurobiological experiments neural activity was recorded with microelectrode arrays, and neural features are provided in the form of binned threshold crossings and spike band power (20 ms bins).

This dataset contains all of the neural activity recorded during these experiments, consisting of 12,100 spoken sentences as well as instructed delay experiments designed to investigate the neural representation of orofacial movement and speech production.

The data have also been formatted for developing and evaluating machine learning decoding methods, and we intend to host a decoding competition based on this data.

**"competitionData"** is a simplified version of the sentences data that has been formatted and partitioned for machine learning research. It contains a "train" and "test" partition for model development, and a held-out "competitionHoldOut" set intended for a speech decoding competition.

Useful information for us is contained in the following fields of this data:

**sentenceText**: S x C character matrix containing the text of each sentence (S = number of sentences, C = maximum number of characters across all sentences included in sentenceText). 

**spikePow** : S x 1 vector containing a time series of spike power neural features for each sentence (S = number of sentences). Each entry is a T x F matrix of binned spike band power (20 ms bins), where T = number of time steps in the sentence and F = number of channels (256). Spike band power was defined as the mean of the squared voltages observed on the channel after high-pass filtering (250 Hz cutoff; units of microvolts squared). The data was denoised with a linear regression reference technique. The channels correspond to the arrays as follows (where 000 refers to the first column of spikePow and 255 refers to the last).

**tx1** : S x 1 vector containing a time series of threshold crossing neural features for each sentence (S = number of sentences). Each entry is a T x F matrix of binned threshold crossing counts (20 ms bins), where T = number of time steps in the sentence and F = number of channels (256). The data was denoised with a linear regression reference technique and a -3.5 x RMS threshold was used. The channels correspond to the arrays in the same way as spikePow described above. Note that threshold crossing counts describe the number of times the voltage recorded on an electrode crossed a threshold within a given time bin (essentially, this roughly counts the number of nearby action potentials observed on an elctrode in a given time bin). 

**tx2** : Same as tx1 but with a -4.5 x RMS threshold.

**tx3** : Same as tx1 but with a -5.5 x RMS threshold.

**tx4** : Same as tx1 but with a -6.5 x RMS threshold.

# Our solutions

1. [***Encoder-decoder Sec2Sec model + attention***]( https://ethen8181.github.io/machine-learning/deep_learning/seq2seq/2_torch_seq2seq_attention.html#Seq2Seq), [link_2](https://www.kaggle.com/code/isikkuntay/gru-with-attention), but since our data is Time x Channels -- matrix with shape (t,256) this model were modified by adding convolutional layers to reduse dimension to (t,1). This model was chosen in attempt to take more information from timeseries data. Attention mechanism should (in theory) help to take into account different part of the data since people think words in their entirety.
