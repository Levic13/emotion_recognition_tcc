# Emotion Recognition — TCC PUCPR

Reconhecimento de emoções faciais com Deep Learning, desenvolvido como Trabalho de Conclusão de Curso em Ciência da Computação na **PUCPR** (previsão: junho/2026).

## O que o projeto faz

Implementa e compara três arquiteturas de redes neurais para classificar **7 emoções básicas** (raiva, desgosto, medo, felicidade, neutro, tristeza, surpresa) a partir de imagens faciais.

| Modelo | Parâmetros | Destaques |
|---|---|---|
| EfficientNet-B0 | ~5.3M | Fine-tuning em duas fases |
| ResNet-50 | ~25.6M | Transfer learning clássico |
| EfficientViT | ~3.2M | Vision Transformer eficiente |

## Principais desafios técnicos

- Desbalanceamento severo de classes (até 23× entre classes) tratado com class weights e data augmentation
- Comparação de arquiteturas CNN vs. Vision Transformer
- Análise de erro por classe e estudos de ablação
- Datasets: **RAF-DB** (29.672 imagens) e **EXPW** (in-the-wild)

## Tecnologias

`Python` `PyTorch` `CUDA 12.1` `Docker` `Jupyter`

## Como rodar

```bash
# 1. Clonar e instalar
git clone https://github.com/Levic13/emotion_recognition_tcc.git
cd emotion_recognition_tcc
pip install -r requirements.txt

# 2. Executar experimentos
python scripts/run_experiments.py

# 3. Ou via Docker
docker-compose up --build
# Jupyter Lab em: http://localhost:8888
```

**Requisitos:** GPU NVIDIA com CUDA 12.1+, 16 GB RAM, ~90 GB de armazenamento.

## Estrutura

```
├── notebooks/       # Análise exploratória e treinamento
├── src/
│   ├── models/      # EfficientNet, ResNet50, EfficientViT
│   ├── training/    # Pipeline de treinamento
│   └── evaluation/  # Métricas e visualizações
├── scripts/         # Setup e execução de experimentos
└── results/         # Logs, gráficos e CSVs
```

## Referências

- Tan & Le (2019). *EfficientNet: Rethinking Model Scaling for CNNs.*
- He et al. (2016). *Deep Residual Learning for Image Recognition.*
- Li et al. (2017). *RAF-DB: Reliable Crowdsourcing for Facial Expression Recognition.*

---

**Orientador:** Prof. Rayson Laroca — PUCPR  
**Autor:** Leandro Cardoso · [LinkedIn](https://linkedin.com/in/leandro-cardoso-aaa803250)
