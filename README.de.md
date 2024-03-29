# GenieBuiltLifeProto

[![en](https://img.shields.io/badge/lang-en-red.svg)](README.md)
[![Gitpod Ready-to-Code](https://img.shields.io/badge/Gitpod-Ready--to--Code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/Actuarial-Sciences-for-Africa-ASA/GenieBuiltLifeProto)

![Work in Progress](docs/assets/wip.png)

## [Installation und Start](#3-installation-und-start)

# Projekt GenieBuiltLifeProto
Bei diesem Projekt handelt es sich um einen Versuch, eine Grundlage für ein Open Source System zur Verwaltung von Lebensversicherungen durch einen Versicherer zu erstellen.

## 1. Entwurfsziele

dieses Projekts sind:

* performante und hoch skalierende  Web App zur* Dialogbearbeitung von Versicherungsverträgen und
* Bereitstellung von Services für den Betrieb
* Lauffähigkeit auf Laptops wie auf Servern
* Nutzung von Cloud Entwicklungsumgebungen 
* Nutzung von Kooperationsplattformenin der Cloud
* Produkt-agnostisches Verwaltungssystem, d.h. maximale Kapselung produktspezifischen Wissens in produktspezifischen Komponenten
  * Rechnungsgrundlagen
  * Tariffunktionen
  * Metadaten tariflicher Funktionen zur Nutzung in Schnittstellen für Dialoge und Services.
  * Steuerung und Validierung von Eingaben für produktspezifische Geschäftsprozesse
* Verwendung einer aktuarsfreundlichen Entwicklungsumgebung hinsichtlich Programmiersprache und vorhandenen Bibliotheken
* Verwendung eines möglichst kohärenten Anwendungs-Stacks, der Tests über alle Ebenen von aktuariellen Funktionen über Persistenz bis zum Browser unterstützt, d.h. kein Umgebungsbruch, zwischen aktuarieller Produktentwicklung von und Entwicklung des Verwaltungssystems.
* Revisionssichere Speicherung von Verträgen durch bitemporale Persistierung

## 2. Funktionsumfang des Prototyps

### 2.1 Funktionsumfang API

Bitemporale CRUD- Aktionen für das gesamte Datenmodell.

### 2.2 Funktionsumfang WebUI

### 2.2.1 Funktionsbereich Search Contracts

#### Anzeige einer Liste von Vertrags-IDs.

<details >
<summary>screenshot: Contracts tab</summary>
<p>
<img src="docs/images/image1.png" alt="Contracts">
</p>
</details>
Anklicken wechselt in die Anzeige der neuesten Vertragsversion.

### 2.2.2 Funktionsbereich Contract Version

#### Anzeige / Bearbeitung von Vertragsversionen.

Das Bearbeiten erfordert einen aktiven Workflow (Transaktion). Dieser entsteht durch Anlegen eines neuen Vertrags, oder durch Eröffnen einer Vertragsmutation.

Ohne geladenen Vertrag wird der Button zum Anlegen eines Vertrages angezeigt.
<details >
<summary>screenshot: Contract version: no contract loaded</summary>
<p>
<img src="docs/images/image2.png" alt="Contracts">
</p>
</details>
Wurde ein unbearbeiteter Vertrag in der Suche ausgewählt worden, erscheint der Button zum Eröffnen einer Mutation.
<details >
<summary>screenshot: Contract version: contract immutable</summary>
<p>
<img src="docs/images/image4.png" alt="Contracts">
</p>
</details>
In beiden Fällen muss zur Eröffnung eines Workflows der Gültigkeitsbeginn angeben werden.
<details >
<summary>screenshot: Contract version: open contract workflow</summary>
<p>
<img src="docs/images/image3.png" alt="Contracts">
</p>
</details>
Danach erscheint der Vertrag als in Bearbeitung. 
<details >
<summary>screenshot: Contract version: contract mutable</summary>
<p>
<img src="docs/images/image6.png" alt="Contracts">
</p>
</details>
<details >
<summary>screenshot: Contract search: mutable contracts shown in red</summary>
<p>
<img src="docs/images/image6a.png" alt="Contracts">
</p>
</details>

Dieser Zustand bleibt erhalten bis

* der Workflow abgebrochen (rollback) oder
* vollendet wird (commit)
* Weitere workflow-bezogene Kommandos bieten
  * Kellern des Änderungsstandes (push)
  * Zurückholen des Änderungsstandes (pop)
  * Persistieren des Änderungsstandes (persist). Nach dem Persistieren 
ist der Ändderungskeller leer.

<details >
<summary>screenshot: Contract version: Workflow Kommandos</summary>
<p>
<img src="docs/images/image7.png" alt="Contracts">
</p>
</details>
<br>

### 2.2.1 Funktionsbereich Contract Version - contract partners

Anklicken öffnet den Abschnitt zur Anzeige / Bearbeitung von Vertragspartnerbeziehungen.
<details >
<summary>screenshot: Contract version: contract partners</summary>
<p>
<img src="docs/images/image8.png" alt="Contract partners">
</p>
</details>

Wenn der Vertrag mutierbar ist

* Auswahl einer Vertragspartnerrolle und
* eines Partners
  
aktivieren den Button zum Einfügen einer neuen Partnerbeziehung].

<details >
<summary>screenshot: Contract version: Auswahl Partnerrolle</summary>
<p><img src="docs/images/image9.png" alt="select contract partner role"></p>
</details>
<details >
<summary>screenshot: Contract version: Auswahl Partner</summary>
<p><img src="docs/images/image10.png" alt="select contract partner"></p>
</details>
</details>
<details >
<summary>screenshot: Contract version: Button zum Einfügen einer neuen Partnerbeziehung</summary>
<p><img src="docs/images/image11.png" alt="add contract partner"></p>
</details>
<details >
<summary>screenshot: Contract version: Neue Partnerbeziehung eingefügt</summary>
<p><img src="docs/images/image12.png" alt="contract partner added"></p>
</details>

### 2.2.2  Funktionsbereich Contract Version - product items

Anklicken öffnet den Abschnitt zur Anzeige / Bearbeitung von Produktpositionen.
<details >
<summary>screenshot: product items expanded</summary>
<p>
<img src="docs/images/image13.png" alt="product items">
</p>
</details>
### 2.2.2.1 Funktionsbereich Contract Version - product items - tariff items

Anklicken öffnet den Abschnitt zur Anzeige / Bearbeitung von Tarifpositionen.

<details >
<summary>screenshot: Tarifpositionen aufgeklappt</summary>
<p>
<img src="docs/images/image14.png" alt="tariff items">
</p>
</details>

Anklicken des Buttons "select" ändert den Button in "calculator"
<details >
<summary>screenshot: Tarifposition selektiert </summary>
<p>
<img src="docs/images/image15.png" alt="tariff item selected">
</p>
</details>

Anklicken des Buttons "calculator" Berechnungsfensteröffnet das Berechnungsfenster:
<details >
<summary>screenshot: Tarifrechner gestartet </summary>
<p>
<img src="docs/images/image16.png" alt="tariff item calculator">
</p>
</details> 
Es können verschiedene Berechnungsziele vorgegeben werden.
<details >
<summary>screenshot: Tarifrechner gestartet </summary>
<p>
<img src="docs/images/image17.png" alt="input calculation target">
</p>
</details>

Nach Vorgabe des Berechnungsziels können die Parameter eingegeben werden.
<details>
<summary>screenshot: Berechnungsziel vorgegeben </summary>
<p>
<img src="docs/images/image18.png" alt="calculation target determined">
</p>
</details>

Eingabedialog 

<details >
<summary>screenshot: Eingabedialog </summary>
<p>
<img src="docs/images/image19.png" alt="calculation target determined">
</p>
</details>


Wenn alle obligatorischen Parameter belegt sind, kann gerechnet werden.
<details >
<summary>screenshot: Berechnungsaufruf </summary>
<p>
<img src="docs/images/image20.png" alt="calculation callable">
</p><p>
<img src="docs/images/image21.png" alt="calculation called">
</p>
</details>

Parameter und Berechnungsergebnis können in die entsprechenden, d.h. ggf. vorhandenen gleichnamigen, Vertragsfelder synchroniert werden
<details >
<summary>screenshot: Synchronisierung mit dem Vertragsstand </summary>
<p>
<img src="docs/images/image22.png" alt="calculation callable">
</p>
</details>

### 2.2.2.1.1 Funktionsbereich Contract Version - product items - tariff items - tariff item partners

Anklicken öffnet den Abschnitt zur Anzeige / Bearbeitung von Partnerbeziehungen zu Tariffpositionen.
<details >
<summary>screenshot: Tarifpositionspartner </summary>
<p>
<img src="docs/images/image23.png" alt="tariff item partners">
</p>
</details>
### 2.3 Funktionsbereich History
Anklicken eines Versionsknoten öffnet die Versionsansicht
<details >
<summary>screenshot: Auswahl Version </summary>
<p>
<img src="docs/images/image24.png" alt="choose uncommitted workflow">
</p>
<p>
<img src="docs/images/image6.png" alt="show uncommited workflow">
</p>
<p>
<img src="docs/images/image25.png" alt="choose committed workflow">
</p>
<p>
<img src="docs/images/image4.png" alt="show committed workflow">
</p>
</details>

Rückwirkende Mutationen verschatten früher erfasste Mutationen mit gleichem oder späterem Gültigkeitsbeginn.
<details >
<summary>screenshot: Rückwirkende Transaktion</summary>
<p>
<img src="docs/images/image26.png" alt="retroactive Transaction">
</p>
<p>
<img src="docs/images/image27.png" alt="select shadowed Transaction">
</p>
</details>

### 2.3.1 Funktionsbereich Search Partner
#### Anzeige einer Liste von Partner-IDs.

<details >
<summary>screenshot: Partners tab</summary>
<p>
<img src="docs/images/image28.png" alt="Partners">
</p>
</details>
Anklicken wechselt in die Anzeige der neuesten Partnerversion.

### 2.3.2 Funktionsbereich Partner

Anzeige Partnerversion 
Die Partnerverwaltung ist rudimentär. Sie enthäĺt nur die tarifrelevanten Partnerdaten und eine Bearbeitung ist in der Webapp nicht möglich, nur über das Vertrags-API [Beispiel: hier ](testAPI.jl)
<details >
<summary>screenshot: Partnerversions tab</summary>
<p>
<img src="docs/images/image29.png" alt="Partner">
</p>
</details>

### 2.3.3 Funktionsbereich Search Product
#### Anzeige einer Liste von Product-IDs.

<details >
<summary>screenshot: Products tab</summary>
<p>
<img src="docs/images/image30.png" alt="Products">
</p>
</details>
Anklicken wechselt in die Anzeige der neuesten Partnerversion.

### 2.3.4 Funktionsbereich Product

Anzeige Produktversion 
Die Produktverwaltung ist rudimentär. Sie enthäĺt nur die tarifrelevanten Partnerdaten und eine Bearbeitung ist in der Webapp nicht möglich, nur über das Vertrags-API [Beispiel: hier ](testAPI.jl)

#### 2.3.4.1 Funktionsbereich Product - Feld tariff parameters

Die Semantik dieses Felds wird aus den Tarif-Debuggerskripten klar.

[Pension](https://github.com/Actuarial-Sciences-for-Africa-ASA/LifeInsuranceProduct.jl/blob/main/testCalPEN.jl)
[SingleLifeRisk](https://github.com/Actuarial-Sciences-for-Africa-ASA/LifeInsuranceProduct.jl/blob/main/testCalcSLR.jl)
[JointLifeRisk](https://github.com/Actuarial-Sciences-for-Africa-ASA/LifeInsuranceProduct.jl/blob/main/testCalcJLR.jl)

#### 2.3.4.2 Funktionsbereich Product - Feld contract attributes

Dieses Feld definiert die dynamischen Attribute der Tarifpositionen.

<details >
<summary>screenshot: Productversion tab</summary>
<p>
<img src="docs/images/image31.png" alt="Partner">
</p>
</details>

## 3 Installation und Start

Das Package braucht eine POSTGRES-Datenbank, den [Konfigurationsordner](db) und Produktdaten [siehe: testSkript](testAPI.jl)
### 3.1 Start unter gitpod

[![Gitpod Ready-to-Code](https://img.shields.io/badge/Gitpod-Ready--to--Code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/Actuarial-Sciences-for-Africa-ASA/GenieBuiltLifeProto)

Beim Start des gitpod workspace wird die Datenbank vorinstalliert und drei Produkte / Verträge werden geladen. VS Code wird gestartet.

### 3.1.1 Web Server starten

In der Terminalansicht Julia starten
    ```julia --project=.```
und das Startskript laden>
 ```include("run.jl")```
Hier braucht man etwas Geduld, die Anwendung wird dann schon noch reaktiv :-).

### 3.1.2 Browser Sitzung  starten

VS Code startet automatisch eine Browsersityung. Falls nicht, die Portanzeige
 ```Menu -> View -> Open View -> Ports```
auswählen und den Port für den Application Web Server anklicken.

BE PATIENT! Initialization takes some time. It gets reactive then!

Three contracts are preloaded: pension, SingleLifeRisk, JointLifeRisk
