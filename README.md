# Project: Using Visual Analytics to Identify Terrorists

In this project, our group implemented a visual analytics design supporting the user task of identifying possible suspects and potential plans for terrorist activity given a dataset of FBI and CIA intelligence documents, as well as related phone records.

To begin building our visual analytics tool, we created a Python notebook to preprocess the text data from the given files. We then created our visualizations and interactive web interface using [D3.js](https://d3js.org/), JavaScript, HTML, and CSS.

## Data Preprocessing Steps

First, we used the [spaCy](https://spacy.io/) Python library to help tokenize the given text files and recognize named entities. This procedure left us with over 200 relevant terms referring to entities in six categories: people, organizations, dates, locations, phone numbers, and bank account numbers. We then aggregated the data and converted it to a format conducive to visualization.

For each recognized term, we extracted four main pieces of information:
* The term’s category.
* A list of intelligence documents in which the term appears.
* A dictionary of related terms, where each related term is mapped to the number of intelligence documents in which it appears together with the main term.
* A pair of 2D coordinates encoding the term's relationship to the other recognized terms. Analysis and dimension reduction were performed with [scikit-learn](https://scikit-learn.org/)’s latent semantic analysis (or LSA) algorithm, based on a frequency matrix of related terms.

## Our Visual Data Exploration Tool

After exporting the preprocessed textual data to JSON—as well as the document filenames and content, we built a web-based visual analytics tool that supports multiple interactive functions.

![CSCI 680 Project 2 Overview](https://user-images.githubusercontent.com/59906090/205465662-1921cd78-4362-4432-85e2-a41a34db459e.png)

Actions that the user can take include the following:
* Hovering over a node displays the term it represents via a tooltip. All other nodes in the graph, except the node(s) the user has previously selected, are temporarily de-emphasized by turning gray.
* Clicking a node adds or removes a term from the user’s current selection. Connections to other nodes—visualized as lines, in the graph—are either highlighted or reset to their original color, depending on whether the node is being selected or deselected.
* Clicking a node also refreshes the display of corresponding text files below the graph. Each term in the user’s selection is highlighted in the document view.
* Clicking a checkbox at the top of the page filters the terms by category. Different category combinations are possible.
* Clicking a button at the top of the page clears the current state of the interactive tool so the user can start over.

Other features conveying information more implicitly include the following:
* Node colors represent the different term categories. The color scheme is mirrored in the document view for ease of reference.
* Node sizes represent the number of links a particular node has to other nodes in the graph. The larger the node, the more nodes it is related to.
* Link widths represent the strength of the relationship between any two nodes. The wider the line, the more intelligence documents the nodes it connects have in common.

## Code

Code available upon request.

## References

Li, T., Shah, A., Luther, K. and North, C., 2018. Crowdsourcing intelligence analysis with context slices. In Chi’18 Sensemaking Workshop.
