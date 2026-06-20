#  Zero-Shot AI Spam Guard

A prototype web application that uses **Zero-Shot Learning** to classify text as either spam/scam or a normal, safe conversation. Unlike traditional spam filters that rely on rigid, pre-trained datasets of specific spam words, this application utilizes a powerful Natural Language Inference (NLI) reasoning engine to logically deduce the intent behind a message.

---

##  Features

* **Zero-Shot Classification:** No training dataset required. The AI dynamically evaluates text against natural language descriptions.
* **Contextual Reasoning:** Uses Facebook's `BART-large-mnli` model to understand intent rather than just matching keywords.
* **Streamlit UI:** Clean, intuitive, and interactive user interface.
* **Smart Caching:** Uses Streamlit's `@st.cache_resource` to load the heavy LLM into memory only once, ensuring fast subsequent evaluations.

---

##  Tech Stack

* [Streamlit](https://streamlit.io/) - For building the interactive web interface.
* [Hugging Face Transformers](https://huggingface.co/docs/transformers/index) - For pipeline integration and downloading the model.
* [PyTorch](https://pytorch.org/) (or TensorFlow) - Underlying deep learning framework.

---

##  Installation & Setup

Follow these steps to get the project running locally.

### 1. Clone the Repository
```bash
git clone [https://github.com/your-username/zero-shot-spam-guard.git](https://github.com/your-username/zero-shot-spam-guard.git)
cd zero-shot-spam-guard

```

### 2. Create a Virtual Environment (Recommended)

```bash
# On macOS/Linux
python3 -m venv venv
source venv/bin/activate

# On Windows
python -m venv venv
venv\Scripts\activate

```

### 3. Install Dependencies

Install Streamlit and Hugging Face Transformers.

```bash
pip install streamlit transformers torch

```

> *Note: Depending on your system setup, you may want to install the specific CPU or GPU version of PyTorch.*

---

##  How to Run

Execute the following command in your terminal to launch the Streamlit app:

```bash
streamlit run app.py

```

> ** Important Note on First Run:** The application uses the `facebook/bart-large-mnli` model, which is approximately **1.6 GB** in size. The very first time you click analyze, the app will pause to download this model to your local machine. Subsequent runs will load instantly from your local cache.

---

##  How It Works

Instead of checking if a text contains words like "WINNER" or "FREE", the backend uses a Natural Language Inference (NLI) technique. It sets up two explicit premises for the AI to choose between:

1. `"a manipulative marketing scam or malicious spam"`
2. `"a normal, casual, safe text message between people"`

The model calculates the probability of which premise best fits the user's input text and displays the classification along with the AI's confidence percentage.

---

