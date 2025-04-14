## FactScore
The repository is an enhanced version of the [original factscore](https://github.com/shmsw25/FActScore), an evaluation pipeline that breaks a LLM generation into a series of atomic facts and computes the percentage of atomic facts supported by the provided database.
See more about the pipeline in factscorer.py.

The changes made are significant:
1. matching titles from the database are searched by embeddings distances rather than by character-level comparison as in the original.
2. you may not pass topic of the generation explicitly: the titles will be found for each generation fact itself.
3. all api requests are sent asynchronously that dramatically reduces the execution time: 5.5 seconds for a batch of three one-sentence generations.
4. you can provide any knowledge source you want (one restriction: it should be json-file), the appropriate database will be created automatically

## Prerequisites
1. json-file with the knowledge source information (see more on its format in database.py)
2. embeddings of the knowledge source titles and trained faiss index for them (see more in create_faiss_index.py)
3. libraries defined in requirements.txt
