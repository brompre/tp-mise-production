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
# on install tox 3 car sinon plusieurs problème de version.
# pas nécessaire d'installer TOX si on execute dans l'environnement
python -m pip install "tox<4"

cd packages/regression_model

# AVEC TOX
# pour ne pas avoir de problème d'instllation de nouveau composants
# ajouter -r pour recreer l'env tox. EX tox -r -e regression_model
# des fois quand un nouveau composant doit être installé tox est en erreur.
# Environnement principal pour les tests du modèle
tox -r -e regression_model
# Environnement pour construire le package localement
tox -r -e install_locally

# Directement dans environnement virtuel
python -m pip install --upgrade pip
python -m pip install -e .

# pour executer l'api 
# Aller dans le répertoire ml_api
pip install -r requirements.txt
python run.py

# Ouvrir un 2e terminal pour executer les tests de l'api
# Il faut être dans son environnement (virtuel?) et aller dans répertoire ml_api
python -m pytest tests
