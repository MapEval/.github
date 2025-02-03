<div align="center">

<h1>MapEval: A Map-Based Evaluation of Geo-Spatial Reasoning in Foundation Models</h1>

<!-- [**Xiangcheng Hu**](https://github.com/JokerJohn)<sup>1</sup> · [**Jin Wu**](https://zarathustr.github.io/)<sup>1</sup> · [**Mingkai  Jia**](https://github.com/MKJia)<sup>1</sup>· [**Hongyu  Yan**](https://scholar.google.com/citations?user=TeKnXhkAAAAJ&hl=zh-CN)<sup>1</sup>· [**Yi  Jiang**](https://yijiang1992.github.io/)<sup>2</sup>· [**Binqian  Jiang**](https://github.com/lewisjiang/)<sup>1</sup>
<br>
[**Wei Zhang**](https://ece.hkust.edu.hk/eeweiz)<sup>1</sup> · [**Wei  He**](https://sites.google.com/view/drweihecv/home/)<sup>3</sup> · [**Ping Tan**](https://facultyprofiles.hkust.edu.hk/profiles.php?profile=ping-tan-pingtan#publications)<sup>1*&dagger;</sup>

<sup>1</sup>**HKUST&emsp;&emsp;&emsp;<sup>2</sup>CityU&emsp;&emsp;&emsp;<sup>3</sup>USTB**  
<br>
&dagger;project lead&emsp;*corresponding author -->

</div>

<p align="center">
    <a href="https://mapeval.github.io/">🌐 Website</a> •
    <a href="https://huggingface.co/papers/2501.00316">📃 Paper</a> •
    <a href="https://huggingface.co/MapEval">🤗 Dataset</a> •
    <a href="https://paperswithcode.com/paper/mapeval-a-map-based-evaluation-of-geo-spatial">🏆 Leaderboard</a> •
    <a href="https://github.com/orgs/mapeval/repositories">💻 Code</a>
</p>


![Alt text](overview.svg)

## 📢 Updates

- 2025-01-31: Paper submitted to ICML 2025 Conference.
- 2024-12-31: We have released our [paper](https://arxiv.org/abs/2501.00316) and [dataset](https://huggingface.co/MapEval). Check it out!
- 2024-11-19: MapEval dataset is increased to 700 questions.
- 2024-10-02: Paper submitted to ICLR 2025 Conference. [Link](https://openreview.net/forum?id=nnAPWDt4hn)
- 2024-09-30: MapEval dataset is created with 573 questions.

## 📖 Abstract

Recent advancements in foundation models have enhanced AI systems' capabilities in autonomous tool usage and reasoning. However, their ability in location or map-based reasoning - which improves daily life by optimizing navigation, facilitating resource discovery, and streamlining logistics - has not been systematically studied. To bridge this gap, we introduce MapEval, a benchmark designed to assess diverse and complex map-based user queries with geo-spatial reasoning. MapEval features three task types (textual, API-based, and visual) that require collecting world information via map tools, processing heterogeneous geo-spatial contexts (e.g., named entities, travel distances, user reviews or ratings, images), and compositional reasoning, which all state-of-the-art foundation models find challenging. Comprising 700 unique multiple-choice questions about locations across 180 cities and 54 countries, MapEval evaluates foundation models' ability to handle spatial relationships, map infographics, travel planning, and navigation challenges. Using MapEval, we conducted a comprehensive evaluation of 28 prominent foundation models. While no single model excelled across all tasks, Claude-3.5-Sonnet, GPT-4o, and Gemini-1.5-Pro achieved competitive performance overall. However, substantial performance gaps emerged, particularly in MapEval, where agents with Claude-3.5-Sonnet outperformed GPT-4o and Gemini-1.5-Pro by 16% and 21%, respectively, and the gaps became even more amplified when compared to open-source LLMs. Our detailed analyses provide insights into the strengths and weaknesses of current models, though all models still fall short of human performance by more than 20% on average, struggling with complex map images and rigorous geo-spatial reasoning. This gap highlights MapEval's critical role in advancing general-purpose foundation models with stronger geo-spatial understanding.

## 🌎 MapEval Overview


We introduce MapEval, a novel benchmark designed to evaluate the geo-spatial reasoning capabilities of foundation models and AI agents in complex map-based scenarios. MapEval addresses a critical gap in existing benchmarks by evaluating models' ability to process heterogeneous geo-spatial contexts, perform compositional reasoning, and interact with real-world map tools. It features three task types— MapEval-API, MapEval-Visual, and MapEval-Textual, that require models to collect world information via map tools, a deep visual understanding, and reason over diverse geo-spatial data (e.g., named entities, coordinates, operational hours, distances, routes, user reviews/ratings, map images), all of which remain challenging for state-of-the-art foundation models. Comprising 700 unique multiple-choice questions across 180 cities and 54 countries, MapEval reflects real-world user interactions with map services while pushing state-of-the-art models to understand spatial relationships, map infographics, travel planning, POI search, and navigation. MapEval ensures geographic diversity, realistic query patterns, and evaluation across multiple modalities. By integrating long contexts, visual complexity, API interactions, and questions requiring commonsense reasoning or recognition of insufficient information (i.e., unanswerability), it offers a rigorous framework for advancing geo-spatial AI capabilities.

With MapEval, we evaluated 28 prominent foundation models, where Claude-3.5-Sonnet, GPT-4o, and Gemini-1.5-Pro showed competitive performance overall. However, significant gaps emerged in MapEval-API, with Claude-3.5-Sonnet agents outperforming GPT-4o and Gemini-1.5-Pro by 16% and 21%, respectively, and even larger disparities compared to open-source models. Our detailed analyses revealed further insights into model strengths and weaknesses. Despite these advances, all models still fall short of human performance by over 20%, especially in handling complex map images and rigorous reasoning, underscoring MapEval's role in advancing geo-spatial understanding. 

## Bencmarking

We benchmarked 28 foundation models on MapEval dataset. The models are evaluated on three task types: MapEval-API, MapEval-Visual, and MapEval-Textual. The models are evaluated on the basis of accuracy. The results are shown below:

### MapEval-Textual

| Model                    | Overall | Place Info | Nearby | Routing | Trip   | Unanswerable |
|--------------------------|:---------:|:------------:|:--------:|:---------:|:--------:|:--------------:|
| Claude-3.5-Sonnet        | **66.33**   | **73.44**      | 73.49  | **75.76**   | **49.25**  | 40.00        |
| Gemini-1.5-Pro           | **66.33**   | 65.63      | **74.70**  | 69.70   | 47.76  | **85.00**        |
| GPT-4o                   | 63.33   | 64.06      | **74.70**  | 69.70   | **49.25**  | 40.00        |
| GPT-4-Turbo              | 62.33   | 67.19      | 71.08  | 71.21   | 47.76  | 30.00        |
| Gemini-1.5-Flash         | 58.67   | 62.50      | 67.47  | 66.67   | 38.81  | 50.00        |
| GPT-4o-mini              | 51.00   | 46.88      | 63.86  | 57.58   | 40.30  | 25.00        |
| GPT-3.5-Turbo            | 37.67   | 26.56      | 53.01  | 48.48   | 28.36  | 5.00         |
| Llama-3.1-70B            | 61.00   | 70.31      | 67.47  | 69.70   | 40.30  | 45.00        |
| Llama-3.2-90B            | 58.33   | 68.75      | 66.27  | 66.67   | 38.81  | 30.00        |
| Qwen2.5-72B              | 57.00   | 62.50      | 71.08  | 63.64   | 41.79  | 10.00        |
| Qwen2.5-14B              | 53.67   | 57.81      | 71.08  | 59.09   | 32.84  | 20.00        |
| Gemma-2.0-27B            | 49.00   | 39.06      | 71.08  | 59.09   | 31.34  | 15.00        |
| Gemma-2.0-9B             | 47.33   | 50.00      | 50.60  | 59.09   | 34.33  | 30.00        |
| Llama-3.1-8B             | 44.00   | 53.13      | 57.83  | 45.45   | 23.88  | 20.00        |
| Qwen2.5-7B               | 43.33   | 48.44      | 49.40  | 42.42   | 38.81  | 20.00        |
| Mistral-Nemo             | 43.33   | 46.88      | 50.60  | 50.00   | 32.84  | 15.00        |
| Mixtral-8x7B             | 43.00   | 53.13      | 54.22  | 45.45   | 26.87  | 10.00        |
| Phi-3.5-mini             | 37.00   | 40.63      | 48.19  | 46.97   | 20.90  | 0.00         |
| Llama-3.2-3B             | 33.00   | 31.25      | 49.40  | 31.82   | 25.37  | 0.00         |
| Human                    | 86.67   | 92.19      | 90.36  | 81.81   | 88.06  | 65.00        |

### MapEval-API

| Model               | Overall | Place Info | Nearby | Routing | Trip   | Unanswerable |
|---------------------|:---------:|:------------:|:--------:|:---------:|:--------:|:--------------:|
| Claude-3.5-Sonnet   | **64.00**   | **68.75**     | **55.42**  | **65.15**   | **71.64**  | 55.00        |
| GPT-4-Turbo         | 53.67   | 62.50      | 50.60  | 60.61   | 50.75  | 25.00        |
| GPT-4o              | 48.67   | 59.38      | 40.96  | 50.00   | 56.72  | 15.00        |
| Gemini-1.5-Pro      | 43.33   | 65.63      | 30.12  | 40.91   | 34.33  | **65.00**        |
| Gemini-1.5-Flash    | 41.67   | 51.56      | 38.55  | 46.97   | 34.33  | 30.00        |
| GPT-3.5-Turbo       | 27.33   | 39.06      | 22.89  | 33.33   | 19.40  | 15.00        |
| GPT-4o-mini         | 23.00   | 28.13      | 14.46  | 13.64   | 43.28  | 5.00         |
| Llama-3.2-90B       | 39.67   | 54.69      | 37.35  | 39.39   | 35.82  | 15.00        |
| Llama-3.1-70B       | 37.67   | 53.13      | 32.53  | 42.42   | 31.34  | 15.00        |
| Mixtral-8x7B        | 27.67   | 32.81      | 18.07  | 27.27   | 38.81  | 15.00        |
| Gemma-2.0-9B        | 27.00   | 35.94      | 14.46  | 28.79   | 26.87  | 45.00        |

#### Comparison between ReAct and Chameleon with GPT-3.5-Turbo

| Model                      | Overall | Place Info | Nearby | Routing | Trip   | Unanswerable |
|----------------------------|:-------:|:----------:|:------:|:-------:|:------:|:------------:|
| ReAct      | 27.33   | 39.06      | 22.89  | 33.33   | 19.40  | 15.00        |
| Chameleon  | 49.33   | 54.69      | 54.21  | 51.51   | 43.28  | 25.00        |

### MapEval-Visual

| Model                     | Overall | Place Info | Nearby | Routing | Counting | Unanswerable |
|---------------------------|:-------:|:----------:|:------:|:-------:|:--------:|:------------:|
| Claude-3.5-Sonnet         | **61.65**   | **82.64**      | 55.56  | **45.00**   | **47.73**    | **90.00**        |
| GPT-4o                    | 58.90   | 76.86      | **57.78**  | 50.00   | **47.73**    | 40.00        |
| Gemini-1.5-Pro            | 56.14   | 76.86      | 56.67  | 43.75   | 32.95    | 80.00        |
| GPT-4-Turbo               | 55.89   | 75.21      | 56.67  | 42.50   | 44.32    | 40.00        |
| Gemini-1.5-Flash          | 51.94   | 70.25      | 56.47  | 38.36   | 32.95    | 55.00        |
| GPT-4o-mini               | 50.13   | 77.69      | 47.78  | 41.25   | 28.41    | 25.00        |
| Qwen2-VL-7B-Instruct      | 51.63   | 71.07      | 48.89  | 40.00   | 40.91    | 40.00        |
| Glm-4v-9b                 | 48.12   | 73.55      | 42.22  | 41.25   | 34.09    | 10.00        |
| InternLm-Xcomposer2       | 43.11   | 70.41      | 48.89  | 43.75   | 34.09    | 10.00        |
| MiniCPM-Llama3-V-2.5      | 40.60   | 60.33      | 32.22  | 32.50   | 31.82    | 30.00        |
| Llama-3-VILA1.5-8B        | 32.99   | 46.90      | 32.22  | 28.75   | 26.14    | 5.00         |
| DocOwl1.5                 | 31.08   | 43.80      | 23.33  | 32.50   | 27.27    | 0.00         |
| Llava-v1.6-Mistral-7B-hf  | 31.33   | 42.15      | 28.89  | 32.50   | 21.59    | 15.00        |
| Paligemma-3B-mix-224      | 30.58   | 37.19      | 25.56  | 38.75   | 23.86    | 10.00        |
| Llava-1.5-7B-hf           | 20.05   | 22.31      | 18.89  | 13.75   | 28.41    | 0.00         |
| Human                     | 82.23   | 81.67      | 82.42  | 85.18   | 78.41    | 65.00        |

## 📝 Citation

If you use this dataset for benchmarking, please cite our paper:
```
@article{dihan2024mapeval,
  title={MapEval: A Map-Based Evaluation of Geo-Spatial Reasoning in Foundation Models},
  author={Dihan, Mahir Labib and Hassan, Md Tanvir and Parvez, Md Tanvir and Hasan, Md Hasebul and Alam, Md Almash and Cheema, Muhammad Aamir and Ali, Mohammed Eunus and Parvez, Md Rizwan},
  journal={arXiv preprint arXiv:2501.00316},
  year={2024}
}
```

<!-- ## Contributors

Thanks to all the contributors! 💖

[![Contributor1](https://avatars.githubusercontent.com/u/66126573?s=50)](https://github.com/tanvirsaad) [![Contributor2](https://avatars.githubusercontent.com/u/62663759?s=50)](https://github.com/mahirlabibdihan) -->