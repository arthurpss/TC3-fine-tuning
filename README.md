# Fine tuning
Esse repositório contém notebooks e scripts para o processo de **Fine-tuning** do modelo [Phi-3-mini](https://huggingface.co/microsoft/Phi-3-mini-4k-instruct) com dados do dataset [beTinti/AmazonTitles-1.3MM](https://huggingface.co/datasets/beTinti/AmazonTitles-1.3MM).

## Visão geral
O TC3 Fine-Tuning é um projeto voltado ao aprimoramento de modelos de linguagem pré-treinados por meio de técnicas de fine-tuning supervisionado. Seu objetivo é treinar o modelo para responder perguntas com base em títulos e descrições de produtos, explorando o uso de dados textuais estruturados e avaliando a qualidade das respostas geradas em cenários reais de e-commerce.

## Configuração do ambiente
Indicamos o uso do Google Colab para a execução dos notebooks, pois utilizamos bastante a integração com o Google Drive. Para rodar localmente serão necessárias adaptações no código, principalmente na fase de limpeza dos dados e extração dos samples/amostras.

# Instalação
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
Devido a limitações de recurso de processamento, o processo de Fine-tuning foi dividido em três notebooks diferentes. 
- [tratar-dados.ipynb](./tratar-dados.ipynb) é utilizado para limpar todos os dados considerados inválidos para o treinamento gerando um novo CSV.
- [transforma-em-json.ipynb](./transforma-em-json.ipynb) tem como objetivo formatar os dados conforme solicitado pela LLM gerando um arquivo JSON como resultado.
- [treino-e-teste.ipynb](./treino-e-teste.ipynb) realiza o treinamento do modelo com os dados formatados, e em seguida faz o teste comparando o modelo treinado com o modelo base usado.


## Nossa experiência
Iniciamos o desafio utilizando o modelo [Minstral 7B](https://huggingface.co/mistralai/Mistral-7B-v0.1) e utilizando o dataset completo, com cerca de 1.3M de registros. Porém, ao iniciar a fase de treinamento, descobrimos que não seria possível seguir desta forma, pois os recursos do colab são limitados e estamos utilizando a versão gratuita. Com isso, optamos por utilizar um modelo menor, o Phi-3-mini mencionado anteriormente, e trabalhar com uma base reduzida (100 mil registros aleatórios).  
No percurso, testamos diferentes hiperparamêtros de configuração do adaptador QLoRa(Quantized Low Rank Adaptation) e do SFTTtrainer e compramos 100 unidades computacionais do Google Colab para conseguir utilizar ambientes de execuções melhores. Desta forma, seguimos com a abordagem de manter os notebooks separados, visto que os dados foram tratados e armazenados enquanto ainda estavamos utilizando a versão gratuita e máquinas com menos recursos, mas, para o treinamento, usamos o ambiente L4.  
Para testar o resultado do modelo treinado, o salvamos no drive, como feito com os datasets e samples e definimos os prompts com base nos registros usados para treinamento. Por fim, comparamos as respostas geradas pelo nosso modelo com as respostas geradas pelo modelo original e vimos que as respostas do nosso modelo eram mais assertivas.
