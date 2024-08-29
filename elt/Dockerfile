FROM python:3.8-slim

# Add PostgreSQL APT repository
RUN apt-get update && apt-get install -y wget gnupg2 lsb-release && \
    echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" | tee /etc/apt/sources.list.d/pgdg.list && \
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - && \
    apt-get update && apt-get install -y postgresql-client-16

# Copy the ELT script into the container
COPY elt_script.py .

# Run the script
CMD ["python", "elt_script.py"]

COPY ./entrypoint.sh /usr/local/bin/docker-php-entrypoint
RUN chmod +x /usr/local/bin/docker-php-entrypoint
