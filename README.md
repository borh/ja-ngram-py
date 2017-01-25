# ja-ngram-py

Simple pure Python 3 program for n-gram extraction from Japanese texts using MeCab and Unidic.

This was primarily made for educational purposes.

# Requirements

Requires MeCab installed and UniDic as the dictionary. MeCab must be on the path.

Only tested on Linux and macOS.

# Usage

```bash
$ ./ja-ngram --help
```

    usage: ja-ngram [-h] [--n [N]] [--n_gram-sep [N_GRAM_SEP]]
                    [--min-freq [MIN_FREQ]]
                    [--positional-pos-filter POSITIONAL_POS_FILTER [POSITIONAL_POS_FILTER ...]]
                    [--features FEATURES [FEATURES ...]]
                    [--features-sep [FEATURES_SEP]] [--transpose [TRANSPOSE]] --in
                    IN [IN ...] --out OUT

    Extracts n-grams using MeCab (UniDic) from multiple input files and outputs an
    n-gram frequency matrix by file. Supports arbitrary filtering of POS sequences
    using regular expressions.

    optional arguments:
      -h, --help            show this help message and exit
      --n [N]               specify the n-gram order (default=2)
      --n_gram-sep [N_GRAM_SEP]
                            specify the separator used to separate n-grams
                            (default='_')
      --min-freq [MIN_FREQ]
                            specify the minimum n-gram frequency of tokens to
                            extract (default=5)
      --positional-pos-filter POSITIONAL_POS_FILTER [POSITIONAL_POS_FILTER ...]
                            specify consecutive regular expressions to match to
                            the POS fields of tokens (Ex. '.*' '記号' to match any
                            POS followed by a symbol)
      --features FEATURES [FEATURES ...]
                            specify which features should be extracted from
                            morphemes (default is 'orth' 'pos')
      --features-sep [FEATURES_SEP]
                            specify the separator used to separate features
                            (default='/')
      --transpose [TRANSPOSE]
                            specify whether to transpose the output matrix or not
                            (default=False)
      --in IN [IN ...]      one or more input file(s) (must be plain text
                            formatted UTF-8 files)
      --out OUT             output file as n-gram frequency count matrix

# Example

If you have a set of UTF-8 formatted Japanese language files, you can extract all 2-grams combinations of any morpheme forming an bigram with a period or other sentence-ending marker by calling `ja-ngram` like so:

```bash
./ja-ngram --in *.txt --out test.csv --n 2 --positional-pos-filter '.*' '記号' --min-freq 2
```

This should output a file, `test.csv`, containing bigrams as columns and rows as files.