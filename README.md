
<h1 align="center">
  bio_anotator
</h1>



<p align="center"><b>bio_anotator</b> is a deep-learning based tool for <b>information extraction</b> in the biomedical domain.
</p>


## Installation

_Note! This is a work in progress. Many things are broken, and the codebase is not stable._

To install bio_anotator, you will need `python3.6`.
install setup.py


### Web-service

To use bio_anotator as a **local** web-service, run

```
(bio_anotator) $ python -m bio_anotator.cli.app
```



There are currently two endpoints, `/annotate/text` and `/annotate/pmid`. Both expect a `POST` request with a JSON payload, e.g.,

```json
{
  "text": "The phosphorylation of Hdm2 by MK2 promotes the ubiquitination of p53."
}
```

or

```json
{
  "pmid": 11835401
}
```

For example, running the web-service locally and using `cURL`

```sh
$ curl -X POST 'http://localhost:5000/annotate/text' \
--data '{"text": "The phosphorylation of Hdm2 by MK2 promotes the ubiquitination of p53."}'
```


### Pre-trained models

First, import the `bio_anotator` class. This is the interface to bio_anotator

```python
from bio_anotator.bio_anotator import bio_anotator
```

then create a `bio_anotator` object

```python
bio_anotator = bio_anotator()
```

and then load the model of our choice

```python
bio_anotator.load('PRGE')
```

To annotate text with the model, just call the `bio_anotator.annotate()` method

```python
bio_anotator.annotate("The phosphorylation of Hdm2 by MK2 promotes the ubiquitination of p53.")
```


You can also call `help()` on any bio_anotator method for more information

```python
from bio_anotator import bio_anotator

bio_anotator = bio_anotator()

help(bio_anotator.annotate)
```

or pass the `--help` flag to any of the command-line interfaces

```
python -m src.cli.train --help
```






