# Automação | Gerador de Pastas para IA | Com Arquivos em PY

## O que esse Script faz?

 ### `Gera Pastas`:

```bash
📂 /model
📂 /dataset
📂 /training
📂 /notebooks
📂 /config
📄 model.py
📄 preprocess.py
📄 train.py
📄 evaluate.py
📄 config.json
📄 docs/model.md
````

## Script:

````bash
#!/bin/bash

echo "=============================================="
echo "      🤖 AI Model Builder - Versão 0.1"
echo "=============================================="
echo ""

# Pastas principais
mkdir -p dataset
mkdir -p model
mkdir -p training
mkdir -p evaluation
mkdir -p notebooks
mkdir -p config
mkdir -p utils
mkdir -p docs
mkdir -p logs

# Arquivos vazios
# model
> model/model.py

# training
> training/train.py

# evaluation
> evaluation/evaluate.py

# utils
> utils/preprocess.py

# config
> config/config.json

# docs
> docs/README.md

# raiz
> requirements.txt
> logs/setup.log

echo ""
echo "=============================================="
echo "   🎉 Estrutura criada com sucesso!"
echo "=============================================="

````
