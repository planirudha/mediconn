# NLP Gedächtnisprotokolle mit Lösung

--- 
---

# Winter Semester 22/23

## Ordne nach Reihnfolge
- Tokenizing
- Lemmatizing
- POS-Tagging
- Constituency parsing
## Boolean Retrieval
- a) Stelle die Incidence Matrix auf für folgende drei lemmatisierte Dokumente:
		Dokumente:
		D1: "Ich esse gerne Hunde und bin kein Fan von Arsch"
		D2: "Meine Mama frisst gerne wie ein schwein und ich finde das nicht gut"
		D3: "Ich fresse gerne Ärsche"

|        | D1  | D2  | D3  |
| ------ | --- | --- | --- |
| Ich    | 1   | 1   | 1   |
| Fresse | 0   | 1   | 1   |
| Arsch  | 1   | 0   | 1   |

- b) Gegeben die query 'ich' UND 'fresse' UND NICHT 'Arsch' erkläre wie boolean retrievalfunktioniert und berechne es mit den Dokumentvektoren.
- 
111 UND 011 UND 010
result = 010
=> Column 2
=> D2

|        | D1  | D2  | D3  |
| ------ | --- | --- | --- |
| Ich    | 1   | 1   | 1   |
| Fresse | 0   | 1   | 1   |
| Arsch  | 1   | 0   | 1   |

## Inline vs standoff annotations beschreiben
Anderes Dokument vs Im text
Beispiel Inline: ["Ich/Noun", "bin/Verb", "groß/Adj"]

## True / False?
- SVM: Margin maximieren - True
- Naive bayes kann nicht mit binären features umgehen - False
- SVM unterstützt natively multi-class - False (natively: 2 classes)
- Bei tf-idf information retrieval wird die similarity zur query berechnet - True

## Markov model
### HMM für gegebene State Tabelle Zeichnen
TODO

### Berechne folgende Emissionsequence:

![](https://md.darmstadt.ccc.de/uploads/4609f435-1979-4fac-9dc1-81460af7c534.png)

$$\begin{align*}
& = & (S_{to 🙁}\; * 🌍) \\
& * & (🙁_{to 😐}\; * 💣) \\
& * & (😐_{to 🙁}\; * 💣)
\end{align*}$$

$=(0.3*0.1) * (0.5*0.7) * (0.4*0.9) = 0.00378$

### Viterbi Algorithmus erklären, wieso ist HMM für POS Tagging schwierig
TODO
wieso ist HMM für POS Tagging schwierig?
Vorschlag:
Using a HMM for POS Tagging is difficult because identifying the POS of homographs while leveraging only one previous tag as context is difficult.

(if there were no homographs, POS tagging would be easy -> just use a look-up table)

## Confusion matrix metrics
n= 1000

| Real ➡<br>Predicted ⬇ | Clean | Fake News |
| --------------------- | ----- | --------- |
| Clean                 | 300   | 400       |
| Fake News             | 100   | 200       |

### Berechne Precision, Recall, F1 und Accuracy.

$$\begin{align*}
& ---------- \\
& Formulars: \\
& P_{class} = \frac{TP}{TP + FP} & \\
& {R_{class} = \frac{TP}{TP + FN}} \\
& F1_{class} = \frac{2PR}{P+R} & \\
& A = \frac{T}{\#Samples} & \\
& ---------- \\
& Clean: \\
& P_{Clean} = \frac{300}{300 + 400} = \frac{3}{7} \approx 0.43 & \\
& R_{Clean} = \frac{300}{300 + 100} = \frac{3}{
4} \approx 0.75 & \\
& F_{Clean} = \frac{2*0.43*0.75}{0.43+0.75} = \frac{129}{
236} \approx 0.55 & \\
& ---------- \\
& Fake\;News: \\
& P_{Fake News} = \frac{200}{200 + 100} = \frac{2}{
3} \approx 0.67 & \\
& R_{Fake News} = \frac{200}{200 + 400} = \frac{1}{
3} \approx 0.33 & \\
& F_{Fake News} = \frac{2*0.67*0.33}{0.67+0.33} = \frac{2211}{
5000} \approx 0.44 & \\
& ---------- \\
& Whole\;Data: \\
& A = \frac{300 + 200}{1000} =  \frac{1}{2} = 0.5
& \\
\end{align*}$$

### Welche dieser Metriken werden für welches Ziel verwendet?
- Precision: Wie viele der als richtig vorhergesagten sind tatsächlich richtig?
- Recall: Wie viele der richtigen wurden als richtig vorhergesagt?
- F1 Score: Harmonische Metrik die P und R berücksichtigt
- Accuracy: Intuitive Metrik zur Bestimmung der anteiligen richtig klassifizierten Samples eines Datensatzes

### Wieso ist die Accuracy hier so schlecht?
Ist halt so. (TODO)

## Crowd Sourcing
### Was sind Vorteile gegenüber manuellem annotieren?
- Kosten
- Zeit
- Oft riesige Datenmenge

### Wo gibt es Probleme bei Crowd Sourcing?
- Qualitätskontrolle
- Copyright
- Ethnical concerns
- Langugage Barriers
- Cultural differences

### Wie Stellt man bei Crowd Sourcing Qualität sicher?
TODO
Finde dazu auf den Folien nichts. Vielleicht wurde das Thema seit letztem Jahr rausgenommen/weniger behandelt?

Aus dem Jahr davor:
HIT acceptance rate, location
Qualifications: pre-tests
Test items with known answers
Redundancy: many people do each task
Machine learning: detect spamming patterns
Verification: subsequent task; by other workers


## TF-IDF
### Lemmatize the following three documents and remove stop words
- Stop words are: "the", "on", "to", "with"
- Documents:
    1. The cat sat on the mat.
    2. She likes to eat apples.
    3. He plays football with his friends.

Result:
- cat sat mat <span style="color:red;">sit?</span>
- she like eat apple
- he play football his friend

### inverted index aufstellen


<span style="color:red;">

|  |  |  |  |
|---------|---------|---------|---------|
| cat | 1 |  |  |
| sit | 1 |  |  |
| mat | 1 |  |  |
| she | 2 |  |  |
| like | 2 |  |  |
| eat | 2 |  |  |
| apple | 2 |  |  |
| he | 3 |  |  |
| play | 3 |  |  |
| football | 3 |  |  |
| his | 3 |  |  |
| friend | 3 |  | |

etwas unnötiges Beispiel...

</span>



### rank mit einer nnn query ausrechnen (mit nur zwei der Dokumente)
TODO

## Page Rank
TODO

### hyperlink, teleport und transition matritzen aufstellen
TODO

### Mit welchen Methoden kann man die Pagerank werte mit der matrix erhalten?
TODO

## Argumente
TODO

### was heißt sound/unsound?  Beispiele liefern
Sound argument is both valid (the conclusion logically follows from premises) and has true premises. Example: "All humans are mortal. Socrates is a human. Therefore, Socrates is mortal."

Unsound argument can either have one or more false premises, or the conclusion does not logically follow from premises (invalid) or both. Example: "All cats are mortal. Socrates is mortal. Therefore, Socrates is a cat."

### Warum ist detection davon wichtig?

Detecting sound versus unsound arguments is crucial for accurately analyzing and understanding the logical structure and validity of textual data. It prevents the propagation of misleading information.

## Span Extraction

### Warum ist Exact Match nicht so gut als Metrik?
<span style="color:red;"> Because answers may be lexically different from the label but semantically correct. 
**Example**
Question: The Amazon rainforest makes up what amount of Earth's rainforests?
Label: over half
Answer: half of</span>

### Was kann alternativ verwendet werden?
<span style="color:red;"> Macro Averaged F1 </span>


## Python

### Code macht falsche POS tags
#### Welche POS tags sind falsch zugeordnet? 
TODO

#### Warum hat der Code fehlerhafte POS tags generiert?
Satz wurde wohl gesplitted ( tokens = str.split() ) und dann wort für wort in nlp(token) übergeben

### Erklären was Funktionsaufrufe machen

get_20newsgroups(): Loads the "20 Newsgroups" dataset for machine learning and text mining experiments from scikit-learn.

vectorizer.fit_transform(): Learns vocabulary and transforms text into numerical vectors in one step, e.g., for TF-IDF scores.

classifier.fit(): Trains classification or regression models on data, learning the relationship between features and target variables.


### "Was machen diese Zeilen Code, zu jeder Zeile eine kleine Erklärung" Kinda Task

### 3 libraries in einem Satz erklären (und Bezug zu NLP)
- **SpaCy** ist eine Bibliothek, die sich auf die schnelle und effiziente Verarbeitung von Texten spezialisiert hat. Sie bietet Funktionen wie Tokenisierung, Lemmatisierung, Part-of-Speech-Tagging und Named Entity Recognition.
- **NLTK** ist eine umfassendere Bibliothek, die eine Vielzahl von Werkzeugen für die NLP-Forschung und -Entwicklung bietet. Dazu gehören Korpora, Tokenizer, Stemmer, Lemmatizer, Parser und Tagger.
- **Torch** ist eine Deep-Learning-Bibliothek, die für die Entwicklung von NLP-Modellen mit neuronalen Netzen verwendet werden kann. Sie bietet eine Vielzahl von Bausteinen für die Implementierung komplexer Modelle, wie z. B. rekurrente neuronale Netze (RNNs) und Transformer.

Sonstige:
- **Numpy**: Lineare Algebra Operationen, effiziente Array Verwaltung & Operationen, Numerische berechnungen

--- 
---

# Summer Semester 21

## Morphemes, freie und bound
TODO

## Lemmatization, Stemming, Difference, Beispiel für ein wort, dass anders ist bei jeweiligen angewendeten
TODO

## Parse Tree zeichnen für "the man shot the man with the gun" (oder so ähnlich) 
TODO

## Pagerank. Ausrechne. Was sind die beiden methoden
TODO

## Ranked retrieval. Precision, mehrere dokumente, q1, p2
TODO

## Mean precision, formel nicht gekannt. P@1 oder so. Das wurde vorher nicht besprochen, stand im aufgabentext eigentlihc aber
   TODO

## Counted vectorizes. Nur counted, nicht ti-df. Allerdings, dort auch cosine similiarty
TODO

## Anschließend, kann ti-idf resultate zurückliefern das gar nicht im query ist? (oder so)
TODO

## Was ist die intuition bei Naive bayes, dass man die vorherige probability nimmt?
TODO

## Diese 4 katoegrien: Strucutral, Presentaition, ... 
TODO

## Query types oder so? 
TODO

## Pipeline einer cQA engine
TODO

##  Input, output, einer meta qa
TODO

## Hidden markov model, state sequence
(S1, S2, S3)
TODO

## Probablity, anhand der Symbole. Viterbi fragezeichen(?), dort anhand der symbole wie man es ausrechen soll.
TODO

## Sufficient arguments, beispiel und beschreiben
    Warum ist das difficult für NLP?
    TODO
    
    
---
---
