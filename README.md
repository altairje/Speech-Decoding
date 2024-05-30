<h1 align="center">Brain-to-Text: Neural Decoding Challenge</h1>

<p align="center">
  <strong>Team: Team 1</strong>
</p>

<p align="center">
  <a href="#project-overview">Overview</a> •
  <a href="#repository-structure">Repository</a> •
  <a href="#datasets">Datasets</a> •
  <a href="#approach">Approach</a> •
  <a href="#results--insights">Results</a> •
  <a href="#conclusion">Conclusion</a> •
  <a href="#contact-information">Contact</a>
</p>

---

## 👥 Team Members
- Adithya Shetty
- Aibek Akhmetkazy
- Altair Toleugazinov
- Daniyal Asif
- Sergey Smetankin

![Screenshot of a comment on a GitHub issue showing an image, added in the Markdown, of an Octocat smiling and raising a tentacle.](https://legendary-digital-network-assets.s3.amazonaws.com/wp-content/uploads/2022/05/09122423/Patrick-Stewart-as-Professor-X-.jpeg)

## 🔍 Project Overview
Our project is part of the "Brain-to-Text Benchmark '24" hosted on Eval.ai, which challenges teams to develop a system capable of translating human neural activity into text using deep learning. This involves decoding EEG data to convert it into sentences.

![Project Description Image](https://raw.githubusercontent.com/fwillett/speechBCI/main/SystemDiagram.png)

## 📂 Repository Structure
- `approach1`: Folder for the first approach using specific neural decoding strategies.
- `approach2`: Folder for the second approach with alternate decoding strategies.
- `approach3`: Folder for the third approach, integrating complex models.
- `baseline`: Folder to run the Baseline model for comparison.
- `requirements.txt`: List of Python dependencies for reproducing the analysis.

## 🔧 Environment Setup and Running the Code

To set up the environment and run the code, please follow these steps:

1. Clone the repository: `git clone https://github.com/your-repo-url`
2. Install dependencies: `pip install -r requirements.txt`
3. Navigate to the approach folder: `cd approach1` (or any other approach)
4. Run the notebook: `jupyter notebook`

## 📊 Datasets
We utilize a dataset from neurobiological experiments where neural activity was recorded with microelectrode arrays. The data consist of 12,100 spoken sentences and include features like threshold crossings and spike band power, which are crucial for developing our decoding models.

### Data Fields
- **sentenceText**: Text of each sentence.
- **spikePow**: Time series of spike power neural features.
- **tx1, tx2, tx3, tx4**: Time series of threshold crossing neural features with different thresholds.

## 🚀 Approach
Our project includes three main approaches to decoding neural signals:

1. **Approach 1**: Involves preprocessing for data normalization, feature extraction by combining `tx1` and `spikePow`, phoneme decoding using a G2p model, and a SpeechBCIModel for generating phoneme probabilities, followed by a language model for text generation.

2. **Approach 2**: Starts with data segmentation and normalization, utilizes `tx1` and `spikePow` for feature extraction, employs a G2p model for phoneme decoding, and uses a convolutional and LSTM network for neural decoding, with an n-gram language model to enhance text coherence.

3. **Approach 3**: Features block-wise normalization, concatenates `tx1` and `spikePow` for input features, uses a Seq2Seq model with attention mechanisms for phoneme-to-text conversion, and includes a GRU-based encoder and decoder for final text prediction.

## 🏁 Results & Insights
The following table compares the Word Error Rate (%) across different approaches:

| Approach    | Word Error Rate (%) |
|-------------|---------------------|
| SOTA        | 8.93                |
| Approach 1  | 13.65               |
| Approach 2  | 14.78               |
| Approach 3  | 15.23               |
| Baseline    | 15.43               |

## 🎉 Conclusion
Our project demonstrates significant advances in the ability to decode speech from neural signals, pushing the boundaries of what's possible in brain-computer interfacing technology.

## 📧 Contact Information
For more details, you can reach out to us:
- Adithya Shetty: Adithya.Shetty@skoltech.ru
- Aibek Akhmetkazy: Aibek.Akhmetkazy@skoltech.ru
- Altair Toleugazinov: Altair.Toleugazinov@skoltech.ru
- Daniyal Asif: Daniyal.Asif@skoltech.ru
- Sergey Smetankin: Sergey.Smetankin@skoltech.ru
