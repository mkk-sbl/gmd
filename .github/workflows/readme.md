continous-integration.yml

definiert einen Workflow für GitHub-Aktion.
 
Diese Aktion wird ausgelöst, wenn ein Ereignis im Repository eintritt, z. B. ein Push zum Hauptzweig oder ein Pull-Request zum Hauptzweig, und Änderungen an Dateien im Verzeichnis input/ vorgenommen werden.

Der Workflow besteht aus zwei Jobs: 'convert-files' und 'tag-wip-rolling-release#, die auf der neuesten Ubuntu-Version laufen.

Der Job convert-files checkt das Repository aus, lädt eine Datei namens xml2gmd herunter, macht sie ausführbar, führt sie aus, um XML-Dateien in GMD-Dateien zu konvertieren, und überträgt die Änderungen mit einer bestimmten Übertragungsnachricht und Autoreninformationen.

Der Job tag-wip-rolling-release checkt das Repository aus und erstellt ein Git-Tag namens wip mit der Meldung "rolling: work in progress" und erzwingt die Veröffentlichung des Tags. Dieser Job hängt von der Fertigstellung des Jobs convert-files ab.
