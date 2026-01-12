
# CHAPTER 16: Natural Language Processing with RNNs and Attention

NLP adalah domain di mana deep learning telah mencapai breakthrough results. Chapter ini mencakup various NLP tasks dengan modern architectures.

## Character-level RNNs

**Character-level RNNs** melatih pada character level untuk generate text:
- Model belajar character patterns, word structures, grammar
- Can generate realistic looking text
- Requires less preprocessing dibanding word-level models
- Slower inference (more characters to generate)

## Word Embeddings

**Word Embeddings** represent words sebagai dense vectors:
- Traditional: one-hot encoding (sparse, high-dimensional)
- Embeddings: dense vectors (low-dimensional, semantic meaning)
- Pre-trained embeddings: Word2Vec, GloVe, FastText

### Embedding Properties:
- Similar words memiliki similar vectors
- Arithmetic operations meaningful: king - man + woman ≈ queen
- Learned dari unlabeled data (unsupervised)

## Sentiment Analysis

**Sentiment Analysis** classify text sebagai positive atau negative (atau multi-class):

### Approaches:
1. Embeddings + RNN/LSTM
2. Pre-trained models (fine-tuning)
3. Attention mechanisms

### Handling Variable-length Text:
- Padding: add zeros untuk shorter sequences
- Masking: tell model untuk ignore padded values
- Dynamic batching: group sequences by length

## Encoder-Decoder Architectures

**Encoder-Decoder** untuk sequence-to-sequence tasks seperti machine translation:
- **Encoder**: reads input sequence, produces context vector
- **Decoder**: generates output sequence conditioning pada context

### Components:
- Encoder layers: stack LSTMs/GRUs untuk learning input representation
- Decoder layers: generate output dari context vector
- Often bidirectional encoder untuk richer representation

## Bidirectional RNNs

**Bidirectional RNNs** process sequences dari kedua directions:
- Forward RNN: left to right
- Backward RNN: right to left
- Concatenate atau add outputs

### Advantages:
- Richer context (future information untuk current position)
- Better representations untuk understanding tasks
- Cannot use untuk generation (need future information)

## Beam Search

**Beam Search** adalah decoding strategy untuk generation:
- Keep top-k candidates (beam width) instead of greedy selection
- Explore multiple hypotheses
- Trade-off: better quality vs slower inference

## Attention Mechanisms

**Attention** allows decoders untuk fokus pada relevant parts dari input:
- Compute attention scores untuk each input element
- Softmax untuk normalize weights
- Weighted sum dari input elements
- Dramatically improved sequence-to-sequence results

### Types:
- **Scaled dot-product attention**: efficient attention mechanism
- **Multi-head attention**: multiple attention heads dalam parallel
- **Self-attention**: attend to different positions dalam same sequence

## Transformer Architecture

**Transformer** revolutionary architecture berdasarkan entirely pada attention:
- No recurrence atau convolution
- Self-attention layers untuk processing sequences
- Positional encodings untuk capturing position information
- Parallel processing possible (unlike RNNs)
- Foundation untuk BERT, GPT, dan modern NLP

### Advantages:
- Powerful untuk capturing long-range dependencies
- Efficient parallelization
- State-of-the-art results pada many NLP tasks

## Modern NLP Models

### BERT (Bidirectional Encoder Representations from Transformers)
- Pre-trained menggunakan masked language modeling
- Fine-tune untuk various downstream tasks
- Bidirectional context

### GPT (Generative Pre-trained Transformer)
- Autoregressive language model
- Fine-tuning untuk various tasks
- Scaling laws: larger models generally better

### Other Innovations
- T5: unified framework untuk NLP tasks
- ELECTRA, RoBERTa: improvements pada BERT
- Domain-specific models: SciBERT, ClinicalBERT, etc.

## Kesimpulan

NLP rapidly evolving field dengan breakthrough innovations. Attention mechanisms dan Transformers revolutionized field, enabling state-of-the-art results. Pre-trained models membuat sophisticated NLP accessible.
