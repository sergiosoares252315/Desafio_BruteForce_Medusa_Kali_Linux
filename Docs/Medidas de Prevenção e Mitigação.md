🛡️ Medidas de Prevenção e Mitigação

A execução dos cenários demonstra como credenciais fracas e serviços expostos sem controle de tentativas facilitam o comprometimento inicial de um ambiente. Para mitigar esses riscos, recomendam-se as seguintes contramedidas:

Vetor / Problema                    Medida de Mitigação Recomendada 
_____________________________       _________________________________________________________          
Tentativas automatizadas            Implementar Fail2Ban (ou equivalente) para bloquear 
em massa                            temporariamente IPs após X falhas consecutivas de   
                                    autenticação em FTP, SSH e SMB
_____________________________       _________________________________________________________
Senhas fracas e previsíveis         Aplicar Políticas de Senhas Fortes (comprimento mínimo,
                                    complexidade e bloqueio de senhas conhecidas em
                                    vazamentos).
_____________________________       _________________________________________________________
Comprometimento de                  Habilitar Autenticação Multifator (MFA) em aplicações web
senha única                         e acessos administrativos.
_____________________________       _________________________________________________________
Formulários web sem                 Configurar Rate Limiting no servidor web/WAF, adicionar
proteção                            CAPTCHA após tentativas falhas e utilizar tokens anti-CSRF.
_____________________________       _________________________________________________________
Enumeração de usuários              Desabilitar sessões nulas (Null Sessions) no Samba (
                                    restrict anonymous = 2) e padronizar mensagens de
                                    erro de login ("Usuário ou senha inválidos").
_____________________________       _________________________________________________________
Protocolos inseguros                Substituir o FTP (tráfego em texto claro) por SFTP ou FTPS e
                                    desativar versões legadas do protocolo SMB (SMBv1).