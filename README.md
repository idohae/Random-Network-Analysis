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
> 원본 네트워크의 특정한 특성들을 유지한 채 무작위 네트워크를 생성하여 원본 네트워크의 고유한 특성을 비교 분석할 수 있다.

> ### 1.1. Erdős–Rényi (ER) model
> p의 확률로 노드 간 엣지를 연결하여 그래프를 생성하는 모델
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
> ### How to Use?
> >       git clone https://github.com/idohae/Random-Network-Analysis.git
> >
> > 위 명령어를 명령창에 입력하여 무작위 네트워크 분석 패키지를 원하는 환경에 다운 받는다.
> >
> > #### 1) 예시 데이터 분석 파일 실행
> > `Analysis.ipynb` 파일을 실행한다.
> > #### 2) 패키지 이용하여 원하는 데이터 분석
> > `random_graph_pkg` 디렉토리를 분석할 데이터 및 분석 코드와 같은 디렉토리 내에 위치시킨다.
> > ```python
> > from random_graph_pkg.random_graph_analysis import *
> > ```
> > 분석할 소스 코드에 위와 같이 패키지를 import 한 후 패키지 함수들을 사용한다.

