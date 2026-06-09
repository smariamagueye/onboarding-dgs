FROM debian:stable-slim
RUN mkdir -p /app/data
RUN echo "Fichier important de l'application - NE PAS SUPPRIMER" > /app/data/donnees_app.txt
RUN mkdir -p /app/logs
RUN dd if=/dev/zero of=/app/logs/debug_old.log bs=1M count=200
RUN echo '#!/bin/sh' > /app/run.sh && \
    echo 'echo "Tentative d écriture par l application..."' >> /app/run.sh && \
    echo 'echo "$(date) ligne de log" >> /app/logs/app.log && echo "OK : l application a pu écrire." || echo "ECHEC : impossible d écrire."' >> /app/run.sh && \
    chmod +x /app/run.sh
CMD ["sleep", "infinity"]

