# Random Network Analysis

## **⋆ . 🎁˚🎄 ✦Members.. 🧸⊹ ･✧**
> 이해정(Haejeong, Lee) <pouwuoq0815@pukyong.ac.kr>
> 
> 김시현(Sihyeon, Kim) <https://github.com/adsfk/Random_Network>
> 
> 장해린(Haerin, Jang) <https://github.com/remote0612/random_network_maker>

---
## 1. Random Network Models
> ### What is it for?
> 원본 네트워크의 특정한 특성들을 유지한 채 [무작위 네트워크를 생성](#221-create-random-graph-)하여 원본 네트워크의 고유한 특성을 비교 분석할 수 있다.
>
> 일반적으로 무작위성의 평균적 특성을 보기 위해 여러 개의 무작위 그래프(앙상블 그래프)를 생성한 후 평균값을 이용해 분석한다.

> ### 1.1. Erdős–Rényi (ER) model
> $p$ 의 확률로 노드 간 엣지를 연결하여 그래프를 생성하는 모델
> 
> 패키지 내에서 default 값은 원본 네트워크의 엣지 밀도를 사용함.
> 
> $p = \frac{\<k\>}{(N-1)}$

> ### 1.2. Configuration model
> 각 노드의 차수(이웃수)를 고정하고 엣지를 무작위 연결하여 그래프를 생성하는 모델

> ### 1.3. Chung-Lu model
> 노드 $i$ 와 노드 $j$ 사이의 엣지를 각 노드의 차수에 따른 확률 $p_{ij}$로 연결하여 그래프를 생성하는 모델
> 
> $p_{ij} = \frac{k_ik_j}{\sum_i{k_i}}$

> ### 1.4. Barabási-Albert (BA) model
> 소수의 초기 노드로 구성된 네트워크에서 시작해, $m$ 개의 미연결 링크를 가진 새로운 노드를 하나씩 추가하며 존재하던 노드와 차수에 따른 확률 $p$ 로 링크를 연결하여 그래프를 생성하는 모델
>
> $p = \frac{k_i}{\sum_j{k_j}}$

---
## 2. Package
```bash
Random-Network-Analysis
├── polbooks
│   ├── polbooks.gml
│   └── polbooks.txt
├── random_graph_pkg
│   ├── __init__.py
│   ├── __pycache__
│   └── random_graph_analysis.py
├── Analysis.ipynb
└── README.md
```
> ### 2.1. How to Use?
> >       git clone https://github.com/idohae/Random-Network-Analysis.git
> >
> > 위 명령어를 명령창에 입력하여 무작위 네트워크 분석 패키지를 원하는 환경에 다운 받는다.
>
> > #### 1) 예시 데이터 분석 파일 실행
> > `Analysis.ipynb` 파일을 실행한다.
>
> > #### 2) 패키지 이용하여 원하는 데이터 분석
> > `random_graph_pkg` 디렉토리를 분석할 데이터 및 분석 코드와 같은 디렉토리 내에 위치시킨다.
> > ```python
> > from random_graph_pkg.random_graph_analysis import *
> > ```
> > 분석할 소스 코드에 위와 같이 패키지를 import 한 후 [패키지 함수들을 사용](#22-analysis-)한다.

> ### 2.2. Analysis [▲](#21-how-to-use)
> `random_graph_pkg`를 이용해 할 수 있는 분석은 다음과 같다.
>
> > #### 2.2.1. Create Random Graph [▲](#what-is-it-for)
> >
> > 원하는 모델의 그래프 생성 함수를 호출하면 무작위 그래프를 반환한다.
> > ```python
> > random_graph_analysis = RandomGraphAnalysis(original_graph)
> > 
> > # G(n,p)의 ER model을 이용한 그래프 생성
> > random_graph_analysis.create_ERnp_graph()
> > 
> > # Configuration model을 이용한 그래프 생성
> > random_graph_analysis.create_config_graph()
> >
> > # Chung-Lu model을 이용한 그래프 생성
> > random_graph_analysis.create_chunglu_graph()
> >
> > # BA model을 이용한 그래프 생성
> > random_graph_analysis.create_BA_graph()
> > ```
> 
> > #### 2.2.2. 무작위 그래프 앙상블 생성
> >
> > 앙상블 그래프 생성 함수에 사용할 무작위 모델 이름과 앙상블 개수를 매개변수로 넘겨준다. 앙상블 그래프 리스트를 반환한다.
> > ```python
> > # ER model 앙상블 그래프 생성
> > random_graph_analysis.create_random_graph_ensemble(random_graph="ER", num_simulations=100)
> > 
> > # Configuration model 앙상블 그래프 생성
> > random_graph_analysis.create_random_graph_ensemble(random_graph="configuration", num_simulations=100)
> > 
> > # Chung-Lu model 앙상블 그래프 생성
> > random_graph_analysis.create_random_graph_ensemble(random_graph="chunglu", num_simulations=100)
> > 
> > # BA model 앙상블 그래프 생성
> > random_graph_analysis.create_random_graph_ensemble(random_graph="BA", num_simulations=100)
> > ```
> 
> > #### 2.2.3. 그래프의 차수 분포 계산
> >
> > 그래프를 인자로 주면 해당 그래프의 차수 분포 array를 반환한다. 그래프를 넘겨주지 않을 경우 객체를 생성할 때 사용한 원본 그래프의 차수 분포를 반환한다.
> > ```python
> > random_graph_analysis.degree_distribution(graph)
> > ```
> 
> > #### 2.2.4. 앙상블 그래프의 차수 분포 계산
> >
> > 앙상블 그래프 리스트를 넘겨주면 차수 분포 array의 리스트를 반환한다.
> > ```python
> > random_graph_analysis.ensemble_degree_distributions(ensemble_graphs_list)
> > ```

