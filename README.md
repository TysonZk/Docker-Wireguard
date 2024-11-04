# Prérequis Docker et Docker Compose installés sur votre serveur.
apt install docker.io
sudo curl -L "https://github.com/docker/compose/releases/download/v2.20.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
pour vérifier docker-compose --version


Istallation

# Étape 1 : Cloner le dépôt

Dans le usr ou root
mkdir -p wireguard
cd wireguared
git clone https://github.com/TysonZk/Docker-Wireguard.git

# Étape 2 : Modifier le fichier docker-compose.yml 
Modifiez le fichier docker-compose.yml pour configurer les variables d’environnement nécessaires :  

Nano docker-compose.yml 

SERVERURL : Spécifiez votre IP publique ou domaine.
PEERDNS : Facultatif. Définissez-le à 8.8.8.8 (Google) ou 1.1.1.1 (Cloudflare) pour le DNS.
PEERS : Nombre de clients que vous souhaitez configurer (par défaut : 1).
Exemple :

# Étape 3 : Démarrer le serveur WireGuard
Pour lancer le serveur, exécutez :
docker-compose up -d

# Étape 4 : Récupérer les configurations clients
Après le démarrage du serveur, les fichiers de configuration des clients seront générés automatiquement dans le répertoire ./config. Vous les trouverez dans des sous-dossiers nommés peer1, peer2, etc., selon le nombre de pairs spécifié.

Pour accéder au fichier de configuration d'un client spécifique :

cd config/peer1  # Remplacez "peer1" par le numéro du pair souhaité


# Variables d'Environnement
PUID : ID de l'utilisateur (par défaut : 1000)
PGID : ID de groupe (par défaut : 1000)
TZ : Fuseau horaire (exemple : Europe/Paris)
SERVERURL : Votre IP publique ou domaine
SERVERPORT : Port pour WireGuard (par défaut : 51820)
PEERS : Nombre de configurations client à générer (par défaut : 1)
PEERDNS : Serveur DNS à utiliser (ex : 8.8.8.8 pour Google DNS)

# Commandes Utiles
Démarrer WireGuard : docker-compose up -d
Arrêter WireGuard : docker-compose down
Voir les logs : docker-compose logs -f
