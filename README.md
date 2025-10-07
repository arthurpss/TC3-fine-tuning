# Fine tuning
Esse repositório contém notebooks e scripts para o processo de **Fine-tuning** do modelo [Phi-3-mini](https://huggingface.co/microsoft/Phi-3-mini-4k-instruct) com dados do dataset [beTinti/AmazonTitles-1.3MM](https://huggingface.co/datasets/beTinti/AmazonTitles-1.3MM).

## Visão geral
O TC3 Fine-Tuning é um projeto voltado ao aprimoramento de modelos de linguagem pré-treinados por meio de técnicas de fine-tuning supervisionado. Seu objetivo é treinar o modelo para responder perguntas com base em títulos e descrições de produtos, explorando o uso de dados textuais estruturados e avaliando a qualidade das respostas geradas em cenários reais de e-commerce.

## Instalação
1. Clone o repositório.
```sh
git clone https://github.com/arthurpss/TC3-fine-tuning.git
cd TC3-fine-tuning
```
2. Crie e ative um ambiente virtual Python:
```sh
python -m venv venv
```
3. Instale as dependências:
```sh
pip install -r requirements.txt
```
## Fluxo de uso
Devido a limitações de recurso de processamento, o processo de Fine-tuning foi dividido em três notebooks diferentes. O primeiro [tratar-dados.ipynb](./tratar-dados.ipynb) é utilizado para limpar todos os dados considerados inválidos para o treinamento gerando um novo CSV, o segundo é o [transforma-em-json.ipynb](./transforma-em-json.ipynb) que tem como objetivo formatar os dados conforme solicitado pela LLM gerando um arquivo JSON como resultado. O terceiro notebook [treino-e-teste.ipynb](./treino-e-teste.ipynb) realiza o treinamento do modelo com os dados formatados, e em seguida faz o teste comparando o modelo treinado com o modelo base usado.

Transformar dados
Use transforma-em-json.ipynb para ler o(s) dataset(s) original(is) e convertê-los em formato JSON ou no formato requerido para o modelo.

Tratar dados / pré-processamento
Execute tratar-dados.ipynb para limpeza, tokenização, balanceamento, divisão em treino/validação/teste, etc.

Treino e teste do modelo
Use treino-e-teste.ipynb para configurar o modelo (definir hiperparâmetros, escolher arquitetura base, etc.), treinar, validar e finalmente testar o modelo.
