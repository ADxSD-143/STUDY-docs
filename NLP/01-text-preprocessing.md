# Module 01 — Text Preprocessing: Complete Practical Reference

**Status:** Completed · **Level:** Beginner → practical AI/ML engineer  
**Main video:** [Text Preprocessing | NLP Course Lecture 3](https://youtu.be/6C0sLtw5ctc)

**Goal:** Understand the common preprocessing steps, write them in Python, understand each important line, and choose steps based on the task.

> Layman version: raw text arrives with inconsistent formatting, markup and noise. Preprocessing organizes what a model needs. But aggressive cleaning can throw away useful meaning.

## 1. Full preprocessing flow

~~~mermaid
flowchart TD
    A[Raw text + task requirements] --> B[Inspect samples and labels]
    B --> C[Keep original text for traceability]
    C --> D[HTML / URL handling]
    D --> E[Unicode and whitespace normalization]
    E --> F[Case normalization if safe]
    F --> G[Contractions / abbreviations / spelling if justified]
    G --> H[Punctuation / special characters / emoji handling]
    H --> I[Tokenization]
    I --> J[Optional stopword filtering]
    J --> K[Optional stemming OR lemmatization]
    K --> L[Inspect outputs and edge cases]
    L --> M[Features / model]
~~~

**This is a menu, not a mandatory recipe.** Not every task needs every step. Modern pretrained Transformers generally need their own tokenizer and often work best with minimally altered text.

## 2. Decide based on the task

| Task | Preserve carefully | Often reasonable |
|---|---|---|
| Sentiment / reviews | Negation (“not good”), emoji, emphasis | Normalize whitespace; consider URL placeholders |
| Spam detection | URLs, email/phone patterns, suspicious punctuation | Replace with placeholders or extract features |
| Named Entity Recognition | Capitalization, punctuation, names, dates | Minimal cleanup and model-specific tokenization |
| Classical search / TF-IDF | Terms, IDs, useful phrases | Lowercase if case is irrelevant; optional n-grams |
| Social/chat analytics | Emojis, hashtags, slang, abbreviations | Documented mapping and normalization |
| Transformer / LLM input | Meaning, context, formatting | Remove only corrupted markup; use matching tokenizer |

## 3. Start with a noisy example

~~~python
raw_text = """
<div>OMG!!! I can't believe this 😭😭
Visit https://example.com/order?id=123
my package was NOT delivered... #angry</div>
"""
print(raw_text)
~~~

This text has HTML, uppercase letters, a contraction, emoji, URL, punctuation and a hashtag. We'll handle them separately to understand the effect of each step.

## 4. Preprocessing steps with code

### Step 1 — Lowercasing / case folding

Meaning: convert uppercase letters to lowercase so “Delivery” and “delivery” are treated alike.

~~~python
text = "The Delivery Was LATE"
print(text.lower())
# the delivery was late
~~~

- **What happens:** lower() returns a lowercase copy of the string.
- **Use:** case-insensitive text classification and classical TF-IDF baselines.
- **Alternative:** casefold() for stronger Unicode-aware caseless matching, or preserve original case.
- **Warning:** capitalization can help NER; case-sensitive IDs and acronyms may be damaged. Keep raw text.

### Step 2 — Remove HTML tags

~~~python
import re

text = "<div>Great product<br>Fast delivery</div>"
text = re.sub(r"<[^>]+>", " ", text)
print(text)
#  Great product Fast delivery
~~~

- **What happens:** re.sub(pattern, replacement, text) replaces matches. The pattern is a simple teaching pattern for angle-bracket tags.
- **Use:** text scraped from web pages.
- **Alternative:** Beautiful Soup or another HTML parser for malformed/complex markup.
- **Warning:** regex is not a complete HTML parser. Preserve meaningful alt text, tables or page structure if needed.

### Step 3 — Remove or replace URLs

~~~python
text = "Read https://example.com/item?id=7 for details"
without_url = re.sub(r"https?://\S+|www\.\S+", " ", text)
placeholder = re.sub(r"https?://\S+|www\.\S+", " URL ", text)
print(without_url)
print(placeholder)
~~~

- **What happens:** pattern matches common HTTP/HTTPS and www links up to whitespace.
- **Delete** when URL content is irrelevant; **replace with URL** when link presence matters, such as spam detection; **extract domain** when the destination itself matters.
- **Limitation:** simple patterns need tests for trailing punctuation and unusual URL formats.

### Step 4 — Normalize whitespace

~~~python
text = "  payment\n\n failed\t yesterday  "
text = re.sub(r"\s+", " ", text).strip()
print(text)
# payment failed yesterday
~~~

- **What happens:** \s+ matches runs of spaces, tabs and newlines; strip() removes outer whitespace.
- **Use:** text copied from PDFs, forms, websites and logs.
- **Warning:** preserve paragraph boundaries when document structure matters.

### Step 5 — Remove punctuation (only if justified)

~~~python
import string

text = "Wow!!! This product is great, isn't it?"
table = str.maketrans("", "", string.punctuation)
print(text.translate(table))
# Wow This product is great isnt it
~~~

- **What happens:** string.punctuation contains ASCII punctuation; maketrans builds a deletion table; translate applies it efficiently.
- **Problem:** isn't becomes isnt; punctuation may signal emotion, sentence boundaries or sarcasm.
- **Alternatives:** replace punctuation with spaces, preserve selected symbols, or let a tokenizer handle punctuation.
- **Performance:** translate is usually preferable to a character-by-character Python loop for this simple operation.
- **Limit:** ASCII punctuation is not all Unicode punctuation.

### Step 6 — Expand contractions

~~~python
contractions = {
    "can't": "cannot",
    "won't": "will not",
    "I'm": "I am",
}

text = "I can't say this is good"
for short_form, full_form in contractions.items():
    text = text.replace(short_form, full_form)
print(text)
~~~

- **What happens:** a dictionary maps a shortened form to a longer form; the loop replaces each known form.
- **Use:** some chat, review and classical NLP pipelines.
- **Warning:** replace() is case-sensitive, may replace substrings, and ambiguous forms like “it's” can mean “it is” or “it has”.
- **Alternative:** use a tested contractions package and validate its output. Expansion is not a mandatory Transformer preprocessing step.

### Step 7 — Expand chat abbreviations / slang

~~~python
short_forms = {
    "idk": "i do not know",
    "brb": "be right back",
    "imo": "in my opinion",
    "gn": "good night",
}

text = "idk if this is good imo"
tokens = text.split()
text = " ".join(short_forms.get(token, token) for token in tokens)
print(text)
# i do not know if this is good in my opinion
~~~

- split() creates whitespace-separated tokens.
- dict.get(token, token) expands known forms and leaves unknown words unchanged.
- join() combines tokens back into a string.
- **Use:** chat/social-media analytics.
- **Warning:** slang varies by community and language. English dictionaries are not enough for Hinglish/code-mixed text; maintain and test a domain-specific mapping.

### Step 8 — Spelling correction (optional)

~~~python
# Optional dependency: pip install textblob
from textblob import TextBlob

text = "The delivary was very late"
corrected = str(TextBlob(text).correct())
print(corrected)
~~~

- TextBlob(text) wraps the string; correct() proposes spelling corrections.
- **Use:** only when typos are common and correction improves measured results.
- **Warning:** can alter names, brands, technical terms, slang and regional words; can be slow on large datasets.
- **Alternatives:** custom vocabulary, domain-specific spell checker, or no correction. Verify package/resource requirements in your environment.

### Step 9 — Stopword handling

Stopwords are frequent words such as “the”, “is” and “and”. They are not automatically useless.

~~~python
# Optional: pip install nltk
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import wordpunct_tokenize

nltk.download("stopwords", quiet=True)
text = "this product is not good"
tokens = wordpunct_tokenize(text)
stop_words = set(stopwords.words("english"))
filtered = [token for token in tokens if token.lower() not in stop_words]

print("All tokens:", tokens)
print("Filtered:", filtered)
~~~

- wordpunct_tokenize splits text into word-like pieces and punctuation.
- set() makes membership checks efficient.
- The list comprehension keeps tokens not present in the stopword set.
- **Critical:** a default English list may remove “not”, changing sentiment meaning. Inspect and customize it.
- **Use:** experiment with classical text features; do not blindly apply to NER, POS, syntax tasks or Transformer inputs.

### Step 10 — Emoji handling

~~~python
# Option A: preserve emojis for sentiment tasks
text = "This is amazing 😍"

# Option B: map known emojis to descriptive tokens
emoji_map = {"😍": " smiling_face_with_hearts ", "😭": " loudly_crying_face "}
for emoji, label in emoji_map.items():
    text = text.replace(emoji, label)
print(text)
~~~

- A mapping replaces only the emoji characters explicitly listed.
- **Use:** reviews, social listening and feedback analysis.
- **Alternatives:** preserve emoji, use an emoji-aware library to convert them to descriptions, or remove them only after evaluation.
- **Warning:** hand-written Unicode-range regex is fragile because emoji can include skin tones, variation selectors and joined sequences.

### Step 11 — Tokenization: sentence vs word vs subword

~~~python
# Optional: pip install nltk
import nltk
from nltk.tokenize import sent_tokenize, wordpunct_tokenize

nltk.download("punkt", quiet=True)
text = "Delivery was late. Support did not reply!"
sentences = sent_tokenize(text)
words = wordpunct_tokenize(text)
print(sentences)
print(words)
~~~

- sent_tokenize segments sentences; wordpunct_tokenize splits into word-like tokens and punctuation.
- **Use:** sentence segmentation for document chunks; word tokens for classical features.
- **Alternatives:** simple split() is fast but fragile; spaCy provides a robust tokenizer and linguistic pipeline.
- **Modern NLP:** Transformer models use model-specific subword tokenizers such as BPE or WordPiece. Always use the tokenizer matching the selected model.
- NLTK resource names can vary by version; if a tokenizer reports a missing resource, follow the error's download instructions.

### Step 12 — Stemming

Stemming reduces word forms with rules. The result may not be a dictionary word.

~~~python
from nltk.stem import PorterStemmer

stemmer = PorterStemmer()
words = ["connect", "connected", "connecting", "connection"]
print([stemmer.stem(word) for word in words])
~~~

- PorterStemmer() creates the stemmer; stem(word) applies its rules.
- **Use:** some classical search and feature-reduction tasks.
- **Alternatives:** Snowball stemmer supports multiple languages; lemmatization uses linguistic information.
- **Warning:** stemming can merge words that should stay distinct. Measure the effect.

### Step 13 — Lemmatization

Lemmatization maps a word to a dictionary base form (lemma), often using linguistic information.

~~~python
# Optional: pip install nltk
import nltk
from nltk.stem import WordNetLemmatizer

nltk.download("wordnet", quiet=True)
nltk.download("omw-1.4", quiet=True)

lemmatizer = WordNetLemmatizer()
print(lemmatizer.lemmatize("cars"))             # car
print(lemmatizer.lemmatize("running", pos="v")) # run
print(lemmatizer.lemmatize("better", pos="a"))  # good
~~~

- WordNetLemmatizer uses the WordNet lexical resource.
- pos supplies a part-of-speech hint: v = verb, a = adjective. Without POS, default behavior treats words as nouns, so “running” may not become “run”.
- **Use:** linguistic analysis and some classical feature normalization.
- **Alternative:** spaCy can provide POS-aware lemmas as part of a pipeline.
- **Warning:** for most pretrained Transformer workflows, stemming and lemmatization are not default requirements.

## 5. Apply cleanup to a pandas column

~~~python
import pandas as pd
import re

df = pd.DataFrame({
    "review": [
        "<p>GREAT product!!!</p>",
        "Delivery was NOT good...",
        "Visit https://example.com for help",
    ]
})

def basic_clean(text):
    text = str(text)
    text = re.sub(r"<[^>]+>", " ", text)                  # simple HTML cleanup
    text = re.sub(r"https?://\S+|www\.\S+", " URL ", text) # keep URL presence
    text = re.sub(r"\s+", " ", text).strip()             # normalize whitespace
    return text.lower()                                  # only for case-insensitive tasks

df["clean_review"] = df["review"].map(basic_clean)
print(df[["review", "clean_review"]])
~~~

- DataFrame stores examples in rows and columns.
- basic_clean applies the documented operations in a fixed order.
- map() applies the function to each cell in the selected column.
- Keep the raw column for debugging and audits.
- For large datasets, compare pandas .str methods with map() on representative data; benchmark instead of assuming which is faster.

## 6. A conservative reusable baseline

This function deliberately avoids stopword removal, spelling correction, stemming and lemmatization.

~~~python
import re
import unicodedata

def conservative_clean(text):
    text = str(text)
    text = unicodedata.normalize("NFKC", text)
    text = re.sub(r"<[^>]+>", " ", text)
    text = re.sub(r"https?://\S+|www\.\S+", " URL ", text)
    text = re.sub(r"\s+", " ", text).strip()
    return text

sample = "  <p>I do NOT like it 😭</p> https://example.com "
print(conservative_clean(sample))
~~~

Expected behavior: simple HTML tags are removed, URL is replaced with URL, whitespace is normalized, and words/negation/emoji are preserved. This is a starting point, not a universally correct pipeline.

## 7. Performance tips

- Prefer str.translate for straightforward ASCII punctuation removal rather than rebuilding strings one character at a time.
- For pandas columns, benchmark .str operations and map() on representative data.
- Avoid expensive spelling correction on every row unless it improves results.
- Test transformations on edge cases before applying them to thousands of rows.
- Preserve raw text and compare downstream metrics for different preprocessing configurations.

## 8. Real-world examples

**Review sentiment:** “This is NOT good 😭!!!” — preserve negation and consider emoji/emphasis. Compare variants on held-out data.

**Spam detection:** “WIN NOW!!! click https://suspicious.example” — URL presence and punctuation may be predictive. Replace or extract them rather than deleting all evidence.

**NER:** “Apple hired Maya in New York.” — capitalization helps identify entities. Avoid blindly lowercasing or removing punctuation.

## 9. Common mistakes

1. Removing “not” or “never”.
2. Deleting URLs when their presence/domain is predictive.
3. Removing punctuation before sentence segmentation or emotion analysis.
4. Correcting names, brands and technical terms incorrectly.
5. Using English stopwords for Hindi/Hinglish text.
6. Treating regex tokenization as production-ready for every language.
7. Applying stemming and lemmatization together without a reason.
8. Manually tokenizing text before a Transformer without checking its requirements.
9. Overwriting raw text and losing debugging ability.
10. Fitting data-dependent transforms on all data before the train/test split.

## 10. Video assignment: movie description dataset

Build a small dataset with title, overview and genre labels using an allowed TMDB API workflow or another permitted source.

1. Inspect missing/empty descriptions and label distribution.
2. Keep the original overview column.
3. Apply conservative cleanup first.
4. Compare it with a more aggressive preprocessing version.
5. Use TF-IDF and a simple classifier in Module 03.
6. Compare per-genre precision, recall and F1; inspect errors.
7. Document the dataset source, API permissions and limitations.

Do not assume every cleaning step improves classification; test it.

## 11. Interview questions

1. Why is preprocessing task-dependent?
2. Stemming vs lemmatization?
3. When should a URL be replaced rather than removed?
4. Why can stopword removal hurt sentiment analysis?
5. Why use a model-specific tokenizer for Transformers?
6. Why is str.translate often better than a character loop for ASCII punctuation?
7. How would you clean HTML, emoji, contractions and product IDs without losing useful signals?

## 12. Video, docs, articles and repositories

- **Main video:** [Text Preprocessing | NLP Course Lecture 3](https://youtu.be/6C0sLtw5ctc) — use as the core lesson; this note expands its techniques with annotated examples and practical caveats.
- **Course notes:** [CampusX NLP course preview](https://learnwith.campusx.in/s/preview/courses/Natural-Language-Processing---NLP-YouTube-691466e7be8ce103a29dbff8).
- **Official book:** [NLTK — Natural Language Processing with Python](https://www.nltk.org/book/).
- **spaCy guide:** [spaCy 101](https://spacy.io/usage/spacy-101).
- **Tokenizer docs:** [Hugging Face Tokenizers](https://huggingface.co/docs/tokenizers/index).
- **Regex reference:** [Python re documentation](https://docs.python.org/3/library/re.html).
- **Pandas docs:** [Working with text data](https://pandas.pydata.org/docs/user_guide/text.html).
- **Repositories:** [NLTK](https://github.com/nltk/nltk), [spaCy](https://github.com/explosion/spaCy), [Hugging Face Transformers](https://github.com/huggingface/transformers).
- **Additional tutorial:** [NLP Demystified — Basic Preprocessing](https://www.nlpdemystified.org/course/basic-preprocessing) — case folding, stopwords, stemming and lemmatization trade-offs.

## Final recap

Preprocessing is not “clean everything.” It is a set of choices for a particular task. Keep raw data, document transformations, inspect examples, and compare alternatives using the downstream evaluation metric.
