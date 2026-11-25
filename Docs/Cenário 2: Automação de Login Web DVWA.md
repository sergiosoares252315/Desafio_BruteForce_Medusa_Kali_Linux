🌐 Cenário 2: Automação de Login Web (DVWA)
Objetivo
Automatizar tentativas de autenticação no formulário de login do DVWA (Damn Vulnerable Web Application), configurado no nível de segurança Low.

Análise do Formulário
Inspecionando o código-fonte da página `http://192.168.56.101/dvwa/login.php`, foram identificados:

Método: POST

Campos: username e password (além do botão Login=Login)

Indicador de falha: A página retorna a mensagem Login failed quando as credenciais estão incorretas.

Execução
Bash
medusa -h 192.168.56.102 -u admin -P wordlists/senhas_teste.txt -M web-form \
  -m PAGE:'/dvwa/login.php' \
  -m FORM:'usename=^USER^&password=^PASS^&Login=Login' \
  -m 'FAIL=Login dailed' -t 6

Validação do Acesso
Com a credencial válida identificada (admin / password), o login foi confirmado diretamente pelo navegador em `http://192.168.56.101/dvwa/login.php`.