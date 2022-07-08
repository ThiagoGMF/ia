# Apresentação de Problemas relacionados

## Tabela PEAS (Perfomance, Environment, Actuators, Sensors)

| Tipo de Agente                               | Medida de desempenho                                                                                                                                    | Ambiente                        | Atuadores                                       | Sensores                                                         |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- | ----------------------------------------------- | ---------------------------------------------------------------- |
| Radar eletrônico                             | Detectar veículos em alta velocidade, fotografar somente veículos que ultrapassem a velocidade máxima permitida, medir a velocidade somente de veículos | rodovia                         | câmera para fotografar a placa do véiculo       | sensores de movimento, sensores para medir a velocidade do carro |
| Smartwatches                                 | Médir oxigênio do sangue, batimentos cardíacos e movimentos do corpo                                                                                    | corpo humano                    | tela do relógio                                 | oxímetro, acelerômetro, monitor cardíaco                         |
| Sistema de vigilância                        | Identificar corretamente pessoas armadas e/ou foragidas da justiça                                                                                      | eventos, restaturantes, cidades | identificador de armas, acesso à ficha criminal | câmeras                                                          |
| Catraca com biometria                        | Cadastrar biometria, reconhecer biometria cadastrada, destravar catraca para biometria reconhecida e manter travada para as não reconhecidas            | lugares privados                | catraca                                         | leitor de biometria                                              |
| Alimentador automático de animais domésticos | Reencher o pote de alimentos do pet de acordo com a forma programada, reproduzir áudio para atrair atenção do pet                                       | casa                            | depósito de alimentos, reprodutor de áudio      | temporizador                                                     |

## Tabela de ambientes

| Ambiente de tarefa                           | Observável    | Agentes | Deterministico | Episódico  | Estático | Discreto |
| -------------------------------------------- | ------------- | ------- | -------------- | ---------- | -------- | -------- |
| Radar eletrônico                             | Parcialmente  | Multi   | Determinístico | Episódico  | Dinâmico | Contínuo |
| Smartwatches                                 | Parcialmente  | Unico   | Estocástico    | Sequencial | Dinâmico | Contínuo |
| Sistema de vigilância                        | Completamente | Multi   | Estocástico    | Sequencial | Dinâmico | Contínuo |
| Catraca com biometria                        | Completamente | Unico   | Determinístico | Episódico  | Estático | Discreto |
| Alimentador automático de animais domésticos | Completamente | Unico   | Determinístico | Episódico  | Estático | Discreto |
