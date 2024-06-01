# Evaluating the Impact of Linearized Attention vs Full-Attention in Graph Transformers

This project aims to investigate the impact of linearized attention mechanisms compared
to the conventional full-attention mechanism.
Specifically we explore [Linformer](https://arxiv.org/abs/2006.04768) and [Performer](https://arxiv.org/abs/2009.14794) adaptations from NLP to the graph domain.

## Abstract

Transformers have revolutionized the field of Natural Language Processing (NLP). Its success has inspired adaptations across various domains, including graph representation learning. However, the conventional full-attention mechanism employed by transformers, suffers from quadratic time and memory complexity, which poses a challenge when dealing with large graphs. This project aims to assess the efficacy of linearized attention mechanisms in graph transformers, specifically comparing the traditional full-attention to the Linformer and Performer adaptations.

We evaluate the three mechanisms on three suitable benchmark datasets, based on their performance and efficiency. The findings show that while the full-attention model marginally outperforms the linearized models on most of the datasets, it requires significantly more memory on larger datasets. Our empirical evaluation indicates that the Performer model slightly surpasses the Linformer in performance, albeit at the cost of increased memory usage.

This research aims to make graph-based learning more scalable and efficient, thereby enabling broader application and research in this field.

## Getting started:

Start by cloning the repository:

```
git clone https://github.com/anna-charlotte/linearized-attention-in-graph-transformers.git
```

Or via SSH:

```
git clone git@github.com:anna-charlotte/linearized-attention-in-graph-transformers.git
```

If you don't already have Poetry installed, by running the following command.
More information on this can be found in the
[Poetry Documentation](https://python-poetry.org/docs/).

```
pip install poetry
poetry install --all-extras
```

Activate the virtual environment with:

```
poetry shell
```

You're now ready to replicate the study's findings.

## Reproduce results:

Running the following commands will retrain the specified model on a dataset of 
your choice.
```
python src/graph-transformer/run_train.py  --model-type {MODELTYPE} --dataset {DATASET}
```


Set the model using `--model-type {MODELTYPE}` to be one of 
`["full-attention", "linformer", "performer"]`.  \
It defaults to `full-attention"`.

Set the dataset using `--dataset {DATASET}` to be one of 
`["Citeseer", "Cora", "Pubmed"]`.\
It defaults to `Citeseer"`.



For example, the following retrains a linformer model on Citeseer:
```
python src/graph-transformer/run_train.py  --model-type linformer --dataset Citeseer
```


The evaluation scores are scored in `plots/plotting_{DATASET}.json`. 
To run the evaluation and plot the results, run:

```
python src/graph-transformer/plotting.py  --dataset {DATASET}
```

