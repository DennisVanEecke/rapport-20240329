# Broncode voor rapport analyse FC - Versie 1.0

Omdat ik geen gebruik kan gemaakt worden van MS Office wordt dit rapport (i.e. `rapport.md`) gepubliceerd als PDF met de plugin ['Markdown preview enhanced'](https://shd101wyy.github.io/markdown-preview-enhanced/#/) van de tekst editor VSCode. Er word ook gebruik gemaakt van de Jupyter notebook plugin omdat deze technologie werd gebruikt om queries te maken. De aanbevolen extensies zijn opgenomen in de vscode settings.

Om te publiceren volstaat het om in het voorbeeld venster in VSCode rechts te klikken en 
dan 'Open in browser' te klikken. Dan kun je met de browser printen naar PDF.

De python code is het best beheersbaar indien je gebruik maakt van een virtual environment. De Python code gebruikt de SPARQLWrapper library en uiteraard Jupyterlab.

Voor de analyses en de queries word gebruik gemaakt van Jupyter notebook: De resultaten worden geprint als output of als een markdown bestand. Die kunnen worden overgenomen of gelinkt in het rapport.

Kopieer het bestand `datasource.py.template`, hernoem die naar `datasource.py` en vul de URL van het SPARQL endpoint in en de andere gegevens. Indien je niet over een username of password beschikt vul je gewoon `None` in.

Na het clonen installeer python virtual als je dat nog niet gedaan hebt met `pip install virtualenv`. Er werd gebruik gemaakt van python versie 3.11.

Dan best de volgende commando's uitvoeren:

`virtualenv venv` *Maak venv*

`source venv/bin/activate` *Activeer venv*

`pip install -r requirements.txt` *Installeer dependencies*

Dan kun je het Jupyter notebook openen en runnen in VSCode als je die editor gebruikt als je de queries voor het rapport wilt uitvoeren. Vergeet niet de kernel van de venv te kiezen voor Jupyter.

In Jupyter kun je de 'query jobs' aanpassen. Het laatste item in de list kun je gebruiken om de query aan of uit te zetten om tijd te besparen wanneer je de cellen opnieuw runt.
