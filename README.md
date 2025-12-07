# tp-mise-production
TP pour cours mise en production

Il faut avoir la version python 3.7 d'installé.

py -3.7 python -m venv ../enA61-prod
py -3.7 -m venv ../enA61-prod

# Pour activé depuis le répertoire tp-mise-production
source ../enA61-prod/Scripts/activate

# pour arrêter l'environnement virtuel
deactivate

# Dans l'env virutel si pas deja fait 
python -m pip install --upgrade pip
python -m pip install tox


cd packages/regression_model