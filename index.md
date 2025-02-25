---
layout: arxiv
---

***Xilin Jiang<sup>1★</sup>, Sukru Samet Dindar<sup>1★</sup>, Vishal Choudhari<sup>1★</sup>, Stephan Bickel<sup>3,4</sup>, Ashesh Mehta<sup>3,4</sup>, Guy M McKhann<sup>1</sup>, Adeen Flinker<sup>2</sup>, Daniel Friedman<sup>2</sup>, Nima Mesgarani<sup>1★</sup>***


<sub>*First two authors conntribute equally.*</sub>

![abstract](figures/demo.png)

Auditory foundation models, including auditory large language models (LLMs), process all sound inputs equally, independent of listener perception. However, human auditory perception is inherently selective: listeners focus on specific speakers while ignoring others in complex auditory scenes. Existing models do not incorporate this selectivity, limiting their ability to generate perception-aligned responses. To address this, we introduce Intention-Informed Auditory Scene Understanding (II-ASU) and present Auditory Attention-Driven LLM (AAD-LLM), a prototype system that integrates brain signals to infer listener attention. AAD-LLM extends an auditory LLM by incorporating intracranial electroencephalography (iEEG) recordings to decode which speaker a listener is attending to and refine responses accordingly. The model first predicts the attended speaker from neural activity, then conditions response generation on this inferred attentional state. We evaluate AAD-LLM on speaker description, speech transcription and extraction, and question answering in multitalker scenarios, with both objective and subjective ratings showing improved alignment with listener intention. By taking a first step toward intention-aware auditory AI, this work explores a new paradigm where listener perception informs machine listening, paving the way for future listener-centered auditory systems.


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

* * *

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
    <b>💡 Attended Speech</b> (hidden from models)<br>
    <audio controls>
      <source src="samples/CS1/att.wav" type="audio/wav">
      Your browser does not support the audio element.
    </audio>
  </div>
</div>

<style>
  .model-name {
    color: grey;
    font-weight: bold;
  }
</style>


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
    <b>💡 Attended Speech</b> (hidden from models)<br>
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
    <b>💡 Attended Speech</b> (hidden from models)<br>
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

* * *

#### **Same-Topic Sample 1**

#### **Same-Topic Sample 2**

* * *

#### **LibriTTS+DNS Sample 1**

#### **LibriTTS+DNS Sample 2**



* * *



#### **Failure Case 1**

#### **Failure Case 2**

* * *

*Within this study, approval of all ethical and experimental procedures and protocols was granted by the university's Institutional Review Board (IRB). The iEEG participants provided informed consent as per the local IRB regulations (IRB protocol number AAAD5482).*



