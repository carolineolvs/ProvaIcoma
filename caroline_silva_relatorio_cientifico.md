# Relatório de Consultoria

**Cliente:** ANATEL – Agência Nacional de Telecomunicações

**Aluna:** Caroline Oliveira Silva


# Problema de Negócio

Identificar automaticamente reclamações de consumidores relacionadas a cortes indevidos, bloqueios ou interrupções de serviços de telecomunicações utilizando técnicas de Inteligência Artificial aplicadas ao conteúdo textual das reclamações.


# Análise Comparativa dos Modelos

Os cinco algoritmos foram treinados utilizando exatamente a mesma base de dados, o mesmo conjunto de atributos preditores extraídos pela técnica TF-IDF, a mesma divisão entre treinamento e teste e o mesmo processo de normalização. Dessa forma, a comparação realizada é cientificamente válida e livre de vazamento de dados.

| Modelo            | Precisão | Recall   | F1-Score |
| ----------------- | -------- | -------- | -------- |
| SVM               | 1,00     | 0,997992 | 0,998995 |
| Rede Neural (MLP) | 1,00     | 0,997992 | 0,998995 |
| KNN               | 1,00     | 0,996535 | 0,998264 |
| Árvore de Decisão | 1,00     | 0,990638 | 0,995297 |
| Random Forest     | 1,00     | 0,786952 | 0,880776 |

Observa-se que todos os modelos apresentaram precisão de 100%, indicando que os casos classificados como cortes indevidos realmente correspondiam a reclamações positivas. Entretanto, a principal diferença entre os algoritmos ocorreu na capacidade de identificar todos os casos reais de corte indevido, medida pelo Recall.

Por esse motivo, o F1-Score foi considerado uma das métricas mais relevantes para comparação, pois representa o equilíbrio entre precisão e capacidade de identificação dos casos positivos.

O SVM e a Rede Neural MLP apresentaram os melhores resultados, ambos com F1-Score de 0,998995 e Recall de aproximadamente 99,8%. O KNN apresentou desempenho muito próximo, enquanto a Árvore de Decisão obteve resultados satisfatórios, porém inferiores aos modelos anteriores. O Random Forest apresentou o menor Recall, demonstrando maior dificuldade em identificar todas as reclamações de corte indevido presentes na base.


# Interpretação Científica dos Resultados

O SVM apresentou excelente desempenho por sua capacidade de trabalhar com dados textuais representados por vetores TF-IDF em espaços de alta dimensionalidade. Seu mecanismo de separação por hiperplanos possibilitou uma identificação extremamente eficiente dos padrões existentes nas reclamações dos consumidores.

A Rede Neural Artificial MLP obteve desempenho equivalente ao SVM, demonstrando grande capacidade de aprendizado de padrões complexos presentes nos textos das reclamações. Entretanto, sua natureza de "caixa preta" torna mais difícil compreender quais características específicas levaram o modelo a determinada decisão.

O KNN também apresentou resultados elevados, porém seu custo computacional foi significativamente maior devido ao grande volume da base de dados da ANATEL, contendo mais de um milhão de registros. Por depender do cálculo de distância entre observações, foi necessária a utilização de uma amostragem representativa para tornar sua execução viável.

A Árvore de Decisão apresentou alta interpretabilidade, permitindo visualizar de forma mais clara os critérios utilizados pelo modelo para realizar as classificações. Contudo, apresentou desempenho ligeiramente inferior aos modelos mais complexos.

O Random Forest apresentou desempenho inferior aos demais modelos neste cenário específico. Embora normalmente seja um modelo robusto devido à combinação de diversas árvores de decisão, neste conjunto de dados textual ele apresentou menor capacidade de recuperar todos os casos positivos, refletindo em um Recall menor.


# Veredito do Consultor

Após a análise dos cinco algoritmos, recomenda-se a utilização do **SVM como solução principal para a identificação automática de reclamações relacionadas a cortes indevidos em serviços de telecomunicações**.

A recomendação é sustentada por três fatores principais:

1. **Melhor desempenho geral**, apresentando o maior F1-Score obtido (0,998995), empatado com a Rede Neural MLP, e uma capacidade de identificação dos casos positivos próxima de 100%.

2. **Maior adequação ao tipo de dado analisado**, pois o SVM apresenta excelente desempenho em problemas de classificação textual utilizando representações TF-IDF de alta dimensionalidade.

3. **Maior transparência quando comparado a modelos de redes neurais**, permitindo uma análise mais compreensível do funcionamento do modelo quando necessário.

Embora a Rede Neural MLP tenha alcançado resultados equivalentes, sua característica de modelo mais complexo e menos interpretável torna o SVM uma alternativa mais adequada para um contexto regulatório como o da ANATEL, onde transparência e confiabilidade são aspectos importantes para auditoria das decisões automatizadas.


# Impacto Ético e Social da Recomendação

A utilização de Inteligência Artificial na análise de reclamações dos consumidores deve ser compreendida como uma ferramenta de apoio aos analistas da ANATEL, e não como um mecanismo totalmente autônomo de decisão.

Um falso negativo pode representar um consumidor que sofreu um corte indevido e não teve seu caso identificado pelo sistema, atrasando uma possível solução. Já um falso positivo pode direcionar esforços de análise para reclamações que não representam um problema real.

A escolha do SVM busca equilibrar alto desempenho estatístico, confiabilidade e responsabilidade no uso da Inteligência Artificial, garantindo que o sistema contribua para uma análise mais rápida e eficiente sem substituir completamente o julgamento humano.


# Conclusão

Com base nos experimentos realizados, conclui-se que o **SVM representa a alternativa mais adequada para implantação em produção**, oferecendo o melhor equilíbrio entre desempenho preditivo, capacidade de generalização, eficiência na classificação de dados textuais e responsabilidade ética para o cenário de identificação de cortes indevidos em serviços de telecomunicações.
