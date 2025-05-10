import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

# Configurações do email
smtp_server = 'smtp.gmail.com'
smtp_port = 587
email_remetente = 'seuemail@gmail.com'
senha = 'sua_senha'  # Substitua pela sua senha ou senha de app

# Dados do destinatário
email_destinatario = 'destinatario@exemplo.com'

# Criando a mensagem
assunto = 'Assunto do Email'
corpo_mensagem = 'Olá! Este é um email enviado automaticamente usando Python.'

# Montando o email
mensagem = MIMEMultipart()
mensagem['From'] = email_remetente
mensagem['To'] = email_destinatario
mensagem['Subject'] = assunto

# Anexando o corpo do email
mensagem.attach(MIMEText(corpo_mensagem, 'plain'))

try:
    # Conectando ao servidor SMTP
    server = smtplib.SMTP(smtp_server, smtp_port)
    server.starttls()  # Inicia a conexão segura
    server.login(email_remetente, senha)
    # Enviando o email
    server.send_message(mensagem)
    print('Email enviado com sucesso!')
except Exception as e:
    print(f'Ocorreu um erro ao enviar o email: {e}')
finally:
    server.quit()
