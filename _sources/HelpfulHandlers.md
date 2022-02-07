# Helpful Handlers

This section of the course handbook has been provided as part of the final group project for the Seminar on Tracking Animal Behavior at the Ruhr-University Bochum in WS21/22.

```{admonition} Project Authors
Sarah, `B.Sc. Psychology`, and Sarah, `B.Sc. Psychology`.
```

## Abstract

In our project we wanted to train a DeepLabCut model to recognize the human right hand and track several hand movements. Therefore, we collected our own video data using a smartphone camera. To reduce the complexity of the model, we decided to focus only on the right hand. We defined specific movements and different actions that we wanted to track and gathered five different types of video footage:

1. Basic hand movement: Simple turning movements of the right hand around its own axis (left, right, up and down). Some grabbing movements and movement of individual fingers.

2. Playing piano: Movements of the right hand when playing some accords/ melody on the keyboard of a piano.

3. Typing on keyboard: Movements of the right hand when typing on the keyboard of a laptop.

4. Writing by hand: Movement of the right hand when writing a text.

5. Waving: Waving and some grabbing movements of the right hand.

We collected two videos per hand per movement type. This resulted in a total collection of 10 videos. For tracking the hand, we decided to set 20 markers. For manual video labeling we decided to extract 10 frames per video.

For our final analysis we were interested in comparing the trajectories of the tracking points of the fingers in the three video types "Waving", "Playing piano" and "typing". We also compared the changes in position of the index finger tip by time in these three different video types.

## Model Evaluation

```{figure} content/helpfulhandlersfig0.svg
---
width: 900px
name: helpfulhandlersfig0
---
Sample of test and training frames from `deeplabcut.evaluate_network()`
```

## Data Analysis

Depicted below are the trajectory plots as they are outputted by DeepLabCut plus a similar trajectory plot for a single label (IT(IndesTip)) that was manually created using matplotlib for three exemplary videos.

```{figure} content/helpfulhandlersfig1.svg
---
width: 600px
name: helpfulhandlersfig1
---
```

```{figure} content/helpfulhandlersfig2.svg
---
width: 600px
name: helpfulhandlersfig2
---
```

```{figure} content/helpfulhandlersfig3.svg
---
width: 600px
name: helpfulhandlersfig3
---
```
