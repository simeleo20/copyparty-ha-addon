# Usa l'immagine Docker di base
FROM copyparty/ac:latest

# Copia lo script di avvio
COPY rootfs/ /

# !!! NUOVA CORREZIONE: Installa 'jq' (necessario per leggere config.json)
RUN apk add --no-cache jq

# Correzione Permessi: Aggiunge i permessi di esecuzione allo script di avvio.
RUN chmod +x /usr/bin/run

# Aggiungi un layer per creare il link simbolico prima dell'esecuzione
# Questo fa in modo che il percorso di lavoro predefinito (/w) punti al punto
# dove il Supervisore di HA mappa i tuoi file (/share)
RUN ln -sf /share /w

# L'ENTRYPOINT DEVE essere il nostro script 'run', 
# in modo che venga eseguito come processo principale.
ENTRYPOINT ["/usr/bin/run"]

# Non è necessario un CMD esplicito.