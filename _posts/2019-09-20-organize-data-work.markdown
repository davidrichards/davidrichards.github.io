---
layout: post
title:  Organize Data Work
summary: Some notes on making data work reproducible.
date:   2019-09-20-13:46:28
categories: raw
---
## Learn to Organize

Taking advantage of the insights we generate requires some organization. Use Jupyter Notebooks with some organization around file location, version, version control, code modules, and tests so our experiments can incrementally develop into higher quality tools.

[Serban, 2019]

### Experiment in Loops

By treating experiments as loops, we can organize our work.

There are treatments and there are subjects. Both are lists. For every treatment, for every subject, run an experiment. That looks like a nested loop.

Create a single function that will call each treatment for a given subject. The treatment might be a data visualization, or a data model, or a metric. Whatever it is, wrapping function will call it. Side effects are necessary at this level to save experiment results.

[Serban, 2019]

### Organize and Link Notebooks

Using a description and an index, the many notebooks we create can be organized better. For example nlp_00 could be the first NLP notebook, and nlp_01 could be the second. This makes it easier to find code and check what's been written.

Create links by first creating anchor tags:

    <a id="some_label"></a>
    
Then link to it within the notebook:

    [Reference Text](#some_label)

Or reference it from another notebook:

    [Reference Text](other_notebook_01.ipynb#some_label)

[Serban, 2019]

### Organize Data and Logs

Keep data in a local data folder. Use consistent versions if there are copies.

For every experiment, log it in a separate spreadsheet. This way we don't have to read all of the notebooks to find out what we've done. Record the model, what it's for, the inputs, and the outputs.

[Serban, 2019]

### DRY

The DRY principle, Don't Repeat Yourself, means you start to write functions, and then organize your functions, then create classes, and reuse your code in many ways. You can save your code in regular `.py` files, (or use the extraction code from FastAI to extract code cells into `.py` files).

Defaults should be used to hide some of the complexity of the code.

[Serban, 2019]

### Remain Reproducible

Make sure your work is reproducible. 

Keep the version of code used in experiments with the experiments, but keep the reusable functions in modules and separate from the experiment code that handles treatments, subjects, and explanations.

Then, store the code in git and include a bash shell script in a cell that changes directories to where the code is stored and checks out the correct version of the code to reproduce the experiments.

Eventually these modules will become Python packages ready to share with others.

[Serban, 2019]

### Write Tests

Learn to write unit tests, even test-driving some of your code.

(Test-driving code means you write a test for code you wish you had, then write the code to make the tests pass, then clean the code if you see anything you can improve. This is called red, green, refactor in some books and articles.)

With tests, it's easier to share, maintain, and improve the code we are writing.

[Serban, 2019]


## References:

Serban, V. (2019, September 20). How to organize code in Python if you are a scientist. Retrieved September 19, 2019, from Medium website: https://towardsdatascience.com/workflow-for-reportable-reusable-and-reproducible-computational-research-45d036c8a908


