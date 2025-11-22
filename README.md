# Malaria Parasite Detection in Microscopic Images Using an Ensemble Approach with Pre-trained CNNs

Malaria diagnosis traditionally relies on manual microscopic examination, which is accurate but slow, labor-intensive, and difficult to deploy in low-resource regions. Recent advances in deep learning offer a promising alternative for automating parasite detection in blood smear images. In this work, we develop a lightweight malaria classification system using three pre-trained CNN models—EfficientNetB0, ResNet18, and MobileNetV2—fine-tuned on a public dataset of parasitized and uninfected red blood cells. The individual model outputs are combined through a soft-voting ensemble to improve robustness and reduce misclassification. Our ensemble is able to achieve 97.46% accuracy, 97.93% precision, 96.84% recall, and a 97.39% F1-score, which outperforms the individual models and provides more consistent predictions. Because of how our approach utilizes small, transfer-learned models, it remains computationally efficient and suitable for deployment in low-resource clinical settings.

<img width="115" height="115" alt="uninfected" src="https://github.com/user-attachments/assets/cd464e52-cfbd-478e-8d61-caa7625208cc" /> <img width="142" height="163" alt="parasitized" src="https://github.com/user-attachments/assets/8a5c84db-2a74-495f-8004-56916c83adc3" />

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install the dependencies.

```bash
git clone https://github.com/OMARALQ101/Malaria-Parasite-Detection-in-Microscopic-Images-Using-an-Ensemble-Approach-with-Pre-trained-CNNs.git
cd Malaria-Parasite-Detection-in-Microscopic-Images-Using-an-Ensemble-Approach-with-Pre-trained-CNNs

pip install -r requirements.txt
```

## The Dataset

Download the Malaria Dataset from [Kaggle](https://www.kaggle.com/datasets/iarunava/cell-images-for-detecting-malaria) (originally published by the [NIH](https://ceb.nlm.nih.gov/repositories/malaria-datasets/))
You should see the directories as follows:

```text
data/malaria_cells_nih/
├── Parasitized/
└── Uninfected/
```

## Accessing The Models Trained in This Project

Use this [link](https://drive.google.com/drive/folders/1StnyM-V8np5PgK1qA5ZixNoTT7CUzPTp?usp=drive_link) to download the models that I trained (I couldn't upload one of the models onto Github due to file size constraint).

## Ensemble Performance

<img width="582" height="432" alt="cmensemble" src="https://github.com/user-attachments/assets/d71af0d5-1ebc-4db1-a127-2047b04f6411" />

```text
========= Parasitized as Positive Class =========
Total samples: 5512
Label counts: tensor([2693, 2819], device='cuda:0')
Pred counts : tensor([2663, 2849], device='cuda:0')
Correct: 5372 Wrong: 140
Accuracy from raw counts: 0.974600870827286
precision: 0.9793466015734911  recall: 0.9684366877052788  f1: 0.9738610853624652  accuracy: 0.9746008708255178
TP, FP, FN, TN: 2608 55 85 2764

========= Uninfected as Positive Class =========
Total samples: 5512
Label counts: tensor([2693, 2819], device='cuda:0')
Pred counts : tensor([2663, 2849], device='cuda:0')
Correct: 5372 Wrong: 140
Accuracy from raw counts: 0.974600870827286
precision: 0.9701649701615649  recall: 0.9804895352927262  f1: 0.9752999244250686  accuracy: 0.9746008708255178
TP, FP, FN, TN: 2764 85 55 2608
```

## EfficientNetB0 Performance

<img width="587" height="455" alt="losscurveefficient" src="https://github.com/user-attachments/assets/37e931dd-d854-4c43-84a2-266a051dc950" /><img width="587" height="455" alt="accuracyefficient" src="https://github.com/user-attachments/assets/85082466-bebd-49fd-a6f1-0df75765bd5f" /><img width="582" height="432" alt="cmefficient" src="https://github.com/user-attachments/assets/c0bf9ac0-8f76-4ea7-b837-4ba94c4f660b" />

```text
========= Parasitized as Positive Class =========
Total samples: 5512
Label counts: tensor([2693, 2819], device='cuda:0')
Pred counts : tensor([2653, 2859], device='cuda:0')
Correct: 5350 Wrong: 162
Accuracy from raw counts: 0.9706095791001451
precision: 0.977007161700049  recall: 0.9624953583328537  f1: 0.969696964693622  accuracy: 0.9706095790983843
TP, FP, FN, TN: 2592 61 101 2758

========= Uninfected as Positive Class =========
Total samples: 5512
Label counts: tensor([2693, 2819], device='cuda:0')
Pred counts : tensor([2653, 2859], device='cuda:0')
Correct: 5350 Wrong: 162
Accuracy from raw counts: 0.9706095791001451
precision: 0.9646729625709526  recall: 0.9783611209614106  f1: 0.9714688220486052  accuracy: 0.9706095790983843
TP, FP, FN, TN: 2758 101 61 2592
```

## ResNet18 Performance

<img width="578" height="455" alt="lossrenet" src="https://github.com/user-attachments/assets/6273d90e-d1eb-4486-9d7e-93289b0055cd" /><img width="587" height="455" alt="accuracyresnet" src="https://github.com/user-attachments/assets/9dbe5f60-db20-4cab-be39-deb729798341" /><img width="582" height="432" alt="cmresnet" src="https://github.com/user-attachments/assets/14fc2e6a-66bf-4662-81be-cdce9402b055" />

```text
========= Parasitized as Positive Class =========
Total samples: 5512
Label counts: tensor([2693, 2819], device='cuda:0')
Pred counts : tensor([2654, 2858], device='cuda:0')
Correct: 5303 Wrong: 209
Accuracy from raw counts: 0.9620827285921626
precision: 0.9679728711342579  recall: 0.9539546973599928  f1: 0.9609126563020768  accuracy: 0.9620827285904171
TP, FP, FN, TN: 2569 85 124 2734

========= Uninfected as Positive Class =========
Total samples: 5512
Label counts: tensor([2693, 2819], device='cuda:0')
Pred counts : tensor([2654, 2858], device='cuda:0')
Correct: 5303 Wrong: 209
Accuracy from raw counts: 0.9620827285921626
precision: 0.9566130160918244  recall: 0.9698474636361482  f1: 0.9631847756908714  accuracy: 0.9620827285904171
TP, FP, FN, TN: 2734 124 85 2569
```

## MobileNetV2 Performance

<img width="587" height="455" alt="losscurvemobilenet" src="https://github.com/user-attachments/assets/b8a388fa-89ac-4047-a575-b44ec3f5036f" /><img width="574" height="455" alt="accuracycurvemobilenet" src="https://github.com/user-attachments/assets/f2340795-b093-49c4-ad1b-35242eb7bf1e" /><img width="582" height="432" alt="cmmobilenet" src="https://github.com/user-attachments/assets/ff99e806-5e5f-4bb1-a063-7cb579a80e4e" />

```text
========= Parasitized as Positive Class =========
Total samples: 5512
Label counts: tensor([2693, 2819], device='cuda:0')
Pred counts : tensor([2688, 2824], device='cuda:0')
Correct: 5335 Wrong: 177
Accuracy from raw counts: 0.9678882438316401
precision: 0.9680059523773512  recall: 0.9662086891906194  f1: 0.9671064807797216  accuracy: 0.9678882438298841
TP, FP, FN, TN: 2602 86 91 2733

========= Uninfected as Positive Class =========
Total samples: 5512
Label counts: tensor([2693, 2819], device='cuda:0')
Pred counts : tensor([2688, 2824], device='cuda:0')
Correct: 5335 Wrong: 177
Accuracy from raw counts: 0.9678882438316401
precision: 0.9677762039625787  recall: 0.9694927279142622  f1: 0.9686337004723816  accuracy: 0.9678882438298841
TP, FP, FN, TN: 2733 91 86 2602
```

## License

[MIT](https://choosealicense.com/licenses/mit/)
