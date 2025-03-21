# <p align="center"><font size=50><strong>NLPCC2025 Shared-Task 1: LLM-Generated Text Detection</strong></font></p> 

<div style="text-align: center;">
    <a href="https://github.com/NLP2CT/NLPCC-2025-Task1/blob/main/README-ZH.md">中文主页</a>
</div>

# Task Introduction

With the rapid advancement of large language models (LLMs), the quality of their generated text is increasingly approaching that of human-written content. However, these models also pose significant challenges, as they may generate hallucinated information, harmful content, or be misused in various ways. As a result, effectively distinguishing between text generated by LLMs and text authored by humans has become a critical and pressing issue. While significant progress has been made in detecting text generated by LLMs, most of this research has been focused on English. In contrast, studies targeting Chinese remain relatively scarce. This shared task seeks to address this gap by developing more robust detectors for identifying text generated by LLMs, thereby advancing research in this area for Chinese.

Participants are tasked with designing and building detection algorithms using the provided raw training data to distinguish between text generated by LLMs and human-written text. During the evaluation phase, the submitted detectors will undergo rigorous testing under conditions that closely simulate real-world scenarios, especially with out-of-distribution data, to comprehensively assess their practical effectiveness and robustness. To ensure fairness and the traceability of results, participants are strictly prohibited from using external data sources or generating new data samples based on external knowledge. Additionally, all training data and related scripts must be submitted for review to guarantee the fairness, transparency, and reproducibility of the task.

# Latest News

- [ 2025.02.27 ] We have released detailed task guidelines and training data—start building a reliable detector now!

# Data Description

We present DetectRL-ZH, a benchmark specifically designed for detecting LLM-generated text in the Chinese domain. It is the Chinese extension of DetectRL, an English benchmark for detecting LLM-generated text in real-world scenarios. DetectRL-ZH is a carefully constructed dataset that simulates real-world conditions, featuring diverse paraphrased, adversarial, and mixed samples. Our test set will be also evaluated under real-world scenarios, and the statistics for the dataset for this shared task are provided below.

## Statistics of Data

- Training Set: The training set includes data from 3 types of LLMs and 3 domains. Specifically, the data sources are ASAP, CNewSum, and CSL. The generators include GPT-4o, GLM-4-flash, and Qwen-turbo. The training set contains totally 32,400 samples.
- Test Set: An additional unknown model and domain data are used as the source of raw data for the final test.

| Split | Source    | GPT4o | GLM  | Qwen  | Machine | Human | Total |
|-------|-----------|-------|------|-------|---------|-------|-------|
| Train | ASAP      | 2700  | 2700 | 2700  | 8100    | 2700  | 32400 |
|       | CNewSum   | 2700  | 2700 | 2700  | 8100    | 2700  |       |
|       | CSL       | 2700  | 2700 | 2700  | 8100    | 2700  |       |
| Dev   | -    |   -   | -    | -     | 1700    | 1100  |  2800 |
| Test  | -    | -     | -    | -     | -       | -     | -     |


## Data Download

The training data and development data can be found in the following Google Drive folder link or Github link:

Google Drive link: https://drive.google.com/drive/folders/1R5KiW7uwQ002dOE2expEYQLbzQ_gMr8j?usp=sharing

Github link: https://github.com/NLP2CT/NLPCC2025-Task1/tree/main/data

##  Data Restriction

- Please note that the provided development set is strictly for model tuning and must not be used for model training.

- To support the development of these detection systems, participants are allowed to perform data augmentation based on the provided raw training data. However, data augmentation must be limited to processing or transforming the original data, such as creating new data samples through methods like cropping, splitting, word replacement, or format adjustment. It is crucial that any paraphrasing strictly preserves the original semantic meaning and does not introduce external knowledge or create entirely new content. This includes a prohibition on using generative LLMs for paraphrasing, as this could inadvertently introduce out-of-distribution knowledge and lead to unfair advantages, but allowing the use of traditional encoder-based models or seq2seq models for paraphrasing.

## Data Format

The data is structured as a JSON object.

For training data:
```json
{
  "text": "text generated by a machine or written by a human",
  "label": "label (human text: 0, machine text: 1)",
  "model": "model that generated the data",
  "source": "source (ASAP, CNewSum, CSL)"
}
```

For dev and test data:
```json
{
  "text": "text generated by a machine or written by a human",
  "label": "label (human text: 0, machine text: 1)",
}
```

# Evaluation Metric

The official evaluation metric for the task is the F1-Score, which effectively measures the performance of a classifier in binary classification tasks.


# Submission & Evaluation

The test data will be released on 2025/04/11. Participants are required to submit test result files (adding a "label" field based on the released test data). A unified system evaluation will be conducted, and the final scores and rankings of all participants will be announced on 2025/04/20 (along with the evaluation answers, allowing participants to verify their results). After receiving the competition results, participants may proceed with writing their papers, with the submission deadline set for 2025/05/22. The prediction file must be a single JSON file containing all texts. Each entry in the JSON file must include the fields "text" and "label".

# Important dates

| Time | Events |
| --- | --- |
| 2025/02/17| announcement of shared tasks and call for participation| 
| 2025/02/17| registration open|
| 2025/02/28| release of detailed task guidelines & training data|
| 2025/03/25| registration deadline|
| 2025/04/11| release of test data| 
| 2025/04/20| participants’ results submission deadline|
| 2025/04/30| evaluation results release and call for system reports and conference paper|
| 2025/05/22| conference paper submission deadline (only for shared tasks)|
| 2025/06/12| conference paper accept/reject notification|
| 2025/06/25| camera-ready paper submission deadline|


# Awards & Results

- The top 3 participating teams in each task and track will be certificated by NLPCC and CCF-NLP.

# Orangizer & Contact

This shared-task is orangized by NLP2CT Lab, University of Macau.

- [Derek, Fai Wong](https://www.fst.um.edu.mo/personal/derek-wong/)
- [Junchao Wu](https://junchaoiu.github.io/)
- [Runzhe Zhan](https://runzhe.me/) 
- [Yulin Yuan](https://fah.um.edu.mo/yulin-yuan/)

If you have any questions about this task, please email to nlp2ct.junchao@gmail.com.

# FAQ

Q: Where can I register for this shared task?

A: The latest registration method is available on the NLPCC 2025 Shared Task official website (http://tcci.ccf.org.cn/conference/2025/cfpt.php). Please fill out the Shared Task 1 registration form (Word document) (http://tcci.ccf.org.cn/conference/2025/sharedTasks/NLPCC2025.SharedTask1.RegistrationForm.doc) as required and send it to nlp2ct.junchao@gmail.com. If you have any questions, feel free to reach out.

Q: Is it allowed to use additional data?

A: Using external data sources is not permitted. However, data augmentation is allowed (see Data Restriction for details).

# References

If you're new to this field, We believe the following papers can help you quickly get familiar with it (continuously updated):

- Wu, J., Yang, S., Zhan, R., Yuan, Y., Chao, L. S., & Wong, D. F. (2025). A survey on LLM-generated text detection: Necessity, methods, and future directions. Computational Linguistics, 1-66.
- Wu, J., Zhan, R., Wong, D. F., Yang, S., Yang, X., Yuan, Y., & Chao, L. S. (2024). DetectRL: Benchmarking LLM-Generated Text Detection in Real-World Scenarios. In The Thirty-eight Conference on Neural Information Processing Systems Datasets and Benchmarks Track.
- Mitchell, E., Lee, Y., Khazatsky, A., Manning, C. D., & Finn, C. (2023, July). Detectgpt: Zero-shot machine-generated text detection using probability curvature. In International Conference on Machine Learning (pp. 24950-24962). PMLR.
- Bao, G., Zhao, Y., Teng, Z., Yang, L., & Zhang, Y. Fast-DetectGPT: Efficient Zero-Shot Detection of Machine-Generated Text via Conditional Probability Curvature. In The Twelfth International Conference on Learning Representations.
- Hans, A., Schwarzschild, A., Cherepanova, V., Kazemi, H., Saha, A., Goldblum, M., ... & Goldstein, T. (2024, July). Spotting LLMs With Binoculars: Zero-Shot Detection of Machine-Generated Text. In International Conference on Machine Learning (pp. 17519-17537). PMLR.
- Guo, B., Zhang, X., Wang, Z., Jiang, M., Nie, J., Ding, Y., ... & Wu, Y. (2023). How close is chatgpt to human experts? comparison corpus, evaluation, and detection. arXiv preprint arXiv:2301.07597.
- Wu, J., Zhan, R., Wong, D. F., Yang, S., Liu, X., Chao, L. S., & Zhang, M. (2025, January). Who Wrote This? The Key to Zero-Shot LLM-Generated Text Detection Is GECScore. In Proceedings of the 31st International Conference on Computational Linguistics (pp. 10275-10292).
