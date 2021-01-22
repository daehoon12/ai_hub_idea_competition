## 인공지능 학습용 데이터 활용 아이디어 공모전  

![image](https://user-images.githubusercontent.com/32921115/105443502-38635c00-5caf-11eb-8556-8ec47ef6ec9d.png)

## 팀원  
[daehoon12(강대훈)](https://github.com/daehoon12)  
[jiminAn(안지민)](https://github.com/jiminAn)  

## 인공지능 학습용 데이터 활용 아이디어 제목  
- 대화형 키오스크 : Hello, Kiosk! (음성인식 기술을 사용한 기존의 키오스크 대체 서비스)  

## 인공지능 학습용 데이터 활용 아이디어 내용  
 대다수의 패스트푸드점/카페/음식점 등에서 점원이 직접 주문을 받지 않고 키오스크라 불리는 무인 자동 주문 기기를 배치해 음식 주문부터 결제까지 사람과의 대화 한 마디 필요없이 결제 과정이 진행되는 모습을 주변에서 흔치 않게 볼 수 있다. 이러한 키오스크는 사업자 입장에서는 인건비 절감, 고객 입장에서는 대기시간과 처리시간이 짧다는 장점이 있지만 해당 시스템이 모두에게 좋기만 한 것은 아니다. **어린이나 노인, 그리고 장애인의 경우 키오스크에 대한 접근성이 크게 떨어진다는 지적이 항상 나오고 있기 때문이다.** 실제로 키오스크 시스템은 고객의 키오스크에 대한 학습을 전제한다. 학습 능력이 빠르고 신문물에 대한 수용능력이 높은 10~30대 사용자는 초기의 키오스크 등장에도 해당 시스템에 금방 적응하며 편리하게 이용하는 모습을 보이나 혼자 키오스크를 사용하기 어려운 어린이와 장애인, 전자기기에 익숙하지 않은 노인들에게는 이러한 키오스크가 하나의 장벽으로 다가왔다. 실제로 키오스크 관련 기사들을 찾아보면 키오스크가 세대간 정보의 격차를 더 심화시키고 오히려 주문 시간이 더 소요되는 반대의 경우도 늘어나고 있는 것을 확인할 수 있다.  


 이러한 문제점을 해결하기 위해 단순히 터치만으로 이루어지는 기계적인 절차의 키오스크 시스템이 아닌 더욱 다양한 사람들을 배려한, **조금 더 인간적인 키오스크인 <대화형 키오스크 : Hello, Kiosk!> **서비스를 제안한다. 해당 서비스는 **음성인식 기술**로 고객의 말을 키오스크가 이해하고, **고객의 요구에 따른 적절한 화면 전환**을 제공하고, **복잡한 절차를 거치지 않는 직관적인 인터페이스**를 가지는 서비스이다.  

### 서비스 제공 절차  

![image](https://user-images.githubusercontent.com/32921115/105442899-fa196d00-5cad-11eb-927a-514028489117.png)  

### 예시  

![image](https://user-images.githubusercontent.com/32921115/105443075-45338000-5cae-11eb-9802-3b36a405de45.png)  

![image](https://user-images.githubusercontent.com/32921115/105443108-541a3280-5cae-11eb-9e08-e31690512d7c.png)  

![image](https://user-images.githubusercontent.com/32921115/105443117-58465000-5cae-11eb-82c6-197534fab9be.png)  

## 인공지능 학습용 데이터 학습방법  
대화형 키오스크 : Hello, Kisosk!는 대화형 인공지능 기술로 자연어 이해(NLU)와 음성처리 기술을
필요로 합니다. **Chatbot, STT의 두 가지 기술**로 기존의 터치식 키오스크와 달리 좀 더 인간적인
키오스크 서비스 개발을 목표로 합니다.

### 1. Speech to text(Speech recognition)
AI hub에서 제공하는 한국인 대화 음성 데이터를 활용하여 **다양한 환경, 연령 및 지역별 화자의
데이터 셋을 학습**해 저품질 음성, 다양한 발화, 실제 대화형 음성에 대해서도 잘 동작하도록 하는
것이 학습 목표

<학습 과정>
1.	원시데이터(음성) PCM을 비트로 바꾸기
2.	샘플링 된 음성 데이터 전처리 하기
3.	짧은 소리로부터 특징 인식하기

즉, **오디오를 처리하기 쉬운 포맷으로 만들어 RNN Model**에 이를 제공한다. 각각의 작은 오디오 조각 마다 **현재 발음되는 소리에 해당하는 문자가 무엇인지 찾는 과정을 거침.** 해당 학습 과정을 거쳐 input으로 들어오는 화자의 발화를 실시간으로 텍스트로 변환  

### 2. Chatbot : NLU  
AI hub에서 제공하는 한국인 대화 데이터를 이용해 사용자의 의도를 파악하여 그에 따라 시스템이 응답 또는 행동을 하는 대화/생성 관리로 구현하며 해당 데이터의 기본 구조는 질의/응답으로 구성되므로 각 문장에서 고유 명사와 복합 명사, 수식 표현 등 **사용자 의도가 반영된 개체(entity)를 추출하여 NLU(Natural Language Understanding)를 통한 화자에 의도에 맞는 응답을 함.**  
 
<학습 과정>  
1.	Speech Recognition을 통해 Text화 된 문장이 Seq2seq Model의 Input으로 들어온다.  
2.	토큰화 뒤 Encoder에서 Word Embedding을 수행하는 Embedding Layer에 값이 들어간다.  
3.	Word Embedding이 되어 숫자 vector가 된 Input을 LSTM에 통과시킨다.  
4.	마지막 LSTM 까지 통과 후 Hidden State (Context Vector)를 가져와 Decoder에 넘긴다.  
5.	Decoder는 문장 시작을 알리는 심볼 <SOS>를 Input으로 받아 다음에 등장할 확률이 높은 단어를 예측, Context Vector는 Decoder의 첫번째 Hidden State 값으로 사용된다.  
6.	계속 반복해 EOS를 출력하면 예측한 문장을 소리와 화면으로 보여준다.  
7.	**Training 방법은 정답을 알려주면서 Learning하는 Teacher Forcing**을 사용하고, 실제 **test 과정에서는 Context Vector와 처음에 문장을 시작하는 심볼 <SOS>만을 입력**으로 받아 다음에 올 단어를 예측하고 다음 RNN Cell의 입력으로 넣는 행위를 반복함.  

![image](https://user-images.githubusercontent.com/32921115/105443399-e9b5c200-5cae-11eb-9c4e-266d62d2732e.png)

1.	Encoder Architecture  
- Embedding Layer와 LSTM layer로 구성  
- Embedding Layer는 Word를 사용자가 Hyperparameter로 설정한 고정길이만큼 숫자로 만들어준다.  
- 이 숫자를 LSTM에 넣고 Output으로 나오는 y^은 버리고 최종적으로 Hidden State만 출력한다.  
- Hidden State는 고정 길이 안에 입력 문장을 번역하는데 필요한 정보를 인코딩한다.  

2.	Decoder Architecture  
- Encoder가 출력한 Hidden State가 첫번째 LSTM 층에 입력됨.  
- 나머지는 RNN 언어 모델을 이용한 문장 생성과 같음.  

### 최종 System Architecture  

![image](https://user-images.githubusercontent.com/32921115/105443449-0d790800-5caf-11eb-8913-9409640c89d7.png)

