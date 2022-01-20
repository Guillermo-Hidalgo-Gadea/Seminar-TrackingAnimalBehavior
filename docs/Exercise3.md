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

### Jupyter notebook related problems

:::{admonition} I am struggling to start DeepLabCut correctly, what to do?
:class: question, dropdown
DeepLabCut can be started as on a **jupyter notebook** by opening the anaconda prompt, activating your DeepLabCut environment and starting ```jupyter notebook``` or ```jupyter lab```. Then open the correct notebook and start executing your code cells. This method is recommended at the beginning to create a new project, extract frames, as well as for model training and analysis. The cell outputs can be saved in jupyter notebook and contain valuable information for later. When it comes to labeling frames though, jupyter notebook can be unresponsive when opening and closing the labeling GUI. Alternatively, DeepLabCut could be started as a **graphical user interface** by opening the anaconda prompt, activating your DeepLabCut environment and running ```python -m deeplabcut```. If you are already working from a jupyter notebook, run ```deeplabcut.launch_dlc()``` to start the GUI from the same notebook. Remember to keep track of output messages in the terminal window.  
:::

:::{admonition} How can I find specific commands in my Jupyter Notebook?
:class: question, dropdown
Your jupyter notebook might be a little difficult to navigate, especially at the beginning. Try making your life a little easier by using markdown cells to comment your code and create a reproducible workflow. Add ```#Title 1``` and ```##Title 1.1``` as well as informative text and notes on how to use the notebook and what each code cell is supposed to do. Remember to add your name to the notebook if you intend to share it with others, and give credit when using open source materials. 
:::

:::{admonition} Jupyter Notebook is not trusted
:class: question, dropdown
Some functions may not work properly if the juypter notebook is not trusted. Click the "not trusted" button to solve the problem. This may happen when you open a notebook from someone else. Make sure to rename the file, save it to your computer and log the changes you do by e.g., adding your name as contributor or author, or changing the date.
:::

:::{admonition} Jupyter Notebook is not responding
:class: question, dropdown
In general, jupyter notebook indicates to be running by the orange sand clock icon in the browser tab. Within the notebook, every code cell is denoted by ```In [ ]:```. While running the cell, the label turns to ```In [ * ]:``` to indicate work in progress. After the process is finished, the cell is numbered ```In [ 1 ]:``` to show the order in which the code cells were executed.  
Sometimes jupyter notebook looks non-responsive but is actually running code in the background. Try to use ```print()``` commands regularly to show some progress in long loops.  
If jupyter notebook is really not responding, you can try interrupting and restarting the kernel. If that does not work either, save the notebook, close the jupyter tabs and kill the process in the terminal with ```Ctr + c```. Then start jupyter notebook again.  
:::


### Data Management tips

:::{admonition} Plan your video recording setting in advance!
:class: question, dropdown
Consider lighting, camera position and video quality before you start your experiment. Camera position and lighting are crucial, when it comes to tracking. Testing the setup to see if it produces a good video before starting the experiment will make your life a lot easier afterwards. Make sure you see everything you want to track (e.g. no body parts are out of frame) and that lighting doesn't produce too many shadows or interferes with identifying body parts. If possible, also make sure there is not to much happening in the background which could be confused in tracking. Playing around with the setup at the beginning might safe you a lot of time afterwards.
:::

:::{admonition} How much video data do I need?
:class: question, dropdown
It depends on what you want to analyze. The easiest and safest would be for you to train a model with all the videos you want to analyze. If that does not work, make sure to have enough videos representative for the entire dataset. For freely moving animals this becomes especially challenging, as you may need video clips from different perspectives. Many videos will only show one side of the animal (2D plane) so at every time point the opposite side stays occluded. By using videos filmed from many different perspectives it’s easier to label everything and capture many angles and body parts.
:::

:::{admonition} Some steps in DeepLabCut take very long!
:class: question, dropdown
Data analysis is a slow process, and should be done carefully. Especially when dealing with large videos or big datasets simple tasks such as copying files from one folder to the other may take hours!  
Some steps such as extracting frames, training a model, and analyzing videos may take very long. Try to plan ahead and let your computer work over night or even over the weekend. 
:::

:::{admonition} How can I compare two models trained on same data?
:class: question, dropdown
The process of extracting frames, e.g., with ```Kmeans``` or creating a training set is stochastic, and will be different every time. What if I want to use the same frames and training set for two different projects? Create a single project first, edit the config.yaml and extract frames. Then duplicate the entire project directory on your computer with a new project name (**note:** remember to update the project name in the config.yaml file, e.g., ```project_path```). To create the training set...

On the other hand, if you want to train two different models, e.g., ```resnet-50``` and ```resnet-101```, use the function ```deeplabcut.create_training_model_comparison()``` to create the same training set for different model architectures.
:::

### Config.yaml related errors

:::{admonition} System cannot find path specified
:class: question, dropdown
Check again the correctness of the path you provided. If the file exists and the path is pointing correctly to it, check the direction of slashes used. Windows naturally uses backslashes for file paths, but these are not allowed in python. Try manually changing the path to forward slashes (e.g., ```C:/Users/Directory/```) or double backslashes (e.g., ```C:\\Users\\Directory\\```). Alternatively, you can use Tkinter as a filedialog to format your directory paths correctly.
:::

* path not found
check the correctness, direction of slashes see windows and linux differences

* choosing project name 
don't use spaces in names and directory

* index error defining skeleton
defining skeleton with more than two body 

- "IndexError: list index out of range"
     --> there mustn't be more than two bodyparts in a skeleton
connection
     --> solution: combine only two bodyparts and watch out for indexing

### Labeling related problems
* multi animal labeling with many occluded markers
use more labels to cover more info, multiple individuals need to have similar marker positions for body parts
having more than 106 frames

* appropriate number id
use multiple videos better than less videos 

1. What should we do if many of the joints we want to mark are covered
or cut off?
  -> use more points to still have an idea of how the individuals move
2. What has to be kept in mind when we use many different angles and
multiple people are involved in labeling?
  -> Be very clear on how you "define" e.g., the top of the head -
otherwise this point will move a lot and cause problems later on
3. If you have multiple animals -> make sure that the names are
different enough so you don't confuse them half way through the labeling
prowess

* marker definition
use group to discuss marker positions 

* anatomy of animal, real skeleton, changing body form
read papers with known skeletons

Unable to identify tracking points on the frames
Solution: Inform yourself about the anatomy of the animal before
defining tracking points. Pay especial attention to how certain body
parts look differently when the animal does certain movements (e.g.
wings applied vs wings spread). Also, check if other researcher already
track the same or a similiar animal and read in their papers, how they
defined the tracking points.

* how many labels are needed 
discuss in group and conduct

labeling of the running
video of the cheetah. Since the video was shot in the savannah and the
cheetahwas running, the movements, especially the legs, were a bit
blurry and therefore you had the impressions that it was also part of
the savannah ground. This makes the labeling a bit more difficult,
especially the legs.

Solution: I worken with my partner on one computer and we labeled
together. So we could better divide what belonged to the animal and what
not. The labeling was much easier.

* Different Group Members identify the tracking points on slightly different locations
Solution: When possible, only one Group member should track the points,
so its uniformly. If you need/want to track as a group, practice
beforehand by disscussing together how you would label some
example-frames.

* direction of labels right and left, front and back
focus on a routine (top to bottom and left to right)

 It’s easy to get confused with the right and left side and label parts wrongly or misplace labelling marks.
-> solution: by setting a fix order that is oriented on the body anatomy or goes from one side to another or from top to bottom it can help you to orientate the labelling on this order so you won’t mess up.

### System related problems

* problems with operating system

* error training model
GPU needed or good CPU, cloud based GPU


2) If you try to train your network and no updates happen in your conda
feed, your processing power is too low probably. You could a) ask
someone with a gpu to train your network, b) use a cloud based gpu or c)
buy a pc with a gpu. However, you need to download a new dlc version
where your gpu is used: dlc ~ gpu. This is a little different and
requires a few more installations.

Be aware that some coding syntax and programs can differ between
operating systems (e.g. anaconda prompt on Windows vs. general terminal
on macOS). Also keep in mind that you might need to perform additional
steps depending on your setup. It might be necessary to allow access to
different things (your computer screen, or even to access python). This
is your computer and you will have a harder time finding your problem
online if its not related to the "general" code.
