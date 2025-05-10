import smtplib
from email.mime.text import MIMEText

# Configurações do servidor de email (trocar pelos seus dados)
sender_email = "seu_email@gmail.com"
receiver_email = "destinatario@gmail.com"
password = "sua_senha"  # ATENÇÃO: Não armazenar senhas diretamente no código!

# Detalhes do email
subject = "Assunto do Email"
body = "Corpo do email."

# Cria o objeto de mensagem
msg = MIMEText(body, "plain")
msg["Subject"] = subject
msg["From"] = sender_email
msg["To"] = receiver_email

# Conecta-se ao servidor SMTP e envia o email
try:
    with smtplib.SMTP_SSL("smtp.gmail.com", 465) as server:  # Usar SMTP_SSL para segurança
        server.login(sender_email, password)
        server.send_message(msg)
    print("Email enviado com sucesso!")
except Exception as e:
    print(f"Erro ao enviar o email: {e}")
