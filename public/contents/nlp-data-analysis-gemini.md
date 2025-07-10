---
id: 'Prompt-Engineering-2025-halfyear-gemini'
title: '대규모 언어 모델(LLM) 프롬프팅 기법 연구 보고서 (2025년 상반기 동향 중심)'
date: '2025-07-03'
author: 'Gemini Deep Research'
excerpt: 'LLM 프롬프팅은 모델의 잠재력을 최대한 활용하기 위해 명확하고 구체적인 지시를 제공하는 것이 핵심이며, CoT, RAG, 자기 수정, 다중 전문가 프롬프팅 등 다양한 고급 기법으로 발전했습니다. 2025년 상반기에는 프롬프트 최적화가 자동화되고 LLM의 신뢰성 및 안전성 확보에 중점을 두면서, LLM이 자율적이고 다목적인 시스템으로 진화하고 있습니다.'
category: '메타 지식'
type: '프롬프트 엔지니어링'
---

# 대규모 언어 모델(LLM) 프롬프트 엔지니어링 연구 보고서 (2025년 상반기 동향 중심)

대규모 언어 모델(LLM)은 인공지능 분야에서 핵심적인 발전을 이루며 다양한 응용 분야에서 핵심적인 역할을 수행하고 있습니다. 이러한 LLM의 잠재력을 최대한 활용하기 위해서는 모델에 대한 효과적인 지침, 즉 '프롬프트 엔지니어링'이 필수적입니다. 프롬프트 엔지니어링은 LLM의 출력을 최적화하고, 복잡한 작업을 수행하며, 모델의 한계를 극복하는 데 중요한 기술로 부상했습니다. 본 보고서는 2025년 상반기까지 알려진 LLM 프롬프트 엔지니어링의 주요 방법론과 최신 동향을 심층적으로 분석하고, 각 기술의 원리, 장점, 한계 및 실제 적용 사례를 포괄적으로 제시합니다. 또한, 프롬프트 엔지니어링의 발전이 LLM의 전반적인 성능과 신뢰성에 미치는 지대한 영향을 조명하고, 향후 발전 방향에 대한 제언을 포함합니다.

## 1\. LLM 프롬프트 엔지니어링의 기본 원칙 및 핵심 개념

효과적인 LLM 프롬프트 엔지니어링은 단순히 질문을 던지는 것을 넘어, 모델이 원하는 결과를 정확하게 생성하도록 유도하는 과정을 포함합니다. 이 과정에는 여러 가지 핵심 원칙이 중요하게 작용합니다.

프롬프트는 명확하고 구체적이어야 합니다. 모델이 모호함 없이 원하는 결과를 정확히 이해할 수 있도록 지시를 명확하게 표현하고, 필요한 세부 사항이나 맥락을 포함하는 것이 중요합니다. 예를 들어, "기후 변화에 대한 요약을 제공하라"는 막연한 문구보다는 "기후 변화에 대한 요약을 300단어 이내로 제공해 주시겠습니까?"와 같이 구체적인 표현을 사용하는 것이 모델과의 상호작용에서 더 효율적입니다.

필요한 제약 조건이나 배경 정보를 제공하여 모델이 고려해야 할 규칙, 세부 사항을 찾아내도록 해야 합니다. 또한, 모델이 생성할 답변의 대상을 명시하면 출력이 명확한 이해 수준에 맞춰 조정됩니다. 예를 들어, "기계 학습 개념을 데이터 과학 전문가에게 설명하라" 또는 "기계 학습 개념을 고등학생에게 설명하라"와 같이 대상 청중을 지정할 수 있습니다.

원하는 출력의 긍정적인 예시와 원치 않는 출력을 피하기 위한 부정적인 예시를 포함하여 모델을 안내할 수 있습니다. 특정 요구 사항을 강조하기 위해 대조적인 예시를 사용하는 것도 효과적입니다. 예를 들어, 메일을 쓸 때는 "포함하라"는 긍정적인 지시어를 사용하고, "잊지 마라"는 부정적인 지시어는 피하는 것이 좋습니다.

프롬프트는 간결하고 집중적이어야 합니다. 지나치게 길거나 복잡한 지침은 피하고, 간결한 정보로 지시를 전달하는 것이 중요합니다. 프롬프트의 여러 섹션을 구분하기 위해

### Instruction\#\#\# 또는 \#\#\#Example\#\#\#과 같은 특정 구분자를 사용할 수 있습니다.

AI 모델의 기능과 한계를 이해하고, 모델의 약점을 활용하기 위해 다양한 프롬프트를 시도해야 합니다. 프롬프트 문구에 따라 모델 출력을 정량적으로 평가하고, 관찰된 모델 동작에 따라 프롬프트를 조정하며, 사용자 피드백을 통해 프롬프트 효과를 개선하는 것이 필수적입니다.

프롬프트 라이브러리는 언어 모델의 동작을 유도하기 위해 특정 지침이나 맥락을 제공하는 것을 의미합니다. 모델에 특정 역할을 부여하여 대화의 맥락을 강조할 수 있습니다. 예를 들어, "당신은 이제 전문 경제학자이다. 최신 인플레이션 전략을 추천하시겠습니까?"와 같이 역할을 부여할 수 있습니다. 복잡한 주제나 작업은 한 번의 간결한 프롬프트로 분할하여 처리하는 것이 효과적입니다. 예를 들어, "로봇, 인공지능이 무엇인지 설명하라. 다음으로, AI, 머신러닝, 딥러닝의 차이점을 설명하라"와 같이 작업을 분할할 수 있습니다. 프롬프트에 구두점을 추가하거나, 지시 순서의 중요성을 전달하기 위해 "단계별로 생각하라"와 같은 문구를 명시할 수 있습니다. 마지막으로, "자연적이고 인간적인 방식으로 발화하라"와 같은 지시를 포함하여 모델이 더 자연스러운 답변을 생성하도록 유도할 수 있습니다.

LLM 프롬프트에서 프롬프트에 너무 많은 요구 사항을 지정하는 것은 오히려 성능 저하를 초래할 수 있다는 점은 중요한 고려 사항입니다. 사용자는 또는 개발자는 LLM이 특정 요구 사항을 따르도록 하기 위해 가능한 한 많은 지침을 프롬프트에 포함하려는 경향이 있습니다. 이는 "더 많은 정보가 더 나은 결과를 낳는다"는 직관적인 가정에 기반합니다. 그러나 연구에 따르면, 모델 모든 요구 사항을 단순히 명시하는 전략은 LLM의 전반적인 지식 추출 능력을 저해할 수 있습니다. 더 많은 요구 사항을 지정할수록 LLM의 성능이 최대 19%까지 떨어질 수 있다는 보고가 있습니다. 또한, 개발자 프롬프트가 종종 불완전하게 지정되어 LLM이 지정되지 않은 요구 사항을 41.1%의 확률로 추론할 수 있지만, 이러한 동작은 안정적이지 않으며 모델 또는 프롬프트 변경 시 전반적인 정확도가 20% 이상 낮아질 가능성이 2배 증가합니다. 특히, 19가지 요구 사항을 한꺼번에 지정했을 때 GPT-4o의 평균 정확도는 85.0%로 낮아졌고, Llama-3.3-70B-Instruct와 같은 소형 모델은 79.7%로 더 낮은 결과를 보였습니다.

이러한 현상은 LLM이 한 번에 처리할 수 있는 지식의 복잡성과 양에 내재된 한계가 있음을 시사합니다. 너무 많은 지시가 주어지면, 모델은 중요한 지시를 간과하거나, 지시들 간의 모호한 관계를 해결하지 못하며 전반적인 성능이 저하될 수 있습니다. 이는 인간이 여러 가지 복잡한 지시를 동시에 받을 때 인지 부하가 증가하고 실수가 늘어나는 것과 유사한 원리입니다. 특정 요구 사항(예: "양자수도 이모티콘" 또는 "긍정 및 부정 예시 사용")의 경우, 명확한 제약 조건이 없어도 정확도가 크게 높아지는 현상이 관찰됩니다. 이는 프롬프트 엔지니어링이 단순히 "더 많이 말하는 것"이 아니라, "무엇을, 어떻게, 그리고 얼마나 말할 것인가"에 대한 전략적인 접근이 필요하다는 것을 의미합니다. 특히, 모델이 기본적으로 잘 따르는 요구 사항에 대해서는 의도적으로 명시하지 않거나, 핵심적인 소수의 요구 사항에 집중하여 프롬프트를 간결하게 유지하는 '의도적 불완전 지정'이 효과적인 전략이 될 수 있습니다. 이는 프롬프트 최적화의 새로운 방향을 제시합니다.

## 2\. 주요 LLM 프롬프트 엔지니어링 기술 심층 분석

LLM 프롬프트 엔지니어링은 단순한 지시를 넘어 복잡한 추론, 외부 지식 활용, 자체 교정, 다중 전문가 모방 등 고차원적인 기능을 갖추게 하는 여러 기술로 발전했습니다.

### 2.1 제로샷 및 퓨샷 프롬프트

#### 개념 및 작동 방식

  * **제로샷 프롬프트 (Zero-shot Prompting)**: 이 기술은 모델에게 어떤 예시도 제공하지 않고, 오직 지시만으로 작업을 수행하도록 요청합니다. 모델은 사전 학습된 방대한 지식을 바탕으로 작업을 이해하고 답변을 생성합니다. 이는 방대한 데이터로 훈련된 LLM의 일반화 능력을 최대한 활용합니다.
  * **퓨샷 프롬프트 (Few-shot Prompting)**: 프롬프트 내에 2\~5개의 소수 예시를 포함하여 모델이 원하는 동작을 학습하고 모방하도록 돕는 기술입니다. 이는 "In-context Learning (ICL)"을 통해 모델이 패턴을 인식하고 새로운 능력에 효과적으로 일반화하도록 돕습니다. 모델은 제공된 예시들을 처리하며 내재된 패턴을 찾아내고, 이를 기반으로 이전에 보지 못한 작업에 대한 해결책을 도출합니다.
  * **원샷 프롬프트 (One-shot Prompting)**: 제로샷과 퓨샷의 중간 형태로, 단 하나의 예시를 제공하여 모델의 이해를 돕고 성능을 향상시킵니다. 이는 기본적인 분류나 구조화된 정보 추출과 같이 특정 지침이 필요한 작업에 유리합니다.

#### 장점 및 한계

  * **제로샷**: 레이블링된 데이터가 부족하거나 응답 속도가 중요할 때 특히 유리합니다. 모델이 예시 입력을 처리하거나 미리 조정할 필요가 없어 프롬프트 크기가 작고 지연 시간이 짧습니다. 그러나 문맥에 모호함이 있거나 미묘한 언어적 뉘앙스가 있을 경우 출력에 미묘한 영향을 미칠 수 있습니다.
  * **퓨샷**: 복잡한 작업에서 더 나은 정확도를 제공하며, 특히 대규모 언어 모델에서 효과적입니다. 새로운 작업에 대한 빠른 적응, 최소한의 데이터 수집 및 준비, 다양한 도메인 및 사용 사례에 대한 유연성이 가능합니다. 하지만 더 큰 프롬프트와 더 많은 토큰을 필요로 하여 계산 비용이 증가할 수 있고, 모델의 컨텍스트 창 크기에 제약을 가할 수 있습니다. 복잡한 추론 작업에는 한계가 있어, 단순히 예시를 추가하는 것만으로는 해결되지 않을 수 있습니다.

#### 주요 적용 사례

  * **제로샷**: 번역, 요약, 감성 분석, 고의적 피드백 분석, 스팸 감지, 소셜 미디어 감성 분석 등 사전 정의된 예시가 필요 없거나 즉각적인 응답이 중요한 작업에 적합합니다.
  * **퓨샷**: 텍스트 분류, 감성 분석, 정보 추출 (이름, 나이, 직업 등), 제목 발명, 챗봇 생성 (특정 스타일의 대화) 등 모델이 패턴을 인식하고 모방해야 하는 복잡한 작업에 유리합니다.

#### 모범 사례 (퓨샷)

  * 프롬프트에 최소 2개에서 최대 5개의 예시를 포함하는 것이 일반적으로 권장됩니다. 너무 적은 예시는 충분한 맥락을 제공하지 못할 수 있고, 너무 많은 예시는 모델을 오도하거나 혼란스럽게 할 수 있습니다.
  * 예시는 다양해야 하며, 긍정적 및 부정적 사례를 모두 포함하여 작업의 경계를 모델이 이해하도록 돕는 것이 중요합니다.
  * 예시의 순서를 무작위로 하고 일관된 형식을 유지해야 모델이 패턴을 효과적으로 학습할 수 있습니다.
  * Input: Output: 또는 INPUT/OUTPUT과 같은 명확한 구분자를 사용하여 예시와 실제 쿼리를 구분해야 합니다. 이 명확성은 모델이 의도를 올바르게 구별하는 데 도움이 됩니다.
  * 초기에는 간결한 예시로 시작하고 필요에 따라 프롬프트 형식을 조정해야 합니다. 너무 일찍부터 복잡하게 만들지 않는 것이 좋습니다.

이러한 현상은 LLM이 예시로부터 '패턴'을 인식하고 새로운 작업에 대한 해결책을 '도출'하는 능력을 활용하기 때문입니다. 단순히 예시의 수가 아니라, '관련성'과 '다양성'에 크게 좌우됩니다. 퓨샷 프롬프트는 예시를 제공하여 모델의 성능을 향상시키는 반면, 더 많은 예시를 제공할수록 모델이 더 잘 학습할 것이라는 가정이 일반적일 수 있습니다. 그러나 퓨샷 프롬프트의 성패는 '예시 선택(Example Selection)', '형식 일관성(Format Consistency)', '컨텍스트 윈도우 관리(Context Window Management)'에 크게 의존합니다. 특히, 효과적인 퓨샷 프롬프트는 관련성 있는 예시의 수와 질 사이에 균형을 이룹니다. 너무 적은 예시는 충분한 맥락을 제공하지 못할 수 있고, 너무 많은 예시는 모델을 오도하거나 혼란스럽게 할 수 있습니다. 또한, 예시는 다양해야 하고 긍정적 및 부정적 사례를 모두 포함하여 작업의 경계를 모델이 이해하도록 돕는 것이 중요합니다. 무작위된 순서는 모델을 혼란스럽게 할 수 있습니다.

### 2.2 CoT (Chain-of-Thought) 프롬프트

#### 개념 및 메커니즘

CoT 프롬프트는 복잡한 다단계 추론 작업을 위해 LLM의 추론 능력을 향상시키는 프롬프트 엔지니어링 기술입니다. 이 기술은 모델이 논리적인 단계의 일관된 시리즈를 사용하여 단계별 추론 과정을 명시적으로 기록하도록 유도함으로써 문제 해결을 용이하게 합니다. CoT는 LLM이 언어적으로 "속으로 생각하는" 능력에서 영감을 얻었으며, 모델 크기가 커질수록 추론 능력과 정확도가 증가하는 '이머전트 능력(emergent ability)'으로 강조됩니다.

CoT의 메커니즘은 사용자가 일반적으로 프롬프트 끝에 "당신의 추론 단계를 설명하라" 또는 "답변을 단계별로 설명하라"와 같은 지시를 추가하여 모델이 결과뿐만 아니라 그 결과에 이르게 된 중간 단계들을 상세히 설명하도록 요청하는 방식으로 작동합니다. 이는 LLM이 출력을 여러 단계로 분해하도록 돕습니다. 예를 들어,

x^2 - 5x + 6 = 0와 같은 이차 방정식을 풀 때, CoT 프롬프트는 LLM이 방정식을 표준 형식으로 식별하고, 계수를 정하고, 이차 공식을 적용하고, 판별식을 계산하고, 최종적으로 x 값을 계산하는 일련의 논리적 단계를 명시하도록 안내합니다.

#### 성능 향상 효과

CoT 프롬프트는 복잡한 문제를 더 간결하고 관리하기 쉬운 단계로 분해하여 LLM이 정보를 더 효과적으로 처리하고 해결하도록 함으로써 정확도와 관련성을 높입니다. 특히 수학 문제 해결 능력은 기준 방식 대비 300% 이상 향상되는 것으로 나타납니다 (GSM8K 벤치마크 기준). 또한, 단순 추론, 상식 추론, 상징적 추론 등 다양한 벤치마크에서 상당한 정확도 향상을 가져옵니다.

#### CoT의 변형 및 활용 전략

  * **제로샷 CoT**: 단순히 "단계별로 생각해보라"는 문구를 추가하는 것만으로도 복잡한 문제에 대한 CoT 추론을 유도할 수 있습니다.
  * **CoT와 퓨샷 프롬프트 결합**: 복잡한 작업의 경우, CoT와 퓨샷 프롬프트를 결합하는 것이 특히 효과적일 수 있습니다.
  * **CoT의 투명성**: CoT 프롬프트의 투명성은 개발자가 모델이 추론하는 과정을 이해하는 데 도움을 주어 오류 및 모델 디버깅에 기여합니다.

CoT는 LLM의 '블랙박스' 특성을 우회하고, '설명 가능한 AI(Explainable AI, XAI)'의 중요한 기반이 됩니다. LLM은 내부 작동 방식이 불투명한 '블랙박스' 모델로, 왜 특정 답변을 생성했는지 이해하기 어렵다는 비판을 받아왔습니다. 그러나 CoT 프롬프트는 LLM을 "블랙박스에서 투명한 추론 기계로 전환시킨다"고 평가됩니다. 이는 모델이 복잡한 작업을 더 간결한 단계로 분해하여 처리함으로써, 사용자가 LLM이 응답에 도달하는 과정에 대한 '제어 및 통찰력'을 얻을 수 있게 해주기 때문입니다. CoT는 '중간 출력 단계'를 생성함으로써 모델이 추론하는 방식에 대한 '투명성과 이해'를 제공합니다.

CoT는 LLM이 최종 답변만을 내뱉는 것이 아니라, 그 답변에 이르는 논리적인 과정을 명시적으로 보여주도록 강제합니다. 이 '단계별 설명'은 인간이 문제를 해결하는 방식과 유사하며, 모델의 내부 '사고 과정'을 가시화합니다. 이러한 가시화는 개발자가 LLM의 오류를 심층적으로 분석하고 디버깅하는 데 중요한 도움을 줍니다. 또한, 사용자는 모델의 답변이 단순히 우연히 나온 것이 아니라, 논리적인 근거를 가지고 있음을 확인할 수 있어 모델에 대한 신뢰도가 높아집니다. CoT는 단순히 LLM의 성능을 향상시키는 기술을 넘어, LLM의 '설명 가능성'을 높이는 근본적인 방법론입니다. 이는 특히 법률 검토, 금융 분석, 의료 진단 등 높은 신뢰성과 투명성이 요구되는 분야에서 LLM의 활용 가능성을 크게 확장시킵니다. CoT가 적용하는 출력 과정의 투명성은 LLM이 단순한 예측기가 아닌, '이해 가능한 지능'으로 인식될 수 있는 중요한 발판을 마련합니다.

### 2.3 RAG (Retrieval-Augmented Generation) 프롬프트

#### 개념 및 메커니즘

RAG는 LLM의 출력을 최적화하기 위해, 모델의 학습 데이터 소스 외부에 있는 지식 기반을 참조하여 답변을 생성하는 과정입니다. 이 기술의 메커니즘은 다음과 같습니다. 먼저 사용자 쿼리를 분석하여 핵심 개념을 식별한 후, 검색 시스템이 외부 코퍼스(예: 인터넷, 도메인별 데이터베이스)에서 관련 문서를 검색합니다. 이 검색된 정보는 LLM에 추가적인 맥락으로 제공되어, 모델이 새로운 지식과 기존 학습 데이터를 결합하여 더 나은 답변을 생성하도록 돕습니다. 이 과정은 외부 데이터를 벡터 표현으로 변환하여 벡터 데이터베이스에 저장하고, 사용자 쿼리를 벡터 표현으로 변환하여 관련 정보를 검색하는 방식으로 이루어집니다.

#### 주요 장점

  * **비용 효율성**: LLM을 특정 조직이나 도메인에 맞게 미세 조정(fine-tuning)하는 데 드는 막대한 계산 및 재정적 비용을 절감합니다. RAG는 새로운 데이터를 LLM에 통합하는 더 비용 효율적인 전략입니다.
  * **최신 정보 적용**: LLM이 최신 연구, 통계, 뉴스 등 최신 정보를 활용할 수 있도록 하여 답변의 정확도와 관련성을 유지하도록 돕습니다. LLM을 라이브 소셜 미디어 피드, 뉴스 사이트 또는 기타 업데이트되는 정보 소스에 직접 연결할 수 있습니다.
  * **사용자 신뢰도 향상**: LLM이 출처를 명시하고 인용할 수 있도록 하여 정확한 정보를 제공하고 사용자 신뢰를 높입니다. 사용자는 필요에 따라 원본 출처를 직접 확인할 수도 있습니다.
  * **개발자 제어력 강화**: 개발자가 LLM의 정보 소스를 제어하고 개발 단계에서 원하는 요구 사항에 집중하거나 오류 기능을 지원할 수 있습니다. 모호한 정보 검색을 제한할 수 있습니다.
  * **지식 확장 및 도메인 전문화**: RAG는 LLM이 기본 학습 데이터를 넘어 외부 지식 소스를 활용하여 지식 범위를 확장하고 특정 도메인(예: 과학 연구, 의료 진단, 법률 분석)에 전문화하도록 돕습니다.
  * **설명 가능한 AI 기여**: 생성 과정에서 사용된 외부 소스를 명확히 보여줌으로써 LLM 출력의 해석 가능성을 높여 AI 시스템에 대한 신뢰와 이해를 증진시킵니다.

#### 2025년 RAG의 발전 동향 및 과제

2025년에는 RAG가 LLM의 한계를 해결하고 새로운 가능성을 열어주는 핵심적인 역할을 할 것으로 예상됩니다. 특히, 멀티모달 검색 시스템과의 통합을 통해 이미지, 비디오, 구조화된 데이터 등 다양한 유형의 데이터를 활용하여 더 포괄적인 언어 생성을 가능하게 할 잠재력이 있습니다.

그러나 RAG는 여러 가지 과제에 직면해 있습니다. 방대하고 다양한 데이터 소스에서 관련 정보를 신속하게 찾는 효율적인 검색 시스템 개발은 여전히 어려운 과정이며, 특히 실시간 응용 프로그램의 경우 더욱 그렇습니다. 검색된 정보의 품질과 신뢰성을 보장하는 것이 중요하며, 품질이 낮은 데이터는 LLM 출력의 오류 가능성을 높일 수 있습니다. 맥락 통제 및 일관성 유지는 여전히 문제입니다. 또한, 개인 정보 보호, 편향, 유해 텍스트 확산 가능성 등 윤리적 고려 사항 또한 RAG 시스템 설계에 필수적입니다.

RAG는 LLM의 '환각(Hallucination)' 문제를 해결하고 '실시간성'을 확보하는 핵심 수단으로 자리매김하고 있습니다. LLM은 학습 데이터에 없는 정보를 추론하거나, 복잡한 추론 과정에서 '환각'이라고 불리는 사실과 다른 내용을 지어내는 경향이 있습니다. 또한, 학습 데이터가 특정 시점까지의 정보만을 포함하므로 최신 정보에 대한 답변은 어렵습니다. RAG의 핵심 이점은 "외부 지식 기반 검색" 및 "최신 정보 적용"에 있습니다. RAG는 "사실 확인 및 검증"을 통해 LLM 생성 출력의 '사실적 정확성 및 신뢰성'을 향상시키고, "잘못된 정보나 불확실한 정보의 확산 위험을 완화"한다고 강조됩니다. 이는 LLM이 즉흥적으로 생성한 정보가 아니라, 검색된 외부 소스에서 정보를 가져오도록 함으로써 환각을 줄이는 메커니즘입니다. 또한, LLM의 학습 데이터는 고정되어 있지만, RAG는 실시간으로 업데이트되는 외부 데이터베이스와 연동될 수 있어, 모델이 항상 최신 정보를 기반으로 답변을 생성할 수 있게 합니다. RAG는 LLM이 가진 고질적인 '환각' 문제와 '정보 최신성' 문제를 동시에 해결하는 강력한 기술입니다. 이는 LLM이 단순히 텍스트를 생성하는 도구를 넘어, 신뢰할 수 있는 '지식 에이전트'로 기능할 수 있는 기반을 제공합니다. 특히 금융 분석, 법률, 의료와 같이 정확성과 최신성이 절대적으로 요구되는 분야에서 RAG는 LLM 도입의 필수적인 요소로 부상하고 있으며, 2025년에도 그 중요성이 더욱 확대될 것으로 예상됩니다.

### 2.4 자체 수정 (Self-Correction) 프롬프트

#### 개념 및 필요성

자체 수정 프롬프트는 LLM의 응답이 정확하고 신뢰할 수 있도록 모델이 자체적으로 출력을 비판하고 개선하도록 유도하는 강력한 전략입니다. LLM은 때때로 부정확하거나 잘못된 답변을 생성하는 경향이 있으며, 어떤 것이 올바른 정보인지 판단하기 어려운 문제가 있습니다. 자체 수정 기술은 이러한 문제를 해결하고 모델이 스스로 오류를 감지하고 수정하도록 돕습니다.

#### 주요 기술 및 작동 원리

  * **Self-Calibration**: 이 기술은 LLM이 응답을 생성한 후 자체적으로 출력을 평가하도록 프롬프트하여, 실수를 보정하고 올바른 및 잘못된 예측의 가능성을 줄이는 데 도움을 줍니다.
  * **Self-Refine**: 인간이 초안을 작성하고 검토 및 개선하는 과정과 유사하게, LLM이 초기 출력을 생성하고 다음 단계에서 반복적으로 개선하여 정확도와 일관성을 향상시킵니다.
  * **Reversing Chain-of-Thought (RCoT)**: CoT 프롬프트의 개념을 역으로 활용하여 환각이나 잘못된 가정을 식별하고 수정하는 데 도움을 줍니다. 모델이 문제를 해결한 후, 초기 솔루션을 기반으로 새로운 문제를 생성하도록 요청하고, 원본 문제와 새로 생성된 문제를 비교하여 불일치를 감지합니다.
  * **Self-Verification**: CoT 프롬프트가 출력에 효과적이지만 오류 수정 메커니즘이 부족하다는 점을 보여줍니다. CoT를 사용하여 여러 후속 솔루션을 생성한 다음, 원본 질문의 일부를 마스킹하여 각 솔루션을 평가합니다. LLM은 질문의 나머지 부분과 생성된 솔루션을 기반으로 마스킹된 정보를 예측해야 합니다.
  * **Chain of Verification (CoVe)**: CoT와 유사하지만, 중간 단계를 생성하는 대신 모델이 초기 응답을 평가하기 위한 검증 질문을 생성하도록 합니다. 모델은 이 질문에 답변한 후 최종 출력을 따릅니다.
  * **Cumulative Reasoning (CR)**: 문제 해결을 여러 단계로 나누고, 각 단계를 LLM이 평가하고 수정하거나 검증하도록 합니다. 최종 응답에 도달할 때까지 교차 검증을 반복합니다.
  * **Chain of Self-Correction (CoSC)**: 2025년 상반기 연구에서 제시된 새로운 메커니즘으로, LLM에 자체 수정 능력을 내재화하도록 설계되었습니다. LLM이 문제를 해결하기 위한 프로그램을 생성하고, 이를 실행하여 출력을 얻은 후, 일련의 자체 수정 단계를 통해 작동합니다. 이 반복적인 과정은 LLM이 출력 단계를 검증하고 수학적 출력의 정확도를 향상시키도록 돕습니다. CoSC-Code-34B 모델은 MATH 데이터셋(가장 어려운 수학적 추론 데이터셋)에서 ChatGPT, GPT-4, 기타 LLM을 능가하는 성능을 보였습니다.

자체 수정 기술은 LLM의 '신뢰성'과 '정확성'을 근본적으로 향상시키며, 특히 '수학적 추론'과 같은 논리적 과정에서 인간의 '느린 사고(slow thinking)' 과정을 모방합니다. LLM의 오류는 종종 '빠른 사고(fast thinking)'에 유리한 즉각적인 패턴 매칭에서 발생합니다. 자체 수정 기술은 이러한 즉각적인 응답 대신, '느린 사고'처럼 단계별로 문제를 분석하고, 중간 결과를 검증하며, 필요에 따라 수정하는 과정을 모델에 주입합니다. 특히 CoSC는 모델이 '프로그램 실행'이라는 외부 도구를 활용하여 자체 출력을 검증하도록 함으로써, 단순히 텍스트 내에서만 추론하는 한계를 넘어섭니다. 이는 모델이 스스로의 '생각'을 '행동'으로 옮기고 그 결과를 '관찰'하여 '피드백'으로 삼는 고차원적인 학습 루프를 형성하는 것을 의미합니다. 이 과정을 통해 모델은 스스로의 오류를 능동적으로 찾아내고 수정함으로써, 논리적 일관성과 사실적 정확도를 획기적으로 향상시킬 수 있습니다.

자체 수정 프롬프트는 LLM의 '지능'을 단순한 언어 생성기를 넘어 '문제 해결자'이자 '자체 학습 능력이 있는 학습자'로 진화시키는 중요한 단계입니다. 특히 수학이나 코딩과 같이 명확한 정답과 논리적 검증이 가능한 분야에서 그 효과가 두드러지며, 이는 LLM이 더욱 복잡하고 비판적인 사고를 요구하는 실제 세계 문제에 적용될 수 있음을 시사합니다. 이러한 기술들은 LLM이 인간의 인지 과정을 모방하며 더욱 신뢰할 수 있는 AI 시스템으로 발전하는 데 핵심적인 역할을 합니다.

### 2.5 다중 전문가 (Multi-expert) 프롬프트

#### 개념 및 메커니즘

다중 전문가 프롬프트(Multi-expert Prompting)는 기존 ExpertPrompting을 개선한 새로운 방법론으로, LLM이 여러 전문가를 시뮬레이션하고, 이들의 응답을 통합한 후, 개별 및 통합 응답 중에서 최상의 것을 선택하여 출력을 개선하는 기술입니다. 이 과정은 단일 CoT(Chain of Thoughts) 내에서 7가지 하위 작업을 활용하여 수행됩니다. 이러한 하위 작업들은 의사 결정 프로세스의 명목 그룹 기술(Nominal Group Technique, NGT)에서 파생되었습니다.

LLM은 입력 지시에 따라 여러 전문가 정체성(expert identities)을 제로샷 프롬프트 스타일로 생성하고, 각 전문가는 독립적으로 지시에 응답합니다. 이후 모델은 이 전문가들의 응답을 통합하고 최상의 응답을 선택합니다. 메타 프롬프트(Meta Prompting)는 LLM을 '지휘자(conductor)'로 활용하여 특정 분야의 전문가인 여러 독립적인 LLM을 관리하는 방식으로 강조됩니다. Brokered Multi-Expert Reflection은 기본 LLM의 출력 결과에 대한 피드백을 제공하기 위해 반성(reflection) 워크플로우 내에서 여러 전문가 LLM을 중개하고 통합함으로써 LLM의 출력 능력을 향상시킵니다.

#### 장점 및 효과

다중 전문가 프롬프트는 기존 ExpertPrompting 대비 진실성(truthfulness), 사실성(factuality), 정보성(informativeness), 유용성(usefulness)을 크게 향상시키고, 독성(toxicity) 및 유해성(hurtfulness)을 감소시킵니다. ChatGPT를 한 번 사용 시 최상의 기준점보다 8.69% 향상된 최고 진실성을 달성했습니다. 이 방법론은 효율적이고, 설명 가능하며, 다양한 시나리오에 대한 우수한 일반화 능력을 가지며, 수동적인 프롬프트 구성이 필요 없습니다. 또한, 단일 전문가가 가질 수 없는 편향을 해결하고, 일반적인 지식에 대한 다양한 관점을 고려하는 데 유리합니다. 환각 및 불일치 문제를 효과적으로 해결하며, 특히 도메인별 작업에서 상당한 잠재력을 보여줍니다.

다중 전문가 프롬프트는 LLM의 '편향'을 줄이고 '다각적인 관점'을 통해 복잡한 문제 해결 능력을 향상시키는 '집단 지성(Collective Intelligence)' AI의 발전입니다. 단일 LLM은 학습 데이터의 편향을 반영하거나, 특정 관점에만 치우친 답변을 생성할 수 있습니다. 이는 특히 윤리적, 사회적, 또는 복잡한 다분야 문제에서 한계로 작용합니다. ExpertPrompting은 "단순한 답변을 제공하는 것은 편향될 수 있고 비합리적일 수 있다는 태도를 도입"할 수 있다는 지적이 있습니다. 이에 대한 해결책으로 Multi-expert Prompting은 "여러 전문가를 시뮬레이션하고, 그들의 응답을 통합하며, 개별 및 통합 응답 중에서 최상의 것을 선택"한다고 설명됩니다. 이 기술은 명목 그룹 기술(Nominal Group Technique)에서 파생된 7가지 하위 작업을 통해 단일 CoT 내에서 진행됩니다. Brokered Multi-Expert Reflection 또한 "여러 전문가 LLM을 통합"함으로써 환각 및 불일치 문제를 해결하고 "도메인별 작업에서 상당한 잠재력"을 보인다고 언급됩니다.

이는 인간 사회에서 여러 전문가가 모여 아이디어를 브레인스토밍하고, 토론을 통해 검증하며, 최종적으로 합의된 최적의 결론을 도출하는 과정과 유사합니다. 다중 전문가 프롬프트는 LLM에 이러한 '집단 지성'의 원리를 적용하는 것을 의미합니다. 단일 LLM이 특정 역할을 맡아 답변을 생성하는 것이 아니라, 여러 '가상 전문가'들이 각자의 관점(예: 윤리학자, 경제학자, 환경론자)에서 문제를 분석하고 답변을 내놓습니다. 이후 이 다양한 답변들을 통합하고 최적의 답변을 선택하는 과정을 통해, 모델은 특정 편향에 갇히지 않고 더 포괄적이고 심층적인 통찰력을 제공할 수 있게 됩니다. 이는 특히 윤리적, 사회적, 또는 복잡한 다분야 문제에서 LLM의 답변 품질과 신뢰성을 크게 향상시킬 수 있습니다. 이 기술은 LLM이 단순히 정보를 나열하는 것을 넘어, '다각적인 분석'과 '종합적인 판단'을 수행하도록 돕는다는 점에서 중요한 발전을 시사합니다.

다음 표에서는 설명한 주요 LLM 프롬프트 기술들을 비교하여 제시합니다.

#### 표 1: 주요 LLM 프롬프트 기술 비교

| 기술 | 정의 | 메커니즘 요약 | 장점 | 단점/한계 | 주요 활용 사례 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **제로샷 프롬프트** | 예시 없이 지시만으로 LLM이 작업을 수행하도록 요청 | 사전 학습된 지식에 전적으로 의존하여 응답 생성 | 빠른 응답, 비용 효율적, 레이블링된 데이터 불필요 | 문맥에 모호, 복잡한 작업에 부적합 | 번역, 요약, 챗봇 생성, 스팸 감지, 감성 분석 |
| **퓨샷 프롬프트** | 프롬프트 내에 2\~5개의 소수 예시를 포함하여 LLM이 패턴을 학습하도록 유도 | 예시를 통해 패턴을 인식하고 새로운 작업에 일반화 (In-context Learning) | 복잡한 작업 정확도 향상, 빠른 적응, 높은 유연성 | 큰 프롬프트, 높은 계산 비용, 컨텍스트 창 제약, 과적합 위험 | 텍스트 분류, 감성 분석, 정보 추출, 제목 발명, 챗봇 생성 |
| **Chain-of-Thought (CoT) 프롬프트** | LLM이 단계별 추론 과정을 명시적으로 기록하여 복잡한 다단계 추론 문제 해결 | "단계별로 생각하라" 지시를 통해 중간 추론 단계 생성 및 명시 | 복잡한 추론 능력 향상, 투명성 증대, 논리적 오류 감소 | 간결한 작업에는 비효율적, 큰 출력 생성 가능성 | 수학 문제, 상식 추론, 복잡한 문제 해결, 법률 분석 |
| **Retrieval-Augmented Generation (RAG) 프롬프트** | LLM이 외부 지식 기반을 참조하여 최신 정보로 답변 생성 | 사용자 쿼리 기반 외부 데이터 검색 후 LLM에 추가 맥락으로 제공 | 최신 정보 적용, 환각 감소, 신뢰성 및 투명성 향상, 비용 효율성 | 효율적인 검색 시스템 구축 난이도, 정보 품질 관리 필요 | 고객 지원 챗봇, 금융 지식 시스템, 법률 정보 검색, 연구 지원 |
| **자체 수정 (Self-Correction) 프롬프트** | LLM이 자체적으로 출력을 비판하고 개선하도록 유도 | 모델이 자체 출력을 평가하고 반복적으로 수정하여 정확도 및 신뢰성 향상 | 답변의 정확도 및 신뢰성 향상, 논리적 일관성 증대 | 복잡한 워크플로우, 추가적인 계산 필요 | 수학 문제 해결, 코드 생성 및 디버깅, 사실 확인, 논리적 분석 |
| **다중 전문가 (Multi-expert) 프롬프트** | LLM이 여러 전문가를 시뮬레이션하고 이들의 응답을 통합하여 최상의 출력 선택 | 여러 가상 전문가 LLM들이 각자의 관점에서 답변 생성 후 통합 및 최적 답변 선택 | 편향 감소, 다각적인 관점 통합, 진실성/사실성/유용성 향상 | 전문가 역할 정의의 복잡성, 통합 과정의 미묘함 | 복잡한 사회/윤리적 문제, 전략 분석, 다분야 의사 결정, 의료 진단 |

## 3\. LLM 프롬프트 최적화 및 평가 전략

LLM 프롬프트의 성능을 극대화하기 위해서는 체계적인 최적화와 정확한 평가가 필수적입니다.

### 3.1 프롬프트 최적화 기술

프롬프트 최적화는 LLM의 출력을 개선하기 위한 핵심적인 과정입니다. 과거에는 프롬프트 엔지니어링이 "임시적이고 시행착오적인 프롬프트 반복" 방식에 의존했습니다. 그러나 이제는 LLM을 활용하여 프롬프트를 개선하고 최적화하는 자동화된 방법론이 부상하고 있습니다.

\*\*자동화된 프롬프트 엔지니어링 (APE)\*\*은 LLM을 활용하여 프롬프트를 개선하고 최적화하는 메타 프롬프트(Meta Prompting) 방법론의 일종입니다. 이 방법론은 초기 입력-출력 쌍을 기반으로 여러 지시 후보를 생성하고, 이 후보들의 성능을 점수화하며, 반복적인 과정을 통해 최적의 성능을 달성하는 지시를 탐색합니다. APE는 인간이 설계한 프롬프트보다 일반적으로 우수한 성능을 보이며, 다양한 시나리오(제로샷, CoT 등)에 적용 가능하고, 작업에 구애받지 않는(task-agnostic) 특성을 가집니다.

\*\*로라 프롬프트 최적화 (LPO)\*\*는 자동화된 프롬프트 엔지니어링 방법론과 통합되어, 프롬프트 내의 특정 '최적화 토큰'에 초점을 맞춰 LLM이 해당 토큰에만 집중하도록 유도합니다. 이 기술은 수학적 추론 벤치마크(GSM8k, MultiArith)에서 뛰어난 성능 향상을 보이며, 수동 최적화 방법보다 더 효율적으로 최적 프롬프트로 수렴합니다.

프롬프트 요구 사항의 **과다 지정 문제**는 LLM 성능 저하의 주요 원인으로 지적됩니다. LLM은 너무 많은 요구 사항이 포함된 프롬프트에 어려움을 겪으며, 이는 성능 저하로 이어질 수 있습니다. 19가지 요구 사항을 한꺼번에 지정했을 때 LLM의 평균 정확도가 크게 낮아지는 현상이 관찰됩니다. 이러한 문제를 해결하기 위한 방안으로, \*\*의도적인 불완전 지정(intentional underspecification)\*\*은 모델이 기본적으로 잘 따르는 요구 사항을 명시하지 않고, 선택된 핵심 요구 사항에만 집중하도록 하는 전략이 될 수 있습니다. 이를 위해서는 요구 사항의 사전 분석, 신뢰할 수 없는 평가 기준 구축, 정량적인 평가 및 모니터링을 포함하는 포괄적인 프로세스가 필요합니다.

2025년 상반기에는 다음과 같은 최신 프롬프트 최적화 기술들이 연구되고 있습니다.

  * **Recursive Self-Improvement Prompting (RSIP) / Alignment via Refinement (AvR)**: 이 반복적인 전략은 모델이 자체 출력을 비판하고 개선하도록 돕습니다. AvR은 CoT를 통해 LLM의 재귀적 사고 능력을 향상시키고, 비판 및 검증 작업을 통해 차등 학습 기술로 최적화합니다. 소수 샷 학습 데이터(3k 샘플)로도 LLaMA-3-8B-Instruct 모델의 성능을 AlpacaEval 2.0에서 20% 이상 향상시키는 효율성을 보입니다.
  * **Multi-Objective Directional Prompting (MODP)**: LLM의 내재적 행동을 추가 목표로 고려하고, 지시 기반의 프롬프트 엔지니어링을 통해 강력하고 보정된 프롬프트를 생성하는 방법론입니다. 정확성, 독성 감소, 특정 출력 형식 준수 등 여러 목표의 균형을 이룹니다.
  * **Mixture of Formats (MOF)**: LLM이 프롬프트 형식의 비일관적인 변화에 민감한 '프롬프트 취약성(prompt brittleness)' 문제를 해결합니다. 퓨샷 예시의 스타일을 다양화하여 모델이 특정 스타일과 대상 응답을 연결하는 것을 방지하고, 일반화 성능을 향상시킵니다.

프롬프트 최적화는 '인간의 시행착오'에서 'LLM의 자동화된 탐색'으로 진화하고 있으며, 이는 LLM 응용 프로그램 개발자의 효율성을 획기적으로 높일 것으로 기대됩니다. 과거에는 수많은 프롬프트 문구를 수동적으로 작성하고 테스트하며 최적의 것을 찾아야 했습니다. 이는 시간과 비용이 많이 드는 비효율적인 과정이었습니다. 그러나 APE, LPO, RSIP/AvR와 같은 자동화된 기술들은 LLM 자체의 지능을 활용하여 프롬프트 개선, 평가, 탐색 과정을 자동화합니다. 이는 LLM이 단순히 최종 결과를 생성하는 도구를 넘어, '자체적으로 최적화하는 도구'로 진화하고 있음을 의미합니다. 이러한 효율적인 최적화는 인간의 개입을 최소화하면서도 프롬프트의 성능과 효율성을 크게 증대시킬 수 있습니다. 프롬프트 최적화의 자동화는 LLM 기반 애플리케이션 개발의 진입 장벽을 낮추고, 더 나은 성능을 더 효율적으로 달성할 수 있게 합니다. 이는 프롬프트 엔지니어링의 '장인 정신'을 '과학적인 프로세스'로 전환하는 중요한 발전입니다. 개발자들은 이제 프롬프트의 세부 문구에 대한 고민보다는, 최적화 알고리즘 설계와 평가 기준 설정에 더 집중할 수 있게 됩니다. 궁극적으로 이는 LLM 기능의 대중화와 산업적 응용을 가속화하는 핵심 동향이 될 것입니다.

### 3.2 LLM 프롬프트 평가 방법론 및 기준

LLM 프롬프트의 효과를 객관적으로 측정하고 개선하기 위해서는 정교한 평가 방법론과 기준이 필수적입니다. LLM 벤치마크는 특정 LLM 모델의 언어 능력, 대화 관련성, 출력 문제 해결 능력 등 전반적인 역량을 평가하는 데 도움을 줍니다. LLM 평가 기준은 정확성, 관련성, 환각 등 사용자가 중요하게 생각하는 기준에 따라 LLM 시스템의 출력을 평가합니다.

#### 기존 기준의 한계 및 LLM-as-a-judge

BLEU/ROUGE와 같은 전통적인 평가는 LLM 출력의 '의미론적 뉘앙스'를 포착하는 데 한계가 있습니다. 대신,

**LLM-as-a-judge**는 LLM을 평가자로 사용하여 언어 루브릭(rubrics)으로 출력을 평가하는 가장 신뢰할 수 있는 방법론으로 강조됩니다. 이 방법론은 G-Eval과 같은 다양한 기술을 필요로 하며, 시스템(RAG, 에이전트, 챗봇) 및 사용 사례(Text-SQL, 챗봇 도우미)에 따라 평가 선택이 달라집니다. 좋은 평가 기준은 정량적(점수 산출), 신뢰성(일관성), 정확성(인간의 기대와 일치)을 충족해야 합니다.

#### RAG 특정 평가

  * **응답 관련성 (Answer Relevancy)**: LLM 출력이 주어진 입력에 대해 유용하고 간결하며 관련성 있는지 평가합니다. 검색된 맥락을 고려하여 관련 문장의 비율을 계산합니다.
  * **맥락적 정확도 (Contextual Precision)**: RAG 파이프라인의 검색기(retriever) 성능을 평가합니다. 검색된 맥락에서 관련 없는 토큰이 관련 있는 토큰보다 더 많이 마스킹되었는지 확인합니다. LLM이 검색된 맥락의 핵심에 나타나는 정보에 더 많은 가중치를 부여하는 것이 중요합니다.

#### 기타 평가 기준

  * **Perplexity**: 모델이 텍스트 샘플을 얼마나 잘 예측하는지 측정하며, 점수가 낮을수록 성능이 좋습니다.
  * **BLEU Score**: 주로 기계 번역에 사용되며, n-그램 일치를 통해 모델 출력과 참조 텍스트를 비교합니다.
  * **ROUGE**: 요약 평가에 유용하며, 모델이 생성한 텍스트가 참조 요약과 얼마나 일치하는지 측정합니다 (n-그램, 시퀀스, 단어 쌍).
  * **F1 Score**: 분류 및 명명된 엔티티 인식 작업에 사용되며, 정밀도(precision)와 재현율(recall)의 균형을 이룹니다.
  * **METEOR**: 정확한 일치뿐만 아니라 동의어 및 어형 변화를 고려하여 인간의 판단과 더 잘 일치하도록 합니다.
  * **BERTScore**: BERT와 같은 모델의 텍스트 임베딩 유사성을 비교하여 의미에 더 중점을 둡니다.
  * **Levenshtein distance**: 두 문자열을 변환하는 데 필요한 최소 단일 문자 편집(삽입, 삭제, 대체) 수를 측정합니다.
  * **작업별 평가**: 대화 시스템의 목표 달성, 작업 완료율, 챗봇 성능 등 특정 작업에 특화된 평가 또한 사용됩니다.
  * **효율성 평가**: 모델이 쿼리에 대한 응답 속도, 메모리 사용량, 에너지 소비량 측정이 중요합니다.

#### 평가 프로세스 및 도구

SuperAnnotate, Amazon Bedrock, Nvidia Nemo, Azure AI Studio, Prompt Flow 등 다양한 도구들이 LLM 평가를 위한 내장 평가 및 사용자 정의 평가 워크플로우를 제공합니다.

LLM 평가 패러다임은 '형식적 정확성'에서 '의미론적 정확성 및 인간적 판단 일치'로 진화하고 있으며, 이는 LLM의 실용적 가치 측정에 필수적입니다. 전통적인 NLP 모델 평가에서는 BLEU, ROUGE와 같은 n-그램 기반의 지표가 널리 사용되었지만, LLM 출력의 '의미론적 뉘앙스'를 포착하는 데 한계가 있습니다. 예를 들어, 동일한 의미를 가지지만 표현 방식이 다른 두 문장은 BLEU 점수가 낮을 수 있지만, 실제로는 둘 다 올바른 답변일 수 있습니다. 'LLM-as-a-judge' 방법론이 "언어 루브릭을 사용하여 LLM을 평가자로 사용하는 가장 신뢰할 수 있는 방법"으로 제시됩니다. 좋은 LLM 평가 기준은 인간의 기대와 최대한 일치하도록 만들어야 합니다. 또한, '배치 프롬프트(Batched Prompting)'와 '프롬프트 압축(Prompt Compression)'이 효율성을 높이면서도 컨텍스트 제약을 완화하는 연구 동향을 보여주며, 'PrExMe'와 'PromptOptMe'와 같은 연구는 다양한 프롬프트 최적화 기법이 LLM 기반 평가 기준의 성능에 미치는 영향을 탐구하고 있습니다.

LLM은 단순히 단어 시퀀스를 생성하는 것을 넘어, 복잡한 의미를 이해하고 추론하며, 창의적인 텍스트를 생성할 수 있습니다. 이러한 능력은 전통적인 n-그램 기반 평가로는 제대로 평가하기 어렵습니다. 'LLM-as-a-judge'는 이러한 의미론적 이해의 간극을 메우기 위해, 또 다른 LLM이 인간처럼 텍스트의 의미, 논리, 맥락적 적합성을 평가하도록 돕습니다. 이는 평가 과정이 '지능적인 판단'을 요구하는 작업임을 의미합니다. 또한, RAG 시스템의 경우, 답변의 정확성뿐만 아니라 검색된 맥락의 관련성(Contextual Precision)까지 평가하는 등 시스템의 특정 아키텍처에 맞춤형 평가가 필요해집니다. LLM 평가의 진화는 LLM이 단순한 계산 기반 시스템이 아니라, 복잡한 인지 능력을 가진 '준-지능' 시스템으로 인식되고 있음을 방증합니다. 이제 평가는 '정답과의 일치'를 넘어 '의미론적 타당성', '인간적 만족도', '시스템의 신뢰성' 등 다차원적인 관점에서 이루어져야 합니다. 이는 LLM 개발 및 응용을 위한 효율적인 관리와 자동화를 위해 필수적이며, LLM이 실제 비즈니스 및 사회 문제 해결에 더 큰 기여를 할 수 있도록 하는 중요한 기반을 제공합니다.

## 4\. 2025년 상반기 LLM 프롬프트 엔지니어링의 최신 동향 및 미래 전망

2025년 상반기는 LLM 프롬프트 엔지니어링 분야에서 핵심적인 발전이 이루어지고 있으며, 이는 LLM의 기능과 응용 분야를 더욱 확장하고 있습니다.

#### 새로운 모델 및 기능의 발전

OpenAI의 "o" 시리즈(o1, o3, o4-mini), Google의 Gemini 2.0/2.5, Anthropic의 Claude 3.7와 같은 모델들은 추론, 코딩, 수학 및 복잡한 문제 해결 능력의 한계를 확장하고 있습니다. 일부 모델은 "사고 과정"을 보여주려고 시도하기도 합니다. 또한, Microsoft의 Phi-3 시리즈와 같이 작지만 효율적인 모델들이 등장하면서, 더 작은 모델과 더 우수한 성능을 제공하면서도 비용 효율성을 높이고 있습니다.

#### 주요 신규 프롬프트 패러다임

  * **Mixture of Formats (MOF)**: LLM이 프롬프트 형식의 비일관적인 변화에 민감한 '프롬프트 취약성(prompt brittleness)' 문제를 해결하기 위해, 퓨샷 예시 내에서 다양한 스타일을 활용하는 기술입니다. 이는 모델이 특정 스타일과 대상 응답을 연결하는 것을 방지하고, 일반화 성능을 향상시킵니다.
  * **Multi-Objective Directional Prompting (MODP)**: LLM의 내재적 행동을 추가 목표로 고려하고, 지시 기반의 프롬프트 엔지니어링을 통해 강력하고 보정된 프롬프트를 생성하는 방법론입니다. 정확성, 독성 감소, 특정 출력 형식 준수 등 여러 목표의 균형을 이룹니다.
  * **Recursive Self-Improvement Prompting (RSIP) / Alignment via Refinement (AvR)**: 모델이 자체 출력을 비판하고 개선하도록 돕는 반복적인 전략입니다. AvR은 CoT를 통해 LLM의 재귀적 사고 능력을 향상시키고, 소수 샷 학습 데이터로도 LLaMA-3-8B-Instruct 모델의 성능을 크게 향상시킵니다.
  * **Context-Aware Decomposition**: 테이블 질의응답(TableQA)과 같은 도메인별 AI 애플리케이션을 위한 동적 컨텍스트 인식 프롬프트 추천 시스템입니다. SQL 기반 테이블 분석 모델(TABSD)은 LLM이 대규모 언어 형식 테이블을 처리하는 능력을 향상시키며, 토큰별 분해 프롬프트(Decomposed Prompting) 또한 연구되고 있습니다.
  * **Calibrated Confidence Prompting**: LLM이 자체 예측에 대해 과도하게 확신하는 경향을 해결하기 위해, 프롬프트를 통해 LLM의 확신 점수를 조정하는 기술입니다. SteeringConf 프레임워크는 확신 조정, 검증, 선택의 세 가지 구성 요소를 포함합니다. 그러나 LLM이 동적인 다중 작업에서 자체 확신을 정량적으로 조정하는 능력은 여전히 부족하다는 연구 결과도 있습니다.

#### 에이전트 AI 및 다중 모델 프롬프트와의 연결

LLM 기반 에이전트 AI(Agentic AI)는 LLM을 다단계 워크플로우에 통합하여 상태를 유지하고 맥락과 일관성을 적용함으로써 LLM의 능력을 한 단계 더 발전시킵니다. Google의 Project Astra나 OpenAI의 Operator와 같은 에이전트 AI는 스마트한 모델과 스마트한 프롬프트가 모두 필요합니다. 통합형 다중 모델(Multimodal) 프롬프트는 텍스트뿐만 아니라 이미지, 오디오, 비디오와 같은 다양한 형태의 데이터를 처리하고 생성하는 프롬프트를 의미합니다. RAG의 미래 발전 방향에도 멀티모달 통합이 포함됩니다.

#### 윤리적 프롬프트 및 안전 문제

편향을 줄이고 AI 출력의 공정성을 높이기 위한 '윤리적 프롬프트'에 대한 더 큰 추진력이 있습니다. LLM의 안전 취약성, 특히 유해한 텍스트와 의미론적으로 관련된 우발적으로 생성된 프롬프트가 안전 메커니즘을 우회할 수 있다는 연구가 ACL 2025에서 발표될 예정입니다. ActorBreaker와 같은 새로운 공격 방법론이 Harmbench에서 최고 공격 성공률을 달성하며, 안전 학습 데이터의 확장의 중요성을 강조합니다.

#### 효율성 및 최적화 강조

수동적인 프롬프트 구성보다는 AI 기반의 프롬프트 설계 자동화가 증가할 것으로 예상됩니다. 강력하면서도 실행 비용이 저렴한 모델의 중요성이 커지고 있습니다.

2025년 상반기 LLM 프롬프트 엔지니어링 연구는 '단일 프롬프트 최적화'를 넘어 '시스템적 지능 강화'와 '안전성 확보'라는 복합적인 목표로 확장되고 있습니다. 2024년에서 2025년으로 넘어가면서 LLM의 "추론, 코딩, 수학, 복잡한 문제 해결" 능력이 한계점을 넘어 확장되고 있습니다. 특히, "Multi-Objective Directional Prompting (MODP)"은 정확성뿐만 아니라 "안전성(safety)"과 같은 여러 목표를 동시에 최적화하며 프롬프트를 설계하는 방법론을 제시합니다. ACL 2025에서 발표될 연구는 LLM의 "안전 취약성"과 "유해한 텍스트로 LLM을 유도하는 다중 샷 프롬프트"에 대한 새로운 공격 방법론인 "ActorBreaker"를 소개하며, "안전 학습 데이터의 확장의 중요성"을 강조합니다. 또한, "Agentic AI"의 등장은 LLM이 단순히 텍스트를 생성하는 것을 넘어 "계획 실행이나 이메일 관리"와 같은 실제 행동을 수행할 수 있게 됨에 따라, 모델과 프롬프트의 제어 지능이 중요해지고 있음을 보여줍니다.

LLM의 역량이 고도화됨에 따라, 단순히 '잘 작동하는' 프롬프트를 만드는 것을 넘어, '안전하게', '다목적적으로', '효율적으로' 작동하는 시스템을 구축하는 것이 중요해지고 있습니다. MODP와 같은 기술들은 단일 성능 지표를 넘어, 윤리적 고려 사항(예: 독성 감소)을 포함한 다중 목표를 최적화함으로써 LLM의 '균형 잡힌 성능'을 가능하게 합니다. ActorBreaker와 같은 공격 연구는 LLM의 안전 메커니즘이 우회될 수 있음을 보여주며, 이는 프롬프트 설계가 단순히 성능 최적화를 넘어 '보안'과 '악용 방지' 측면까지 고려해야 함을 의미합니다. 또한, 에이전트 AI의 발전은 프롬프트 엔지니어링이 이제 단일 쿼리-응답 상호작용을 넘어, 복잡한 다단계 작업 워크플로우와 외부 도구 사용을 제어하는 '지능형 제어 메커니즘'으로 진화하고 있음을 시사합니다. 2025년 상반기 LLM 프롬프트 엔지니어링 연구는 LLM이 단순한 언어 모델이 아니라, 실제 세계에 영향을 미치는 '실용 시스템'으로 발전하고 있음을 명확히 보여줍니다. 이에 따라 프롬프트 엔지니어링은 '개별 프롬프트 작성 기술'에서 'LLM 기반 시스템의 설계 및 운영 전략'으로 그 범위가 확장되고 있습니다. 이는 LLM의 잠재력을 최대한 활용하면서도, 사회적 책임과 안전성을 동시에 확보해야 하는 중요한 과제를 안고 있으며, 향후 LLM 연구 및 개발의 주요 방향성을 제시합니다.

다음 표는 2025년 상반기에 부상하는 주요 LLM 프롬프트 패러다임을 요약합니다.

#### 표 2: 2025년 상반기 최신 프롬프트 패러다임

| 패러다임 | 핵심 개념 | 주요 특징 | 잠재적 영향/기여 |
| :--- | :--- | :--- | :--- |
| **Mixture of Formats (MOF)** | 프롬프트 형식의 비일관적 변화에 대한 LLM의 민감성('프롬프트 취약성') 해결 | 퓨샷 예시 내에서 다양한 스타일을 활용하여 모델이 내용에 집중하도록 유도 | LLM의 '강건성' 향상, 다양한 입력 형식에 대한 일관된 성능 유지 |
| **Multi-Objective Directional Prompting (MODP)** | LLM의 내재적 행동을 다중 목표로 고려한 프롬프트 최적화 | 정확성, 안전성, 출력 형식 준수 등 여러 목표의 균형을 지시 기반으로 최적화 | LLM의 '균형 잡힌 성능' 지원, 실제 애플리케이션의 신뢰성 및 유용성 증대 |
| **Recursive Self-Improvement Prompting (RSIP) / Alignment via Refinement (AvR)** | LLM이 자체 출력을 반복적으로 비판하고 개선하도록 하는 자체 학습 메커니즘 | CoT를 통한 재귀적 사고 능력 향상, 비판/검증 작업 통한 최적화 | LLM의 '자체 개선' 능력 강화, 복잡한 추론 및 문제 해결 능력 향상 |
| **Context-Aware Decomposition** | 복잡한 작업을 컨텍스트에 따라 여러 하위 작업으로 분해하여 처리 | SQL 기반 테이블 분석, 토큰별 분해 프롬프트 등을 통해 특정 도메인에 최적화 | 도메인별 AI 애플리케이션의 정확성 및 효율성 증대, 복잡한 데이터 처리 능력 강화 |
| **Calibrated Confidence Prompting** | LLM이 자체 예측에 대해 과도하게 확신하는 경향을 해결하기 위한 신뢰도 조정 | 프롬프트를 통해 LLM의 확신 점수를 조정하여 과도한 확신 문제 해결 | LLM 답변의 '신뢰성' 향상, 잘못된 정보 전달 위험 감소 |

## 결론 및 제언

2025년 상반기 LLM 프롬프트 엔지니어링 분야는 기본적인 명확성, 간결성, 맥락 제공 원칙을 기반으로, 복잡한 추론(CoT), 외부 지식 활용(RAG), 자체 문제 해결(Self-Correction), 다각적인 관점 통합(Multi-expert) 등 고도화된 기술들로 빠르게 발전하고 있습니다. 특히, 프롬프트 최적화는 인간의 수동 작업에서 LLM의 자동화된 탐색으로 진화하고 있으며, 평가 방법론 또한 의미론적 정확성 및 인간적 판단 일치에 중점을 두는 방향으로 나아가고 있습니다. 프롬프트의 과다 지정 및 취약성 문제에 대한 해결책 또한 활발히 연구되고 있습니다.

이러한 발전은 LLM의 기능을 극대화하고 실제 세계 문제에 효과적으로 적용하기 위한 중요한 기반을 마련하고 있습니다. LLM이 단순히 언어 생성기를 넘어, 신뢰할 수 있는 지식 에이전트, 문제 해결자, 그리고 자체적으로 개선하는 시스템으로 진화하고 있음을 명확히 보여줍니다.

#### 실용적 제언

  * **기본 원칙 숙지**: 아무리 최신 기술이라도 명확하고 간결하며 맥락을 포함하는 프롬프트 작성의 기본 원칙을 향상 숙지해야 합니다.
  * **복잡성에 따른 기술 선택**: 단순 작업에는 제로샷을, 특정 패턴 학습이 필요한 경우 퓨샷을, 다단계 추론에는 CoT를, 최신 정보나 외부 지식이 필요한 경우 RAG를 활용하는 등 작업의 복잡성과 요구 사항에 따라 적절한 프롬프트 기술을 선택해야 합니다.
  * **신뢰성 확보를 위한 노력**: LLM의 환각 및 편향 문제를 해결하기 위해 자체 수정 및 다중 전문가 프롬프트와 같은 신뢰성 향상 기술을 적극적으로 도입하고, 이를 위한 평가 기준 및 프로세스를 구축해야 합니다.
  * **자동화된 최적화 도구 활용**: 프롬프트 엔지니어링의 효율성을 높이기 위해 APE, LPO, RSIP/AvR와 같은 자동화된 프롬프트 최적화 도구의 도입을 고려해야 합니다.
  * **정량적인 평가 및 모니터링**: LLM 애플리케이션의 성능을 정량적으로 모니터링하고, LLM-as-a-judge와 같은 정교한 평가 방법론을 사용하여 인간의 기대에 부합하는지 확인하며, 반복적으로 개선해야 합니다.
  * **안전성 및 윤리적 고려**: LLM의 안전 취약성에 대한 인식을 높이고, 윤리적 프롬프트 원칙을 준수하며 유해한 텍스트 생성을 방지해야 합니다.

#### 향후 연구 및 발전 방향

  * LLM의 '재귀적 사고' 및 '메타 인지' 능력 강화 연구가 지속될 것입니다. 이는 LLM이 더욱 복잡한 문제를 효율적으로 해결하고 스스로 학습하는 데 필수적입니다.
  * 멀티모달 RAG 및 에이전트 AI와의 통합을 통해 LLM의 실제 세계 상호작용 능력이 더욱 확장될 것입니다. 이는 LLM이 텍스트를 넘어 다양한 형태의 데이터를 이해하고 처리하며, 실제 환경에서 복잡한 작업을 수행하는 데 기여할 것입니다.
  * 프롬프트 취약성 문제에 대한 근본적인 해결과 LLM의 '강건성'을 높이는 연구가 중요해질 것입니다. 이는 LLM 기반 시스템의 안전성과 신뢰성을 확보하는 데 필수적인 요소입니다.
  * LLM의 '설명 가능성'과 '투명성'을 높이는 연구는 신뢰성 높은 AI 시스템 구축에 필수적입니다. CoT와 같은 기술을 더욱 발전시켜 LLM의 의사 결정 과정을 명확히 밝히는 연구가 계속될 것입니다.
  * AI 시스템의 '자율 학습 및 개선' 능력을 더욱 고도화하는 방향으로 프롬프트 엔지니어링이 발전할 것입니다. 이는 LLM 개발 및 운영 비용의 효율성을 극대화하고, 인간의 개입 없이도 모델이 지속적으로 성능을 향상시키도록 할 것입니다.

궁극적으로 이는 LLM 기반 시스템의 상용화와 신뢰성 확보에 기여할 것입니다.

-----

### 참고 자료

1.  Prompt Engineering for Large Language Models – Business ..., 7월 3, 2025에 접속함, [https://open.ocolearnok.org/aibusinessapplications/chapter/prompt-engineering-for-large-language-models/](https://open.ocolearnok.org/aibusinessapplications/chapter/prompt-engineering-for-large-language-models/)
2.  26 Prompting Principles for Optimal LLM Output - Pareto.AI, 7월 3, 2025에 접속함, [https://pareto.ai/blog/26-prompting-principles-for-llms](https://pareto.ai/blog/26-prompting-principles-for-llms)
3.  What Prompts Don't Say: Understanding and Managing Underspecification in LLM Prompts, 7월 3, 2025에 접속함, [https://arxiv.org/html/2505.13360v1](https://arxiv.org/html/2505.13360v1)
4.  [2505.13360] What Prompts Don't Say: Understanding and Managing Underspecification in LLM Prompts - arXiv, 7월 3, 2025에 접속함, [https://arxiv.org/abs/2505.13360](https://arxiv.org/abs/2505.13360)
5.  Zero Shot Prompting vs. Few-Shot Prompting: Techniques and Real-World Applications, 7월 3, 2025에 접속함, [https://www.beam.cloud/blog/prompting-techniques](https://www.beam.cloud/blog/prompting-techniques)
6.  Prompt engineering techniques: Top 5 for 2025 - K2view, 7월 3, 2025에 접속함, [https://www.k2view.com/blog/prompt-engineering-techniques/](https://www.k2view.com/blog/prompt-engineering-techniques/)
7.  Shot-Based Prompting: Zero-Shot, One-Shot, and Few-Shot Prompting - Learn Prompting, 7월 3, 2025에 접속함, [https://learnprompting.org/docs/basics/few\_shot](https://learnprompting.org/docs/basics/few_shot)
8.  arXiv:2402.07927v2 [cs.AI] 16 Mar 2025, 7월 3, 2025에 접속함, [https://arxiv.org/pdf/2402.07927](https://arxiv.org/pdf/2402.07927)
9.  Master Few-Shot Prompting to Improve AI Performance - Relevance AI, 7월 3, 2025에 접속함, [https://relevanceai.com/prompt-engineering/master-few-shot-prompting-to-improve-ai-performance](https://relevanceai.com/prompt-engineering/master-few-shot-prompting-to-improve-ai-performance)
10. Few Shot Prompting : Definition, Usage and Example - Kata.ai's Blog\!, 7월 3, 2025에 접속함, [https://kata.ai/blog/few-shot-prompting-definition-usage-and-example/](https://kata.ai/blog/few-shot-prompting-definition-usage-and-example/)
11. What is chain of thought (CoT) prompting? | IBM, 7월 3, 2025에 접속함, [https://www.ibm.com/think/topics/chain-of-thoughts](https://www.ibm.com/think/topics/chain-of-thoughts)
12. Chain-of-thought prompting 101 - K2view, 7월 3, 2025에 접속함, [https://www.k2view.com/blog/chain-of-thought-prompting/](https://www.k2view.com/blog/chain-of-thought-prompting/)
13. What is RAG? - Retrieval-Augmented Generation AI Explained - AWS, 7월 3, 2025에 접속함, [https://aws.amazon.com/what-is/retrieval-augmented-generation/](https://aws.amazon.com/what-is/retrieval-augmented-generation/)
14. What is RAG (Retrieval Augmented Generation)? - Trantor, 7월 3, 2025에 접속함, [https://www.trantorinc.com/blog/what-is-rag-retrieval-augmented-generation](https://www.trantorinc.com/blog/what-is-rag-retrieval-augmented-generation)
15. Introduction to Self-Criticism Prompting Techniques for LLMs, 7월 3, 2025에 접속함, [https://learnprompting.org/docs/advanced/self\_criticism/introduction](https://learnprompting.org/docs/advanced/self_criticism/introduction)
16. Embedding Self-Correction as an Inherent Ability in Large Language Models for Enhanced Mathematical Reasoning - arXiv, 7월 3, 2025에 접속함, [https://arxiv.org/html/2410.10735v2](https://arxiv.org/html/2410.10735v2)
17. Embedding Self-Correction as an Inherent Ability in Large Language Models for Enhanced Mathematical Reasoning - ResearchGate, 7월 3, 2025에 접속함, [https://www.researchgate.net/publication/384929606\_Embedding\_Self-Correction\_as\_an\_Inherent\_Ability\_in\_Large\_Language\_Models\_for\_Enhanced\_Mathematical\_Reasoning](https://www.researchgate.net/publication/384929606_Embedding_Self-Correction_as_an_Inherent_Ability_in_Large_Language_Models_for_Enhanced_Mathematical_Reasoning)
18. Embedding Self-Correction as an Inherent Ability in Large Language Models for Enhanced Mathematical Reasoning | OpenReview, 7월 3, 2025에 접속함, [https://openreview.net/forum?id=8Dj6OEMj6W](https://openreview.net/forum?id=8Dj6OEMj6W)
19. Multi-expert Prompting Improves Reliability, Safety and Usefulness ..., 7월 3, 2025에 접속함, [https://aclanthology.org/2024.emnlp-main.1135/](https://aclanthology.org/2024.emnlp-main.1135/)
20. Multi-expert Prompting Improves Reliability, Safety and Usefulness of Large Language Models - ACL Anthology, 7월 3, 2025에 접속함, [https://aclanthology.org/2024.emnlp-main.1135.pdf](https://aclanthology.org/2024.emnlp-main.1135.pdf)
21. Multi-expert Prompting Improves Reliability, Safety and Usefulness of Large Language Models | OpenReview, 7월 3, 2025에 접속함, [https://openreview.net/forum?id=XRcVKe9SwMw](https://openreview.net/forum?id=XRcVKe9SwMw)
22. A Complete Guide to Meta Prompting - PromptHub, 7월 3, 2025에 접속함, [https://www.prompthub.us/blog/a-complete-guide-to-meta-prompting](https://www.prompthub.us/blog/a-complete-guide-to-meta-prompting)
23. Enhancing LLM Reasoning Capabilities Through Brokered Multi-Expert Reflection, 7월 3, 2025에 접속함, [https://www.researchgate.net/publication/390862251\_Enhancing\_LLM\_Reasoning\_Capabilities\_Through\_Brokered\_Multi-Expert\_Reflection](https://www.researchgate.net/publication/390862251_Enhancing_LLM_Reasoning_Capabilities_Through_Brokered_Multi-Expert_Reflection)
24. arXiv:2504.20355v1 [cs.CL] 29 Apr 2025, 7월 3, 2025에 접속함, [https://arxiv.org/pdf/2504.20355](https://arxiv.org/pdf/2504.20355)
25. Advanced Prompt Engineering Techniques for 2025: Beyond Basic Instructions - Reddit, 7월 3, 2025에 접속함, [https://www.reddit.com/r/PromptEngineering/comments/1k7jrt7/advanced\_prompt\_engineering\_techniques\_for\_2025/](https://www.reddit.com/r/PromptEngineering/comments/1k7jrt7/advanced_prompt_engineering_techniques_for_2025/)
26. Advances in LLM Prompting and Model Capabilities: A 2024-2025 Review : r/ClaudeAI, 7월 3, 2025에 접속함, [https://www.reddit.com/r/ClaudeAI/comments/1kijb7i/advances\_in\_llm\_prompting\_and\_model\_capabilities/](https://www.google.com/search?q=https://www.reddit.com/r/ClaudeAI/comments/1kijb7i/advances_in_llm_prompting-and-model-capabilities/)
27. Unlocking Recursive Thinking of LLMs: Alignment via ... - arXiv, 7월 3, 2025에 접속함, [https://arxiv.org/pdf/2506.06009](https://arxiv.org/pdf/2506.06009)
28. MODP: Multi Objective Directional Prompting - arXiv, 7월 3, 2025에 접속함, [https://arxiv.org/html/2504.18722v1](https://arxiv.org/html/2504.18722v1)
29. (PDF) MODP: Multi Objective Directional Prompting - ResearchGate, 7월 3, 2025에 접속함, [https://www.researchgate.net/publication/391247557\_MODP\_Multi\_Objective\_Directional\_Prompting](https://www.researchgate.net/publication/391247557_MODP_Multi_Objective_Directional_Prompting)
30. arXiv:2504.06969v1 [cs.CL] 9 Apr 2025, 7월 3, 2025에 접속함, [https://arxiv.org/pdf/2504.06969](https://arxiv.org/pdf/2504.06969)
31. 20 LLM evaluation benchmarks and how they work - Evidently AI, 7월 3, 2025에 접속함, [https://www.evidentlyai.com/llm-guide/llm-benchmarks](https://www.evidentlyai.com/llm-guide/llm-benchmarks)
32. LLM Evaluation Metrics: The Ultimate LLM Evaluation Guide - Confident AI, 7월 3, 2025에 접속함, [https://www.confident-ai.com/blog/llm-evaluation-metrics-everything-you-need-for-llm-evaluation](https://www.confident-ai.com/blog/llm-evaluation-metrics-everything-you-need-for-llm-evaluation)
33. LLM Evaluation: Frameworks, Metrics, and Best Practices | SuperAnnotate, 7월 3, 2025에 접속함, [https://www.superannotate.com/blog/llm-evaluation-guide](https://www.superannotate.com/blog/llm-evaluation-guide)
34. arXiv:2503.02756v1 [cs.CL] 4 Mar 2025, 7월 3, 2025에 접속함, [https://arxiv.org/pdf/2503.02756](https://arxiv.org/pdf/2503.02756)
35. [2506.20815] Dynamic Context-Aware Prompt Recommendation for Domain-Specific AI Applications - arXiv, 7월 3, 2025에 접속함, [https://arxiv.org/abs/2506.20815](https://arxiv.org/abs/2506.20815)
36. arXiv:2502.13422v1 [cs.CL] 19 Feb 2025, 7월 3, 2025에 접속함, [https://arxiv.org/pdf/2502.13422](https://arxiv.org/pdf/2502.13422)
37. Decomposed Prompting: Unveiling Multilingual Linguistic Structure Knowledge in English-Centric Large Language Models - arXiv, 7월 3, 2025에 접속함, [https://arxiv.org/html/2402.18397v1](https://arxiv.org/html/2402.18397v1)
38. Calibrating LLM Confidence with Semantic Steering: A Multi-Prompt Aggregation Framework - arXiv, 7월 3, 2025에 접속함, [https://arxiv.org/html/2503.02863v1](https://arxiv.org/html/2503.02863v1)
39. Two LLMs Debate, Both Are Certain They've Won - arXiv, 7월 3, 2025에 접속함, [http://arxiv.org/pdf/2505.19184](http://arxiv.org/pdf/2505.19184)
40. arXiv:2503.16416v1 [cs.AI] 20 Mar 2025, 7월 3, 2025에 접속함, [https://arxiv.org/pdf/2503.16416](https://arxiv.org/pdf/2503.16416)
41. ACL 2025 Main Conference LLMs know their vulnerabilities: Uncover Safety Gaps through Natural Distribution Shifts \\faWarningWARNING: This paper contains model outputs that may be considered offensive. - arXiv, 7월 3, 2025에 접속함, [https://arxiv.org/html/2410.10700v2](https://arxiv.org/html/2410.10700v2)