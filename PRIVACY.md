# Política de Privacidade — Concordia ERP & Concordia MCP

**Última atualização:** 19 de novembro de 2026  
**Controlador:** Immaculata Digital (`concordiaerp.com`)  
**Contato / Encarregado (DPO):** contato@concordiaerp.com

---

## 1. Escopo
Esta Política de Privacidade descreve como o **Concordia ERP** e o servidor oficial **Concordia MCP (`https://mcp.concordiaerp.com/mcp`)** coletam, utilizam, armazenam e protegem os dados quando você conecta um agente de Inteligência Artificial (como Claude, Google Antigravity, OpenAI Codex, Cursor ou OpenCode) à sua conta.

## 2. Dados Acessados pelo Servidor MCP
O **Concordia MCP** atua exclusivamente como um gateway autenticado entre o agente de IA autorizado por você e a API oficial do Concordia ERP (`api-concordia.concordiaerp.com`):
- **Isolamento Multi-Tenant:** todas as requisições são estritamente isoladas ao seu `tenant_id`.
- **Escopo por Usuário:** o token emitido via OAuth 2.1 (`/integracoes/conectar-mcp`) herda somente as permissões que o seu usuário já possui nos Grupos de Acesso do Concordia ERP.
- **Rotas Administrativas Bloqueadas:** operações sensíveis de gestão de usuários, grupos de acesso e tenants permanecem bloqueadas por padrão na *Hard Denylist* de tokens.

## 3. Armazenamento e Retenção
- O servidor **Concordia MCP (`mcp.concordiaerp.com`) é stateless**: ele **não armazena** o conteúdo das suas conversas, prompts, produtos, pedidos, clientes ou respostas da API em banco de dados próprio.
- **Logs operacionais mínimos:** para fins de segurança, auditoria e prevenção contra abuso (*rate limiting*), registramos apenas metadados técnicos (timestamp, método RPC, nome da tool chamada, prefixo mascarado do token, status HTTP e latência) no Google Cloud Logging. Nenhum dado pessoal (PII) ou corpo de requisição é gravado nos logs.
- **Tokens:** tokens de acesso são armazenados na base do Concordia ERP exclusivamente em formato de hash criptográfico irreversível.

## 4. Compartilhamento com Terceiros (Agentes de IA)
Ao autorizar a conexão MCP, os dados retornados pelas ferramentas que você solicitar serão enviados ao cliente/provedor de IA que você escolheu conectar (por exemplo, Anthropic, Google ou OpenAI), sujeitos às respectivas políticas de privacidade desses provedores. O Concordia ERP não vende nem compartilha seus dados com terceiros para fins publicitários.

## 5. Seus Direitos (LGPD — Lei nº 13.709/2018)
Você pode, a qualquer momento:
- **Revogar o acesso imediatamente** em **Integrações → API Tokens** no Concordia ERP.
- **Restringir permissões** específicas do token MCP gerado.
- Solicitar confirmação de tratamento, acesso, correção ou eliminação de dados pelo e-mail `contato@concordiaerp.com`.

## 6. Segurança
Todas as comunicações ocorrem exclusivamente via HTTPS/TLS, com autenticação OAuth 2.1 + PKCE (`S256`), cabeçalhos de segurança (`Helmet`), proteção contra *open redirect* e limitação de taxa (*rate limiting*).
