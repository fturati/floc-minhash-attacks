
The files `movielens_extractor.py` and `tranco_preprocessor` do not need to be run individually. The necessary functions will be called when needed elsewhere.

An example to run the main function of tranco_preprocessor and movielens_extractor:
```shell
# assuming terminal starts in this directory
cd ../..
python -m FLoC.preprocessing.tranco_preprocessor
python -m FLoC.preprocessing.movielens_extractor
python -m FLoC.preprocessing.vocab_corpus_builder
```

However, if changes to the generation of the training and test data for the GAN are to be made the file `vocab_corpus_builder.py` needs to be run.
Some part of the file `vocab_corpus_builder` are taken and adapted from [TILGAN](https://github.com/shizhediao/TILGAN/blob/main/unconditional_generation/utils.py) by [@shizhediao](https://github.com/shizhediao).
TILGAN was also tried in addition to LeakGAN, however we had better results when experimenting with LeakGAN.