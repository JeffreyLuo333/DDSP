# DDSP-VST
<img src="images/DDSP-VST.jpg" width="750" height="250"> 

To explore the capabilities of a novel AI-driven sound synthesizer, renowned for its unique prowess in transforming any sound into diverse instrumental tones while maintaining the intricacies of pitch and dynamics, I engaged in an experiment. I trained a Differentiable Digital Signal Processing VST neural synthesizer specifically for cello using a 10-minute soundtrack featuring the instrument. Subsequently, I played the piano, and the synthesizer seamlessly converted my piano tones into the deep, vibrant timbres of a cello, showcasing the technology's transformative potential.

## About this document

This document has following three sections:
- <a href="#transform-the-familiar-into-the-unexpected">Transform the familiar into the unexpected</a>,
- <a href="#play-it-like-a-synth">Play it like a Synth</a>,
- <a href="#training-and-using-customized-model">Training and using customized model</a>.

## Transform the familiar into the unexpected
I have been experimenting with the transformative capabilities of DDSP, using AI singer Merrow's singing recordings as input for the DDSP flute and trumpet modules. This has resulted in a wide spectrum of timbres that diverge significantly from the original voice.
```diff
- Unmute the speaker in the video clip to listen to the ~5 second recording.
```
- __Merrow Solo:__
  
https://github.com/JeffreyLuo333/DDSP-VST/assets/114297879/cd875813-750a-409d-a1e8-5776a280acbc

- __Transform Merrow to Flute:__

https://github.com/JeffreyLuo333/DDSP-VST/assets/114297879/b2b01e89-8424-491a-82c2-c72fe38b1048

- __Transform Merrow to Trumpet:__

https://github.com/JeffreyLuo333/DDSP-VST/assets/114297879/da4be448-40f4-454f-bfe2-357b4360197a

## Play it like a Synth
I utilized the DDSP-VST in a manner similar to a conventional VST for my investigative purposes. In this exploration, I employed two instruments, namely a violin and a cello, which I personally trained, to facilitate the comparison. The outcomes derived from the DDSP-VST were evaluated against two other VST plugins from Studio, which i sample-based, and SWAM, which is based on phsyical model.
__(<span style="color: red;">Unmute the speaker in the video clip to listen to the ~10 second recording.</span>)__

### Cello:  
- __DDSP Violin VST__
  
https://github.com/JeffreyLuo333/DDSP-VST/assets/114297879/f2eec8f9-be95-406f-bf7e-c12de8843e1d

- Studio Violin VST
  
https://github.com/JeffreyLuo333/DDSP-VST/assets/114297879/c46910e1-30b9-484c-aba3-90023acfe229

- __SWAM Violin VST__
  
https://github.com/JeffreyLuo333/DDSP-VST/assets/114297879/d45f85f4-fb9d-4a58-91e2-3053262c99c3

### Violin: 
- __DDSP Cello VST__

https://github.com/JeffreyLuo333/DDSP-VST/assets/114297879/d707f775-8f7c-4f97-ae65-5fbf365c825d

- __Studio Cello VST__

https://github.com/JeffreyLuo333/DDSP-VST/assets/114297879/9bca26ee-48bb-43af-842c-1e497573cbf5

- __SWAM Cello VST__

https://github.com/JeffreyLuo333/DDSP-VST/assets/114297879/ef965a42-f3a9-4b54-8016-a28023b9c83a

## Training and using customized model
### Environment Setup

- Upload the training_notbook.ipynb under notebook to https://colab.research.google.com/.

    [<img src="images/EnvSetup01.jpg" width="624" height="364">](https://colab.research.google.com/)

- After uploading the file, you will find cells containing code. Click on the ▶ button in the upper left corner to execute the first cell and set up the environment. Please wait until it's completed (a ☑ will appear in the upper left corner).

    <img src="images/EnvSetup02.jpg" width="624" height="88">

- You need to restart the runtime to continue.

    <img src="images/EnvSetup03.jpg" width="624" height="323">

- After restarting, execute cell 2 directly as shown in the screenshot below __(<span style="color: red;">DO NOT rerun the first cell</span>)__, and verify if the output matches the result displayed below:

     <img src="images/EnvSetup04.jpg" width="624" height="359">

### Prepare Data
If everything is functioning as expected, we can proceed to the final cell for training. However, before starting the training process, it's essential to upload your training audio files to Google Drive. Custom models can be trained effectively with as little as 10 minutes of audio data in either .wav or .mp3 format. For the best results, consider using "monophonic" audio, meaning there's only one note being played at a time. It's ideal to use audio from a single recording session with the same microphone and reverb settings for optimal training outcomes.

You need create a folder on your drive with your audio files in it, for example, I create a folder DDSP_training/CelloSuiteBach and put all mp3 files inside the folder:

<img src="images/PrepareData01.png" width="500" height="350">

### Start Training

Before we start training, we need set a name for our model in the 3rd cell:

<img src="images/StartTraining01.jpg" width="624" height="208">

Then press the ▶ button in the upper left of 3rd cell to start training, you will see some output of this cell and a popup ask for google drive permission, choose __<span style="color: red;">Connect to google Drive</span>__ to continue.

<img src="images/StartTraining02.png" width="500" height="200">

The output of the cell will let you pick your folder that contains your training data. Select the folder and training will automatically start.

<img src="images/StartTraining03.jpg" width="624" height="309">


<img src="images/StartTraining04.jpg" width="624" height="309">

You will observe output similar to the following during the training process. Please be aware that training can be time-consuming when using the free Colab service. If you happen to experience a disconnection, simply reconnect and follow the steps mentioned earlier, ensuring that you select the same folder. The training will continue from where it was paused or left off.

<img src="images/StartTraining05.jpg" width="624" height="152">

### Use the New Model
After the training is completed, the Colab should automatically export, compress (zip), and download your model folder. If the download doesn't start automatically, you can locate the model in your training folder with a name like __<span style="color: red;">ddsp-training-{date-time}/{Name}</span>__.

To use your model, you should unzip the folder and place the entire contents in the plugin model folder. On macOS, the plugin model folder path is typically __<span style="color: red;">Documents/Magenta/DDSP/Models</span>__. You can also access this folder within the plugin's panel.

<img src="images/NewModel01.png" width="400" height="500">
