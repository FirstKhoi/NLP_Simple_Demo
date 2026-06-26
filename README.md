# 🤖 NLP Studio

A powerful, user-friendly web application for Natural Language Processing tasks including translation, spell checking, and document processing. Built with [Streamlit](https://streamlit.io/) and powered by advanced AI models.

---

## ✨ Features

### 🌍 **Translate Tab**
Instantly translate text between multiple languages with automatic language detection.

- **Auto Language Detection**: Automatically identifies the source language
- **Support for 8 Languages**: Vietnamese, English, French, Japanese, Chinese, Korean, Spanish, German
- **Smart Handling**: Detects if text is already in target language
- **Minimum Length**: Requires at least 3 characters for translation

### ✏️ **Correction Tab**
Fix spelling and grammar errors in your text with intelligent spell checking.

- **Multi-Language Support**: English, Spanish, French, Portuguese, German, Russian, Arabic, Basque, Latvian, Dutch
- **Smart Capitalization**: Preserves original case (UPPERCASE, Title Case, lowercase)
- **Change Detection**: Shows whether corrections were made
- **Real-time Feedback**: Displays the detected language and correction status

### 📄 **Document Lab Tab** (Advanced Processing)
Upload and process entire documents with AI-powered features.

#### Supported File Formats:
- **TXT** - Plain text files
- **DOCX** - Microsoft Word documents  
- **PDF** - PDF documents

#### Processing Options:
1. **📝 Summarize Text**
   - Uses DistilBART AI model for efficient summarization
   - Best optimized for English text
   - Breaks large documents into chunks for processing
   - Generates concise summaries up to 3 chunks

2. **🌐 Translate Entire File**
   - Translates full document content to any supported language
   - Handles large files by processing in chunks
   - Downloads result as TXT or DOCX format

#### Download Options:
- Export as **TXT** (plain text)
- Export as **DOCX** (Word document with formatting)

---

## 🌐 Live Demo

**Try it now without installation!** 👉 [**https://nlpsimpledemobykhoi.streamlit.app/**](https://nlpsimpledemobykhoi.streamlit.app/)

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Minimum 2GB RAM (4GB+ recommended for summarization)

### Installation

1. **Clone or download this repository**
   ```bash
   git clone <repository-url>
   cd nlp-studio
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Download required NLTK data** (first time only)
   ```bash
   python -c "import nltk; nltk.download('punkt'); nltk.download('averaged_perceptron_tagger')"
   ```

### Running the Application

```bash
streamlit run main.py
```

The app will open in your browser at `http://localhost:8501`

---

## 📖 How to Use

### **Translation**

1. Go to the **"Translate"** tab
2. Paste or type your text in the input area (minimum 3 characters)
3. Select your desired target language from the dropdown
4. Click **"Translate"** button
5. View the result with source and target language labels

**Example:**
- Input: "Hello, how are you?"
- Target: Vietnamese
- Output: "Xin chào, bạn khỏe không?"

### **Spelling Correction**

1. Go to the **"Correction"** tab
2. Paste text with potential spelling errors
3. Click **"Check spelling"** button
4. Review corrected text and language detection
5. See whether changes were made

**Example:**
- Input: "Yesturday, I recieveed a mesage from my freind."
- Output: "Yesterday, I received a message from my friend."

### **Document Processing**

1. Go to the **"Document Lab"** tab
2. Click **"Choose a document"** and upload a TXT, DOCX, or PDF file
3. Review the **"Preview extracted content"** section
4. Select an action:
   - **Summarize Text** - Generate AI summary
   - **Translate Entire File** - Translate to chosen language
5. Click **"Process document"**
6. View results and download in your preferred format

**Example Workflow:**
1. Upload a 5-page PDF report (English)
2. Select "Summarize Text"
3. AI generates 1-2 paragraph summary
4. Download as DOCX for easy sharing

---

## 📋 Dependencies

| Package | Purpose |
|---------|---------|
| `streamlit` | Web app framework |
| `deep-translator` | Google Translate API wrapper |
| `langdetect` | Language detection |
| `langcodes` | Language code utilities |
| `nltk` | Natural Language Toolkit for tokenization |
| `pyspellchecker` | Spell checking engine |
| `transformers` | Hugging Face models for summarization |
| `torch` | PyTorch (required by transformers) |
| `python-docx` | Read/write DOCX files |
| `pypdf` | Read PDF files |
| `sentencepiece` | Tokenization for models |

---

## 🌐 Supported Languages

### Translation (8 languages)
- 🇻🇳 Vietnamese (vi)
- 🇺🇸 English (en)
- 🇫🇷 French (fr)
- 🇯🇵 Japanese (ja)
- 🇨🇳 Chinese (zh-CN)
- 🇰🇷 Korean (ko)
- 🇪🇸 Spanish (es)
- 🇩🇪 German (de)

### Spell Checking (10 languages)
- English (en)
- Spanish (es)
- French (fr)
- Portuguese (pt)
- German (de)
- Russian (ru)
- Arabic (ar)
- Basque (eu)
- Latvian (lv)
- Dutch (nl)

---

## ⚙️ Configuration

### Customizing Languages

Edit the `TARGET_LANGS` dictionary in `main.py`:
```python
TARGET_LANGS = {
    "Vietnamese": "vi",
    "English": "en",
    # Add more languages here
}
```

### Adjusting Summarization Parameters

In the Document Lab section, you can modify:
- **chunk_size**: Size of text chunks (default: 2000 characters)
- **max_length**: Maximum summary length (default: 130 tokens)
- **min_length**: Minimum summary length (default: 30 tokens)

---

## 🎨 UI/UX Features

- **Modern Dark/Light Theme**: Adaptive color scheme
- **Responsive Design**: Works on desktop and tablet
- **Real-time Results**: Instant feedback for translation and spell check
- **Error Handling**: Clear error messages for troubleshooting
- **Example Pills**: Quick-start examples in each tab
- **Progress Indicators**: Loading spinners for long operations
- **Download Buttons**: Easy export options

---

## 📊 Performance Notes

### First-Run Behavior
- **Translation**: First translation loads Google Translator (fast)
- **Summarization**: First summarization loads DistilBART model (~2GB download)
  - Subsequent runs are faster (models cached)
  - May take 30-60 seconds on first use

### Limitations
- **Summarization**: Optimized for English text; other languages may have variable results
- **File Size**: Large files are processed in 4000-character chunks
- **Summarization Chunks**: Maximum 3 chunks processed to prevent CPU overload
- **Minimum Input**: 3 characters required for translation/spell check

---

## 🔧 Troubleshooting

### Issue: "Unable to detect the language"
**Solution**: Ensure text is at least 3 characters and in a recognized language

### Issue: Summarization takes too long
**Solution**: 
- The model is downloading on first use (~2GB)
- For large documents, it only processes first 3 chunks
- Consider using a machine with more RAM

### Issue: Spell checker says "language not supported"
**Solution**: Currently supports 10 languages. Check the supported list in "Spell Checking (10 languages)" section

### Issue: Translation error or API issues
**Solution**: 
- Check internet connection (uses Google Translate)
- Verify text length (minimum 3 characters)
- Try again after a few seconds

---

## 💡 Tips & Tricks

1. **Use Examples**: Click "Try an example" to see sample inputs
2. **Batch Processing**: Process multiple documents one by one
3. **Quality Check**: Preview extracted content before processing
4. **Format Preservation**: Use DOCX format to maintain formatting
5. **Language Mix**: Works with multiple languages in one document

---

## 📝 Example Workflows

### Workflow 1: Translate Business Email
1. Open **Translate** tab
2. Paste email content
3. Select target language
4. Copy translated text to email

### Workflow 2: Proofread and Save
1. Open **Correction** tab
2. Paste your document excerpt
3. Get corrections
4. Copy corrected text back to document

### Workflow 3: Summarize Research Paper
1. Go to **Document Lab**
2. Upload PDF of research paper
3. Select "Summarize Text"
4. Download summary as DOCX
5. Share with team

### Workflow 4: Multilingual Document
1. Upload document to **Document Lab**
2. Select "Translate Entire File"
3. Choose target language
4. Download translated version in Word format

---

## 🔐 Privacy & Security

- ✅ All processing happens on your local machine
- ✅ Uses Google Translate API (standard privacy terms apply)
- ✅ No data stored after session ends
- ⚠️ Uploaded files are processed in memory, not permanently saved

---

## 📜 License

This project is open source and available under the MIT License.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

### Ideas for Enhancement:
- Support for more languages
- Batch file processing
- Advanced summarization settings
- Text sentiment analysis
- Named entity recognition

---

## 📞 Support

For issues or questions:
1. Check the **Troubleshooting** section above
2. Review error messages carefully
3. Ensure all dependencies are installed correctly
4. Try upgrading Streamlit: `pip install --upgrade streamlit`

---

## 🎯 Future Roadmap

- [ ] Support for more than 8 translation languages
- [ ] Advanced summarization with user-adjustable parameters
- [ ] Batch processing for multiple files
- [ ] Sentiment analysis feature
- [ ] Named entity recognition
- [ ] Text classification
- [ ] Dark mode toggle
- [ ] User preferences saving

---

**Last Updated**: June 2024  
**Version**: 1.0  
**Built with ❤️ using Streamlit and Transformers**
