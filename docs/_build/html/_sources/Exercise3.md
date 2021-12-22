# DeepLabCut Notebook Demo


## How to get started
1. Installation of Anaconda and DeepLabCut environment
2. Start DeepLabCut either through the GUI or Jupyter Notebook
3. Take a minute to describe your dataset and research ideas
4. Manage your behavioral video data, e.g., split into trials
5. Create a new Project and load your behavioral video data
6. Define labeling markers and skeleton on your config.yaml file
7. Extract, label and check frames, before creating a training dataset
8. Train your model using a GPU 
9. Analyze your data and create labeled videos

## Starting DeepLabCut with Jupyter
1. Open Anaconda Prompt
2. conda activate DEEPLABCUT (environment)
3. jupyter notebook / jupyter lab / ipython
4. import deeplabcut ...

## Downloading Jupyter Notebooks
On the next page you will find a [Guided DeepLabCut Tutorial](https://guillermo-hidalgo-gadea.github.io/Seminar-TrackingAnimalBehavior/DLCjupyter.html), a jupyter notebook I prepared containing the most important steps needed to start your own project.
1. Download the notebook as .ipynb file
2. Rename the file and move it to your working directory
3. Open the notebook with jupyter lab or notebook
4. Start taking notes and make the notebook yours 

## How does it work
```{figure} content/dlcworkflow.png
---
width: 800px
name: dlc_workflow
---
DeepLabCut workflow from Nath et al. 2019.
```

## Troubleshooting

```{admonition} Student contribution
:class: tip
The following tips and tricks were put together with the help of students during real troubleshooting in course exercises. Thank you for your contribution! 
```

:::{admonition} How do I get help?
:class: question, dropdown
1. Check out the known issues reported on [GitHub](https://github.com/DeepLabCut/DeepLabCut/issues) using keywords from your error messages. 2. Read the [GitHub Documentation](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues) for best practices on how to open new issues.
3. Go through the tips and tricks sections in the [Documentation](https://deeplabcut.github.io/DeepLabCut/docs/intro.html) to find any errors in your procedure or code.
:::

:::{admonition} Example Question?
:class: question, dropdown
Custom Answer. Student assignment for day 4. 
:::