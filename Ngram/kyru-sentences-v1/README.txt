kyru-sentences v1: Kyrgyz (ky) and Russian (ru) sentences for language identification

train.jsonl     125,000 words of each language
val.jsonl       1,000 sentences of each language
test.jsonl      1,000 sentences of each language
metadata.json   sources, split settings, counts, dataset_sha256

One JSON object per line:
  {"id": "test-00001", "lang": "ky", "text": "...", "doc_id": "kyrtext:...", "source": "kyrtext/web"}

All sentences of one web page (doc_id) are in the same file.

Kyrgyz: KyrText (huggingface.co/datasets/tchubakov/kyrtext), web rows of the
test split. Its dataset card names no licence: do not publish these sentences
until that is checked.
Russian: FineWeb-2 (huggingface.co/datasets/HuggingFaceFW/fineweb-2), rus_Cyrl
pages from .kg sites. ODC-By 1.0, and Common Crawl's terms of use.
