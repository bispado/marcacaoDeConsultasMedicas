# README do Projeto de Agendamento Médico - Gustavo Bispo Cordeiro

**Projeto:** [https://github.com/bispado/marcacaoDeConsultasMedicas](https://github.com/bispado/marcacaoDeConsultasMedicas)
**Aluno:** Gustavo Bispo Cordeiro
**RM:** 558515
**Turma:** 2TDSPY

Este documento fornece uma visão geral das telas do aplicativo de agendamento médico, suas funcionalidades e tecnologias utilizadas. Este projeto foi desenvolvido como parte das atividades do curso, e esta documentação tem como objetivo detalhar a estrutura e o funcionamento do aplicativo.

## Visão Geral

O aplicativo foi desenvolvido utilizando React Native e Styled Components, oferecendo uma interface amigável e responsiva para diferentes tipos de usuários: administradores, médicos e pacientes. O aplicativo permite que os usuários agendem, confirmem ou cancelem consultas, além de gerenciar seus perfis e informações de usuários (para administradores).

O foco principal deste projeto é demonstrar a aplicação dos conhecimentos adquiridos no curso, incluindo o uso de React Native, estilização com Styled Components, gerenciamento de rotas com React Navigation, e persistência de dados local com AsyncStorage.

## Telas do Aplicativo

### 1. AdminDashboardScreen

-   **Descrição:** Painel administrativo para gerenciar consultas e usuários.
-   **Funcionalidades:**
    -   Visualização das últimas consultas agendadas.
    -   Confirmação ou cancelamento de consultas pendentes.
    -   Navegação para a tela de gerenciamento de usuários.
    -   Navegação para a tela de perfil do administrador.
    -   Função de logout.
-   **Componentes:**
    -   `Header`: Componente de cabeçalho reutilizável.
    -   `Button`: Componente do react-native-elements para botões estilizados.
    -   `ListItem`: Componente do react-native-elements para exibir informações da consulta.
-   **Estado:**
    -   `appointments`: Lista de consultas agendadas.
    -   `users`: Lista de usuários cadastrados.
    -   `loading`: Indicador de carregamento de dados.
-   **Observações:**
    -   Essa tela é acessível apenas para usuários com a role de "admin".
    -   Permite o gerenciamento centralizado das consultas e usuários do sistema.

### 2. CreateAppointmentScreen

-   **Descrição:** Tela para pacientes agendarem novas consultas.
-   **Funcionalidades:**
    -   Seleção de data e horário da consulta.
    -   Seleção do médico e especialidade.
    -   Agendamento da consulta com validação dos dados.
-   **Componentes:**
    -   `Header`: Componente de cabeçalho reutilizável.
    -   `Input`: Componente do react-native-elements para entrada de dados.
    -   `Button`: Componente do react-native-elements para botões estilizados.
    -   `DoctorList`: Componente para listar médicos disponíveis.
    -   `TimeSlotList`: Componente para listar horários disponíveis.
-   **Estado:**
    -   `date`: Data da consulta.
    -   `selectedTime`: Horário selecionado.
    -   `selectedDoctor`: Médico selecionado.
    -   `loading`: Indicador de carregamento durante o agendamento.
    -   `error`: Mensagem de erro, se houver.
-   **Observações:**
    -   A lista de médicos (`availableDoctors`) é estática e definida diretamente no componente. Em uma implementação real, essa lista seria carregada de um backend.
    -   Validações básicas são realizadas para garantir que todos os campos obrigatórios sejam preenchidos antes do agendamento.

### 3. DoctorDashboardScreen

-   **Descrição:** Painel do médico para visualizar e gerenciar suas consultas.
-   **Funcionalidades:**
    -   Visualização das consultas agendadas para o médico.
    -   Confirmação ou cancelamento de consultas pendentes.
    -   Navegação para a tela de perfil do médico.
    -   Função de logout.
-   **Componentes:**
    -   `Header`: Componente de cabeçalho reutilizável.
    -   `Button`: Componente do react-native-elements para botões estilizados.
    -   `ListItem`: Componente do react-native-elements para exibir informações da consulta.
-   **Estado:**
    -   `appointments`: Lista de consultas agendadas para o médico.
    -   `loading`: Indicador de carregamento de dados.
-   **Observações:**
    -   As consultas exibidas são filtradas com base no `doctorId` do usuário logado, garantindo que o médico visualize apenas suas próprias consultas.
    -   A funcionalidade de confirmar ou cancelar consultas permite o controle do médico sobre sua agenda.

### 4. HomeScreen

-   **Descrição:** Tela inicial do paciente para visualizar suas consultas agendadas.
-   **Funcionalidades:**
    -   Listagem de consultas agendadas.
    -   Navegação para a tela de criação de nova consulta.
    -   Atualização da lista de consultas (pull-to-refresh).
-   **Componentes:**
    -   `HeaderContainer` e `HeaderTitle`: Componentes para o cabeçalho da tela.
    -   `Button`: Componente do react-native-elements para botões estilizados.
    -   `FlatList`: Componente do React Native para listas otimizadas.
-   **Estado:**
    -   `appointments`: Lista de consultas agendadas para o paciente.
    -   `refreshing`: Indicador de atualização da lista.
-   **Observações:**
    -   A lista de médicos (`doctors`) é estática e utilizada para exibir informações do médico na tela.
    -   A tela utiliza o componente `FlatList` para renderizar a lista de consultas de forma eficiente, otimizando o desempenho.

### 5. LoginScreen

-   **Descrição:** Tela de login para os usuários acessarem o aplicativo.
-   **Funcionalidades:**
    -   Autenticação do usuário com email e senha.
    -   Navegação para a tela de registro de novo paciente.
-   **Componentes:**
    -   `Input`: Componente do react-native-elements para entrada de dados.
    -   `Button`: Componente do react-native-elements para botões estilizados.
-   **Estado:**
    -   `email`: Email do usuário.
    -   `password`: Senha do usuário.
    -   `loading`: Indicador de carregamento durante o login.
    -   `error`: Mensagem de erro, se houver.
-   **Observações:**
    -   A tela oferece exemplos de credenciais para facilitar o teste do aplicativo.
    -   A autenticação é simulada, e em uma implementação real, seria integrada a um sistema de autenticação robusto.

### 6. PatientDashboardScreen

-   **Descrição:** Painel do paciente para visualizar e gerenciar suas consultas.
-   **Funcionalidades:**
    -   Visualização das consultas agendadas para o paciente.
    -   Navegação para a tela de agendamento de nova consulta.
    -   Navegação para a tela de perfil do paciente.
    -   Função de logout.
-   **Componentes:**
    -   `Header`: Componente de cabeçalho reutilizável.
    -   `Button`: Componente do react-native-elements para botões estilizados.
    -   `ListItem`: Componente do react-native-elements para exibir informações da consulta.
-   **Estado:**
    -   `appointments`: Lista de consultas agendadas para o paciente.
    -   `loading`: Indicador de carregamento de dados.
-   **Observações:**
    -   As consultas exibidas são filtradas com base no `patientId` do usuário logado, garantindo que o paciente visualize apenas suas próprias consultas.

### 7. ProfileScreen

-   **Descrição:** Tela para visualizar o perfil do usuário.
-   **Funcionalidades:**
    -   Visualização dos dados do usuário (nome, email, função).
    -   Função de logout.
    -   Navegação para voltar à tela anterior.
-   **Componentes:**
    -   `Header`: Componente de cabeçalho reutilizável.
    -   `Button`: Componente do react-native-elements para botões estilizados.
-   **Estado:**
    -   Dados do usuário (obtidos do contexto de autenticação).
-   **Observações:**
    -   A tela exibe informações básicas do usuário, como nome, email e role.
    -   O avatar do usuário é um placeholder e pode ser substituído por uma imagem real.

### 8. RegisterScreen

-   **Descrição:** Tela de registro para novos pacientes criarem suas contas.
-   **Funcionalidades:**
    -   Criação de conta com nome, email e senha.
    -   Navegação para a tela de login após o registro bem-sucedido.
-   **Componentes:**
    -   `Input`: Componente do react-native-elements para entrada de dados.
    -   `Button`: Componente do react-native-elements para botões estilizados.
-   **Estado:**
    -   `name`: Nome completo do paciente.
    -   `email`: Email do paciente.
    -   `password`: Senha do paciente.
    -   `loading`: Indicador de carregamento durante o registro.
    -   `error`: Mensagem de erro, se houver.
-   **Observações:**
    -   A tela realiza validações básicas para garantir que todos os campos obrigatórios sejam preenchidos antes do registro.
    -   Após o registro bem-sucedido, o usuário é redirecionado para a tela de login.

### 9. UserManagementScreen

-   **Descrição:** Tela para administradores gerenciarem os usuários do sistema.
-   **Funcionalidades:**
    -   Listagem de usuários cadastrados.
    -   Exclusão de usuários.
    -   Navegação para adicionar novo usuário (funcionalidade não implementada).
-   **Componentes:**
    -   `Header`: Componente de cabeçalho reutilizável.
    -   `Button`: Componente do react-native-elements para botões estilizados.
    -   `ListItem`: Componente do react-native-elements para exibir informações do usuário.
-   **Estado:**
    -   `users`: Lista de usuários cadastrados.
    -   `loading`: Indicador de carregamento de dados.
-   **Observações:**
    -   Essa tela é acessível apenas para usuários com a role de "admin".
    -   A funcionalidade de adicionar novo usuário não foi implementada neste projeto.

## Tecnologias Utilizadas

-   **React Native:** Framework para construção de aplicativos mobile utilizando JavaScript e React.
-   **Styled Components:** Biblioteca para estilização de componentes React utilizando CSS-in-JS.
-   **React Navigation:** Biblioteca para gerenciamento de rotas e navegação entre telas.
-   **React Native Elements:** Conjunto de componentes de interface do usuário pré-estilizados.
-   **AsyncStorage:** API do React Native para armazenamento de dados localmente.
-   **Context API:** Para gerenciamento de estado global (autenticação do usuário).

## Notas Adicionais

-   O armazenamento de dados (consultas e usuários) é feito localmente utilizando AsyncStorage. Em um cenário real, seria recomendado utilizar um backend para persistência dos dados.
-   As telas utilizam um sistema de temas (`theme.js`) para manter a consistência visual do aplicativo.
-   O hook `useFocusEffect` é utilizado para carregar os dados quando as telas estão em foco, garantindo que os dados sejam atualizados sempre que o usuário retorna à tela.
-   Os componentes `DoctorList` e `TimeSlotList` foram criados para facilitar a seleção de médicos e horários na tela de agendamento.
-   A autenticação do usuário é simulada, utilizando AsyncStorage para persistir as informações do usuário logado.

## Desafios e Aprendizados

Durante o desenvolvimento deste projeto, enfrentei os seguintes desafios:

-   **Gerenciamento de Estado:** Utilizar o Context API para gerenciar o estado de autenticação do usuário e compartilhá-lo entre os componentes.
-   **Persistência de Dados:** Implementar o armazenamento de dados local com AsyncStorage, garantindo a persistência das informações entre as sessões.
-   **Estilização:** Utilizar Styled Components para criar componentes reutilizáveis e manter a consistência visual do aplicativo.
-   **Navegação:** Implementar a navegação entre as telas utilizando React Navigation, garantindo uma experiência de usuário fluida e intuitiva.

Através deste projeto, pude consolidar meus conhecimentos em React Native e aplicar as melhores práticas de desenvolvimento mobile. Além disso, aprendi a lidar com desafios como gerenciamento de estado, persistência de dados e estilização de componentes.
