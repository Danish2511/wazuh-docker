FROM wazuh/wazuh-manager:4.7.3

# Install Postfix and required dependencies
RUN apt-get update && apt-get install -y postfix mailutils

# Configure Postfix
COPY ./postfix/main.cf /etc/postfix/main.cf
COPY ./postfix/sasl_passwd /etc/postfix/sasl_passwd
RUN postmap /etc/postfix/sasl_passwd
RUN chmod 400 /etc/postfix/sasl_passwd /etc/postfix/sasl_passwd.db

# Start Postfix service
CMD service postfix restart && tail -f /dev/null