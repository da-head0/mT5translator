# mT5 Translator kor-eng
[AI Hub의 구어체](https://aihub.or.kr/aidata/87) & 265편의 넷플릭스 자막을 학습시켜 mT5 모델로 만든 자연스러운 번역기
---
[mT5](https://arxiv.org/abs/2010.11934) : 2020년 10월 구글에서 발표한 101개국의 언어로 사전학습시킨 딥러닝 모델입니다. 

huggingface를 바탕으로 한 [simpletransfomers](https://github.com/ThilinaRajapakse/simpletransformers) 라이브러리를 활용하여, 
mT5 모델을 fine-tuning 시켰습니다. [링크](https://huggingface.co/AimB/mT5-en-kr-natural)
```
pip install simpletransformers
from simpletransformers.t5 import T5Model

model = T5Model("mt5", "AimB/mT5-en-kr-natural")
print(model.predict(["I feel good today"]))
print(model.predict(["우리집 고양이는 세상에서 제일 귀엽습니다"]))
```
단 4줄의 코드만으로 어떤 환경에서든, 제가 fine-tuning한 모델을 사용해보실 수 있습니다.

## 번역 예시
```
kor> 너 참 예쁘다 
eng> you look pretty 
```
```
kor> 우리집 고양이가 세상에서 제일 귀엽습니다
eng> my cat is the most cute in the world 
# the cutest 가 일반적이지만 The most cute란 표현도 쓰이긴 합니다.
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
