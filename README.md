## Projeto Móvel Green Keeper: Diário de Plantas e Lembretes de Rega

Projeto da disciplina de Programação de Dispositivos Móveis com React Native + Expo (foco em Android).

Orientador: Prof. Luiz Gustavo Turatti

A solução compartilhada neste repositório consiste no desenvolvimento de uma plataforma móvel para auxiliar cuidadores de plantas domésticas a gerenciar ciclos de rega e combater o esquecimento através do uso de notificações programadas (recurso nativo). Implementa as operações CRUD (Create, Read, Update, Delete) com persistência em tempo real.

# Equipe do projeto

202302380999 - Lucas Olimpio Jardim

202303691289 - Ellen de Souza Ribeiro Jardim


# Sumário

1. Visão Geral e Problemática

2. Arquitetura e Requisitos

3. Configuração de Acesso aos Dados (Firebase)

4. Estrutura do Projeto

5. Instalando Dependências

6. Executando o Projeto

7. Telas do Projeto

<a id="visao-geral"></a>


## 1. Visão Geral e Problemática

O Green Keeper resolve a problemática sociocomunitária da perda de plantas por rega inadequada. A solução técnica envolve a aplicação de três pilares:

CRUD e Persistência: O usuário cadastra e gerencia suas plantas.

Lógica de Rega: O sistema calcula a nextWatering com base no waterIntervalDays.

Recurso Nativo: O sistema agendada uma Notificação Push para a data e hora da próxima rega.

<a id="requisitos"></a>




## 2. Arquitetura e Requisitos

|Requisito                |    Tecnologia                         |    Observação                                                 |
|-------------------------|---------------------------------------|---------------------------------------------------------------|
|Plataforma               |    React Native + Expo                |    Desenvolvimento Cross-Platform.                            |
|Gerenciador de Estado    |    React Hooks (useState, useEffect)  |    Para gerenciamento local e de dados.                       |
|Navegação                |    React Navigation                   |    Navegação em formato Stack (Home, Detalhes, Cadastro).     |
|Persistência / Backend   |    Firebase Firestore                 |    Base de Dados NoSQL e Sincronização em Tempo Real (BaaS).  | 
|Recurso Nativo           |    expo-notifications                 |    Implementação do lembrete de rega.                         |


🔧 Dependências Essenciais:

 -@react-navigation/native

 -@react-navigation/stack

 -firebase

 -expo-notifications



## 3. 🔐 Configuração de Acesso aos Dados (Firebase) <a id="acesso-dados"></a>

O projeto utiliza o Firebase Firestore para persistência de dados.

Banco de dados: Firebase Firestore (NoSQL, em nuvem).

Coleção Principal: Os dados são armazenados na coleção privada do usuário:
/artifacts/{__app_id}/users/{userId}/plants

 Estrutura de um Documento 'Planta':

| Campo             |     Tipo             |    Descrição                                             |
|-------------------|----------------------|----------------------------------------------------------|
|id                 |   string (doc ID)    |   Identificador único.                                   |
|name               |   string             |   Nome da planta (ex: Jibóia).                           | 
|species            |   string             |   Nome da espécie (opcional).                            |
|lastWatered        |   timestamp          |   Data da última rega.                                   | 
|nextWatering       |   timestamp          |   Próxima data de rega calculada (para Notificação).     |
|waterIntervalDays  |   number             |   Intervalo em dias (ex: 7).                             | 

 
Acesso: O projeto utiliza o __initial_auth_token e __firebase_config para autenticar o usuário anonimamente e garantir o acesso seguro aos dados no Firestore, conforme as diretrizes acadêmicas.





## 4. 📁 Estrutura do projeto: <a id="estrutura"></a>

A estrutura de pastas segue as melhores práticas para modularizar o desenvolvimento React Native:

  DiárioDePlantas/
  
   ├── src/
   |   |
   │   ├── components/       # Elementos reutilizáveis (Cards, Inputs)
   |   |
   │   ├── screens/          # As telas da sua navegação (Home, Details, NewPlant)
   |   |
   │   ├── services/         # Lógica de negócio: firebase.js e notifications.js
   |   |
   │   └── navigation/       # Configuração do React Navigation
   |
   ├── App.js                # Componente principal que gerencia a navegação
   |
   ├── package.json
   |
   └── app.json              # Configurações do Expo






## 5. 📦 Instale os requisitos do projeto: <a id="instalacao"></a>

Instruções para instalação em um computador com Windows 11 (adaptável para Linux/macOS):

Instalar Node.js e Expo CLI:

npm install -g expo-cli


Clonar o Repositório:

git clone [LINK DO SEU REPOSITÓRIO]
cd DiárioDePlantas


Instalar as Dependências do Projeto:

npm install
 OU
yarn install


Certifique-se de que as dependências essenciais (firebase, @react-navigation/stack, expo-notifications) estão listadas em package.json.

Instalar o Aplicativo Expo Go:
Baixe o aplicativo Expo Go em seu dispositivo móvel para testar o projeto.

ExpoGo (Google Play Store)

ExpoGo (Apple App Store)



## 6. 🚀 Execute o projeto: <a id="execucao"></a>

Inicie o servidor de desenvolvimento do Expo:

npx expo start





Execute no Dispositivo Móvel:
Use o aplicativo Expo Go para escanear o código QR que aparecerá no terminal ou no navegador para carregar o aplicativo em seu celular.
