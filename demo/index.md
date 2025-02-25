---
layout: review
---

![abstract](figures/abstract.png)

<span style="color: black;">
<b>Abstract</b>: Auditory foundation models, including auditory large language models (LLMs), process all sound inputs equally, independent of listener perception. However, human auditory perception is inherently selective: listeners focus on specific speakers while ignoring others in complex auditory scenes. Existing models do not incorporate this selectivity, limiting their ability to generate perception-aligned responses. To address this, we introduce Intention-Informed Auditory Scene Understanding (II-ASU) and present Auditory Attention-Driven LLM (AAD-LLM), a prototype system that integrates brain signals to infer listener attention. AAD-LLM extends an auditory LLM by incorporating intracranial electroencephalography (iEEG) recordings to decode which speaker a listener is attending to and refine responses accordingly. The model first predicts the attended speaker from neural activity, then conditions response generation on this inferred attentional state. We evaluate AAD-LLM on speaker description, speech transcription and extraction, and question answering in multitalker scenarios, with both objective and subjective ratings showing improved alignment with listener intention. By taking a first step toward intention-aware auditory AI, this work explores a new paradigm where listener perception informs machine listening, paving the way for future listener-centered auditory systems.
</span>

<style>
  .table-container {
    overflow-x: auto;
    width: 100%;
  }
  table {
    width: max-content;
    border-collapse: collapse;
  }
  th, td {
    padding: 10px;
    border: 1px solid black;
    text-align: left;
    white-space: nowrap; /* Prevent text from wrapping */
  }
</style>

<style>
  .model-name {
    color: grey;
    font-weight: bold;
  }

  .model-name b {
    color: black;
  }
  
</style>

<hr style="height: 3px; background-color: grey; border: none;">

<div style="background-color: #FFF2E5; padding: 15px; border-left: 5px solid #FFB899; font-style: italic;">
In the clinical setting, the listener's brain signal is used to decode the attended speaker. We show example responses of AAD-LLM compared with responses of SALMONN and Qwen2-Audio. The <b>Oracle Answer</b> is the response of a finetuned Qwen2-Audio trained and evaluated on the oracle (ground-truth attended/unattended) speaker, representing the performance <b>upper bound</b>.
</div>

#### **Clinical Sample 1: Female and Male**
<div style="display: flex; align-items: center; gap: 20px;">
  <div>
    <b>🎧 Speech Mixture</b><br>
    <audio controls>
      <source src="samples/CS1/mix.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>💡 Attended Speech</b> (attention decoded from brain)<br>
    <audio controls>
      <source src="samples/CS1/att.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
</div>


<div class="table-container">
  <table>
    <tr>
      <th>Question 1</th>
      <th>Model Answers 1</th>
      <th>Question 2</th>
      <th>Model Answers 2</th>
      <th>Question 3</th>
      <th>Model Answers 3</th>
    </tr>
    <tr>
      <td>Who is the speaker that the subject is paying attention to?</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>The speaker is a woman.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>The specific identity of the speaker is unknown without additional context.</i> <br>
        <b>AAD-LLM</b>: <i>A female speaker with high pitch and normal tempo.</i>
      </td>
      <td>Transcribe the attended speaker.</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>We do offer sessions with our five minute personal trainers.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>um sandwich place with a five minute drive from this area.</i> <br>
        <b>AAD-LLM</b>: <i>We do offer sessions with our personal trainers.</i>
      </td>
      <td>What is the unattended speaker's speech about?</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>Offering sessions with personal personal trainers.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>The unattended speaker's speech is inaudible...</i> <br>
        <b>AAD-LLM</b>: <i>Tom's Sandwich Place is five minutes away.</i>
      </td>
    </tr>
    <tr>
      <td><b>Oracle Answer 1</b></td>
      <td><b>Oracle Answer 2</b></td>
      <td><b>Oracle Answer 3</b></td>
    </tr>
    <tr>
      <td><i>A female speaker with high pitch and normal tempo.</i></td>
      <td><i>We do offer sessions with our personal trainers.</i></td>
      <td><i>Tom's Sandwich Place is five minutes away.</i></td>
    </tr>
  </table>
</div>


#### **Clinical Sample 2: Female and Female**
<div style="display: flex; align-items: center; gap: 20px;">
  <div>
    <b>🎧 Speech Mixture</b><br>
    <audio controls>
      <source src="samples/CS2/mix.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>💡 Attended Speech</b><br>
    <audio controls>
      <source src="samples/CS2/att.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
</div>

<div class="table-container">
  <table>
    <tr>
      <th>Question 1</th>
      <th>Model Answers 1</th>
      <th>Question 2</th>
      <th>Model Answers 2</th>
      <th>Question 3</th>
      <th>Model Answers 3</th>
    </tr>
    <tr>
      <td>Please write down all words spoken by the attended speaker.</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>I'm a vintage changer to my second twentieth class cost.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>Mike gave a ginger to me on my twenty-first birthday.</i> <br>
        <b>AAD-LLM</b>: <i>My uncle gifted Ginger to me on my twentieth birthday.</i>
      </td>
      <td>What was the occasion for the gift?</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>The occasion for the gift is not mentioned in the given sentence.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>The occasion for the gift was Mike's birthday.</i> <br>
        <b>AAD-LLM</b>: <i>The occasion was my twentieth birthday.</i>
      </td>
      <td>Can you identify the person the subject is NOT listening to?</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>No, I cannot identify the person the subject is not listening to.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>Mike.</i> <br>
        <b>AAD-LLM</b>: <i>A female speaker with high pitch and normal tempo.</i>
      </td>
    </tr>
    <tr>
      <td><b>Oracle Answer 1</b></td>
      <td><b>Oracle Answer 2</b></td>
      <td><b>Oracle Answer 3</b></td>
    </tr>
    <tr>
      <td><i>My uncle gifted ginger to me on my twentieth birthday.</i></td>
      <td><i>The gift was given on the speaker's twentieth birthday.</i></td>
      <td><i>A female speaker with high pitch and normal tempo.</i></td>
    </tr>
  </table>
</div>

#### **Clinical Sample 3: Male and Male**
<div style="display: flex; align-items: center; gap: 20px;">
  <div>
    <b>🎧 Speech Mixture</b><br>
    <audio controls>
      <source src="samples/CS3/mix.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>💡 Attended Speech</b><br>
    <audio controls>
      <source src="samples/CS3/att.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
</div>

<div class="table-container">
  <table>
    <tr>
      <th>Question 1</th>
      <th>Model Answers 1</th>
      <th>Question 2</th>
      <th>Model Answers 2</th>
      <th>Question 3</th>
      <th>Model Answers 3</th>
    </tr>
    <tr>
      <td>What is the attended speech about?</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>A high school reunion.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>The high time to start thinking about having children.</i> <br>
        <b>AAD-LLM</b>: <i>Time to consider carbon neutrality options.</i>
      </td>
      <td>What phrase indicates urgency in the speaker's statement?</td>
      <td rowspan="3">
       <span class="model-name">SALMONN</span>: <i>I THINK IT IS HIGH TIME THAT WE START THINKING ABOUT THE NOT TOO DISTANT FUTURE.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>The phrase "it is high time that we start thinking about" indicates urgency.</i> <br>
        <b>AAD-LLM</b>: <i>The phrase "high time" indicates urgency.</i>
      </td>
      <td>In the unattended speech, on what floor does the speaker want the room?</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>The speaker wants the room on the top floor.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>The speaker wants the room on the ground floor.</i> <br>
        <b>AAD-LLM</b>: <i>The ninth floor.</i>
      </td>
    </tr>
    <tr>
      <td><b>Oracle Answer 1</b></td>
      <td><b>Oracle Answer 2</b></td>
      <td><b>Oracle Answer 3</b></td>
    </tr>
    <tr>
      <td><i>Time to consider carbon neutrality now.</i></td>
      <td><i>The phrase "high time" indicates urgency in the speaker's statement.</i></td>
      <td><i>The speaker wants the room on the ninth floor.</i></td>
    </tr>
  </table>
</div>

<hr style="height: 3px; background-color: grey; border: none;">

<div style="background-color: #FFF2E5; padding: 15px; border-left: 5px solid #FFB899; font-style: italic;">
For same-topic samples below, we replaced the background speaker with another speaker talking about the same topic as the foreground speaker. Therefore, selecting the correct speaker is necessary to answer the question correctly.
</div>

#### **Same-Topic Sample 1**

<div style="display: flex; align-items: center; gap: 20px;">
  <div>
    <b>🎧 Speech Mixture</b><br>
    <audio controls>
      <source src="samples/ST1/mix.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>💡 Attended Speech</b><br>
    <audio controls>
      <source src="samples/ST1/att.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>🔊 Distractor Speech</b><br>
    <audio controls>
      <source src="samples/ST1/uatt.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
</div>

<div class="table-container">
  <table>
    <tr>
      <th>Question</th>
      <th>Model Answers</th>
    </tr>
    <tr>
      <td>Listen to the attended talker: what is the address mentioned?</td>
      <td rowspan="3">
        <span class="model-name">Qwen2-Audio</span>: <i>The address mentioned is 378456 apartments north avenue.</i> <br>
        <b>AAD-LLM</b>: <i>Three Seven Eight three seven eight South Street, Apartment C.</i>
      </td>
    </tr>
    <tr>
      <td><b>Oracle Answer</b></td>
    </tr>
    <tr>
      <td><i>The address is three seven eight, three seven eight South Street, Apartment C.</i></td>
    </tr>
  </table>
</div>

#### **Same-Topic Sample 2**

<div style="display: flex; align-items: center; gap: 20px;">
  <div>
    <b>🎧 Speech Mixture</b><br>
    <audio controls>
      <source src="samples/ST2/mix.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>💡 Attended Speech</b><br>
    <audio controls>
      <source src="samples/ST2/att.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>🔊 Distractor Speech</b><br>
    <audio controls>
      <source src="samples/ST2/uatt.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
</div>

<div class="table-container">
  <table>
    <tr>
      <th>Question</th>
      <th>Model Answers</th>
    </tr>
    <tr>
      <td>Listen to the attended talker: how often does the speaker go hiking?</td>
      <td rowspan="3">
        <span class="model-name">Qwen2-Audio</span>: <i>The speaker goes hiking rarely.</i> <br>
        <b>AAD-LLM</b>: <i>The speaker goes hiking very often.</i>
      </td>
    </tr>
    <tr>
      <td><b>Oracle Answer</b></td>
    </tr>
    <tr>
      <td><i>The speaker goes hiking very often.</i></td>
    </tr>
  </table>
</div>

#### **Same-Topic Sample 3**

<div style="display: flex; align-items: center; gap: 20px;">
  <div>
    <b>🎧 Speech Mixture</b><br>
    <audio controls>
      <source src="samples/ST3/mix.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>💡 Attended Speech</b><br>
    <audio controls>
      <source src="samples/ST3/att.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>🔊 Distractor Speech</b><br>
    <audio controls>
      <source src="samples/ST3/uatt.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
</div>

<div class="table-container">
  <table>
    <tr>
      <th>Question</th>
      <th>Model Answers</th>
    </tr>
    <tr>
      <td>Listen to the attended talker: what does the speaker imply about the progress toward space travel?</td>
      <td rowspan="3">
        <span class="model-name">Qwen2-Audio</span>: <i>The speaker implies that space travel remains a distant dream despite recent advancements in private space companies.</i> <br>
        <b>AAD-LLM</b>: <i>The speaker implies that there has been significant progress made by private companies in making space travel more feasible.</i>
      </td>
    </tr>
    <tr>
      <td><b>Oracle Answer</b></td>
    </tr>
    <tr>
      <td><i>The speaker implies that there is significant progress being made in achieving their dreams of floating in space.</i></td>
    </tr>
  </table>
</div>

<hr style="height: 3px; background-color: grey; border: none;">

<div style="background-color: #FFF2E5; padding: 15px; border-left: 5px solid #FFB899; font-style: italic;">
AAD-LLM can also run without the brain signal. Users need to provide the speaker vector (label) of the target speaker. We show examples of responses on synthetic LibriTTS + DEMAND speech mixtures with one of the speakers chosen as the target.
</div>

#### **LibriTTS+DEMAND Sample 1**

<div style="display: flex; align-items: center; gap: 20px;">
  <div>
    <b>🎧 Speech Mixture</b><br>
    <audio controls>
      <source src="samples/OL1/mix.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>💡 Attended Speech</b> (by user-provided speaker label)<br>
    <audio controls>
      <source src="samples/OL1/att.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
</div>

<div class="table-container">
  <table>
    <tr>
      <th>Question 1</th>
      <th>Model Answers 1</th>
      <th>Question 2</th>
      <th>Model Answers 2</th>
      <th>Question 3</th>
      <th>Model Answers 3</th>
    </tr>
    <tr>
      <td>ASR the attended speaker.</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>Somewhere however the desire for these changes must arise in the minds of individuals. The old man turned around and around carefully examined and discovered on the napkin a ring several strange red characters.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>The old man turned around, examined the ground carefully, and discovered on the napkin several strange red characters.</i> <br>
        <b>AAD-LLM</b>: <i>Somewhere, however, the desire for these changes must arise in the minds of individuals.</i>
      </td>
      <td>ASR the unattended speaker.</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>Somewhere however the desire for these changes must arise in the minds of individuals. The old man turned around and around carefully examined and discovered on the napkin a ring several strange red characters.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>The old man turned to ground and round carefully examined it discovered on the napkin several strange red characters.</i> <br>
        <b>AAD-LLM</b>: <i>The old man turned it round and round, carefully examined it, and discovered on the nape of its neck several strange red characters.</i>
      </td>
      <td>Describe the attended speaker.</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>The attended speaker is describing the examination of changes on the nape of the neck in several strange red characters. Somewhere however the desire for these changes must arise in the minds of individuals.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>The speaker is male, speaks English, and conveys a disgusted mood in his speech.</i> <br>
        <b>AAD-LLM</b>: <i>A male speaker with normal pitch and low tempo.</i>
      </td>
    </tr>
    <tr>
      <td><b>Oracle Answer 1</b></td>
      <td><b>Oracle Answer 2</b></td>
      <td><b>Oracle Answer 3</b></td>
    </tr>
    <tr>
      <td><i>Somewhere, however, the desire for these changes must arise in the minds of individuals.</i></td>
      <td><i>The old man turned it round and round, carefully examined it, and discovered on the nape of its neck several strange red characters.</i></td>
      <td><i>A male speaker with normal pitch and low tempo.</i></td>
    </tr>
  </table>
</div>

#### **LibriTTS+DEMAND Sample 2**

<div style="display: flex; align-items: center; gap: 20px;">
  <div>
    <b>🎧 Speech Mixture</b><br>
    <audio controls>
      <source src="samples/OL2/mix.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>💡 Attended Speech</b><br>
    <audio controls>
      <source src="samples/OL2/att.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
</div>

<div class="table-container">
  <table>
    <tr>
      <th>Question 1</th>
      <th>Model Answers 1</th>
      <th>Question 2</th>
      <th>Model Answers 2</th>
      <th>Question 3</th>
      <th>Model Answers 3</th>
    </tr>
    <tr>
      <td>What is the main subject of the attended speaker's speech?</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>Not specified in the given sentences. I shut the queen up in the bath and tried to suffocate her and the old woman had her own ugly daughter and twilight gathered that the happy family did not know together where she was.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>Not specified in the provided subtitles.</i> <br>
        <b>AAD-LLM</b>: <i>Old woman hides daughter from king.</i>
      </td>
      <td>Can you provide an overview of what the unattended speaker is saying?</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>And shut the queen up in the bath and tried to suffocate her father and the guests had their own ugly daughter and twilight gathered that the happy family did not know she was alive. I swear i've been crying but the girls would not leave her so woman with her abandoned daughter in the twilight bathed and came and sat together round the fire.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>A shut up had been placed in front of the bath and tried to suffocate her and the old woman for her own ugly daughter and in the queen's bed that the king might not know she was away.</i> <br>
        <b>AAD-LLM</b>: <i>Guests left as family gathered by fire.</i>
      </td>
      <td>What was the intention of shutting the queen up in the bath?</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>The intention was to suffocate the queen and her father.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>The intention was to prevent the queen from leaving, as the girls would not let her go without their father.</i> <br>
        <b>AAD-LLM</b>: <i>The intention was to suffocate her.</i>
      </td>
    </tr>
    <tr>
      <td><b>Oracle Answer 1</b></td>
      <td><b>Oracle Answer 2</b></td>
      <td><b>Oracle Answer 3</b></td>
    </tr>
    <tr>
      <td><i>Queen imprisoned, daughter hidden from king.</i></td>
      <td><i>Guests left early; family gathered by fire.</i></td>
      <td><i>They tried to suffocate her.</i></td>
    </tr>
  </table>
</div>

<hr style="height: 3px; background-color: grey; border: none;">

<div style="background-color: #FFF2E5; padding: 15px; border-left: 5px solid #FFB899; font-style: italic;">
AAD-LLM may fail if two speakers are too similar in acoustic, making it hard to decode and select the attended speaker, as shown in the example below.
</div>

#### **Failure Case**

<div style="display: flex; align-items: center; gap: 20px;">
  <div>
    <b>🎧 Speech Mixture</b><br>
    <audio controls>
      <source src="samples/FC1/mix.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>💡 Attended Speech</b><br>
    <audio controls>
      <source src="samples/FC1/att.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
  <div>
    <b>🔊 Distractor Speech</b><br>
    <audio controls>
      <source src="samples/FC1/uatt.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
</div>

<div class="table-container">
  <table>
    <tr>
      <th>Question 1</th>
      <th>Model Answers 1</th>
      <th>Question 2</th>
      <th>Model Answers 2</th>
      <th>Question 3</th>
      <th>Model Answers 3</th>
    </tr>
    <tr>
      <td>Transcribe the words of the speaker being listened to.</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>It seems like i set the bar too high for myself this week.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>It seems like I said the bar will be there in about forty minutes.</i> <br>
        <b>AAD-LLM</b>: <i>To the offer, The driver will be there in about forty minutes.</i>
      </td>
      <td>What is the attended speech about?</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>Setting the bar too high for oneself.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>Someone named Barto coming over in about forty minutes.</i> <br>
        <b>AAD-LLM</b>: <i>Driver will arrive in forty minutes.</i>
      </td>
      <td>Identify the person whom the subject is listening to.</td>
      <td rowspan="3">
        <span class="model-name">SALMONN</span>: <i>It is not specified in the given sentence who the subject is listening to.</i> <br>
        <span class="model-name">Qwen2-Audio</span>: <i>Harry.</i> <br>
        <b>AAD-LLM</b>: <i>A male speaker with low pitch and high tempo.</i>
        (The description is accurate, but it is true for both speakers.)
      </td>
    </tr>
    <tr>
      <td><b>Oracle Answer 1</b></td>
      <td><b>Oracle Answer 2</b></td>
      <td><b>Oracle Answer 3</b></td>
    </tr>
    <tr>
      <td><i>Seems like I set the bar too high for myself this time.</i></td>
      <td><i>I’ve set unrealistic expectations for myself.</i></td>
      <td><i>A male speaker with low pitch and high tempo.</i></td>
    </tr>
  </table>
</div>


<hr style="height: 3px; background-color: grey; border: none;">

<b>Disclaimer</b>: *Within this study, approval of all ethical and experimental procedures and protocols was granted by the university's Institutional Review Board (IRB). The iEEG participants provided informed consent as per the local IRB regulations (IRB protocol number to be disclosed).*
