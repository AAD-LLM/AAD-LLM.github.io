---
layout: arxiv
---

***Xilin Jiang<sup>1★</sup>, Sukru Samet Dindar<sup>1★</sup>, Vishal Choudhari<sup>1★</sup>, Stephan Bickel<sup>3,4</sup>, Ashesh Mehta<sup>3,4</sup>, Guy M McKhann<sup>1</sup>, Adeen Flinker<sup>2</sup>, Daniel Friedman<sup>2</sup>, Nima Mesgarani<sup>1★</sup>***


<sub>*First two authors conntribute equally.*</sub>

![abstract](figures/demo.png)

Auditory foundation models, including auditory large language models (LLMs), process all sound inputs equally, independent of listener perception. However, human auditory perception is inherently selective: listeners focus on specific speakers while ignoring others in complex auditory scenes. Existing models do not incorporate this selectivity, limiting their ability to generate perception-aligned responses. To address this, we introduce Intention-Informed Auditory Scene Understanding (II-ASU) and present Auditory Attention-Driven LLM (AAD-LLM), a prototype system that integrates brain signals to infer listener attention. AAD-LLM extends an auditory LLM by incorporating intracranial electroencephalography (iEEG) recordings to decode which speaker a listener is attending to and refine responses accordingly. The model first predicts the attended speaker from neural activity, then conditions response generation on this inferred attentional state. We evaluate AAD-LLM on speaker description, speech transcription and extraction, and question answering in multitalker scenarios, with both objective and subjective ratings showing improved alignment with listener intention. By taking a first step toward intention-aware auditory AI, this work explores a new paradigm where listener perception informs machine listening, paving the way for future listener-centered auditory systems.



* * *

#### **Clinical Sample 1: Female and Male**
🎧 **Speech Mixture**: [▶️ Listen](samples/clinical1_mixture.wav)  
👂 **Attended Speech**: [▶️ Listen](samples/clinical1_attended.wav)  

<style>
  .model-name {
    color: grey;
    font-weight: bold;
  }
</style>

<table>
  <tr>
    <th>Question</th>
    <th>Answers</th>
    <th>Question</th>
    <th>Answers</th>
  </tr>
  <tr>
    <td>blablabla</td>
    <td rowspan="3">
      <span class="model-name">SALMONN</span>: <i>"blablabla"</i> <br>
      <span class="model-name">Qwen2-Audio</span>: <i>"blablabla"</i> <br>
      <b>AAD-LLM</b>: <i>"blablabla"</i>
    </td>
    <td>blablabla</td>
    <td rowspan="3">
      <span class="model-name">SALMONN</span>: <i>"blablabla"</i> <br>
      <span class="model-name">Qwen2-Audio</span>: <i>"blablabla"</i> <br>
      <b>AAD-LLM</b>: <i>"blablabla"</i>
    </td>
  </tr>
  <tr>
    <td><b>Oracle Answer</b></td>
    <td><b>Oracle Answer</b></td>
  </tr>
  <tr>
    <td>blablabla</td>
    <td>blablabla</td>
  </tr>
</table>

#### **Clinical Sample 2: Female and Female**

#### **Clinical Sample 3: Male and Male**

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



