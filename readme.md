# CRIAÇÃO DE DASHBOARD PARA ACOMPANHAMENTO DO PLANEJAMENTO ESTRATÉGICO DE INVESTIMENTOS EM UMA EMPRESA DO RAMO DE PETRÓLEO

#### Aluno: Renata Huhn Nunes (https://github.com/renatahuhn)
#### Orientador: Anderson Nascimento (https://github.com/link_do_github).

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

https://github.com/link_do_repositorio
Portifolio.xlsm
Alimentação Investimentos Quinquenio_vf.xlsx
mm_ planoestrategico.architect
mm_planoestrategico.png
script_alterainvestimento.sql
script_carrega_dimensao.sql
ETL01_CarregaTabelaPortfolio.ktr
ETL02_CarregaTabelaInvestimento.ktr
ETL03_CarregaDim-Portfolio.ktr
ETL04_Carrega-ft-investimento.ktr
JOB-AtualizaDados.kjb
ETL01_CarregaPlanilhaPortfolio.png
ETL02_CarregaPlanilhaInvestimento.png
ETL03-CarregaDimPotfolio.png
ETL04_CarregaDimInvestimento.png
JOB-AtualizaDados.png
ST_tbl_portfolio.png
ST_tbl_investimento.png
DW_dim_portfolio.png
DW_ft_investimento.png
Dahsboard_PlanoEstrategico_vf.pbix


### Resumo

Uma empresa do ramo de petróleo realiza anualmente o planejamento dos investimentos para os próximos anos. O presente trabalho apresenta o desenvolvimento de um banco de dados e um dashboard para acompanhamento do planejamento destes investimentos, em suas múltiplas versões até a aprovação final, para uma área de projetos de obras em refinarias de petróleo. O objetivo final do trabalho era o desenvolvimento de um dashboard com as informações solicitadas pela gerência responsável. Para desenvolvimento foram realizadas uma modelagem multidimensional, criação de uma datawarehouse, transformação dos dados com o PDI e criação do dashboard. Com a conclusão do presente trabalho, foi possível migrar as apresentações que antes eram realizadas em apresentações de PowerPoint para o PowerBI, reduzindo significativamente o esforço de atualização após revisões no planejamento.

### Abstract <!-- Opcional! Caso não aplicável, remover esta seção -->

<!-- trocar o texto abaixo pelo resumo do trabalho, em inglês -->

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin pulvinar nisl vestibulum tortor fringilla, eget imperdiet neque condimentum. Proin vitae augue in nulla vehicula porttitor sit amet quis sapien. Nam rutrum mollis ligula, et semper justo maximus accumsan. Integer scelerisque egestas arcu, ac laoreet odio aliquet at. Sed sed bibendum dolor. Vestibulum commodo sodales erat, ut placerat nulla vulputate eu. In hac habitasse platea dictumst. Cras interdum bibendum sapien a vehicula.

Proin feugiat nulla sem. Phasellus consequat tellus a ex aliquet, quis convallis turpis blandit. Quisque auctor condimentum justo vitae pulvinar. Donec in dictum purus. Vivamus vitae aliquam ligula, at suscipit ipsum. Quisque in dolor auctor tortor facilisis maximus. Donec dapibus leo sed tincidunt aliquam.

Donec molestie, ante quis tempus consequat, mauris ante fringilla elit, euismod hendrerit leo erat et felis. Mauris faucibus odio est, non sagittis urna maximus ut. Suspendisse blandit ligula pellentesque tincidunt malesuada. Sed at ornare ligula, et aliquam dui. Cras a lectus id turpis accumsan pellentesque ut eget metus. Pellentesque rhoncus pellentesque est et viverra. Pellentesque non risus velit. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.

### 1. Introdução

Este documento tem por finalidade coletar, analisar e definir as principais necessidades do projeto do estudo de caso do Planejamento de Investimentos em uma Empresa do Ramo de Petróleo. O documento procura demonstrar os principais problemas atuais e o foco investigativo desejado pelo cliente.

### 2. Modelagem

2.1. Descrição do Estudo de Caso

Uma empresa do ramo de petróleo (daqui em diante chamada de “Empresa X”)realiza obras em refinarias de petróleo visando a aumentar seus ativos ou a realizar melhorias na infraestrutura. Cada obra é tratada na empresa como um projeto e o conjunto de projetos em andamento compõem o que é chamado de “Portfólio de Investimentos” da companhia.
Com o objetivo de planejar o fluxo de caixa e a necessidade de capital, a Empresa X realiza anualmente o planejamento dos seus investimentos em obras para os próximos anos. Esse planejamento é chamado de “Plano Estratégico”. São geradas muitas versões de planilhas, uma vez que há muitas gerências responsáveis pela execução de cada um dos projetos e o planejamento pode ser revisado ao longo do período chamado “janela de planejamento”. Os valores são planejados a partir do ano atual até o fim do projeto (visão prospectiva), mas o enfoque principal do planejamento é no investimento do quinquênio (próximos 5 anos).
Após o fim da janela de planejamento pelas gerências responsáveis, é iniciada a etapa das aprovações em diversos níveis gerenciais. A cada nível, são solicitadas novas revisões no planejamento, até que seja aprovado no fim do ano o número final do investimento planejado.
Até o ano passado, a apresentação do planejamento era realizada por meio de uma planilha de PowerPoint. A cada revisão de planilha era necessário atualizar todos os gráficos e copiá-los manualmente para a apresentação de slides, gerando um esforço grande para atualização e incorrendo em riscos de erro humano.
O presente trabalho foi desenvolvido com a finalidade de elaborar um projeto de BI que ajude na visualização do alto volume de dados disponíveis, ajudando a Companhia a entender melhor a evolução dos investimentos ao longo dos próximos anos, para que possam usar no processo de aprovação do investimento proposto e na divulgação do orçamento após a aprovação final.
O presente projeto tratará o valor do investimento anual, em milhões de reais, bem como os desvios a cada ano e as justificativas para os desvios, como fato ativo a ser estudado. A proposta é cobrir as informações a respeito da junção das dimensões com o fato e consequentemente extrair informações que possam servir como auxílio para a Empresa X para tomar decisões futuras, aumentando a eficiência das comunicações e aumentando a confiabilidade das informações.
É desejável que o projeto trate o processo de negócio de forma que seja
possível obter relatórios com as informações dos valores do Plano Estratégico aprovado no ano de 2023 e do Plano Estratégico em aprovação no ano de 2024, bem como a comparação entre esses números para identificação de possíveis diferenças no planejamento, chamadas de “desvios”. Será possível estratificar os valores por ano, por gerência, por projeto, bem como visualizar as principais causas e as justificativas para desvios entre Planos.
Ao final do projeto, é esperado que, além da construção do Data
Warehouse, seja desenvolvido um dashboard com os dados mais relevantes
sobre os investimentos planejados para os próximos anos, de forma que os
gestores possam ter informações rápidas a qualquer momento.

2.2. Descrição do Modelo Transacional e Modelo Multidimensional

A Empresa X possui um sistema de informação integrado onde são
armazenados os dados de planejamento dos investimentos, bem como informações gerais de todos os projetos que compõem o portfólio de investimentos da companhia, além de outros dados que fogem ao escopo do projeto e por isso não serão listados aqui.
Todos os dados utilizados no processo serão coletados do banco de
dados disponibilizado pela Empresa X, contendo os valores de investimento planejados. As tabelas usadas como modelo de input para o presente trabalho encontram-se neste Repository: “Alimentação Investimentos Quinquenio_vf.xlsx” e “Portfolio.xlsm”.

2.2.1. Definição de Requisitos
Foram realizadas entrevistas com os stakeholders para compreender as
necessidades das gerências e também para identificar a viabilidade do
cumprimento dos requisitos. Além disso, as apresentações em PowerPoint realizadas em anos anteriores foram usadas como principais referências para elaboração do dashboard.
Na entrevista com os stakeholders, foram identificados como principais a gerente da área PMO, o gerente geral do portfólio de projetos e como key user a analista de custos da gerência PMO. Foram realizadas duas entrevistas iniciais: na primeira os três stakeholders mencionados acima detalharam suas necessidades e requisitos principais na segunda foi realizado acesso guiado às bases de dados com potencial de utilização no projeto. Após essas entrevistas, foi desenvolvido o primeiro protótipo do dashboard. Ao longo do desenvolvimento, foram realizadas reuniões mais curtas com a key user para realização de alguns questionamentos, pedidos de informações adicionais e validações intermediárias.
Na entrevista inicial, foi utilizado o plano de ação 5W2H, definindo os seguintes itens: 
i)O que: A elaboração de um projeto de BI com a disponibilização de um dashboard com dados para tomada de decisão e análise comparativa.
ii)Porque: Porque os stakeholders desejam ter acesso ao valores de investimentos planejados no Plano Estratégico de forma acessível e fácil.
iii)Onde: O BI deverá ser baseado nele nos sistemas e bancos de dados da empresa X.
iv)Quem: Farão uso dos dashboards todos os envolvidos no planejamento do Plano Estratégico, como gerências de projeto, a gerência PMO e os gestores da empresa X responsáveis pela aprovação do Plano Estratégico.
v) Quando: O projeto deve ser encerrado antes do encerramento da primeira janela de planejamento, que ocorrerá no dia 13/12/2024.
vi)Como: Um dashboard elaborado no Microsoft Power BI será entregue como objeto principal. Será construído também um Data Warehouse, alimentado por um processo de ETL.
vii)Com que frequência: O dashboard será atualizado sob demanda, ao fim de cada janela de planejamento e após as reuniões de aprovação com a cadeia gerencial da empresa.
Os requisitos identificados nas entrevistas foram:
Análise dos totais planejados no Plano Estratégico 2024-2028 (antigo) e Plano Estratégico 25-29 (atual); análise dos desvios entre os dois planos estratégicos; visão anual do valor total planejado; detalhamento anual do investimento planejado por projeto na visão prospectiva (2025+); análise detalhada dos 5 maiores desvios por projeto (a maior e a menor), com suas respectivas justificativas; análise das principais causas de desvio, por rubrica; detalhamento por gerência do investimento planejado por projeto no quinquênio 2025 a 2029, e justificativas para desvios.

2.2.2. Processo de BI e Modelo Multidimensional
A estruturação do processo de BI no projeto foi da seguinte forma: entrada e armazenamento de dados no PostgreSQL, tratamento de dados no Pentaho Data Integration e por fim a análise dos dados usando o PowerBI.
A análise dos dados é a etapa final do processo e depende de cada uma das
etapas anteriores para o pleno funcionamento e o software Power BI foi escolhido para realizar a última etapa por ser a ferramenta oficial adotada pela Companhia.
O mecanismo de banco de dados PostgreSQL foi escolhido para o armazenamento dos dados relacionais pela sua popularidade na comunidade
de desenvolvimento e pelo custo zero de licença. O software escolhido para a carga do Data Warehouse foi o Pentaho Data Integration, que oferece uma integração satisfatória entre os outros componentes do processo e também pelas possibilidades que dispõem para a transformação dos dados provenientes do modelo transacional. O processo tem como entrada de dados um único banco de dados relacional nomeado “st_planoestrategico”. O datawarehouse criado foi nomeado “dw_planoestrategico”.
O modelo multidimensional foi orientado pelas necessidades elucidadas com os stakeholders, bem como pelos dados disponíveis no banco de dados transacional. O diagrama Entidade Relacionamento (“modelo estrela”) encontra-se neste Repository: “mm_planoestrategico.architect”.

2.3. Elaboração do Datawarehouse

O Data Warehouse será a fonte integradora de informações da empresa, a tecnologia será utilizada com o intuito de servir de base para a camada de aplicação que será responsável por fornecer dados para a tomada de decisão na organização.
Dentre as estratégias para arquitetura Data Warehouse existentes (Global, Independente ou Integrada), foi escolhida a arquitetura Independente para o escopo do projeto em função de existência somente do banco de dados plano_estrategico.
Dentre as abordagens de construção do Data Warehouse previstas (Top-Down ou Botton-Up), optou-se pela Bottom-Up pois possibilita um retorno mais rápido, já que a estrutura poderá ser utilizada pela organização antes mesmo de se completar toda a construção do Data Warehouse.
Dentre as arquiteturas físicas para o Data Warehouse (On-Premises ou Nuvem), optou-se por Nuvem pelas vantagens listadas abaixo:
- Suporte elástico e escalável para requisitos de armazenamento ou computação complexos ou variáveis;
- Facilidade no uso;
- Facilidade de gerenciamento;
- Contenção de custos.

2.4. Projeto de ETL

O projeto de ETL usou apenas uma fonte: o banco de dados disponibilizado pela Empresa X, contendo dados sobre investimentos e projetos. Foi usado o software Pentaho Data Integration para realizar a extração e tratamento dos dados. Todos os arquivos estão neste Repository, sob os nomes: “ETL01_CarregaTabelaPortfolio”, “ETL02_CarregaTabelaInvestimento.krt”, “ETL03_CarregaDimPortfolio.krt”,“ETL04_Carrega-ft-investimento.krt”,”JOB-AtualizaDados.kjb”.
Para a carga do stage, carregamos as duas planilhas do modelo transacional. Para carga da planilha “Portfolio”, carregamos a planilha salva nas pastas de rede da gerência PMO, realizamos a correção dos strings, para apagar eventuais espaços desnecessários e normalizar a escrita dos elementos da planilha, colunas foram renomeadas para melhor leitura dos bancos de dados.
Para a carga da planilha “Alimentação Investimentos Quinquenio_vf”, foi realizado a renomeação das colunas e tratamento dos strings.
Para a carga da dimensão portfolio, carregamos dados do stage “st_planoestrategico” para o datawarehouse “dw_planoestrategico”.
Para o carregamento do fato investimento, as foi necessário realizar o cálculo dos valores dos desvios entre planos estratégicos e o desvio acumulado no quinquênio 25-29. Foi também necessário calcular os valores acumulados do investimento total planejado no Plano Estratégico 24-28 e no Plano Estratégico 25-29. Para este último também foi calculado o valor planejado apenas no quinquênio 25-29. Depois foi pego o SK de todas as dimensões para gravar o resultado na tabela fato.
Para finalizar, foi criado um job para agilizar o processo de atualização do DW, visto que o dashboard precisará ser atualizado constantemente.


### 3. Resultados

O dashboard foi elaborado utilizando a ferramenta Microsoft Power BI. Microsoft Power BI é uma ferramenta de desenvolvimento que permite a construção de painéis com informações gerenciais que permite a análise de negócios e análise de dados abordados.
As informações foram inseridas no dashboard de forma a demonstrar de
forma fácil e intuitiva todos os requisitos do cliente levantados durante a fase de entrevistas.
O dashboard elaborado pode ser encontrado neste Repository sob o nome “Dashboard Plano Estrategico_vf.pbix” 
Este dashboard apresenta a visualização das informações solicitadas pelos clientes durante o levantamento de requisitos. Apresenta os valores aprovados do Plano Estratégico realizado no ano de 2023 e os valores planejados no Plano Estratégico em aprovação no ano de 2024. Além disso, é apresentada a comparação entre esses dois Planos Estratégicos para identificação de desvios. Há visualizações distintas, onde são possíveis estratificações dos valores por ano, por gerência e/ou por projeto, bem como visualização das principais causas e justificativas para desvios entre Planos.
O dashboard foi aprovado pelas partes interessadas e publicado no Wokspace Premium da gerência responsável pela consolidação e apresentação dos dados(Gerencia PMO – projec management office). A partir disso o dashboard pôde ser compartilhado via link online para consulta e visualização das partes interessas em tempo real. A atualização do dashboard é feita a cada encerramento de etapa de revisão de dados, conforme calendário acordado entre as partes interessadas.
 

### 4. Conclusões

Este projeto foi concluído dentro do prazo necessário pela Gerência PMO, para realização das apresentações de aprovação do Plano Estratégico 2025-2029. Os stakeholders demonstraram satisfação com o resultado alcançado. O dashboard é uma ferramenta que auxiliará as equipes dos projetos e gestores a visualizar uma grande quantidade de dados de forma organizada e rápida, o que vai acelerar sua capacidade de tomada de decisões.
Este projeto seguiu o processo do BI Convencional, propiciando uma boa oportunidade de elaborar um modelo dinâmico, funcional e útil para a empresa em questão. O modelo multidimensional e a criação do Data Warehouse permitirão o processamento ágil dos dados, permitindo que o cliente tenha sempre informações atualizadas para tomada de decisões e saber informações relevantes de valores financeiros planejados.
Entende-se que o presente projeto atendeu a todos os objetivos e requisitos estabelecidos pelo cliente desde a primeira entrevista.

---

Matrícula: 221.100.904

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
























