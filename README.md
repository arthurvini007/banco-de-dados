Este documento apresenta a estrutura e a lógica para a organização do Data Lakehouse que será desenvolvido. Optamos por utilizar uma estrutura transacional, uma vez que esse modelo armazena os dados de forma estruturada em linha, ou seja, os dados são gravados no disco como linhas, e não em colunas. Esse formato é particularmente vantajoso quando é necessário obter informações completas sobre um cliente em uma tabela de usuários, permitindo a coleta eficiente dos dados desejados.

No entanto, esse modelo pode ser menos eficiente quando o objetivo é realizar operações que envolvem apenas uma coluna específica, como contar o número de clientes em um determinado CEP. Nesse caso, o sistema precisa carregar não apenas a coluna de CEP, mas também colunas como nome, endereço e user_id.

**Principais pontos a serem considerados:**

- **Garantir a integridade dos dados;**
- **Manter baixa latência nas operações;**
- **Monitorar eficientemente os sistemas operacionais.**

## 1- Entendimento do fluxo de dados:

Para estruturar adequadamente o banco de dados, é fundamental entender como os dados chegam até nós, o que permitirá uma análise mais precisa e um melhor planejamento da arquitetura.

- **1.1- Cadastro de Pessoas ou Empresa:**
- **1.2- Eixo ou Estrutura:**
- **1.3- Inscrições ou Serviço:**
- **1.4- Programas ou Agendamento de Equipamento:**
- **1.5- Feedback de Programas e Feedback da Estrutura:**
#### 1.1- Cadastro de Pessoas ou Empresa:

O primeiro contato ocorre quando uma pessoa ou empresa demonstra interesse em um de nossos programas ou quando identifica uma necessidade que nossa estrutura pode ajudar a solucionar. A coleta de dados é realizada por meio de formulários ou inscrições em algum programa ou serviço.

- **Cadastro de Pessoa Física:** [Link para Formulário]  
    Nosso formulário de cadastro para pessoas físicas coleta informações essenciais para mapear a usabilidade do usuário em nosso ecossistema. Os dados solicitados incluem: Nome Completo, CPF, Data de Nascimento, Faixa Etária, Gênero, Orientação Sexual, Raça/Etnia, Faixa de Renda Mensal, Escolaridade, Estado Civil, CEP, Logradouro, Número, Bairro, Complemento, Cidade, Estado, Email, Telefone e Área de Interesse, além do **ID da Empresa** (caso aplicável).
    
- **Cadastro de Empresa:** [Link para Formulário]  
    Para o cadastro de empresas, coletamos dados fundamentais para entender a usabilidade da organização em nosso ecossistema. As informações solicitadas incluem: Razão Social, Nome Fantasia, CNPJ, CEP, Logradouro, Número, Complemento, Bairro, Cidade, Estado, Email, Telefone de Contato, além do **ID da Pessoa** responsável.
    

Com esse mapeamento inicial, já é possível realizar microanálises com base nos dados fornecidos. À medida que as interações com nosso ecossistema aumentam, as análises se tornam mais robustas, permitindo uma visão cada vez mais estruturada e abrangente.

#### 1.2- Eixo ou Estrutura:

Na segunda etapa, devera mapear para onde ele irar , se vai ser em algum eixo para se inscrever em algum programa de algum determinado eixo ou ele irar usar a estrutura disponível no nosso ecossistema , também pode estar em um eixo e estar utilizando algum serviço.

- **Inscrição em Programas** [Link para Formulário]  
	Nesta etapa, o usuário poderá se inscrever em programas de seu interesse. Ao fazer isso, sua ficha será enriquecida em nosso banco de dados. A inscrição é realizada com base nos editais de cada programa, relacionando o usuário a um ou mais eixos temáticos, como **Familiaridade com Ferramentas Digitais** e **Interesse em Áreas Específicas de Inovação e Tecnologia**, além dos dados já previamente cadastrados. Isso formaliza sua inscrição.
    
- **Agendamento de Serviços** [Link para Formulário]  
	O usuário poderá agendar ou contratar um dos serviços disponíveis em nossa estrutura, como: **Laboratórios de Prototipagem e Fabricação Digital**, **Produção Musical**, **Criação**, **Fotografia e Filmagem**, **Moda e Estamparia**, **COWORKING**, **Salas Empresariais**, **Treinamento** ou **Showroom**.
    

Com essa segunda coleta de dados, nossa base de informações se expande, permitindo um acompanhamento mais preciso das interações e interesses dos usuários.

#### 1.3- Inscrições ou Serviço:

Na Terceira etapa, após o cadastro no nosso ecossistema, para qualquer nova interação com nossos programas ou serviços, será necessário realizar uma inscrição ou agendar um serviço específico.

- **Inscrição em Programas** [Link para Formulário]  
    Nesta etapa, o usuário poderá se inscrever em programas de seu interesse. Ao fazer isso, sua ficha será enriquecida em nosso banco de dados. A inscrição é realizada com base nos editais de cada programa, relacionando o usuário a um ou mais eixos temáticos, como **Familiaridade com Ferramentas Digitais** e **Interesse em Áreas Específicas de Inovação e Tecnologia**, além dos dados já previamente cadastrados. Isso formaliza sua inscrição.
    
- **Agendamento de Serviços** [Link para Formulário]  
    O usuário poderá agendar ou contratar um dos serviços disponíveis em nossa estrutura, como: **Laboratórios de Prototipagem e Fabricação Digital**, **Produção Musical**, **Criação**, **Fotografia e Filmagem**, **Moda e Estamparia**, **COWORKING**, **Salas Empresariais**, **Treinamento** ou **Showroom**.
    

Com essa segunda coleta de dados, nossa base de informações se expande, permitindo um acompanhamento mais preciso das interações e interesses dos usuários.

#### 1.4- Programas ou Agendamento de Equipamento:

Na quarta etapa, o foco é a confirmação da participação nos programas escolhidos e o uso de equipamentos agendados. Essa fase permite a validação dos usuários que foram aprovados nos programas para os quais se inscreveram e possibilita o monitoramento dos equipamentos mais solicitados.

- **Aprovação em Programas** [Link para Formulário]  
    Após a inscrição, o usuário será informado sobre sua aprovação nos programas correspondentes. A partir deste momento, ele estará apto a participar das atividades e terá acesso aos conteúdos e recursos oferecidos. Os dados sobre sua participação são vinculados aos **eixos temáticos** previamente selecionados, como **Inovação**, **Tecnologia** ou **Economia Criativa**, e passam a fazer parte de nosso sistema de acompanhamento de desempenho e evolução.
    
- **Agendamento de Equipamentos** [Link para Formulário]  
    Nessa etapa, o usuário pode agendar o uso de equipamentos disponíveis, como: **Impressoras 3D**, **Cortadoras a Laser**, **Câmeras Profissionais**, **Estúdios de Gravação**, **Laboratórios de Moda**, entre outros. O sistema irá registrar o equipamento solicitado e o tempo de uso, ajudando no gerenciamento de recursos e na identificação dos equipamentos mais demandados.
    

Essas interações fornecem insights valiosos, permitindo a otimização dos serviços oferecidos, com base no monitoramento das atividades dos usuários e da utilização de equipamentos.

#### 1.5- Feedback de Programas e Feedback da Estrutura:

Nesta quinta etapa, a coleta de feedback é fundamental para garantir a melhoria contínua dos programas e da infraestrutura oferecida. Com base nas experiências dos usuários, ajustamos e aperfeiçoamos nossas iniciativas, assegurando que estejam alinhadas às necessidades e expectativas da comunidade.

- **Feedback de Programas** [Link para Formulário]  
    Ao final de cada programa com formulários direcionados especificamente para cada eixo , o usuário será solicitado a fornecer um feedback detalhado sobre sua experiência. O formulário incluirá perguntas sobre a qualidade dos conteúdos abordados, a aplicabilidade prática do aprendizado, a didática dos facilitadores e o impacto do programa em suas atividades pessoais ou profissionais. Também será solicitado que o usuário avalie os seguintes aspectos:
    
    - **Relevância do Conteúdo** para seu desenvolvimento.
    - **Facilidade de Acesso aos Recursos** e materiais de apoio.
    - **Contribuição para seu Crescimento** nas áreas de inovação e tecnologia. Essas informações serão utilizadas para refinar e aprimorar futuros programas.
- **Feedback da Estrutura** [Link para Formulário]  
    O usuário também será incentivado a avaliar a infraestrutura utilizada durante sua participação. O feedback abrangerá:
    
    - **Qualidade e Funcionamento dos Equipamentos** (ex: Laboratórios de Prototipagem, Estúdios de Gravação, Câmeras).
    - **Conforto e Funcionalidade dos Espaços** (ex: Coworking, Salas Empresariais, Showroom).
    - **Disponibilidade e Suporte Técnico**. O objetivo é identificar possíveis melhorias na infraestrutura física e tecnológica, garantindo que os equipamentos e os espaços continuem atendendo às necessidades dos usuários de maneira eficiente e confortável.

A coleta de feedback permitirá um ciclo contínuo de melhoria, impulsionando a inovação e a excelência dos programas e da estrutura oferecida, ao mesmo tempo em que proporciona uma experiência mais satisfatória para os usuários.


## 2- Construção do banco de Dados:

Nesta seção, apresentaremos a construção e estruturação do banco de dados, destacando os **modelos relacionais** e **modelos lógicos** desenvolvidos especificamente para atender às necessidades desse sistema. Através desses modelos, será possível visualizar a organização dos dados, as relações entre as entidades e a lógica aplicada para garantir a eficiência e escalabilidade do banco de dados.

- **Modelos Relacionais**:  
    O modelo relacional define a estrutura básica do banco de dados, estabelecendo as tabelas, colunas e os relacionamentos entre elas. Aqui, são mapeadas as entidades principais, como usuários, programas, equipamentos e interações, além das **chaves primárias** e **chaves estrangeiras** que garantem a integridade referencial dos dados. Este modelo permite uma visão clara das dependências e conexões entre diferentes áreas do sistema.
    
- **Modelos Lógicos**:  
    O modelo lógico detalha como os dados serão organizados e acessados, otimizando o desempenho das consultas e operações no banco de dados. Ele inclui definições de **tipos de dados**, **restrições** e **índices**, além da lógica que orienta as regras de negócios aplicadas. A estrutura lógica foi projetada para facilitar a expansão futura do sistema, garantindo flexibilidade no armazenamento e recuperação dos dados, além de suportar grandes volumes de informações.
    

Essa abordagem permite que o banco de dados seja robusto e escalável, suportando de forma eficiente o crescimento do sistema e assegurando uma gestão otimizada das informações.

- **2.1- Modelo Relacional**
- **2.2- Modelo Logico**

### 2.1- Modelo Relacional:

Nesta seção, detalhamos a estrutura relacional do banco de dados, focando em como as informações estão organizadas em tabelas e relacionamentos. O **modelo relacional** é essencial para garantir a integridade dos dados, a eficiência das consultas e a escalabilidade do sistema. Abaixo estão os principais componentes do modelo relacional adotado:
 1. Tabela: `CAD_PESSOA`

- **Descrição**: Armazena informações pessoais de indivíduos, como nome, CPF, endereço, gênero, e outros dados demográficos.
- **Colunas**:
    - `ID_PESSOA` (PK, VARCHAR 50): Identificador único da pessoa.
    - `NOME_COMPLETO` (VARCHAR 255): Nome completo da pessoa.
    - `CPF` (VARCHAR 14): Cadastro de Pessoa Física.
    - `DATA_NASCIMENTO` (DATE): Data de nascimento.
    - `FAIXA_ETARIA` (VARCHAR 50): Faixa etária da pessoa.
    - `GENERO` (VARCHAR 50): Gênero da pessoa.
    - `ORIENTACAO_SEXUAL` (VARCHAR 50): Orientação sexual.
    - `RACA_ETNIA` (VARCHAR 50): Raça ou etnia.
    - `FAIXA_DE_RENDA` (TEXT): Faixa de renda da pessoa.
    - `ESCOLARIDADE` (VARCHAR 50): Nível de escolaridade.
    - `CEP` (VARCHAR 10): Código postal da residência.
    - `LOGRADOURO` (VARCHAR 255): Nome da rua ou avenida.
    - `NUMERO` (VARCHAR 10): Número da residência.
    - `BAIRRO` (VARCHAR 100): Bairro.
    - `COMPLEMENTO` (VARCHAR 255): Complemento do endereço.
    - `CIDADE` (VARCHAR 100): Cidade.
    - `ESTADO` (VARCHAR 2): Estado.
    - `EMAIL` (VARCHAR 255): Endereço de e-mail.
    - `TELEFONE` (VARCHAR 20): Número de telefone.
    - `AREA_DE_ATUACAO` (VARCHAR 100): Área de atuação profissional.
    - `ID_EMPRESA` (INT, FK): Referência à tabela `CAD_EMPRESA` (empresa à qual a pessoa está associada).



 2. Tabela: `CAD_EMPRESA`

- **Descrição**: Armazena dados de empresas, incluindo seus dados cadastrais e informações de contato.
- **Colunas**:
    - `ID_EMPRESA` (PK, VARCHAR 50): Identificador único da empresa.
    - `ID_PESSOA` (INT, FK): Referência à tabela `CAD_PESSOA` (pessoa associada à empresa).
    - `RAZAO_SOCIAL` (VARCHAR 255): Razão social da empresa.
    - `NOME_FANTASIA` (VARCHAR 255): Nome fantasia.
    - `CNPJ` (VARCHAR 18): Cadastro Nacional de Pessoa Jurídica.
    - `CEP` (VARCHAR 10): Código postal da sede.
    - `LOGRADOURO` (VARCHAR 255): Nome da rua ou avenida da empresa.
    - `NUMERO` (VARCHAR 10): Número da sede.
    - `COMPLEMENTO` (VARCHAR 255): Complemento do endereço.
    - `BAIRRO` (VARCHAR 100): Bairro.
    - `CIDADE` (VARCHAR 100): Cidade.
    - `ESTADO` (VARCHAR 2): Estado.
    - `EMAIL` (VARCHAR 255): E-mail de contato.
    - `TELEFONE_CONTATO` (VARCHAR 20): Telefone de contato.



 3. Tabela: `PROGRAMAS`

- **Descrição**: Armazena informações sobre os programas cadastrados, cada um vinculado a um domínio específico.
- **Colunas**:
    - `ID_PROGRAMA` (PK, INT): Identificador único do programa.
    - `ID_DOMINIO` (INT, FK): Referência à tabela `DOMINIOS`.
    - `TITULO_PROGRAMA` (VARCHAR 255): Título do programa.



 4. Tabela: `INSCRICOES`

- **Descrição**: Registra as inscrições de pessoas em programas específicos.
- **Colunas**:
    - `ID_INSCRICAO` (PK, INT): Identificador único da inscrição.
    - `ID_PROGRAMA` (INT, FK): Referência à tabela `PROGRAMAS`.
    - `ID_PESSOA` (INT, FK): Referência à tabela `CAD_PESSOA`.
    - `DATA_INSCRICAO` (DATE): Data da inscrição.



 5. Tabela: `PARTICIPANTE_PROGRAMA`

- **Descrição**: Tabela associativa que relaciona programas com as inscrições de participantes.
- **Colunas**:
    - `ID_PROGRAMA` (INT, FK): Referência à tabela `PROGRAMAS`.
    - `ID_INSCRICAO` (INT, FK): Referência à tabela `INSCRICOES`.
    - **Chave Primária Composta**: `ID_PROGRAMA`, `ID_INSCRICAO`.



 6. Tabela: `DOMINIOS`

- **Descrição**: Armazena informações sobre domínios e seus responsáveis.
- **Colunas**:
    - `ID_DOMINIO` (PK, INT): Identificador único do domínio.
    - `NOME_DOMINIO` (VARCHAR 255): Nome do domínio.
    - `RESPONSAVEL_DOMINIO` (VARCHAR 255): Nome do responsável pelo domínio.



 7. Tabela: `PROGRAMA_ODS`

- **Descrição**: Relaciona programas com os Objetivos de Desenvolvimento Sustentável (ODS).
- **Colunas**:
    - `ID_PROGRAMA` (INT, FK): Referência à tabela `PROGRAMAS`.
    - `ID_ODS` (INT, FK): Referência à tabela `ONU_ODS`.
    - **Chave Primária Composta**: `ID_PROGRAMA`, `ID_ODS`.



 8. Tabela: `ONU_ODS`

- **Descrição**: Armazena informações sobre os Objetivos de Desenvolvimento Sustentável.
- **Colunas**:
    - `ID_ODS` (PK, INT): Identificador único do ODS.
    - `NOME_ODS` (VARCHAR 255): Nome do ODS.



 9. Tabela: `SERVICO`

- **Descrição**: Armazena serviços oferecidos, como os de laboratórios e infraestrutura.
- **Colunas**:
    - `ID_SERVICO` (PK, INT): Identificador único do serviço.
    - `TITULO_SERVICO` (VARCHAR 255): Título do serviço.


 10. Tabela: `AGENDAMENTO_SERVICO`

- **Descrição**: Registra os agendamentos de serviços pelos usuários.
- **Colunas**:
    - `ID_AGENDAMENTO` (PK, INT): Identificador único do agendamento.
    - `ID_SERVICO` (INT, FK): Referência à tabela `SERVICO`.
    - `ID_PESSOA` (INT, FK): Referência à tabela `CAD_PESSOA`.
    - `DATA_AGENDAMENTO` (DATE): Data do agendamento.


 11. Tabela: `LABORATORIOS_SALAS`

- **Descrição**: Armazena informações sobre laboratórios e salas, bem como seus serviços associados.
- **Colunas**:
    - `ID_LABORATORIO` (PK, INT): Identificador único do laboratório.
    - `NOME_LABORATORIO` (VARCHAR 255): Nome do laboratório.
    - `ID_SERVICO` (INT, FK): Referência à tabela `SERVICO`.
    - `DESCRICAO` (TEXT): Descrição do laboratório.



 12. Tabela: `EQUIPAMENTO`

- **Descrição**: Armazena informações sobre os equipamentos disponíveis nos laboratórios.
- **Colunas**:
    - `ID_EQUIPAMENTO` (PK, AUTOINCREMENT): Identificador único do equipamento.
    - `NOME_EQUIPAMENTO` (VARCHAR 255): Nome do equipamento.
    - `DESCRICAO` (TEXT): Descrição do equipamento.
    - `DISPONIBILIDADE` (BOOLEAN): Status de disponibilidade do equipamento.
    - `ID_LABORATORIO` (INT, FK): Referência à tabela `LABORATORIOS_SALAS`.



 13. Tabela: `AGENDAMENTO_INFRA`

- **Descrição**: Registra agendamentos de infraestrutura, relacionando equipamentos e laboratórios com serviços agendados.
- **Colunas**:
    - `ID_AGENDAMENTO_INFRA` (PK, AUTOINCREMENT): Identificador único do agendamento de infraestrutura.
    - `ID_AGENDAMENTO` (INT, FK): Referência à tabela `AGENDAMENTO_SERVICO`.
    - `ID_LABORATORIO` (INT, FK): Referência à tabela `LABORATORIOS_SALAS`.
    - `ID_EQUIPAMENTO` (INT, FK): Referência à tabela `EQUIPAMENTO`.



 14. Tabela: `FORMULARIOS_FEEDBACK_PROGRAMAS`

- **Descrição**: Registra feedbacks fornecidos por participantes de programas.
- **Colunas**:
    - `ID_FORMULARIO` (PK, AUTOINCREMENT): Identificador único do formulário.
    - `ID_INSCRICAO` (INT, FK): Referência à tabela `INSCRICOES`.
    - `ID_PESSOA` (INT, FK): Referência à tabela `CAD_PESSOA`.
    - `ID_DOMINIO
### 2.3- Modelo Lógico

 Tabela `CAD_PESSOA`

Armazena informações detalhadas sobre as pessoas participantes, com dados pessoais, endereço e área de atuação. Também possui uma chave estrangeira para associar a pessoa a uma empresa.

- **ID_PESSOA**: Identificador único da pessoa (chave primária).
- **NOME_COMPLETO**: Nome completo da pessoa.
- **CPF**: Cadastro de Pessoa Física.
- **DATA_NASCIMENTO**: Data de nascimento da pessoa.
- **FAIXA_ETARIA**: Faixa etária da pessoa.
- **GENERO**: Gênero da pessoa.
- **ORIENTACAO_SEXUAL**: Orientação sexual da pessoa.
- **RACA_ETNIA**: Raça/etnia da pessoa.
- **FAIXA_DE_RENDA**: Faixa de renda da pessoa.
- **ESCOLARIDADE**: Nível de escolaridade.
- **ENDEREÇO**: Inclui CEP, logradouro, número, complemento, bairro, cidade e estado.
- **EMAIL**: E-mail de contato.
- **TELEFONE**: Telefone de contato.
- **AREA_DE_ATUACAO**: Área de atuação profissional da pessoa.
- **ID_EMPRESA**: Chave estrangeira que referencia a empresa na tabela `CAD_EMPRESA`.

 Tabela `CAD_EMPRESA`

Contém informações sobre empresas e tem uma relação com a tabela `CAD_PESSOA`.

- **ID_EMPRESA**: Identificador único da empresa (chave primária).
- **ID_PESSOA**: Chave estrangeira que associa a empresa a uma pessoa.
- **RAZAO_SOCIAL**: Razão social da empresa.
- **NOME_FANTASIA**: Nome fantasia da empresa.
- **CNPJ**: Cadastro Nacional de Pessoa Jurídica.
- **ENDEREÇO**: Inclui CEP, logradouro, número, complemento, bairro, cidade e estado.
- **EMAIL**: E-mail de contato da empresa.
- **TELEFONE_CONTATO**: Telefone de contato da empresa.

 Tabela `PROGRAMAS`

Armazena informações dos programas que fazem parte do sistema.

- **ID_PROGRAMA**: Identificador único do programa (chave primária).
- **ID_DOMINIO**: Chave estrangeira que associa o programa a um domínio.
- **TITULO_PROGRAMA**: Título do programa.

 Tabela `INSCRICOES`

Registra as inscrições das pessoas nos programas.

- **ID_INSCRICAO**: Identificador único da inscrição (chave primária).
- **ID_PROGRAMA**: Chave estrangeira que referencia o programa.
- **ID_PESSOA**: Chave estrangeira que referencia a pessoa inscrita.
- **DATA_INSCRICAO**: Data em que a inscrição foi realizada.

 Tabela `PARTICIPANTE_PROGRAMA`

Relaciona os programas com as inscrições.

- **ID_PROGRAMA**: Chave estrangeira que referencia o programa.
- **ID_INSCRICAO**: Chave estrangeira que referencia a inscrição.
- **Chave primária composta**: (ID_PROGRAMA, ID_INSCRICAO).

 Tabela `DOMINIOS`

Armazena informações sobre domínios de programas e serviços.

- **ID_DOMINIO**: Identificador único do domínio (chave primária).
- **NOME_DOMINIO**: Nome do domínio.
- **RESPONSAVEL_DOMINIO**: Nome do responsável pelo domínio.

 Tabela `PROGRAMA_ODS`

Relaciona programas aos Objetivos de Desenvolvimento Sustentável (ODS) da ONU.

- **ID_PROGRAMA**: Chave estrangeira que referencia o programa.
- **ID_ODS**: Chave estrangeira que referencia o ODS.
- **Chave primária composta**: (ID_PROGRAMA, ID_ODS).

 Tabela `ONU_ODS`

Armazena informações dos ODS da ONU.

- **ID_ODS**: Identificador único do ODS (chave primária).
- **NOME_ODS**: Nome do ODS.

 Tabela `SERVICO`

Armazena os serviços disponíveis no sistema.

- **ID_SERVICO**: Identificador único do serviço (chave primária).
- **TITULO_SERVICO**: Título do serviço.

 Tabela `AGENDAMENTO_SERVICO`

Armazena agendamentos de serviços.

- **ID_AGENDAMENTO**: Identificador único do agendamento (chave primária).
- **ID_SERVICO**: Chave estrangeira que referencia o serviço agendado.
- **ID_PESSOA**: Chave estrangeira que referencia a pessoa que agendou o serviço.
- **DATA_AGENDAMENTO**: Data do agendamento.

 Tabela `LABORATORIOS_SALAS`

Armazena informações sobre laboratórios e salas.

- **ID_LABORATORIO**: Identificador único do laboratório/sala (chave primária).
- **NOME_LABORATORIO**: Nome do laboratório ou sala.
- **ID_SERVICO**: Chave estrangeira que referencia o serviço relacionado ao laboratório/sala.
- **DESCRICAO**: Descrição do laboratório/sala.

 Tabela `EQUIPAMENTO`

Armazena informações sobre os equipamentos disponíveis nos laboratórios.

- **ID_EQUIPAMENTO**: Identificador único do equipamento (chave primária).
- **NOME_EQUIPAMENTO**: Nome do equipamento.
- **DESCRICAO**: Descrição do equipamento.
- **DISPONIBILIDADE**: Indica se o equipamento está disponível.
- **ID_LABORATORIO**: Chave estrangeira que referencia o laboratório ao qual o equipamento pertence.

 Tabela `AGENDAMENTO_INFRA`

Armazena informações sobre agendamentos de infraestrutura, como equipamentos e laboratórios.

- **ID_AGENDAMENTO_INFRA**: Identificador único do agendamento de infraestrutura (chave primária).
- **ID_AGENDAMENTO**: Chave estrangeira que referencia o agendamento de serviço.
- **ID_LABORATORIO**: Chave estrangeira que referencia o laboratório.
- **ID_EQUIPAMENTO**: Chave estrangeira que referencia o equipamento.

 Tabela `FORMULARIOS_FEEDBACK_PROGRAMAS`

Armazena os formulários de feedback sobre os programas.

- **ID_FORMULARIO**: Identificador único do formulário (chave primária).
- **ID_INSCRICAO**: Chave estrangeira que referencia a inscrição relacionada ao feedback.
- **ID_PESSOA**: Chave estrangeira que referencia a pessoa que forneceu o feedback.
- **ID_DOMINIO**: Chave estrangeira que referencia o domínio do programa.
- **NOME_FORMULARIO**: Nome do formulário.
- **DATA_CRIACAO**: Data de criação do formulário.

 Tabela `PERGUNTAS`

Armazena as perguntas dos formulários de feedback.

- **ID_PERGUNTA**: Identificador único da pergunta (chave primária).
- **ID_DOMINIO**: Chave estrangeira para associar a pergunta a um domínio específico.
- **PERGUNTA**: Texto da pergunta.
- **TIPO_PERGUNTA**: Tipo da pergunta (ex: escala, texto, sim/não).

 Tabela `RESPOSTAS_FEEDBACK_PROGRAMAS`

Armazena as respostas dos formulários de feedback sobre os programas.

- **ID_RESPOSTA**: Identificador único da resposta (chave primária).
- **ID_FORMULARIO**: Chave estrangeira que referencia o formulário.
- **ID_PERGUNTA**: Chave estrangeira que referencia a pergunta.
- **ID_INSCRICAO**: Chave estrangeira que referencia a inscrição.
- **RESPOSTA**: Texto da resposta.

 Tabela `FEEDBACK_INFRAESTRUTURA`

Armazena feedbacks sobre a infraestrutura utilizada nos agendamentos.

- **ID_PESSOA**: Chave estrangeira que referencia a pessoa que forneceu o feedback.
- **ID_AGENDAMENTO**: Chave estrangeira que referencia o agendamento.
- **ID_PERGUNTA**: Chave estrangeira que referencia a pergunta do feedback.
- **RESPOSTA**: Texto da resposta.

 Tabela `PERGUNTAS_FEEDBACK_INFRAESTRUTURA`

Armazena as perguntas dos formulários de feedback sobre a infraestrutura.

- **ID_PERGUNTA**: Identificador único da pergunta (chave primária).
- **PERGUNTA**: Texto da pergunta.

## 3- Criação de um Protótipo com dados randômicos

Para a criação desse protótipo, nossa equipe desenvolveu uma estrutura de banco de dados , e colocamos para desenvolvimento no colab , um código em python onde criamos dados randomicamente usando as bibliotecas (Faker e Random).

Importando as Bibliotecas:

Este código importa uma variedade de módulos e bibliotecas que fornecem funcionalidades para manipulação de dados, interação com bancos de dados, geração de dados falsos e operações relacionadas a data e hora. Cada módulo tem um propósito específico e é utilizado para diferentes tarefas em projetos de programação e análise de dados.

![[Pasted image 20240918083543.png]]
Estruturação das tabelas elaboradas na modelagem de bando de dados logico:

Este script cria a estrutura inicial necessária para gerenciar dados complexos em um banco de dados, permitindo operações como o registro de pessoas, empresas, programas e agendamentos, bem como a coleta de feedbacks e a gestão de infraestrutura.

![[Pasted image 20240918083503.png]]
Criação da tabela CAD_PESSOA:

Este código é usado para visualizar as colunas existentes na tabela `CAD_PESSOA` de um banco de dados SQLite. Ele executa uma consulta PRAGMA para obter informações sobre as colunas da tabela e, em seguida, exibe os nomes dessas colunas numerados, facilitando a revisão da estrutura da tabela.

![[Pasted image 20240918083838.png]]
Com isso usamos o fake e random para criar cadastro de pessoas fictícias:

Este código gera e insere registros fictícios na tabela `CAD_PESSOA` de um banco de dados SQLite. Utiliza a biblioteca `Faker` para criar dados realistas e garantir a unicidade dos CPFs e e-mails. A função `insert_into_cad_pessoa` preenche a tabela com uma quantidade especificada de registros, garantindo que a tabela seja populada com dados variados e realistas para fins de teste ou desenvolvimento.

![[Pasted image 20240918084809.png]]
![[Pasted image 20240918084843.png]]
![[Pasted image 20240918084928.png]]

Criação da tabela CAD_EMPRESA:

Este código consulta a estrutura da tabela `CAD_EMPRESA` em um banco de dados SQLite, obtendo informações sobre suas colunas. Ele imprime o nome de cada coluna na tabela, numerando-as para facilitar a leitura. É útil para obter uma visão geral da estrutura de uma tabela e verificar os nomes das colunas e suas respectivas ordens.

![[Pasted image 20240918090007.png]]

Com isso usamos o fake e random para criar cadastro de empresas fictícias:

O código cria e popula a tabela `CAD_EMPRESA` com registros fictícios, utilizando a biblioteca `Faker` para gerar dados realistas e a biblioteca `random` para selecionar aleatoriamente valores de uma lista. A função é configurável para inserir um número específico de registros, e as alterações são confirmadas no banco de dados após a inserção.

![[Pasted image 20240918090226.png]]

Criação da tabela DOMINIOS:

O código define um dicionário que associa domínios a responsáveis e utiliza uma função para inserir essas associações em uma tabela `DOMINIOS` em um banco de dados SQLite. A função `inserir_into_dominios` faz uso do dicionário para gerar e executar instruções SQL que adicionam registros à tabela, e confirma as alterações no banco de dados.

![[Pasted image 20240918090439.png]]

Criando a tabela PROGRAMAS:

O código define um dicionário que mapeia títulos de programas para identificadores de domínios e utiliza uma função para inserir esses dados na tabela `PROGRAMAS` de um banco de dados SQLite. A função `insert_into_programa` extrai informações do dicionário, executa instruções SQL para inserir cada programa na tabela e confirma as alterações no banco de dados.

![[Pasted image 20240918090609.png]]

Criando a tabela INSCRICAO: 

O código define a função `insert_into_inscricoes_programas` para gerar e inserir um número especificado de inscrições aleatórias na tabela `INSCRICOES` de um banco de dados SQLite. Ele seleciona aleatoriamente IDs de pessoas e programas, gera datas de inscrição dentro de um intervalo definido, e insere esses dados na tabela. Após a inserção, as alterações são confirmadas no banco de dados.

![[Pasted image 20240918090854.png]]

Criando a tabela PARTICIPANTE_PROGRAMA:

O código define a função `insert_into_programas_participante` para gerar e inserir um número especificado de associações entre programas e inscrições na tabela `PARTICIPANTE_PROGRAMA` de um banco de dados SQLite. Ele seleciona aleatoriamente IDs de programas e inscrições, verifica se a combinação já existe para evitar duplicações, e insere os dados na tabela apenas se a combinação não estiver presente. Após a inserção, as alterações são confirmadas no banco de dados.

![[Pasted image 20240918091104.png]]

Criando a tabela ONU_ODS:

O código define e executa a função `insert_into_onu_ods` para inserir dados na tabela `ONU_ODS`. A função utiliza uma lista de Objetivos de Desenvolvimento Sustentável (ODS) e insere cada item na tabela com um identificador único. Após a inserção dos dados, a função confirma as alterações no banco de dados e imprime uma mensagem de sucesso.

![[Pasted image 20240918091228.png]]

Criando tabela relacionando os programas com as ods , PROGRAMA_ODS:

O código realiza a associação entre programas e Objetivos de Desenvolvimento Sustentável (ODS) em um banco de dados SQLite. Primeiro, ele consulta e recupera IDs e títulos dos programas da tabela `PROGRAMAS`. Em seguida, define uma lista de IDs de ODS e usa uma função para inserir essas associações na tabela `PROGRAMA_ODS`. A função itera sobre os IDs dos programas e ODS, e para cada par, executa uma inserção na tabela. Após as inserções, confirma as alterações no banco de dados.

![[Pasted image 20240918091502.png]]

Criando uma tabela SERVICO: 

O código define e insere dados na tabela `SERVICO` de um banco de dados SQLite. Primeiro, uma lista de serviços é criada, contendo diferentes tipos de serviços oferecidos. A função `insert_into_servicos` é então utilizada para inserir cada serviço dessa lista na tabela `SERVICO`. Para cada serviço, um comando SQL `INSERT INTO` é executado, adicionando o nome do serviço à tabela. Após a inserção de todos os serviços, as alterações são confirmadas no banco de dados com `sqlite_conn.commit()`.

![[Pasted image 20240918091958.png]]

Criando a tabela AGENDAMENTO_SERVICO:

O código cria uma função chamada `insert_into_agendamento_servico` que insere registros fictícios de agendamentos de serviços em uma tabela de um banco de dados SQLite. A função realiza as seguintes etapas:

1. **Recuperação de Dados**: Obtém a lista de IDs de serviços e IDs de pessoas cadastradas no banco de dados.
2. **Definição de Intervalo de Datas**: Estabelece um período específico (de 15 de janeiro de 2024 a 1º de agosto de 2024) para os agendamentos.
3. **Geração de Registros**: Para um número especificado de registros (500 por padrão), seleciona aleatoriamente um serviço e uma pessoa e gera uma data e hora de agendamento dentro do intervalo definido.
4. **Inserção no Banco de Dados**: Insere esses dados na tabela de agendamentos de serviços.
5. **Confirmação das Alterações**: Salva as mudanças feitas no banco de dados.

A função é então executada para adicionar 500 registros de agendamento fictícios.

![[Pasted image 20240918092418.png]]

Criando a tabela LABORATORIO:

O código define um dicionário com nomes e descrições de diversos laboratórios e inclui uma função para inserir essas informações em uma tabela de banco de dados. A função extrai os nomes e descrições dos laboratórios do dicionário e, em seguida, insere cada um no banco de dados, confirmando a operação e imprimindo uma mensagem de sucesso após cada inserção. Finalmente, todas as alterações são confirmadas no banco de dados.

![[Pasted image 20240918092615.png]]

Criando a tabela de EQUIPAMENTO:

O código insere dados sobre equipamentos em um banco de dados. Ele usa um dicionário para mapear os nomes e descrições dos equipamentos e consulta a tabela de laboratórios para obter seus IDs. A função `inserir_equipamento()` adiciona cada equipamento à tabela `EQUIPAMENTO`, atribuindo-o a um laboratório com base na sua posição na lista e definindo sua disponibilidade de forma aleatória. Após a inserção, as mudanças são confirmadas no banco de dados.

![[Pasted image 20240918092842.png]]
![[Pasted image 20240918092913.png]]

Criando tabela AGENDAMENTO_INFRA:

O código associa aleatoriamente laboratórios e equipamentos a agendamentos de um serviço específico ("Laboratórios de Criação e Prototipagem"). Primeiro, ele busca os IDs dos agendamentos relacionados a esse serviço, bem como todos os IDs de laboratórios e equipamentos disponíveis. Em seguida, a função `inserir_agendamento_infra()` insere essas associações na tabela `AGENDAMENTO_INFRA`, vinculando cada agendamento a um laboratório e a um equipamento selecionados aleatoriamente.

![[Pasted image 20240918093315.png]]

Criando a tabela FORMULARIOS_FEEDBACK_PROGRAMAS:

O código insere dados fictícios na tabela `FORMULARIOS_FEEDBACK_PROGRAMAS`. Primeiro, ele recupera IDs das tabelas `INSCRICOES`, `CAD_PESSOA` e `DOMINIOS`. Em seguida, define a função `gerar_dados_feedback()`, que cria 100 registros de feedback. Para cada registro, o código seleciona aleatoriamente um ID de inscrição, pessoa e domínio, gera respostas fictícias para 9 perguntas e cria um nome e uma data para o formulário de feedback. Esses dados são então inseridos na tabela `FORMULARIOS_FEEDBACK_PROGRAMAS`, e as alterações são confirmadas no banco de dados.

![[Pasted image 20240918093804.png]]

Criando tabela Perguntas_Adicionais_Feedbacks:

Primeiramente, o código define uma lista de perguntas. Em seguida, a função `gerar_perguntas_adicionais()` é responsável por inserir essas perguntas no banco de dados. Para cada pergunta na lista, a função seleciona aleatoriamente um ID de domínio (presumivelmente obtido anteriormente). Em seguida, ela executa uma instrução SQL para inserir o ID do domínio e a pergunta na tabela `PERGUNTAS_ADICIONAIS_FEEDBACK_PROGRAMAS`. Após a inserção de todas as perguntas, as mudanças são confirmadas no banco de dados com um `commit`.

![[Pasted image 20240918094556.png]]
Criando a tabela Respostas_Formulários:

O código realiza a inserção de respostas simuladas em um banco de dados de feedback. Primeiro, ele recupera os IDs de inscrições, pessoas e perguntas adicionais. Em seguida, seleciona aleatoriamente metade dos participantes registrados. Para cada participante selecionado, o código obtém o formulário correspondente e gera respostas simuladas com base nas perguntas e suas descrições. Essas respostas são então inseridas no banco de dados, e as alterações são salvas.

![[Pasted image 20240918101353.png]]
![[Pasted image 20240918101410.png]]
Criando a tabela FEEDBACK _PERGUNTAS_INFRA:

O código define uma lista de perguntas relacionadas à infraestrutura de laboratórios e as insere em uma tabela de feedback. A lista de perguntas inclui tópicos como a qualidade dos equipamentos, adequação do espaço físico, e eficiência da equipe de suporte. A função `inserir_perguntas_infra` percorre essa lista e insere cada pergunta na tabela `FEEDBACK_PERGUNTAS_INFRAESTRUTURA` no banco de dados. Após inserir todas as perguntas, as alterações são salvas no banco de dados.

![[Pasted image 20240918101556.png]]

Criando a tabela Feedback_Perguntas_Infra:

O código realiza a coleta de IDs de pessoas, agendamentos e perguntas de infraestrutura a partir das tabelas correspondentes no banco de dados. Em seguida, define uma função para gerar respostas aleatórias para as perguntas sobre infraestrutura, com opções variando conforme o tipo de pergunta, como satisfação geral ou adequação dos equipamentos. A função `gerar_feedback_infraestrutura` insere 50 registros de feedback, associando aleatoriamente IDs de pessoas e agendamentos com respostas geradas para cada pergunta de infraestrutura. Finalmente, as alterações são salvas no banco de dados com o comando `sqlite_conn.commit()`.

![[Pasted image 20240918102130.png]]

## 4 - API

Este projeto implementa uma solução que integra uma API desenvolvida com **FastAPI** e uma aplicação web construída com **Streamlit**, permitindo o gerenciamento de dados em um banco de dados PostgreSQL de forma intuitiva e dinâmica.

A API FastAPI é responsável por gerenciar as operações no banco de dados, como a listagem de tabelas, consulta de dados e inserção de novos registros. Entre as rotas principais da API estão `/tables/`, que retorna as tabelas disponíveis, `/data/{table_name}/`, que consulta os dados de uma tabela específica, e `/insert/`, que permite a inserção de novos registros.

A conexão com o banco de dados é gerenciada por meio do **SQLAlchemy**, que também possibilita a execução das consultas e inserções de dados. Para garantir a eficiência do acesso, uma sessão de banco de dados (`SessionLocal`) é criada e corretamente fechada após cada operação.

A interface web é desenvolvida em Streamlit, oferecendo uma forma prática de interação com a API. O usuário pode:

- Visualizar as tabelas disponíveis.
- Aplicar filtros dinâmicos em colunas numéricas, de texto ou de data para uma análise mais precisa.
- Inserir dados diretamente em qualquer tabela, por meio de formulários gerados dinamicamente.

Toda a arquitetura é organizada em módulos separados, o que facilita a manutenção e a ampliação do projeto. O sistema é ideal para quem busca uma maneira simplificada de manipular dados sem a necessidade de utilizar comandos SQL diretamente, sendo útil tanto para inserção quanto para visualização e filtragem de dados.

Estruturação do projeto :

![[Pasted image 20240930100233.png]]
### Pasta APP :

![[Pasted image 20240930100534.png]]

Este projeto está dividido em diversos arquivos na pasta `app`, cada um com sua responsabilidade no sistema. Abaixo está um resumo das principais funções e componentes dos arquivos fornecidos:

1. **`database.py`**

- Define a conexão com o banco de dados PostgreSQL usando o SQLAlchemy.
- Utiliza variáveis de ambiente para obter o IP do Docker e cria a URL de conexão com o banco de dados.
- `engine`: Responsável por criar a engine do banco de dados PostgreSQL.
- `SessionLocal`: Função para criar sessões com o banco de dados, garantindo que operações como consultas e inserções sejam tratadas adequadamente.
- `Base`: Classe base do SQLAlchemy para definição dos modelos das tabelas.
- `get_db()`: Função geradora que cria e encerra a sessão do banco de dados de forma segura.

![[Pasted image 20240930100148.png]]

2. **`main.py` (API FastAPI)**

- **Rotas de API**:
    - **`/tables/`**: Retorna uma lista com os nomes das tabelas disponíveis no banco de dados.
    - **`/data/{table_name}/`**: Retorna os dados de uma tabela específica do banco de dados. Usa SQLAlchemy para carregar dinamicamente a tabela e consultar os dados.
    - **`/insert/`**: Insere dados em uma tabela especificada. Verifica se a tabela e as colunas existem, e, em seguida, realiza a inserção no banco.
- **Pydantic Model**:
    - `InsertData`: Define o modelo de dados que será enviado para a inserção no banco de dados. Inclui o nome da tabela (`table_name`) e os dados a serem inseridos (`data`).
![[Pasted image 20240930103531.png]]![[Pasted image 20240930103615.png]]

3. **`models.py`**

- Define o modelo `Inscricao` da tabela `inscricoes` no banco de dados.
- A tabela `inscricoes` contém as colunas:
    - `id_inscricao`: ID da inscrição, chave primária.
    - `id_programa`: ID do programa.
    - `id_pessoa`: ID da pessoa.
    - `data_inscricao`: Data da inscrição.
- O SQLAlchemy é utilizado para mapear essas colunas para o banco de dados.

 ![[Pasted image 20240930103819.png]]

### Pasta Streamlit_app :

A pasta `streamlit_app` é parte de um projeto que combina **Streamlit** e **FastAPI** para criar uma interface web interativa. Ela permite que os usuários visualizem, filtrem e insiram dados em um banco de dados de forma simples.

Os principais arquivos incluem ferramentas para filtrar dados (numéricos e textuais), listar e recuperar tabelas do banco, e inserir novos registros. A conexão com o banco de dados é gerida pelo SQLAlchemy, enquanto o **FastAPI** oferece rotas para manipulação de dados, que são utilizadas pela interface gráfica em **Streamlit**.

![[Pasted image 20240930104503.png]]

 1. **`apply_filters.py`**

- **Função**: Aplica filtros genéricos aos dados de uma tabela, combinando diferentes tipos de filtros, como numéricos e de texto, para refinar os resultados.
- **Descrição**: Este arquivo provavelmente importa os filtros específicos de `filter_numeric.py` e `filter_text.py`, combinando-os para filtrar os dados de uma tabela com base em múltiplos critérios.
- **Uso**: Centraliza a aplicação de todos os filtros disponíveis em uma função única. Útil quando é necessário aplicar filtros complexos em conjunto.

![[Pasted image 20240930105619.png]]

 2. **`filter_data.py`**

- **Função**: Define os filtros que podem ser aplicados aos dados, tanto numéricos quanto textuais.
- **Descrição**: Pode ser um arquivo central para armazenar a lógica de diferentes tipos de filtragem (numérica, textual, etc.). Provavelmente reutiliza as funções específicas de `filter_numeric.py` e `filter_text.py` para criar uma interface mais simples para aplicar filtros.
- **Uso**: Serve como ponto de partida para determinar os tipos de filtros que podem ser aplicados a uma tabela ou conjunto de dados.

![[Pasted image 20240930105657.png]]

 3. **`filter_numeric.py`**

- **Função**: Aplica filtros numéricos aos dados.
- **Descrição**: Este arquivo contém funções para filtrar dados com base em critérios numéricos, como intervalos de valores (por exemplo, filtrar valores maiores ou menores que um número, ou dentro de um intervalo específico).
- **Uso**: Filtra colunas que possuem dados numéricos, aplicando condições como “maior que”, “menor que” ou “entre” em colunas numéricas de uma tabela.

![[Pasted image 20240930105725.png]]

 4. **`filter_text.py`**

- **Função**: Aplica filtros baseados em texto aos dados.
- **Descrição**: Este arquivo contém funções para filtrar colunas textuais, por exemplo, buscando por palavras-chave ou strings específicas.
- **Uso**: Filtra colunas de texto, permitindo busca por palavras exatas ou expressões parciais (como buscas com `LIKE` em SQL).

![[Pasted image 20240930105824.png]]

 5. **`get_table_data.py`**

- **Função**: Recupera os dados de uma tabela específica.
- **Descrição**: Este arquivo contém a lógica para acessar o banco de dados e retornar todos os dados de uma tabela determinada. Provavelmente utiliza a função `read_table_data()` que já foi descrita em arquivos como o `main.py`.
- **Uso**: É usado quando é necessário obter os dados de uma tabela completa para exibição ou para filtragem.

![[Pasted image 20240930105940.png]]

 6. **`get_tables.py`**

- **Função**: Lista todas as tabelas disponíveis no banco de dados.
- **Descrição**: Contém funções que inspecionam o banco de dados e retornam a lista de tabelas existentes. Utiliza SQLAlchemy para inspecionar o esquema do banco de dados.
- **Uso**: É útil para gerar uma lista dinâmica de tabelas que podem ser selecionadas pelo usuário na interface do Streamlit, fornecendo as tabelas que estão disponíveis para visualização ou manipulação.

![[Pasted image 20240930110508.png]]
 7. **`insere.py`**

- **Função**: Insere dados em uma tabela do banco de dados.
- **Descrição**: Este arquivo contém a lógica para inserir novos registros em uma tabela específica. Ele pode validar as colunas e os dados antes de realizar a inserção no banco.
- **Uso**: Processa dados fornecidos pelo usuário e insere-os em uma tabela do banco de dados. Ele provavelmente é chamado quando o usuário submete novos dados através da interface.

![[Pasted image 20240930110543.png]]
![[Pasted image 20240930110631.png]]
 8. **`main.py`**

- **Função**: Arquivo principal da API FastAPI.
- **Descrição**: Define as rotas da API, como listar tabelas, ler dados de uma tabela e inserir novos dados. Conecta-se ao banco de dados usando SQLAlchemy e é responsável por fornecer os dados para a interface Streamlit.
- **Uso**: Serve como ponto de entrada da aplicação FastAPI. Todas as operações principais, como recuperação de dados, inserção e listagem de tabelas, são gerenciadas por este arquivo.

![[Pasted image 20240930110702.png]]
 9. **`url_base.py`**

- **Função**: Define a URL base de conexão com o banco de dados.
- **Descrição**: Contém a URL base que é usada para conectar-se ao banco de dados PostgreSQL. A URL pode ser montada dinamicamente com base no endereço IP do contêiner Docker ou outro ambiente de execução.
- **Uso**: Este arquivo é responsável por definir a conexão com o banco de dados, sendo utilizado em outros scripts, como `main.py`, para estabelecer a comunicação com o banco de dados.
![[Pasted image 20240930110747.png]]


### Arquivos complementares :

Este arquivo **Dockerfile** descreve a construção de uma imagem Docker para uma aplicação Python, que combina **FastAPI** e **Streamlit**, e utiliza o **Supervisor** para gerenciar múltiplos processos dentro do contêiner. Aqui está uma descrição detalhada de cada parte:

1. **Imagem base**:
    
    - A imagem base utilizada é o **Python 3.12.4** (`FROM python:3.12.4`), garantindo que o ambiente de execução tenha o Python instalado na versão especificada.
2. **Diretório de trabalho**:
    
    - Define o diretório de trabalho como `/app` (`WORKDIR /app`), onde os comandos e arquivos subsequentes serão executados e armazenados.
3. **Instalação de dependências**:
    
    - Copia o arquivo `requirements.txt` para o diretório de trabalho e executa o comando para instalar as dependências do projeto Python usando `pip` sem armazenar arquivos temporários (`--no-cache-dir`), economizando espaço no contêiner.
4. **Cópia do código da aplicação**:
    
    - Copia todos os arquivos da aplicação para o diretório de trabalho no contêiner (`COPY . .`).
5. **Instalação do Supervisor**:
    
    - O `Supervisor` é instalado para gerenciar e iniciar múltiplos processos dentro do contêiner (como FastAPI e Streamlit). O comando instala o Supervisor e limpa os caches para otimizar o espaço no contêiner.
6. **Configuração do Supervisor**:
    
    - O arquivo `supervisord.conf` (um arquivo de configuração do Supervisor) é copiado para o diretório apropriado (`/etc/supervisor/conf.d/`), onde define quais serviços serão gerenciados.
7. **Script de inicialização**:
    
    - O script `start.sh` é copiado para o diretório `/app` e recebe permissões de execução (`chmod +x`), tornando-o pronto para ser executado como ponto de entrada do contêiner.
8. **Exposição de portas**:
    
    - O contêiner expõe duas portas:
        - **8000** para a API FastAPI.
        - **8501** para a interface Streamlit.
9. **Comando final**:
    
    - O comando `CMD ["/app/start.sh"]` define o script `start.sh` como o ponto de entrada do contêiner, ou seja, será executado quando o contêiner iniciar, gerenciando os processos definidos pelo Supervisor (FastAPI e Streamlit).

Esse **Dockerfile** cria um ambiente completo e controlado para executar tanto o FastAPI quanto o Streamlit em paralelo dentro de um único contêiner.

![[Pasted image 20240930112124.png]]

O arquivo **LF_start.sh** é um script de inicialização em Bash, projetado para ser executado em um ambiente de contêiner Docker. Abaixo está uma descrição detalhada de suas funcionalidades:

1. **Shebang**:
    
    - A primeira linha (`#!/bin/bash`) indica que o script deve ser executado usando o interpretador Bash, garantindo que os comandos sejam interpretados corretamente.
2. **Execução do script `database.py`**:
    
    - O script chama `database.py` com um argumento que é passado como uma variável de ambiente (`$DOCKER_IP`). A variável `DOCKER_IP` deve conter o endereço IP do contêiner ou do serviço de banco de dados que o script `database.py` irá utilizar.
    - O símbolo `&` ao final do comando permite que o script `database.py` seja executado em segundo plano. Isso significa que o script continuará a executar os comandos subsequentes enquanto `database.py` é executado.
3. **Início do Supervisor**:
    
    - O comando `exec /usr/bin/supervisord -c /etc/supervisor/conf.d/supervisord.conf` inicia o **Supervisor**, que é um sistema de gerenciamento de processos. A opção `-c` especifica o caminho para o arquivo de configuração do Supervisor (`supervisord.conf`), que contém definições sobre quais processos devem ser gerenciados e como.

![[Pasted image 20240930112226.png]]

O arquivo **app_streamlit.py** é um script Python que serve como ponto de entrada para uma aplicação Streamlit. Aqui está uma descrição detalhada de suas funcionalidades:

1. **Importações**:
    
    - `from streamlit_app.url_base import BASE_URL`: Esta linha importa a constante `BASE_URL` do módulo `url_base` localizado na pasta `streamlit_app`. Essa constante pode ser utilizada para definir URLs base para chamadas de API ou para configuração da aplicação.
    - `from streamlit_app.main import main`: Esta linha importa a função `main` do módulo `main`, que provavelmente contém a lógica principal da aplicação Streamlit, incluindo a definição da interface do usuário e o controle de fluxo.
2. **Execução da Aplicação**:
    
    - `if __name__ == "__main__":`: Esta condição verifica se o script está sendo executado como o programa principal (ou seja, não está sendo importado como um módulo em outro script).
    - `main()`: Se a condição for verdadeira, a função `main()` é chamada, iniciando a execução da aplicação Streamlit.

![[Pasted image 20240930112345.png]]

O **requirements.txt** lista as dependências necessárias para o projeto Python, incluindo:

1. **fastapi**: Framework para construir APIs rápidas e eficientes.
2. **uvicorn**: Servidor ASGI para executar aplicações FastAPI.
3. **sqlalchemy**: Biblioteca para manipulação de bancos de dados com suporte a ORM.
4. **psycopg2-binary**: Adaptador para conectar-se a bancos de dados PostgreSQL.
5. **asyncpg**: Biblioteca assíncrona para interagir com PostgreSQL de forma otimizada.
6. **streamlit**: Ferramenta para criar aplicações web interativas e dashboards.
7. **requests**: Biblioteca para realizar requisições HTTP de maneira simples.

Essas bibliotecas são essenciais para o funcionamento eficiente da aplicação.

![[Pasted image 20240930112545.png]]

O **start.sh** é um script em Bash utilizado para inicializar a aplicação. Suas principais funcionalidades incluem:

1. **Execução do script `database.py`**: O script inicia o `database.py`, passando como argumento o IP do Docker (`DOCKER_IP`). Este processo é executado em segundo plano (`&`), permitindo que o script continue sua execução.
    
2. **Início do Supervisor**: Após a execução do script de banco de dados, o script utiliza o `supervisord` para gerenciar processos. O comando `exec` substitui o shell atual pelo processo do Supervisor, usando a configuração especificada em `/etc/supervisor/conf.d/supervisord.conf`.
    

Esse script é fundamental para garantir que a configuração do banco de dados e a gestão dos processos da aplicação sejam realizadas corretamente na inicialização.

![[Pasted image 20240930112646.png]]

O **supervisord.conf** é um arquivo de configuração para o Supervisor, que gerencia a execução de processos. Aqui está um resumo de suas principais seções e funcionalidades:

1. **Configuração do Supervisor**:
    
    - **nodaemon=true**: Esta opção permite que o Supervisor execute em primeiro plano, útil para facilitar o desenvolvimento e a depuração.
2. **Configuração do programa Uvicorn**:
    
    - **program
        
        **: Define um programa chamado `uvicorn` que executa a aplicação FastAPI.
        - **command**: Especifica o comando para iniciar o Uvicorn, incluindo o módulo da aplicação e as configurações de host e porta.
        - **directory**: Define o diretório de trabalho onde o comando será executado.
        - **autostart=true**: O programa será iniciado automaticamente quando o Supervisor for iniciado.
        - **autorestart=true**: O programa será reiniciado automaticamente em caso de falha.
        - **stderr_logfile** e **stdout_logfile**: Especificam os arquivos de log para erros e saídas padrão, respectivamente.
3. **Configuração do programa Streamlit**:
    
    - **program
        
        **: Define um programa chamado `streamlit` que executa a aplicação Streamlit.
        - **command**: Especifica o comando para iniciar o Streamlit, incluindo o arquivo da aplicação e as configurações de porta e endereço.
        - **directory**: Define o diretório de trabalho para o comando.
        - **autostart=true** e **autorestart=true**: Assim como o programa Uvicorn, o Streamlit será iniciado automaticamente e reiniciado em caso de falha.
        - **stderr_logfile** e **stdout_logfile**: Definem os arquivos de log para erros e saídas padrão.

Esse arquivo é essencial para garantir que os serviços da aplicação (FastAPI e Streamlit) sejam gerenciados de forma eficiente, com reinícios automáticos em caso de falhas e registro de logs para monitoramento.

![[Pasted image 20240930112800.png]]
