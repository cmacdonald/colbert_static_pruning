# ColBERT - Static Pruning

This repository is the virtual appendix for the paper ``The Reasonable Efficacy of IDF in Multi-Representation Dense Retrieval Pruning'' (Under Review).

It makes use of [PyTerrier](https://github.com/terrier-org/pyterrier/) and [PyTerrier_ColBERT](https://github.com/terrierteam/pyterrier_colbert) to demonstrate the power of static-pruning methods for reducing ColBERT indices without loss of effectiveness.


## Notebooks

This repository contains four notebooks:
 - [idf-pruning.ipynb](notebooks/idf-pruning.ipynb) - PyTerrier notebook to run the Original, IDF doc-centric and IDF-uniform approaches from Section 5.1, as well as create the indices for Section 5.2.
 - [baseline-pruning.ipynb](notebooks/baseline-pruning.ipynb) - PyTerrier notebook to run the random doc-centric and stopword approaches from Section 5.1.
 - [pruned-indices.ipynb](notebooks/pruned-indices.ipynb) - PyTerrier notebook to create the runs for the indices in Section 5.2.
 - [results-analysis.ipynb](notebooks/results-analysis.ipynb) - PyTerrier notebook to create the figures for Section 5.1.

## Index

In order to run the above notebooks, you will require a PyTerrier ColBERT index of the MSMARCO v1 passage ranking corpus. This can be created using the following PyTerrier code:

```python
import pyterrier as pt
from pyterrier_colbert.indexing import ColBERTIndexer
checkpoint="http://www.dcs.gla.ac.uk/~craigm/ecir2021-tutorial/colbert_model_checkpoint.zip"
indexer = ColBERTIndexer(checkpoint, "/path/to/index", "index_name", chunksize=3)
indexer.index(pt.get_dataset("msmarco_passage").get_corpus_iter())
!ln -s /path/to/index/index_name/ivfpq.262144.faiss /path/to/index/index_name/ivfpq.faiss 
```
Space consumption of the final index is 185GB, as mentioned in the paper.

## Run Files

## Citation

To follow.

## Credits

 - Antonio Acquavia, University of Pisa
 - Craig Macdonald, University of Glasgow
 - Nicola Tonelloto, University of Pisa
