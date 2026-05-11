Emotion Recognition TCC — Deep Learning Project
Projeto de Trabalho de Conclusão de Curso (TCC) em Ciência da Computação pela Pontifícia Universidade Católica do Paraná (PUCPR), focado no reconhecimento de emoções faciais utilizando técnicas modernas de Deep Learning.

Nota: Este repositório é um fork do projeto original desenvolvido em colaboração com Alexandre Beiruth. Minha participação envolveu treinamento e avaliação dos modelos, tratamento de desbalanceamento de classes, experimentos com data augmentation e análise comparativa de arquiteturas.


Sobre o Projeto
O projeto implementa e compara três arquiteturas de redes neurais profundas para classificação de sete emoções básicas a partir de expressões faciais em imagens:
ModeloParâmetrosCaracterísticasEfficientNet-B0~5.3MCompound scaling, mobile-friendly, fine-tuning em duas fasesResNet-50~25.6MSkip connections, transfer learning, arquitetura consolidadaEfficientViT~3.2MVision Transformer eficiente, mecanismo de atenção compacto
Emoções Reconhecidas
Raiva · Desgosto · Medo · Felicidade · Neutro · Tristeza · Surpresa

Destaques Técnicos

Transfer learning com fine-tuning nas três arquiteturas
Tratamento de desbalanceamento severo de classes (até 23× entre classes) via class weights e data augmentation
Análise de erro detalhada com identificação de vieses por classe
Estudos de ablação para comparação de componentes dos modelos
Containerização com Docker para reprodutibilidade
Monitoramento de recursos (CPU, GPU, memória) durante treinamento
Exportação automática de métricas em CSV e visualizações


Datasets Utilizados
DatasetImagensDescriçãoRAF-DB29.672Imagens de alta qualidade com anotações confiáveisEXPWvariávelImagens em ambiente não controlado (in-the-wild)
Os dados processados, modelos treinados, logs e resultados completos estão disponíveis no Google Drive do projeto (acesso mediante solicitação).

Requisitos do Sistema
Hardware:

GPU: NVIDIA com CUDA 12.1+ (RTX 3060 ou superior recomendado)
RAM: 16 GB mínimo
Armazenamento: ~90 GB (datasets + modelos)

Software:

Python 3.8+
Ubuntu 24.04 LTS (recomendado)
Docker 20.10+ (opcional)
NVIDIA Drivers 525.60+


Instalação
Opção 1 — Automatizada
bashgit clone https://github.com/Leandro-Cardoso/emotion_recognition_tcc.git
cd emotion_recognition_tcc
python scripts/setup_environment.py
source venv/bin/activate
Opção 2 — Manual
bashpython3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
pip install -r requirements.txt
pip install -e .
Opção 3 — Docker
bashdocker-compose up --build
# Jupyter Lab disponível em: http://localhost:8888

Uso Rápido
bash# Preparar datasets (estrutura esperada)
data/raw/RAF-DB
data/raw/EXPW

# Executar todos os experimentos
python scripts/run_experiments.py

# Executar modelo específico
python scripts/run_experiments.py --models efficientnet

# Iniciar Jupyter Lab
jupyter lab

Estrutura do Projeto
emotion_recognition_tcc/
├── README.md
├── Dockerfile & docker-compose.yml
├── requirements.txt & setup.py
│
├── data/
│   ├── raw/          # Datasets originais
│   └── processed/    # Dados pré-processados
│
├── notebooks/        # Análise exploratória e treinamento step-by-step
│
├── src/
│   ├── models/       # Implementações: EfficientNet, ResNet50, EfficientViT
│   ├── data/         # Carregamento e pré-processamento
│   ├── training/     # Pipeline de treinamento
│   ├── evaluation/   # Avaliação e métricas
│   ├── inference/    # Inferência em tempo real
│   └── utils/        # Utilitários gerais
│
├── scripts/
│   ├── setup_environment.py
│   ├── run_experiments.py
│   └── generate_reports.py
│
└── results/
    ├── models/       # Checkpoints .pth
    ├── logs/         # Histórico de treinamento
    ├── plots/        # Matrizes de confusão e gráficos
    └── csv_outputs/  # Métricas exportadas

Configuração Principal
yaml# config/config.yaml
data:
  preprocessing:
    image_size: 224
    normalize: true

training:
  batch_size: 32
  epochs: 100
  learning_rate: 0.001
  mixed_precision: true

models:
  efficientnet:
    pretrained: true
    dropout_rate: 0.5

Tecnologias Utilizadas
Mostrar Imagem
Mostrar Imagem
Mostrar Imagem
Mostrar Imagem

Referências

Tan, M., & Le, Q. (2019). EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks.
He, K., et al. (2016). Deep Residual Learning for Image Recognition.
Li, S., et al. (2017). Reliable Crowdsourcing and Deep Locality-Preserving Learning for Facial Expression Recognition.
Liu, Z., et al. (2015). The Expression in-the-Wild (ExpW) Database.


Orientação Acadêmica

Orientador: Prof. Rayson Laroca — PUCPR
Instituição: Pontifícia Universidade Católica do Paraná
Curso: Bacharelado em Ciência da Computação
Conclusão prevista: Junho de 2026


Leandro Cardoso · LinkedIn · PUCPR 2026
