FROM oraclelinux:8.8 AS builder
WORKDIR /app

# seems to speed things up
ENV LANG=C.UTF-8
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ENV PATH="/venv/bin:$PATH"

COPY requirements-live.txt .

ARG SSH_PRIVATE_KEY

RUN  \
     python3.8 -m venv /venv && \
     pip install --no-cache-dir -r requirements-live.txt

#######
# Final Image
#

FROM oraclelinux:8.8  AS app

WORKDIR /app


ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ENV PIP_DISABLE_PIP_VERSION_CHECK=1
ENV PATH="/venv/bin:$PATH"
ENV PYTHONPATH /app/src

COPY crontab /etc/cron.d/run-analyzer

RUN \
     dnf module install python38 


# Apply the Crontab
RUN chmod 0644 /etc/cron.d/run-analyzer && crontab /etc/cron.d/run-analyzer

# Start the Cron service
CMD ["crond", "-f"]


COPY --from=builder /venv /venv
COPY . .