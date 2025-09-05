# Podcast Model

A Python pipeline for generating AI-powered podcast episodes from articles, PDFs, or plain text. It automatically creates a script in conversational style and synthesizes speech for multiple speakers, outputting a downloadable `.wav` file.

## 🚀 Features

- **Multi-Input Support:** Accepts URLs (articles), PDFs, or plain text as input.
- **Script Generation:** Uses LLMs (DeepSeek-R1-Distill-Qwen-1.5B) to generate engaging, informal, and conversational podcast scripts.
- **Voice Synthesis:** Employs Kokoro TTS to create dialogues between two virtual speakers.
- **Automated Workflow:** End-to-end process includes text extraction, script writing, voice generation, and audio merging.
- **Customizable Voices:** Supports selection of different voice types and languages for each speaker.

## 🧩 Main Components

- `process_input(input_data)`: Handles PDF, URL, or text input and extracts content.
- `text_model(content, length)`: Generates a podcast script using a language model.
- `tts_model(...)`: Converts script lines to audio with distinct voices for each speaker.
- `combined_audio(audio_files)`: Merges all voice segments into a single `.wav` file.
- `podcast_model(...)`: Orchestrates the full pipeline from text to final audio.

## 🖥️ Dependencies

- `transformers`
- `kokoro >= 0.9.2`
- `soundfile`
- `PyPDF2`
- `pdfplumber`
- `requests`
- `beautifulsoup4`
- `pydub`
- `tqdm`

Install requirements:
```bash
pip install transformers accelerate bitsandbytes PyPDF2 pdfplumber requests beautifulsoup4 kokoro>=0.9.2 soundfile pydub tqdm
```

## 🔑 Setup

1. **GPU Support Recommended:** For fast inference (optional).
2. **Hugging Face Auth:**  
   Log in with your Hugging Face token if required by the model:
   ```python
   from huggingface_hub import login
   login(token="YOUR_HF_TOKEN")
   ```

## ⚡ Usage Example

```python
text_link = "https://www.pbs.org/newshour/politics/how-the-white-house-calculated-trumps-sweeping-new-tariffs"
podcast_model(
    text_link,
    'af_heart', 'a',        # Speaker 1 voice and type
    'bm_george', 'b',       # Speaker 2 voice and type
    "1 minute"              # Podcast length
)
# Outputs: combined_audio.wav
```

## 📄 Script Output Example

```json
{
    "topic": "AGI",
    "podcast": [
        {"speaker": 2, "line": "So, AGI, huh? Seems like everyone's talking about it these days."},
        {"speaker": 1, "line": "Yeah, it's definitely having a moment, isn't it?"},
        ...
    ]
}
```

## 📝 Notes

- Output is a single `.wav` file with both speakers' voices.
- Designed for educational, prototyping, and creative use.
- Example voices: see Kokoro documentation for more options.

---
MIT License (or specify your own)
