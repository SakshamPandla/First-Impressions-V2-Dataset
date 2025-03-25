---
license: cc-by-nc-4.0
task_categories:
- video-classification
- text-classification
- audio-classification
language:
- en
size_categories:
- 1K<n<10K
---

# Dataset Card for Dataset Name

The first impressions data set, comprises 10000 clips (average duration 15s) extracted from more than 3,000 different YouTube high-definition (HD) videos of people facing and speaking in English to a camera. The videos are split into training, validation and test sets with a 3:1:1 ratio. People in videos show different gender, age, nationality, and ethnicity.

Videos are labeled with personality traits variables. Amazon Mechanical Turk (AMT) was used for generating the labels. A principled procedure was adopted to guarantee the reliability of labels. The considered personality traits were those from the Five Factor Model (also known as the Big Five), which is the dominant paradigm in personality research. It models human personality along five dimensions: *Extraversion, Agreeableness, Conscientiousness, Neuroticism and Openness*. Thus each clip has ground truth labels for these five traits represented with a value within the range [0, 1]. 

## Dataset Details

### Dataset Description

> [!WARNING]
> Some information stated in here is not precise and has not been uploaded yet to Hugging Face. The dataset will be uploaded in the future weeks.

Here, we also introduce an extension of this dataset. Specifically, we supplement the dataset with new language data (transcriptions), which complements the existing sensory data (videos) as well as a new job-interview variable (interview annotations), which complements the existing personality trait variables (trait annotations).

**Transcriptions:** All words in the video clips were transcribed by the professional transcription service Rev. In total, 435984 words were transcribed (183861 non-stopwords), which corresponds to 43 words per video on average (18 non-stopwords). Among these words, 14535 were unique (14386 non-stopwords).

**Interview annotations:** In addition to labeling the apparent personality traits, AMT workers labeled each video with a variable indicating whether the person should be invited or not to a job interview (the "job-interview variable"). This variable is also represented with a value within the range [0, 1].

- **Curated by:** ChaLearn Looking at People, CVC, UAB
- **Language(s) (NLP):** English
- **License:** Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)

#### Groundtruth file format

The annotations and transcriptions are stored in pickled dictionaries. There should be one file for annotations and one file for transcriptions per phase.

Each video has one transcription (if there was nothing to transcribe in a video, its corresponding transcription will be an empty string). Each transcription is a unicode object. The transcription file is a single dictionary. That is, its keys are the names of the videos, and their values are the corresponding transcriptions. For example: `transcription['a_video_name']` would give the transcriptions of the video called `'a_video_name'`.

Each video has also six annotations (five traits and one interview). Each annotation is a value between zero and one. The annotation file is a dictionary of dictionaries. That is, the keys of the outer dictionary are the names of the annotations and their values are dictionaries. The keys of the inner dictionaries are the names of the videos and their values are the actual annotations corresponding to the keys of the outer dictionaries. For example:

`annotation['interview']['a_video_name']` would give the value for the interview annotation of the video called `'a_video_name'`.
`annotation['openness']['another_video_name']` would give the value for the openness annotation of the video called `'another_video_name'`.

#### Gender and ethnicity annotations

We are making avaiable gender and ethnicity annotations for the first impressions data set. The labels were made avaiable by Heysem Kaya and Albert Ali Salah. 

The labels are as follows:
* Ethnicity: Asian=1,Caucasian=2,African-American=3
* Gender: Male=1, Female=2
* Group ID: Age Range
  1. [0,6]
  2. [7,13]
  3. [14,18]
  4. [19,24]
  5. [25,32]
  6. [33,45]
  7. [46,60]
  8. 61+

#### Pairwise data

These are the original pairwise annotations of the First Impressions dataset.

Big-Five relationship:

```text
# friendly, = Extraversion
# authentic, = Agreeableness
# organized, = Conscientiousness
# comfortable, = Emotion Stability = the Inverse of 'Neurotisicm'
# imaginative, = Openness

# interview = interview
```

The original raw pairwise annotations of the FI dataset have been realeased. Find them [here](http://chalearnlap.cvc.uab.es/dataset/24/data/68/description/).

#### Predicted attributes (soft-labels)

- Predicted values (Attractiveness score and perceived age) are provided for a subset of the FI dataset (Caucasian), based on Ethnicity annotations already provided with the data.
- Predicted values were used as soft labels, and used as proof of concept in \cite{Junior_2021_WACV}.
- Attractiveness range from 1 to 5.
- Gender labels (1=male; 2=female) were manually annotated as "perceived gender".

Predicted attributes (attractiveness and perceived age) used in [WACVW'2021 paper](https://openaccess.thecvf.com/content/WACV2021W/HBU/papers/Jacques_Person_Perception_Biases_Exposed_Revisiting_the_First_Impressions_Dataset_WACVW_2021_paper.pdf) can be found [here](http://chalearnlap.cvc.uab.es/dataset/24/data/69/description/).

### Dataset Sources

<!-- Provide the basic links for the dataset. -->

- **Repository:** Data available [here](https://chalearnlap.cvc.uab.cat/dataset/24/description/).
- **Paper 1:** J.-I. Biel, O. Aran, and D. Gatica-Perez, You Are Known by How You Vlog: Personality Impressions and Nonverbal Behavior in YouTube in Proc. AAAI Int. Conf. on Weblogs and Social Media (ICWSM), Barcelona, Jul. 2011
- **Paper 2:** J.-I. Biel and D. Gatica-Perez, The YouTube Lens: Crowdsourced Personality Impressions and Audiovisual Analysis of Vlogs, IEEE Trans. on Multimedia, Vol. 15, No. 1, pp. 41-55, Jan. 2013
- **Paper (Gender and ethnicity):** Escalante, H. J.; Kaya, H.; Salah, A. A.; Escalera, S.; Gucluturk, Y.; Guclu, U.; Baró, X.; Guyon, I.; Jacques Junior, J. C. S.; Madadi, M.; Ayache, S.; Viegas, E.; Gurpinar, F.; Wicaksana, A.S.; Liem, C.C.S.; van Gerven, M. A. J.; van Lier, R. "Modeling, Recognizing, and Explaining Apparent Personality from Videos," IEEE Transactions on Affective Computing (TAC), 2020.

## Citation

In case you use this data, please cite the following papers:

**BibTeX:**

@InProceedings{10.1007/978-3-319-49409-8_32,
  author="Ponce-L{\'o}pez, V{\'i}ctor and Chen, Baiyu and Oliu, Marc and Corneanu, Ciprian and Clap{\'e}s, Albert and Guyon, Isabelle and Bar{\'o}, Xavier and Escalante, Hugo Jair and Escalera, Sergio",
  editor="Hua, Gang and J{\'e}gou, Herv{\'e}",
  title="ChaLearn LAP 2016: First Round Challenge on First Impressions - Dataset and Results",
  booktitle="Computer Vision -- ECCV 2016 Workshops",
  year="2016",
  publisher="Springer International Publishing",
  pages="400--418",
  isbn="978-3-319-49409-8"
}

@InProceedings{Junior_2021_WACV,
    author    = {Junior, Julio C. S. Jacques and Lapedriza, Agata and Palmero, Cristina and Baro, Xavier and Escalera, Sergio},
    title     = {Person Perception Biases Exposed: Revisiting the First Impressions Dataset},
    booktitle = {Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision (WACV) Workshops},
    month     = {January},
    year      = {2021},
    pages     = {13-21}
}

@ARTICLE{8999746,
  author={H. J. {Escalante} and H. {Kaya} and A. A. {Salah} and S. {Escalera} and Y. {Güç;lütürk} and U. {Güçlü} and X. {Baró} and I. {Guyon} and J. C. S. {Jacques Junior} and M. {Madadi} and S. {Ayache} and E. {Viegas} and F. {Gurpinar} and A. S. {Wicaksana} and C. {Liem} and M. A. J. {Van Gerven} and R. {Van Lier}},
  journal={IEEE Transactions on Affective Computing},
  title={Modeling, Recognizing, and Explaining Apparent Personality from Videos},
  year={2020},
  doi={10.1109/TAFFC.2020.2973984}
}

## Dataset Card Contact

For further contact, please go to ChaLearn Group website in [here](https://chalearnlap.cvc.uab.cat/).

## Disclaimer 

Despite all of the efforts devoted to the compilation and curation of resources available in this website, we cannot guarantee that collected data including associated annotations and labels (obtained through manually, automatically and a semi-automatically processes) are representative samples of a real application scenario. The adopted data gathering and labeling methodologies may not include exhaustive and/or inclusive mechanisms that allow users to reach conclusive findings. More importantly, we strongly advise users NOT using the resources available in this site to build systems that make decisions and recommendations that have a direct or indirect impact into people's lives. Likewise, we acknowledge and apologize for those resources and publications available in this site may use ambiguous terms (e.g., gender vs. sex or ethnicity vs. race), we have not deliberately aimed to cause controversy or affect users in any form.