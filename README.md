# Exercício de Prototipagem - Sistema de Gestão de Processos Digitais (SGPD)

## Visão Geral

Este documento contém os artefatos de modelagem do Sistema de Gestão de Processos Digitais (SGPD), desenvolvido como parte da Experiência Prática da disciplina de Prototipagem de Sistemas Computacionais.

O sistema tem como objetivo centralizar e rastrear chamados internos, substituindo processos informais como e-mail, WhatsApp e papel.

---

## Diagramas

### Diagrama de Casos de Uso

Para visualizar o diagrama:

1. Acesse https://app.diagrams.net/
2. Clique em "Abrir diagrama existente"
3. Selecione o arquivo do diagrama
4. Visualize e edite conforme necessário

**Conteúdo do Diagrama de Casos de Uso:**

- Autenticação do sistema
- Tela Principal
- Acesso negado
- Chamados abertos
- Informações do chamado
- Meus chamados
- Puxar chamados abertos
- Chat

### Diagrama de Classes

**Arquivo:** diagrama-classes.drawio

---

## Classe: Usuario

| Campo | Tipo |
|-------|------|
| id | int |
| Email | string |
| Senha | string |
| Nome | string |
| Funcao | string |
| Criado_em | DateTime |
| Atualizado_em | DateTime |

**Métodos:**
- CadastrarUsuario()
- AlterarUsuario()
- ExcluirUsuario()
- AtivarDesativarUsuario()

---

## Classe: Chamado

| Campo | Tipo |
|-------|------|
| id | int |
| Usuario_id | int |
| Responsavel_usuario_id | int |
| Usuario_finalizado_id | int |
| Titulo | string |
| Descricao | string |
| Situacao | string (pendente, concluido) |
| Criado_em | DateTime |
| Atualizado_em | DateTime |

**Métodos:**
- AbrirChamado()
- DistribuirChamado()
- AtualizarChamado()
- FinalizarChamado()

---

## Classe: Chamado_chat

| Campo | Tipo |
|-------|------|
| id | int |
| Chamado_id | int |
| Usuario_id | int |
| Funcao_usuario | string |
| Mensagem | String |
| Criado_em | DateTime |

**Métodos:**
- EnviarMesagemChat()
- FinalizarChamado()

---

## Perfis de Acesso

| Perfil | Funcionalidades |
|--------|-----------------|
| Usuário | Criar chamado, Visualizar meus chamados, Acompanhar em tempo real, Avaliar atendimento |
| Gestor | Distribuir chamados, Visualizar todos chamados, Gerar relatórios e métricas |
| Técnico | Assumir chamados, Interagir via chat, Finalizar chamados com descrição da solução |

---

## Requisitos Funcionais (5)

| ID | Requisito | Prioridade |
|----|-----------|------------|
| RF01 | Sistema deve permitir login com controle de permissões por perfil | Alta |
| RF02 | Usuário deve criar chamado com descrição e indicar se é recorrente | Média |
| RF03 | Gestor deve visualizar e distribuir chamados pendentes para técnicos | Média |
| RF04 | Sistema deve permitir comunicação via chat entre usuário, gestor e técnico | Alta |
| RF05 | Técnico deve finalizar chamado registrando a solução aplicada | Alta |

---

## Requisitos Não Funcionais (3)

| ID | Categoria | Descrição |
|----|-----------|-----------|
| RNF01 | Usabilidade | Interface simples e intuitiva para todos os perfis |
| RNF02 | Desempenho | Sistema deve responder em até 2 segundos |
| RNF03 | Segurança | Login e controle de permissões por perfil |

---

## Falhas e Impactos Operacionais

| Falha | Atividade BPMN | Impacto |
|-------|----------------|---------|
| Fechar chamado sem ter solucionado | Encerramento de chamado | Atrasos de tarefas |

---

## Observações

Os diagramas representam o fluxo do Sistema de Gestão de Processos Digitais (SGPD) com os perfis: Usuário, Gestor e Técnico Responsável.

Após encerrado, o chamado permanece armazenado por 90 dias para consulta futura.