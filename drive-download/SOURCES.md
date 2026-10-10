# Sources of the corpus files

Built 2026-10-09 by `tools/fetch_corpus.py` from two Hugging Face datasets, through
the datasets-server rows API (fixed offsets into fixed revisions; no download):

- **KyrText**, `tchubakov/kyrtext` (revision `60a136cf1aaa`): Kyrgyz text
  collected by Tilek Chubakov, 2.3 million rows in sources books-clean, courts, laws,
  web and wiki. No licence is stated on the dataset card: classroom use only.
- **FineWeb-2**, `HuggingFaceFW/fineweb-2`, config `rus_Cyrl` (revision
  `af9c13333eb9`): Russian web text from Common Crawl, filtered by
  the FineWeb-2 pipeline (Penedo et al., 2024). Licence ODC-By 1.0, plus the Common
  Crawl terms of use.

`provenance.jsonl` lists every row used (dataset, split, row number, id, lines kept).

| File | Slice | Split | Rows from | Rows read | Words kept |
|---|---|---|---|---|---|
| `train_kyrgyz.txt` | KyrText web (news) | train | 1,000,000 | 100 | 5,003 |
| `train_kyrgyz.txt` | KyrText books-clean | train | 0 | 6 | 1,508 |
| `train_kyrgyz.txt` | KyrText laws | train | 250,000 | 40 | 1,016 |
| `train_kyrgyz.txt` | KyrText wiki | train | 2,300,000 | 100 | 1,523 |
| `train_russian.txt` | FineWeb-2 rus_Cyrl web | train | 500,000,000 | 100 | 4,515 |
| `heldout_kyrgyz.txt` | KyrText web (news), test split | test | 10,000 | 40 | 1,515 |
| `heldout_russian.txt` | FineWeb-2 rus_Cyrl web | train | 100,000,000 | 40 | 1,030 |

## Cleaning

Line by line, at most 40 lines per row. A line is dropped by the first rule
it breaks (the rules are listed in `tools/fetch_corpus.py`); lines dropped:

| Rule | Lines |
|---|---|
| short | 313 |
| latin | 260 |
| language | 104 |
| digits | 60 |
| code | 37 |
| symbols | 31 |
| duplicate | 16 |
| caps | 12 |
| chars | 10 |
| spaced | 6 |
| adult (rows) | 5 |
| fragment | 5 |
| alphabet | 1 |

Kept: 616 lines, 16,110 words.
