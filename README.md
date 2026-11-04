# Exam Prep Assistant (Matric and Inter)

A Streamlit app that helps Pakistani **Matric (Class 9-10)** and **Intermediate (Class 11-12)** students prepare for exams using **their own textbook**.

1. The student uploads a chapter.
2. The app creates practice questions (MCQs, short and long questions) from that chapter only.
3. The student writes answers, and the app checks them **against the chapter**, gives marks, and shows what was missed.
4. Explanations come in **English, اردو (Urdu) or Roman Urdu**.

It uses Google's **Gemini Flash** model.

## Features

- Upload **PDF, DOCX, TXT** or **photos of pages** (PNG/JPG). Scanned and Urdu books are read with the AI reader.
- Choose level, difficulty, subject, topic focus and how many MCQs (1 mark), short questions (2 marks) and long questions (5 marks).
- MCQs are marked instantly; written answers are marked 0 to full marks with feedback, missed points, a model answer and a quote from the chapter.
- Urdu text is shown right-to-left in a Nastaliq font.
- Running score and a downloadable results report (.txt).

## Project structure

```
.
├── app.py             # Streamlit app
├── requirements.txt   # Python dependencies
└── README.md
```

## Run locally

1. Get a free Gemini API key at https://aistudio.google.com/apikey
2. Install and run:

```bash
pip install -r requirements.txt
export GEMINI_API_KEY="your-key"      # Windows PowerShell: $env:GEMINI_API_KEY="your-key"
streamlit run app.py
```

You can also paste the key into the app's sidebar instead of using an environment variable.

## Deploy on Streamlit Community Cloud

1. Push this repo to GitHub (never commit your API key).
2. Go to https://share.streamlit.io and sign in with GitHub.
3. Click **Create app**, pick the repo, branch `main`, and main file `app.py`.
4. Open **Advanced settings → Secrets** and add:

```toml
GEMINI_API_KEY = "your-key"
```

5. Click **Deploy**.

## Configuration

| Setting | Where | Default |
|---|---|---|
| `GEMINI_API_KEY` | Streamlit secrets or environment variable | none (or enter in sidebar) |
| Model name | Sidebar field | `gemini-flash-latest` |
| Explanation language | Sidebar | English |

If you see "model not found", type a current Flash model name (for example `gemini-2.5-flash`) in the sidebar.

## Tips

- **Scanned or Urdu PDF?** Tick **Use the AI reader**. Open "Text the app read from your chapter" to confirm it was read correctly.
- **Photos:** take clear, straight, well-lit pictures of each page and upload them in order.
- **Very long chapters:** only the first 120,000 characters are used. Upload one chapter at a time.
- **Free key limits:** Gemini free keys have per-minute limits. If you hit one, wait a minute and try again.

## Limitations

- Questions and marking are made by AI, so they can contain mistakes. Check important answers with your textbook and teacher. This is a study aid, not an official board marking scheme.
- Your chapter text and answers are sent to the Gemini API. Use only material you are allowed to use, and do not upload personal information.
