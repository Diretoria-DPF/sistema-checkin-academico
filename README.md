# 🏛️ Sistema de Check-in Inteligente (Arquitetura Decoupled)

Este é um projeto de engenharia de software desenvolvido para resolver gargalos operacionais em portarias de eventos acadêmicos, eliminando filas, erros de digitação e fraudes através da automação por QR Code.

O sistema opera em uma **arquitetura híbrida e Serverless**:
* **Frontend (Apresentação):** Hospedado estaticamente no GitHub Pages (SPA em HTML/JS).
* **Backend (Regras de Negócio e Banco de Dados):** Construído via Google Apps Script (GAS), transformando o Google Sheets em uma API RESTful privada.

## 🔬 O Problema vs. A Solução

**O Cenário Tradicional:** O controle de presença em aulas abertas e ligas acadêmicas depende de listas de papel ou formulários estáticos, gerando gargalos, perda de dados e falta de controle de acesso simultâneo.

**A Engenharia da Solução:**
Desenvolvi uma aplicação de **Interface Dupla (Dual-Mode SPA)** em um único arquivo de distribuição.
1. **Face Pública:** O usuário gera sua credencial digital. O QR Code gerado atua como um *Token*.
2. **Face Restrita (Terminal):** Autenticada via backend. O fiscal utiliza o leitor de QR Code integrado na aplicação web para extrair a matrícula, consultar o banco de dados, verificar regras de fraude e carimbar a presença em poucos segundos.

## 🛡️ Camadas de Segurança Implementadas

* **Separação de Preocupações (Decoupled Architecture):** Nenhuma regra de validação ou senha reside no código público (Frontend). Todas as checagens ocorrem na nuvem.
* **Token Dinâmico anti-fraude:** O sistema cruza o Evento Ativo com a Matrícula, impedindo acessos duplicados.
* **Proteção de Iframe Bypass:** Migração do frontend para um domínio independente, contornando políticas de restrição de câmera de navegadores móveis e sandboxes.

## 🚀 Como testar a aplicação

O frontend está hospedado e vivo no GitHub Pages.
1. Acesse o portal.
2. Simule a criação de um cadastro inserindo uma matrícula genérica. O sistema retornará uma credencial visual instantaneamente.
3. *Nota:* A interface administrativa (Modo Fiscal) requer credenciais de acesso operacionais da diretoria da instituição onde o sistema foi implantado.

---
**Autoria:** Daniel Pires Francisco  
**Contexto de Aplicação:** Solução desenvolvida para a rotina de gestão universitária (LAIFT).
