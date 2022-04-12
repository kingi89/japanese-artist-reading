# japanese-artist-reading

Kanji reading dictionary for Japanese artists (etc) to be used with [Kakasi](http://kakasi.namazu.org/index.html.en). Useful for e.g. getting the correct rōmaji reading of your currently playing artist's name.

The repository has two main files with identical contents, but with different encoding:

* jar-dictionary.txt: UTF-8
* jar-dictionary.euc.txt: EUC-JISX0213

To use, pass the `jar-dictionary.euc.txt` to `kakasi` as an additional dictionary (*jisyo1*); for example:
```sh
echo "南条愛乃" | kakasi -i utf-8 -o utf-8 -Ha -Ka -Ja -Ea -ka -s jar-dictionary.euc.txt
# nanjou yoshino
```

See `kakasi(1)` for general usage of Kakasi.

To convert the files from one to another, `iconv` can be used:

```sh
iconv -f UTF-8 -t EUC-JISX0213 jar-dictionary.txt >jar-dictionary.euc.txt
```

## About this dictionary and its criteria

This dictionary contains reading-kanji pairs for personal and proper names. To be considered to be included, the name must meet these requirements:

1. It is a name (or a part of) of a person or unit credited in at least one published musical piece:
  - an artist (real name or pseudonym)
  - a music group, unit or band
  - a composer, lyricist or arranger
2. It is written in Japanese characters (kanji, hiragana, katakana) only, and at least one of the characters is a kanji
3. Kakasi's default dictionary does not have a correct reading for it
4. There doesn't exist a more common general reading for the name
