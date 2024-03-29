# mT5 Translator kor-eng
[AI Hub 구어체 말뭉치](https://aihub.or.kr/aidata/87) & 265편의 넷플릭스 자막을 학습시켜 mT5 모델로 만든 자연스러운 번역기
---
[mT5](https://arxiv.org/abs/2010.11934) : 101개국의 언어로 사전 학습된 Text to Text Transfomer 기반 딥러닝 모델입니다. 

huggingface를 바탕으로 한 [simpletransfomers](https://github.com/ThilinaRajapakse/simpletransformers) 라이브러리를 활용하여, 
mT5 모델을 fine-tuning 시켰습니다. [링크](https://huggingface.co/AimB/mT5-en-kr-natural)
```
pip install simpletransformers
from simpletransformers.t5 import T5Model

model = T5Model("mt5", "AimB/mT5-en-kr-natural")
print(model.predict(["I feel good today"]))
print(model.predict(["우리 집 고양이는 세상에서 제일 귀엽습니다"]))
```
단 4줄의 코드만으로 어떤 환경에서든, 제가 fine-tuning한 모델을 사용해보실 수 있습니다.
(긴 문장보다 짧은 문장이 더 정확하게 번역됩니다. 현재 주어/목적어를 혼동하는 이슈가 있습니다.)

## 번역 예시
```
kor> 너 참 예쁘다 
eng> you look pretty 
```
```
kor> 우리 집 고양이가 세상에서 제일 귀엽습니다
eng> my cat is the most cute in the world 
```
```
kor> 적당히 바람이 시원해 기분이 좋아요
eng> I feel good. I feel a good wind.
```
```
kor> 네가 밥 먹으러 가자고 했잖아
eng> you told me to go eat.
```

## 성능
|    | Model    | Dataset    | size   |   BLEU |
|---:|:---------|:-----------|:-------|-------:|
|  0 | mT5-base | aihub+subs | 51만   |  18.03 |

## Requirements
```
simpletransfomers
```

## References
[How to Train an mT5 Model for Translation With Simple Transformers](https://towardsdatascience.com/how-to-train-an-mt5-model-for-translation-with-simple-transformers-30ba5fa66c5f)
