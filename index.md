<h1>WIP</h1>

Here is a table with **WER** results of the baseline model, Kaldi_NL, as well as different versions of zero-shot Whisper tested on various datasets:

|Model\Dataset|bn_nl|cts_nl|Jasmin_q_5|
|---|---|---|---|
|Kaldi_NL|12.6%|38.6%|**20.9%**|
|Whisper v2|12.9%|25.9%|31.8%*|
|Whisper v3|13.8%|28.1%|-|
|Whisper v2 w/ VAD|<b>11.7%|<b>25.3%|24.5%*|
|Whisper v3 w/ VAD|14.2%|26.5%|-|

**bn_nl** = Broadcast News programmes in the Netherlands, from the N-Best 2008 evaluation dataset<br>
**cts_nl** = Conversational Telephone Speech in the Netherlands, from the N-Best 2008 evaluation dataset<br>
**Jasmin_q_5** = Read speech (comp_**q**) of category **5** of speakers (the elderly) for the **Jasmin**-CGN corpus

\* There is an issue with the alignment of the hypothesis and reference files. The first word of each segment is timestamped by Whisper before the start timestamp of the segment. Thus, it is recognized as an insertion and, in the actual segment, the first word is recognized as deleted by the transcriber, even though Whisper manages to transcribe it correctly. This will be investigated and fixed soon in order to allow a fair comparison with Kaldi_NL.

<br><br>
And here are results for the same models on bn_nl with the foreign speech lines removed from the dataset:

|Model\Dataset|bn_nl|
|---|---|
|Kaldi_NL|12.1%|
|Whisper v2|12.4%|
|Whisper v3|13.7%|
|**Whisper v2 w/ VAD**|**11.3%**|
|Whisper v3 w/ VAD|14.0%|

Something to note about this setup of the dataset is that Whisper v3 was already able to recognize foreign speech and ignore it. The only notable exception was for a German speaker, where I assume that it was still transcribed because German and Dutch are very similar as languages.