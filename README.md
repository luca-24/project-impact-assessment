# Project Impact Assessment
Estimate the impact of Innovation &amp; Development projects as their relevance w.r.t. the United Nations' Sustainable Development Goals.

This repository contains the code based on the paper "Estimating the Expected Impact of Research \& Innovation Projects".

## Abstract

A rising application area in the context of Big Data and Artificial Intelligence is the development of tools that can support the decision-making process of research &amp; innovation (R&amp;I) activities, including the evaluation of requirements, the monitoring of throughput and the assessment of short- and long-term results. In particular, estimating the impact that an R&amp;I project will have in the future is a challenging task, due to the wide variety of factors that can favour or, conversely, hinder its success. In addition, there are several - often conflicting - dimensions that should be included in the assessment of the impact, including (but not limited to) the scientific, economic, societal and environmental dimensions. In this work, we propose an algorithmic approach, based on Natural Language Processing and Machine Learning, that predicts the relevance of a project with respect to the 17 "Sustainable Development Goals" set by the United Nations, which in recent years have come to represent a recognized benchmark in impact evaluation. The algorithm exploits BERT word-embeddings to represent the projects' abstracts and the goal descriptions in a vector space that captures their semantics; a set of similarity scores is computed between the projects and the goals and, consequently, is fed into a multi-label classifier, which produces the final ranking of goals for each project, sorted by relevance. The experimental validation, performed on a real-world dataset, shows that our approach is effective at producing accurate rankings of goals and that it outperforms other state-of-the-art methods in terms of ranking precision.

## Usage

It is recommended to install the requirements in a Python virtual environment to avoid modifying system state. 
```bash
python -m venv .env
source .env/bin/activate

```
Execute the following commands to install the requirements.
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

## Notebooks

The code to execute the algorithms described in the paper is contained in the following Jupyter notebooks:
- ``data_preparation.ipynb``: pre-processing and cleaning of the data.
- ``evaluation.ipynb``: metrics to evaluate the classification.
- ``explanation.ipynb``: detection of relevant words and sentences in project abstracts.
- ``matching_algorithm.ipynb``: baseline approach described in the paper.
- ``nlp_functions.ipynb``: Natural Language Processing for project and goal descriptions.
- ``supervised_approaches.ipynb``: set of approaches based on supevised classifiers.
- ``utils.ipynb``: utility functions.

## Data

The datasets used in the experimental section of the paper are publicly availbale through the following resources:

### RIS3-MCAT

Data platform of the Generalitat de Catalunya, which makes available the data of European projects funded through Horizon2020 with Catalan participation: http://ris3mcat.gencat.cat/#/. 

The button "Descarrega en csc" in the header of the webpage allows downloading the whole dataset as a .csv file. This file is already available in the ``data`` folder of this repository as ``ris3-mcat-projects.csv``; the cleaned and filtered version with only English text, obtained after running the ``data_preparation.ipynb`` notebook, is available as ``ris3-mcat-projects-cleaned-en.csv``.

### Sustaibable Development Goals

Official page of the United Nations, describing the 17 goals that represent "the blueprint to achieve a better and more sustainable future for all. They address the global challenges we face, including poverty, inequality, climate change, environmental degradation, peace and justice". https://www.un.org/sustainabledevelopment/sustainable-development-goals/

The textual information about the goal has been manually extracted for each goal (for example, from https://www.un.org/sustainabledevelopment/poverty/) from the general introduction at the top of the page and from the sections "Facts and Figures" and "Goal X Targets". This data is available in the ``data`` folder of this repository as ``un-goals.xlsx``.
