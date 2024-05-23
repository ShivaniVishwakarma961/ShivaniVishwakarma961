- 👋 Hi, I’m @Shivani Vishwakarma
pip install apscheduler
from datetime import datetime
from apscheduler.schedulers.blocking import BlockingScheduler

# Function to send notification
def send_birthday_notification():
    print("Happy Birthday! 🎉")

# Set up scheduler
scheduler = BlockingScheduler()

# Assume birthday is on May 23, schedule notification
birthday = datetime(datetime.now().year, 5, 23)
scheduler.add_job(send_birthday_notification, 'date', run_date=birthday)

# Start the scheduler
scheduler.start()
import smtplib
from email.mime.text import MIMEText

def send_email(subject, message, to_email):
    # Email configuration
    sender_email = "your-email@example.com"
    password = "your-email-password"

    # Setup the MIME
    msg = MIMEText(message)
    msg['From'] = sender_email
    msg['To'] = to_email
    msg['Subject'] = subject

    # Sending the email
    server = smtplib.SMTP('smtp.example.com', 587)
    server.starttls()
    server.login(sender_email, password)
    server.sendmail(sender_email, to_email, msg.as_string())
    server.quit()

send_email("Happy Birthday!", "Wishing you all the best today!", "friend@example.com")
