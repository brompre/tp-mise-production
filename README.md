# tp-mise-production
TP pour cours mise en production

Il faut avoir la version python 3.7 d'installé.

# Créer son environnement virtuel si pas déjà fait
py -3.7 -m venv ../enA61-prod

# Pour activé depuis le répertoire tp-mise-production
source ../enA61-prod/Scripts/activate

# pour arrêter l'environnement virtuel
deactivate

# Dans l'env virutel si pas deja fait 
python -m pip install --upgrade pip
python -m pip install tox


cd packages/regression_model
# pour ne pas avoir de problème d'instllation de nouveau composants
# ajouter -r pour recreer l'env tox. EX tox -r -e regression_model
# des fois quand un nouveau composant doit être installé tox est en erreur.
# Environnement principal pour les tests du modèle
tox -r -e regression_model
# Environnement pour construire le package localement
tox -r -e install_locally

# ajout section ml_api pour flask car on ne veut pas avoir d'erreur de version de composant
# on laisse l'environnement virtuel clean avec tox et les env tox vont avoir les composants nécessaire pour le projet. 
# Obliger de forcer Jinja2==2.11.3 avec flask 1.0.2
tox -r -e ml_api