# Usa l'immagine Docker di base
FROM copyparty/ac:latest

# Copia lo script di avvio
COPY rootfs/ /

# Aggiungi un layer per creare il link simbolico prima dell'esecuzione
# (Questo può essere fatto anche nello script 'run', ma è più pulito qui)
# Questo fa in modo che il percorso di lavoro predefinito (/w) punti al punto
# dove il Supervisore di HA mappa i tuoi file (/share)
RUN ln -sf /share /w

# L'ENTRYPOINT originale verrà sovrascritto dal nostro script 'run'

# Imposta il comando di avvio come lo script 'run' (già fatto nel 'run')
ENTRYPOINT ["/usr/bin/run"]