---
title: Häufig gestellte Fragen zu Azure Machine Learning (FAQs) | Microsoft-Dokumentation
description: 'Einführung in Azure Machine Learning: häufig gestellte Fragen (FAQ) zu Abrechnung, Funktionen und Einschränkungen von Clouddiensten für die optimierte Vorhersagemodellierung.'
keywords: Einführung in maschinelles Lernen,Vorhersagemodellierung,was ist maschinelles Lernen
services: machine-learning
documentationcenter: ''
author: heatherbshapiro
ms.author: hshapiro
manager: hjerez
editor: cgronlun
ms.assetid: a4a32a06-dbed-4727-a857-c10da774ce66
ms.service: machine-learning
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: get-started-article
ms.date: 06/02/2017
ms.openlocfilehash: 4ea48300e83e1faa1250d2fba7c37a82825c820f
ms.sourcegitcommit: e2adef58c03b0a780173df2d988907b5cb809c82
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2018
---
# <a name="azure-machine-learning-frequently-asked-questions-billing-capabilities-limitations-and-support"></a>Häufig gestellte Fragen zu Azure Machine Learning: Abrechnung, Funktionen, Einschränkungen und Support
Hier sind einige häufig gestellte Fragen (FAQs) und die entsprechenden Antworten zu Azure Machine Learning aufgeführt. Bei Azure Machine Learning handelt es sich um einen Clouddienst zum Entwickeln von Vorhersagemodellen und Operationalisieren von Lösungen mithilfe von Webdiensten. Diese FAQs liefern Antworten zur Verwendung des Diensts, z.B. in Bezug auf das Abrechnungsmodell, Funktionen, Einschränkungen und den Support.

**Haben Sie eine Frage, die hier nicht aufgeführt ist?**

Für Azure Machine Learning gibt es ein Forum auf MSDN, in dem Mitglieder der Data Science-Community Fragen zu Azure Machine Learning stellen können. Das Forum wird vom Azure Machine Learning-Team überwacht. Suchen Sie im [Azure Machine Learning-Forum](http://social.msdn.microsoft.com/Forums/windowsazure/home?forum=MachineLearning) nach Antworten, oder stellen Sie eine neue Frage.

## <a name="general-questions"></a>Allgemeine Fragen
**Was ist Azure Machine Learning?**

Azure Machine Learning ist ein vollständig verwalteter Dienst, mit dem Sie Lösungen zu Vorhersageanalyse in der Cloud erstellen, testen, betreiben und verwalten können. Mit einem Browser können Sie sich anmelden, Daten hochladen und sofort mit Experimenten im Bereich Machine Learning beginnen. Dank der Vorhersagemodellierung per Drag & Drop, einer umfangreichen Modulpalette und einer Bibliothek mit Ausgangsvorlagen können Sie gängige Aufgaben im Bereich Machine Learning schnell und einfach ausführen. Weitere Informationen finden Sie auf der Übersichtsseite zu [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/). Eine Einführung in Machine Learning mit wichtigen Begriffen und Konzepten finden Sie unter [Einführung in Azure Machine Learning](what-is-machine-learning.md).

[!INCLUDE [machine-learning-free-trial](../../../includes/machine-learning-free-trial.md)]

**Was ist Machine Learning Studio?**

Machine Learning Studio ist eine Workbench-Umgebung, auf die Sie über einen Webbrowser zugreifen. Machine Learning Studio enthält eine Palette von Modulen in einer visuellen Kompositionsoberfläche, in der Sie durchgängige Datenworkflows in Form von Experimenten erstellen können.

Weitere Informationen zu Machine Learning Studio finden Sie unter [Was ist Machine Learning Studio?](what-is-ml-studio.md)

**Was ist der Machine Learning-API-Dienst?**

Mit dem Machine Learning-API-Dienst können Sie Ihre Vorhersagemodelle, z.B. in Machine Learning Studio erstellte Modelle, als skalierbare, fehlertolerante Webdienste bereitstellen. Die vom Machine Learning-API-Dienst erstellten Webdienste sind REST-APIs. Sie bieten eine Schnittstelle für die Kommunikation zwischen externen Anwendungen und Ihren Predictive Analytics-Modellen.

Weitere Informationen finden Sie unter [Nutzen eines Azure Machine Learning-Webdiensts](consume-web-services.md).

**Wo sind meine klassischen Webdienste aufgeführt? Wo sind meine neuen (Azure Resource Manager-basierten) Webdienste aufgeführt?**

Mit dem klassischen Bereitstellungsmodell und dem neuen Azure Resource Manager-Bereitstellungsmodell erstellte Webdienste sind im Portal [Microsoft Azure Machine Learning-Webdienste](https://services.azureml.net/) aufgeführt.

Klassische Webdienste finden Sie auch in [Machine Learning Studio](http://studio.azureml.net) auf der Registerkarte **Webdienste**.

## <a name="azure-machine-learning-questions"></a>Fragen zu Azure Machine Learning
**Was sind Azure Machine Learning-Webdienste?**

Machine Learning-Webdienste stellen eine Schnittstelle zwischen einer Anwendung und einem Machine Learning-Workflow-Bewertungsmodell dar. Von einer externen Anwendung kann Azure Machine Learning verwendet werden, um in Echtzeit mit einem Machine Learning-Workflow-Bewertungsmodell zu kommunizieren. Mit einem Aufruf eines Machine Learning-Webdiensts werden Vorhersageergebnisse an eine externe Anwendung zurückgegeben. Zur Durchführung eines Webdienstaufrufs übergeben Sie einen API-Schlüssel, der beim Bereitstellen des Webdiensts erstellt wurde. Ein Machine Learning-Webdienst basiert auf REST, einer verbreiteten Architektur für Webprogrammierungsprojekte.

Azure Machine Learning verfügt über zwei Arten von Webdiensten:

* Anforderung/Antwort-Dienst (Request-Response Service, RRS): Ein hochskalierbarer Webdienst mit kurzer Wartezeit, der eine Schnittstelle für zustandslose Modelle bereitstellt, die mit Machine Learning Studio erstellt und bereitgestellt wurden.
* Batch Execution Service (BES): Ein asynchroner Dienst für die Bewertung eines Stapels für Datensätze.

Es gibt mehrere Möglichkeiten, die REST-API zu nutzen und auf den Webdienst zuzugreifen. Beispielsweise können Sie eine Anwendung in C#, R oder Python schreiben und dabei den Beispielcode verwenden, der für Sie beim Bereitstellen des Webdiensts generiert wurde.

Den Beispielcode finden Sie hier:
- Seite „Consume“ (Verbrauchen) für den Webdienst im Azure Machine Learning-Webdienste-Portal
- API-Hilfeseite im Webdienstdashboard in Machine Learning Studio

Sie können auch die Microsoft Excel-Beispielarbeitsmappe verwenden, die für Sie erstellt wurde und im Webdienstdashboard in Machine Learning Studio verfügbar ist.

**Was sind die wichtigsten Updates für Azure Machine Learning?**

Die neuesten Updates finden Sie unter [Neuerungen in Azure Machine Learning](whats-new.md).

## <a name="machine-learning-studio-questions"></a>Fragen zu Machine Learning Studio
### <a name="import-and-export-data-for-machine-learning"></a>Importieren und Exportieren von Daten für Machine Learning
**Welche Datenquellen unterstützt Machine Learning?**

Sie haben drei Möglichkeiten, um Daten in ein Machine Learning Studio-Experiment herunterzuladen:

- Hochladen einer lokalen Datei als Dataset
- Verwenden eines Moduls zum Importieren von Daten aus Clouddatendiensten
- Importieren eines in einem anderen Experiment gespeicherten Datasets

Weitere Informationen zu den unterstützten Dateiformaten finden Sie unter [Importieren von Trainingsdaten in Machine Learning Studio](import-data.md).

#### <a id="ModuleLimit"></a>Wie groß können Datasets für meine Module sein?
Module in Machine Learning Studio unterstützen in normalen Anwendungsfällen Datasets bis zu einer Größe von 10 GB an dichten numerischen Daten. Wenn ein Modul mehrere Eingaben akzeptiert, entspricht der Wert von 10 GB der Summe aller Eingabegrößen. Sie können auch Teile größerer Datasets übernehmen, indem Sie Abfragen aus Hive oder Azure SQL-Datenbank verwenden, oder Sie können die Vorverarbeitung per Lernen nach Anzahl vor der Erfassung nutzen.  

Die folgenden Typen von Daten können während der Featurenormalisierung in größere Datasets erweitert werden und sind auf weniger als 10 GB beschränkt:

* Platzsparend
* Kategorisch
* Zeichenfolgen
* Binärdaten

Die folgenden Module sind auf Datasets mit einer Größe von unter 10 GB beschränkt:

* Empfohlene Module
* Modul „Synthetic Minority Oversampling Technique (SMOTE)“
* Skripting-Module: R, Python, SQL
* Module, bei denen die Größe der Ausgabedaten die der Eingabedaten überschreiten kann, z.B. Join oder Feature-Hashing.
* Kreuzvalidierung, Tune Model Hyperparameters, Ordinal Regression und One-vs-All Multiclass, wenn eine sehr große Anzahl von Iterationen durchgeführt wird.

#### <a id="UploadLimit"></a>Was sind die Limits für Datenuploads?
Laden Sie die Daten für Datasets, die größer als einige GB sind, in Azure Storage oder Azure SQL-Datenbank hoch, oder verwenden Sie Azure HDInsight, anstatt die Daten direkt aus einer lokalen Datei hochzuladen.

**Können Daten von Amazon S3 gelesen werden?**

Wenn Ihre Daten nicht sehr umfangreich sind und Sie diese Daten über eine HTTP-URL verfügbar machen möchten, können Sie das Modul zum [Importieren von Daten][import-data] verwenden. Größere Datenmengen sollten Sie zunächst in Azure Storage übertragen und anschließend mit dem Modul zum [Importieren von Daten][import-data] in das Experiment übernehmen.
<!--

<SEE CLOUD DS PROCESS>
-->

**Gibt es eine integrierte Bildeingabefunktion?**

Informationen zur Bildeingabefunktion finden Sie in der Referenz unter [Importieren von Bildern][image-reader].

### <a name="modules"></a>Module
**Der gewünschte Algorithmus, die Datenquelle, das Datenformat oder die Datentransformation sind nicht in Azure Machine Learning Studio enthalten. Welche Optionen habe ich?**

Sie können im [Forum für Benutzerfeedback](http://go.microsoft.com/fwlink/?LinkId=404231) nachsehen, welche Funktionswünsche wir momentan verfolgen. Stimmen Sie für den entsprechenden Vorschlag ab, wenn eine von Ihnen gewünschte Funktion bereits angefordert wurde. Falls die gewünschte Funktion nicht vorhanden ist, können Sie eine neue Anfrage erstellen. Sie können den Status Ihrer Anfrage ebenfalls in diesem Forum verfolgen. Wir verfolgen diese Liste regelmäßig und aktualisieren den Verfügbarkeitsstatus von Features häufig. Außerdem können Sie die integrierte Unterstützung von R und Python nutzen, um bei Bedarf benutzerdefinierte Transformationen zu erstellen.

**Kann ich meinen vorhandenen Code in Machine Learning Studio verwenden?**

Ja. Sie können Ihren vorhandenen R- oder Python-Code in Machine Learning Studio importieren, zusammen im gleichen Experiment mit den Lernmodulen in Azure Machine Learning ausführen und die Lösung als Webdienst über Azure Machine Learning bereitstellen. Weitere Informationen finden Sie unter [Erweitern Ihres Experiments mit R](extend-your-experiment-with-r.md) und [Ausführen von Python-Machine Learning-Skripts in Azure Machine Learning Studio](execute-python-scripts.md).

**Ist es möglich, z.B. mit [PMML](http://en.wikipedia.org/wiki/Predictive_Model_Markup_Language) ein Modell zu definieren?**

Nein, die Predictive Model Markup Language (PMML) wird nicht unterstützt. Sie können benutzerdefinierten R- und Python-Code verwenden, um ein Modul zu definieren.

**Wie viele Module kann ich parallel in meinem Experiment ausführen?**  

Sie können bis zu vier Module in einem Experiment parallel ausführen.

### <a name="data-processing"></a>Datenverarbeitung
**Gibt es eine Möglichkeit zum interaktiven Anzeigen von Daten (neben R-Visualisierungen) im Experiment?**

Klicken Sie auf die Ausgabe eines Moduls, um die Daten zu visualisieren und Statistiken abzurufen.

**Bei der Vorschau von Ergebnissen oder Daten in einem Browser ist die Anzahl von Zeilen und Spalten beschränkt. Warum?**

Da unter Umständen große Datenmengen an einen Browser gesendet werden, ist die Datengröße beschränkt, um eine Verlangsamung von Machine Learning Studio zu verhindern. Es ist besser, alle Daten herunterzuladen und Excel oder ein anderes Tool zu verwenden, um die gesamten Daten bzw. Ergebnisse zu visualisieren.

### <a name="algorithms"></a>Algorithmen
**Welche vorhandenen Algorithmen werden in Machine Learning Studio unterstützt?**

Machine Learning Studio unterstützt moderne Algorithmen, z.B. skalierbare Boosted Decision-Strukturen, Bayessche Empfehlungssysteme, tiefe neuronale Netze und die von Microsoft Research entwickelten „Entscheidungsdschungel“. Skalierbare Open Source-Pakete für Machine Learning-Pakete, z.B. Vowpal Wabbit, sind ebenfalls enthalten. Machine Learning Studio unterstützt Algorithmen für Machine Learning für mehrklassige und binäre Klassifizierung, Regression und Clustering. Weitere Informationen finden Sie in der vollständigen Liste der [Machine Learning-Module][machine-learning-modules].

**Wird automatisch der richtige Machine Learning-Algorithmus für meine Daten vorgeschlagen?**

Nein. Es gibt in Machine Learning Studio aber verschiedene Möglichkeiten zum Vergleichen der Ergebnisse jedes Algorithmus, um die richtige Wahl für das jeweilige Problem zu treffen.

**Gibt es Richtlinien zum Auswählen eines Algorithmus für die bereitgestellten Algorithmen?**

Informationen hierzu finden Sie unter [Auswählen eines Algorithmus](algorithm-choice.md).

**Wurden die bereitgestellten Algorithmen in R oder Python geschrieben?**

Diese Algorithmen wurden größtenteils in kompilierten Sprachen geschrieben, um eine bessere Leistung zu erzielen.

**Gibt es nähere Informationen zu den Algorithmen?**

Die Dokumentation enthält Informationen zu den Algorithmen und Parameter für die Feinabstimmung, damit Sie den Algorithmus für Ihre Zwecke optimieren können.  

**Gibt es Unterstützung für das Onlinelernen?**

Nein, derzeit wird nur programmgesteuertes erneutes Trainieren unterstützt.

**Können die Ebenen eines Modells für ein neuronales Netz mit dem integrierten Modul visualisiert werden?**

Nein.

**Kann ich eigene Module in C# oder einer anderen Sprache erstellen?**

Derzeit können Sie nur R verwenden, um neue benutzerdefinierte Module zu erstellen.

### <a name="r-module"></a>R-Modul
**Welche R-Pakete sind in Machine Learning Studio verfügbar?**

Machine Learning Studio unterstützt bereits über 400 CRAN R-Pakete. Hier finden Sie die [aktuelle Liste](http://az754797.vo.msecnd.net/docs/RPackages.xlsx) mit allen enthaltenen Paketen. Lesen Sie auch die Anweisungen zum Abrufen dieser Liste unter [Erweitern des Experiments mit R](extend-your-experiment-with-r.md). Falls das gewünschte Paket nicht in der Liste enthalten ist, können Sie den Namen des Pakets im [Forum für Benutzer-Feedback](http://go.microsoft.com/fwlink/?LinkId=404231) hinterlassen.

**Ist es möglich, benutzerdefinierte R-Module zu erstellen?**

Ja. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten R-Modulen in Azure Machine Learning](custom-r-modules.md).

**Gibt es eine REPL-Umgebung für R?**

Nein, in Studio ist keine REPL-Umgebung (Read-Eval-Print-Loop) enthalten.

### <a name="python-module"></a>Python-Modul
**Ist es möglich, benutzerdefinierte Python-Module zu erstellen?**

Derzeit nicht. Sie können aber ein oder mehrere Module vom Typ [Python-Skript ausführen][python] verwenden, um das gleiche Ergebnis zu erzielen.

**Gibt es eine REPL-Umgebung für Python?**

Sie können die „Jupyter Notebooks“ in Machine Learning Studio verwenden. Weitere Informationen finden Sie unter [Introducing Jupyter Notebooks in Azure ML Studio](http://blogs.technet.com/b/machinelearning/archive/2015/07/24/introducing-jupyter-notebooks-in-azure-ml-studio.aspx)(Einführung in Jupyter Notebooks in Azure Machine Learning Studio).

## <a name="web-service"></a>Webdienst
### <a name="retrain"></a>Erneutes Trainieren
**Wie kann ich Azure Machine Learning-Modelle programmgesteuert neu trainieren?**

Verwenden Sie die APIs für das erneute Trainieren. Weitere Informationen finden Sie unter [Programmgesteuertes erneutes Trainieren von Machine Learning-Modellen](retrain-models-programmatically.md). Außerdem ist Beispielcode unter [Microsoft Azure Machine Learning Retraining Demo](https://azuremlretrain.codeplex.com/)(Microsoft Azure Machine Learning – Demo für erneutes Trainieren) verfügbar.

### <a name="create"></a>Erstellen
**Kann ich das Modell lokal oder in einer Anwendung ohne Internetverbindung bereitstellen?**

Nein.

**Gibt es eine Grundlatenz, die für alle Webdienste erwartet wird?**

Informationen hierzu finden Sie unter [Einschränkungen für Azure-Abonnements](../../azure-subscription-service-limits.md).

### <a name="use"></a>Verwenden Sie
**Wann sollte ich mein Vorhersagemodell als Stapelausführungsdienst oder als Anfrage-Antwort-Dienst ausführen?**

Der Anfrage-Antwort-Dienst (Request Response Service, RRS) ist ein hoch skalierbarer Webdienst mit niedriger Latenz, der eine Schnittstelle für zustandslose Modelle bereitstellt, die in der Experimentumgebung erstellt und bereitgestellt wurden. Der Stapelausführungsdienst (Batch Execution Service, BES) dient zur asynchronen Bewertung eines Stapels von Datensätzen. Die Eingabe für BES gleicht der für RRS verwendeten Dateneingabe. BES liest im Gegensatz zu RRS einen Block von Einträgen aus einer Vielzahl von Quellen, z.B. Azure Blob Storage, Azure Table Storage, Azure SQL-Datenbank, HDInsight (Hive-Abfrage) und HTTP-Quellen. Weitere Informationen finden Sie unter [Nutzen eines Azure Machine Learning-Webdiensts](consume-web-services.md).

**Wie aktualisiere ich das Modell für den bereitgestellten Webdienst?**

Sie können ein Vorhersagemodell für einen bereitgestellten Dienst aktualisieren, indem Sie das Experiment bearbeiten und erneut ausführen, das Sie beim Erstellen und Speichern des trainierten Modells verwendet haben. Nachdem die neue Version des trainierten Modells verfügbar ist, werden Sie von Machine Learning Studio gefragt, ob Sie Ihren Webdienst aktualisieren möchten. Ausführliche Informationen zum Aktualisieren eines bereitgestellten Webdiensts finden Sie unter [Bereitstellen von Machine Learning-Webdiensten](publish-a-machine-learning-web-service.md).

Sie können auch die APIs zum erneuten Trainieren verwenden.
Weitere Informationen finden Sie unter [Programmgesteuertes erneutes Trainieren von Machine Learning-Modellen](retrain-models-programmatically.md). Außerdem ist Beispielcode unter [Microsoft Azure Machine Learning Retraining Demo](https://azuremlretrain.codeplex.com/)(Microsoft Azure Machine Learning – Demo für erneutes Trainieren) verfügbar.

**Wie überwache ich meinen Webdienst in der Produktionsumgebung?**

Nachdem Sie ein Vorhersagemodell bereitgestellt haben, können Sie es über das Portal der Azure Machine Learning-Webdienste überwachen. Jeder bereitgestellte Dienst hat ein eigenes Dashboard mit Überwachungsinformationen für den jeweiligen Dienst. Weitere Informationen dazu, wie Sie bereitgestellte Webdienste verwalten, finden Sie unter [Verwalten eines Webdiensts im Azure Machine Learning-Webdienste-Portal](manage-new-webservice.md) und [Verwalten eines Azure Machine Learning-Arbeitsbereichs](manage-workspace.md).

**Kann ich die Ausgabe meines RRS/BES an einer Stelle einsehen?**

Für RRS wird das Ergebnis normalerweise in der Antwort des Webdiensts ausgegeben. Sie können es auch in Azure Blob Storage schreiben. Bei BES wird die Ausgabe standardmäßig in ein Blob geschrieben. Sie können die Ausgabe außerdem mit dem Modul zum [Exportieren von Daten][export-data] in eine Datenbank oder Tabelle schreiben.

**Können Webdienste nur aus Modellen erstellt werden, die in Machine Learning Studio erstellt wurden?**

Nein. Webdienste können auch direkt mit Jupyter Notebooks und RStudio erstellt werden.

**Wo finde ich Informationen zu Fehlercodes?**

Eine Liste mit Fehlercodes und den dazugehörigen Beschreibungen finden Sie unter [Machine Learning-Modul-Fehlercodes](https://msdn.microsoft.com/library/azure/dn905910.aspx) .

## <a name="scalability"></a>Skalierbarkeit
**Wie skalierbar ist der Webdienst?**

Derzeit wird der Standardendpunkt mit 20 gleichzeitigen RRS-Anforderungen pro Endpunkt bereitgestellt. Sie können dies auf 200 gleichzeitige Anforderungen pro Endpunkt skalieren, und jeder Webdienst kann auf 10.000 Endpunkte pro Webdienst skaliert werden, wie unter [Skalieren eines Webdiensts](scaling-webservice.md) beschrieben. Bei BES kann jeder Endpunkt 40 Anforderungen gleichzeitig verarbeiten, und weitere Anforderungen werden in eine Warteschlange eingereiht. Diese Anforderungen in der Warteschlange werden automatisch ausgeführt, wenn die Warteschlange geleert wird.

**Werden R-Aufträge auf die Knoten verteilt?**

Nein.  

**Wie viele Daten kann ich für das Training verwenden?**

Module in Machine Learning Studio unterstützen in normalen Anwendungsfällen Datasets bis zu einer Größe von 10 GB an dichten numerischen Daten. Wenn für ein Modul mehr als eine Eingabe verwendet wird, beträgt die Gesamtgröße für alle Eingaben 10 GB. Sie können über Hive- oder Azure SQL-Datenbankabfragen oder per Vorverarbeitung durch Module vom Typ [Lernen durch Anzahl][counts] auch Teile größerer Datasets übernehmen.  

Die folgenden Typen von Daten können während der Featurenormalisierung in größere Datasets erweitert werden und sind auf weniger als 10 GB beschränkt:

* Platzsparend
* Kategorisch
* Zeichenfolgen
* Binärdaten

Die folgenden Module sind auf Datasets mit einer Größe von unter 10 GB beschränkt:

* Empfohlene Module
* Modul „Synthetic Minority Oversampling Technique (SMOTE)“
* Skripting-Module: R, Python, SQL
* Module, bei denen die Größe der Ausgabedaten die der Eingabedaten überschreiten kann, z.B. Join oder Feature Hashing.
* Cross-Validate, Tune Model Hyperparameters, Ordinal Regression und One-vs-All Multiclass, wenn eine sehr große Anzahl von Iterationen durchgeführt wird.

Laden Sie die Daten für Datasets, die größer als einige GB sind, in Azure Storage oder Azure SQL-Datenbank hoch, oder verwenden Sie HDInsight, anstatt die Daten direkt aus einer lokalen Datei hochzuladen.

**Gibt es Vektorgrößenbeschränkungen?**

Zeilen und Spalten sind jeweils auf die .NET-Einschränkung für Ganzzahlen beschränkt: 2.147.483.647.

**Kann ich die Größe des virtuellen Computers anpassen, auf dem der Webdienst ausgeführt wird?**

Nein.  

## <a name="security-and-availability"></a>Sicherheit und Verfügbarkeit
**Wer hat standardmäßig Zugriff auf den HTTP-Endpunkt für den Webdienst? Wie kann ich den Zugriff auf den Endpunkt einschränken?**

Nach der Bereitstellung eines Webdiensts wird ein Standardendpunkt für den Dienst erstellt. Der Standardendpunkt kann über seinen API-Schlüssel aufgerufen werden. Sie können zusätzliche Endpunkte mit eigenen Schlüsseln über das Webdiensteportal oder programmgesteuert mithilfe der APIs der Webdienstverwaltung hinzufügen. Zugriffsschlüssel sind erforderlich, um Aufrufe für den Webdienst durchzuführen. Weitere Informationen finden Sie unter [Nutzen eines Azure Machine Learning-Webdiensts](consume-web-services.md).

**Was passiert, wenn mein Azure-Speicherkonto nicht gefunden werden kann?**

In Machine Learning Studio ist ein vom Benutzer bereitgestelltes Azure-Speicherkonto zum Speichern von temporären Daten beim Ausführen des Workflows erforderlich. Dieses Speicherkonto wird für Machine Learning Studio beim Erstellen eines Arbeitsbereichs zur Verfügung gestellt. Wenn das Speicherkonto nach dem Erstellen des Arbeitsbereichs gelöscht wird, funktioniert der Arbeitsbereich nicht mehr, und alle darin enthaltenen Experimente schlagen fehl.

Wenn Sie das Speicherkonto versehentlich löschen, können Sie es mit identischem Namen und in derselben Region neu erstellen. Führen Sie anschließend die erneute Synchronisierung des Zugriffsschlüssels durch.

**Was geschieht, wenn mein Speicherkonto-Zugriffsschlüssel nicht mehr synchronisiert ist?**

In Machine Learning Studio ist ein vom Benutzer bereitgestelltes Azure-Speicherkonto zum Speichern von temporären Daten beim Ausführen des Workflows erforderlich. Dieses Speicherkonto wird für Machine Learning Studio beim Erstellen des Arbeitsbereichs zur Verfügung gestellt, und die Zugriffsschlüssel werden diesem Arbeitsbereich zugewiesen. Wenn Zugriffsschlüssel nach dem Erstellen des Arbeitsbereichs geändert werden, kann dieser Arbeitsbereich nicht mehr auf das Speicherkonto zugreifen. Er funktioniert nicht mehr, und alle in diesem Arbeitsbereich enthaltenen Experimente schlagen fehl.

Wenn Sie Zugriffsschlüssel für Speicherkonten geändert haben, müssen Sie die Zugriffsschlüssel im Arbeitsbereich über das Azure-Portal neu synchronisieren.  

## <a name="support-and-training"></a>Support und Lernmaterial
**Wo erhalte ich Lernmaterial für Azure Machine Learning?**

Im [Azure Machine Learning Documentation Center](https://azure.microsoft.com/services/machine-learning/) finden Sie Videoanleitungen und Leitfäden. Diese ausführlichen Leitfäden enthalten eine Einführung in die Dienste und beschreiben den Lebenszyklus der Daten vom Import und der Bereinigung der Daten bis hin zur Erstellung von Vorhersagemodellen und der Bereitstellung der Modelle in der Produktionsumgebung mit Azure Machine Learning.

Wir fügen dem Machine Learning Center fortlaufend neues Material hinzu. Sie können jederzeit zusätzliches Material für das Machine Learning Center im [Forum für Benutzerfeedback](https://windowsazure.uservoice.com/forums/257792-machine-learning)anfordern.

Es werden auch Schulungen unter [Microsoft Virtual Academy](http://www.microsoftvirtualacademy.com/training-courses/getting-started-with-microsoft-azure-machine-learning)angeboten.

**Wo erhalte ich Support für Azure Machine Learning?**

Technischen Support für Azure Machine Learning erhalten Sie, indem Sie den [Azure-Support](/support/options/) besuchen und **Machine Learning** auswählen.

Für Azure Machine Learning gibt es außerdem ein Community-Forum auf MSDN, in dem Sie Fragen zu Azure Machine Learning stellen können. Das Forum wird vom Azure Machine Learning-Team überwacht. Wechseln Sie zum [Azure-Forum](http://social.msdn.microsoft.com/Forums/windowsazure/home?forum=MachineLearning).

## <a name="billing-questions"></a>Fragen zur Abrechnung
**Wie funktioniert die Abrechnung von Machine Learning?**

Azure Machine Learning verfügt über zwei Komponenten: Machine Learning Studio und Machine Learning-Webdienste.

Zum Evaluieren von Machine Learning Studio können Sie den kostenlosen Free-Tarif nutzen. Im Free-Tarif können Sie auch einen klassischen Webdienst bereitstellen, der über eingeschränkte Kapazität verfügt.

Wenn Azure Machine Learning Ihre Anforderungen erfüllt, können Sie sich für den Standard-Tarif registrieren. Für die Registrierung müssen Sie über ein Microsoft Azure-Abonnement verfügen.

Im Standard-Tarif wird Ihnen jeder Arbeitsbereich, den Sie in Machine Learning Studio definieren, monatlich berechnet. Wenn Sie in Studio ein Experiment ausführen, werden Ihnen die Computeressourcen berechnet, die beim Ausführen des Experiments genutzt werden. Beim Bereitstellen eines klassischen Webdiensts fallen Kosten für Transaktionen und Computestunden (auch als „Berechnungsstunden“ bezeichnet) basierend auf der nutzungsbasierten Abrechnung an.

Mit den neuen (Resource Manager-basierten) Webdiensten werden Abrechnungspläne eingeführt, mit denen die Kosten besser vorhergesagt werden können. Im Rahmen der gestaffelten Preise werden für Kunden, die eine große Menge an Kapazität benötigen, Rabatte angeboten.

Wenn Sie einen Plan erstellen, akzeptieren Sie feste Kosten, die mit einer enthaltenen Menge von API-Computestunden und API-Transaktionen verbunden sind. Falls Sie höhere enthaltene Mengen benötigen, können Sie Ihrem Plan Instanzen hinzufügen. Wenn es um höhere Mengen geht, können Sie einen Plan mit höherem Tarif wählen, der über deutlich höhere enthaltene Mengen und einen besseren Rabatt verfügt.

Nachdem die enthaltenen Mengen in den vorhandenen Instanzen aufgebraucht sind, wird für die weitere Nutzung die Überschreitungsrate des Abrechnungsplantarifs berechnet.

> [!NOTE]
Die enthaltenen Mengen werden alle 30 Tage neu zugeordnet, und nicht genutzte Mengen werden nicht auf den nächsten Zeitraum übertragen.

Weitere Informationen zur Abrechnung und zu Preisen finden Sie unter [Machine Learning Preise](https://azure.microsoft.com/pricing/details/machine-learning/).

**Gibt es eine kostenlose Testversion von Machine Learning?**

 Azure Machine Learning verfügt über eine kostenlose Abonnementoption, die unter [Machine Learning Preise](https://azure.microsoft.com/pricing/details/machine-learning/) beschrieben wird. Bei der Anmeldung an [Machine Learning Studio](https://studio.azureml.net/?selectAccess=true&o=2) ist eine 8-Stunden-Testversion für die schnelle Evaluierung verfügbar.

 Wenn Sie sich für die kostenlose Azure-Testversion anmelden, können Sie außerdem die Azure-Dienste einen Monat lang ausprobieren. Weitere Informationen zur kostenlosen Azure-Testversion finden Sie in den [häufig gestellten Fragen zur kostenlosen Testversion von Azure](https://azure.microsoft.com/pricing/free-trial-faq/).

**Was ist eine Transaktion?**

Eine Transaktion stellt einen API-Aufruf dar, auf den Azure Machine Learning reagiert. Transaktionen der Aufrufe vom Typ Anforderung/Antwort-Dienst (Request-Response Service, RRS) und Stapelausführungsdienst (Batch Execution Service, BES) werden aggregiert und basierend auf Ihrem Abrechnungsplan berechnet.

**Kann ich die enthaltenen Transaktionsmengen in einem Plan sowohl für RRS-Transaktionen als auch für BES-Transaktionen verwenden?**

Ja. Ihre Transaktionen für RRS und BES werden aggregiert und basierend auf Ihrem Abrechnungsplan berechnet.

**Was ist eine API-Computestunde?**

Eine API-Computestunde ist die Abrechnungseinheit für die Dauer von API-Aufrufen mithilfe von Machine Learning-Computeressourcen. Alle Aufrufe werden zu Abrechnungszwecken aggregiert (also zusammengefasst).

**Wie lange dauert ein typischer Produktions-API-Aufruf?**

Die Dauer von Produktions-API-Aufrufen kann erheblich variieren und von einigen hundert Millisekunden bis hin zu einigen Sekunden reichen. Für einige API-Aufrufe kann der Vorgang je nach Komplexität der Daten und des Machine Learning-Modells auch mehrere Minuten dauern. Die beste Möglichkeit zur Einschätzung der Produktions-API-Aufrufzeiten besteht darin, basierend auf dem Machine Learning-Dienst einen Benchmark für ein Modell zu erstellen.

**Was ist eine Studio-Computestunde?**

Eine Studio-Computestunde ist die Abrechnungseinheit für den gesamten Zeitraum, in dem für Experimente Computeressourcen in Studio genutzt werden.

**Welchen Zweck hat bei neuen (Azure Resource Manager-basierten) Webdiensten der Dev/Test-Tarif?**

Resource Manager-basierte Webdienste verfügen über mehrere Ebenen (Tarife), die Sie zum Bereitstellen Ihres Abrechnungsplans verwenden können. Der Dev/Test-Tarif ist eine Ebene mit begrenzten enthaltenen Mengen. So können Sie Ihr Experiment als Webdienst testen, ohne dass Kosten anfallen. Darüber hinaus haben Sie die Möglichkeit, sich mit der Funktionsweise vertraut zu machen.

**Gibt es separate Speichergebühren?**

Der Free-Tarif von Machine Learning erfordert keinen separaten Speicher und lässt diesen nicht zu. Für den Standard-Tarif von Machine Learning benötigen Benutzer ein Azure-Speicherkonto. Azure Storage [wird separat abgerechnet](https://azure.microsoft.com/pricing/details/storage/).

**Wird für Machine Learning Hochverfügbarkeit unterstützt?**

Ja. Ausführliche Informationen und eine Beschreibung der Vereinbarung zum Servicelevel (SLA) finden Sie unter [Machine Learning Preise](https://azure.microsoft.com/pricing/details/machine-learning/).

**Auf welcher Art von Computeressourcen werden meine Produktions-API-Aufrufe ausgeführt?**

Der Machine Learning-Dienst ist ein mehrinstanzenfähiger Dienst. Die eigentlichen Computeressourcen, die auf dem Back-End verwendet werden, variieren und wurden in Bezug auf die Leistung und die Vorhersagbarkeit optimiert.

### <a name="management-of-new-resource-manager-based-web-services"></a>Verwaltung von neuen (Resource Manager-basierten) Webdiensten
**Was passiert, wenn ich meinen Plan lösche?**

Der Plan wird aus dem Abonnement entfernt, und die Nutzung wird Ihnen anteilig berechnet.

> [!NOTE]
Es ist für Sie nicht möglich, einen Plan zu löschen, der von einem Webdienst verwendet wird. Um den Plan zu löschen, müssen Sie dem Webdienst entweder einen neuen Plan zuweisen oder den Webdienst löschen.

**Was ist eine Planinstanz?**

Eine Planinstanz ist eine Einheit von enthaltenen Mengen, die Sie Ihrem Abrechnungsplan hinzufügen können. Wenn Sie für den Abrechnungsplan einen Abrechnungstarif wählen, ist darin eine Instanz enthalten. Falls Sie mehr enthaltene Mengen benötigen, können Sie dem Plan Instanzen des ausgewählten Abrechnungstarifs hinzufügen.

**Wie viele Planinstanzen kann ich hinzufügen?**

Ein Abonnement kann über eine Instanz des Dev/Test-Tarifs verfügen.

Für die Tarife Standard S1, Standard S2 und Standard S3 können Sie beliebig viele Instanzen hinzufügen.

> [!NOTE]
Je nach voraussichtlicher Nutzung kann es unter Umständen kostengünstiger sein, ein Upgrade auf einen Tarif mit mehr enthaltenen Mengen durchzuführen, anstatt dem aktuellen Tarif Instanzen hinzuzufügen.

**Was passiert, wenn ich Plantarife ändere (Upgrade/Downgrade)?**

Der alte Plan wird gelöscht, und die aktuelle Nutzung wird anteilig berechnet. Für den restlichen Zeitraum wird ein neuer Plan mit allen enthaltenen Mengen des Tarifs erstellt, für den das Upgrade/Downgrade durchgeführt wurde.

> [!NOTE]
Enthaltene Mengen werden pro Zeitraum zugeordnet, und nicht genutzte Mengen werden nicht übertragen.

**Was passiert, wenn ich die Anzahl von Instanzen in einem Plan erhöhe?**

Mengen werden anteilig einbezogen, und es kann bis zu 24 Stunden dauern, bis sie wirksam werden.

**Was passiert, wenn ich eine Instanz eines Plans lösche?**

Die Instanz wird aus dem Abonnement entfernt, und die Nutzung wird Ihnen anteilig berechnet.

### <a name="sign-up-for-new-resource-manager-based-web-services-plans"></a>Registrieren für neue (Resource Manager-basierte) Webdienstpläne
**Wie kann ich mich für einen Plan registrieren?**

Sie haben zwei Möglichkeiten, Abrechnungspläne zu erstellen.

Bei der ersten Bereitstellung eines Resource Manager-basierten Webdiensts können Sie einen vorhandenen Plan wählen oder einen neuen Plan erstellen.

Pläne, die Sie auf diese Weise erstellen, befinden sich in Ihrer Standardregion, und Ihr Webdienst wird in dieser Region bereitgestellt.

Wenn Sie Dienste in anderen Regionen als der Standardregion bereitstellen möchten, kann es ratsam sein, Ihre Abrechnungspläne vor dem Bereitstellen des Diensts zu definieren.

In diesem Fall können Sie sich am Azure Machine Learning-Webdienste-Portal anmelden und zur Seite mit den Plänen navigieren. Auf dieser Seite können Sie Pläne hinzufügen, Pläne löschen und vorhandene Pläne bearbeiten.

**Mit welchem Plan soll ich beginnen?**

Wir empfehlen Ihnen, mit dem Tarif Standard S1 zu beginnen und die Nutzung Ihres Diensts zu überwachen. Wenn Sie feststellen, dass Sie Ihre enthaltenen Mengen schnell verbrauchen, können Sie Instanzen hinzufügen oder zu einem höheren Tarif wechseln und bessere Rabatte in Anspruch nehmen. Sie können Ihren Abrechnungsplan je nach Bedarf während des Abrechnungszyklus anpassen.

**In welchen Regionen sind die neuen Pläne verfügbar?**

Die neuen Abrechnungspläne sind in den drei Produktionsregionen verfügbar, in denen wir die neuen Webdienste unterstützen:

* USA Süd Mitte
* Europa, Westen
* Südostasien

**Ich verfüge über Webdienste in mehreren Regionen. Benötige ich einen Plan für jede Region?**

Ja. Die Preise der Pläne variieren je nach Region. Wenn Sie einen Webdienst in einer anderen Region bereitstellen, müssen Sie dafür einen regionsspezifischen Plan zuweisen. Weitere Informationen finden Sie unter [Verfügbare Produkte nach Region]( https://azure.microsoft.com/regions/services/).

### <a name="new-web-services-overages"></a>Neue Webdienste – Überschreitungen
**Wie kann ich überprüfen, ob ich die Grenzen für meine Webdienstnutzung überschritten habe?**

Sie können die Nutzung Ihrer Pläne im Azure Machine Learning-Webdienste-Portal auf der Seite „Pläne“ anzeigen. Melden Sie sich am Portal an, und klicken Sie anschließend auf die Menüoption **Pläne**.

In den Spalten **Transaktionen** und **Compute** der Tabelle werden die enthaltenen Mengen des Plans und die Nutzung in Prozent angezeigt.

**Was passiert, wenn ich die enthaltenen Mengen des Dev/Test-Tarifs aufgebraucht habe?**

Dienste, denen ein Dev/Test-Tarif zugewiesen wurde, werden beendet, bis der nächste Zeitraum beginnt oder bis Sie sie in einen kostenpflichtigen Tarif verschieben.

**Wie werden bei klassischen Webdiensten und Überschreitungen von neuen (Resource Manager-basierten) Webdiensten die Preise für Workloads vom Typ Anforderung/Antwort (RRS) und Batch (BES) berechnet?**

Bei einer RSS-Workload zahlen Sie für jeden API-Transaktionsaufruf, den Sie vornehmen, und für die mit diesen Anforderungen verbundenen Computezeit. Zur Berechnung der Kosten für RRS-Produktions-API-Transaktionen wird die Gesamtzahl Ihrer durchgeführten API-Aufrufe mit dem Preis pro 1.000 Transaktionen (anteilsmäßig für die einzelnen Transaktionen) multipliziert. Zur Berechnung der Kosten für Ihre RSS-API-Produktions-API-Berechnungsstunden wird die Summe der für jeden API-Aufruf benötigten Zeit mit der Gesamtzahl an API-Transaktionen und dem Preis pro Produktions-API-Berechnungsstunde multipliziert.

Beispiel: Für eine Standard S1-Überschreitung lautet das Ergebnis für 1.000.000 API-Transaktionen mit einer Ausführungszeit von je 0,72 Sekunden für Produktions-API-Transaktionen „500 USD“ (1.000.000 * 0,50 USD/1.000 API-Transaktionen) und für Produktions-API-Berechnungsstunden „400 USD“ (1.000.000 * 0,72 Sek. * 2 USD/Std.). Dies ergibt eine Gesamtsumme von 900 USD.

Bei BES-Workloads erfolgt die Abrechnung nach dem gleichen Prinzip. Allerdings stehen die API-Transaktionskosten hier für die Anzahl von initiierten Batchaufträgen, und die Kosten für Computestunden stellen die Computezeit im Zusammenhang mit diesen Batchaufträgen dar. Zur Berechnung der Kosten für BES-Produktions-API-Transaktionen wird die Gesamtzahl der initiierten Aufträge mit dem Preis pro 1.000 Transaktionen (anteilsmäßig für die einzelnen Transaktionen) multipliziert. Zur Berechnung der Kosten für BES-Produktions-API-Berechnungsstunden wird die Summe der für die Ausführung der einzelnen Zeilen in Ihrem Auftrag benötigten Zeit mit der Gesamtzahl an Zeilen in Ihrem Auftrag, mit der Gesamtzahl an Aufträgen und mit dem Preis pro Produktions-API-Berechnungsstunde multipliziert. Bei Verwendung des Machine Learning-Rechners zeigt der Transaktionszähler die Anzahl von Aufträgen an, die ausgeführt werden sollen, und im Feld für die Zeit pro Transaktion wird die Gesamtzeit angezeigt, die zur Ausführung aller Zeilen in den einzelnen Aufträgen benötigt wird.

Beispiel für eine Standard S1-Überschreitung: Sie senden 100 Aufträge pro Tag, die jeweils 500 Zeilen umfassen und deren Ausführung jeweils 0,72 Sekunden dauert. Ihre monatlichen Überschreitungskosten für Produktions-API-Transaktionen betragen 1,55 USD (100 Aufträge pro Tag = 3.100 Aufträge/Monat * 0,50 USD je 1.000 API-Transaktionen). Die Kosten für Produktions-API-Berechnungsstunden liegen bei 620 USD (500 Zeilen * 0,72 Sek. * 3.100 Aufträge * 2 USD/Std.). Dies ergibt eine Gesamtsumme von 621,55 USD.

### <a name="azure-machine-learning-classic-web-services"></a>Klassische Azure Machine Learning-Webdienste
**Ist die nutzungsbasierte Bezahlung noch verfügbar?**

Ja. Klassische Webdienste sind in Azure Machine Learning weiterhin verfügbar.  

### <a name="azure-machine-learning-free-and-standard-tier"></a>Azure Machine Learning – Free- und Standard-Tarif
**Was ist im Free-Tarif von Azure Machine Learning inbegriffen?**

Der Free-Tarif von Azure Machine Learning soll Ihnen eine detaillierte Einführung in Azure Machine Learning Studio ermöglichen. Hierzu benötigen Sie für die Anmeldung nur ein Microsoft-Konto. Der Free-Tarif umfasst den kostenlosen Zugriff auf einen Azure Machine Learning Studio-Arbeitsbereich pro [Microsoft-Konto](https://www.microsoft.com/account/default.aspx). In diesem Tarif können Sie bis zu 10 GB Speicher nutzen und Modelle als Staging-APIs operationalisieren. Workloads werden im Free-Tarif nicht durch eine SLA abgedeckt und sind lediglich für Entwicklungszwecke und die private Nutzung vorgesehen. 

Arbeitsbereiche im Free-Tarif weisen die folgenden Einschränkungen auf:

* Workloads können nicht auf Daten zugreifen, indem sie eine Verbindung mit einem lokalen Server herstellen, auf dem SQL Server ausgeführt wird.
* Sie können keine neuen Resource Manager-basierten Webdienste bereitstellen.


**Was ist im Standard-Tarif und den Plänen von Azure Machine Learning inbegriffen?**

Der Standard-Tarif von Azure Machine Learning ist eine kostenpflichtige Produktionsversion von Azure Machine Learning Studio. Die Monatsgebühr für Azure Machine Learning Studio wird pro Arbeitsbereich und Monat in Rechnung gestellt. Angefangene Monate werden anteilig abgerechnet. Azure Machine Learning Studio-Versuchstunden werden pro Computestunde für aktive Versuche (Experimente) in Rechnung gestellt. Angefangene Stunden werden anteilig abgerechnet.  

Die Berechnung des Azure Machine Learning-API-Diensts richtet sich danach, ob es sich um einen klassischen Webdienst oder einen neuen (Resource Manager-basierten) Webdienst handelt.

Die unten angegebenen Kosten werden pro Arbeitsbereich für Ihr Abonnement aggregiert.

* Machine Learning-Arbeitsbereich-Abonnement: Das Machine Learning-Arbeitsbereich-Abonnement umfasst eine Monatsgebühr, die Zugriff auf einen Machine Learning-Arbeitsbereich ermöglicht. Das Abonnement ist zum Ausführen von Experimenten in Studio sowie für die Nutzung der Produktions-APIs erforderlich.
* Studio-Versuchstunden: Hierbei werden alle Computegebühren zusammengefasst, die durch laufende Experimente in Machine Learning Studio und laufende Produktions-API-Aufrufe in der Stagingumgebung anfallen.
* Greifen Sie auf Daten zu, indem Sie eine Verbindung mit einem lokalen Server, auf dem SQL Server ausgeführt wird, in Ihren Modellen für Training und Bewertung herstellen.
* Für klassische Webdienste:
  * Produktions-API-Berechnungsstunden: Dieser Zähler umfasst Computegebühren, die durch in der Produktion ausgeführte Webdienste anfallen.
  * Produktions-API-Transaktionen (in 1000): Dieser Zähler umfasst die Gebühren, die pro Aufruf Ihres Produktionswebdiensts anfallen.

Abgesehen von den oben genannten Gebühren werden die Gebühren für neue (Resource Manager-basierte) Webdienste anhand des ausgewählten Plans aggregiert:

* API-Plan Standard-S1/S2/S3 (Einheiten): Dieser Zähler steht für den Typ der Instanz, der für Resource Manager-basierte Webdienste ausgewählt wurde.
* Überschreitung API-Computestunden Standard-S1/S2/S3 (Einheiten): Enthält Computegebühren, die für die in der Produktion ausgeführten Resource Manager-basierten Webdienste anfallen, nachdem die enthaltenen Mengen in vorhandenen Instanzen aufgebraucht sind. Die zusätzliche Nutzung wird anhand der Überschreitungsrate berechnet, die dem Tarif des S1/S2/S3-Plans zugeordnet ist.
* Überschreitung API-Transaktionen Standard-S1/S2/S3 (in 1.000): Enthält Gebühren, die pro Aufruf Ihres Resource Manager-basierten Webdiensts für die Produktion anfallen, nachdem die enthaltenen Mengen in vorhandenen Instanzen aufgebraucht sind. Die zusätzliche Nutzung wird anhand der Überschreitungsrate berechnet, die dem Tarif des S1/S2/S3-Plans zugeordnet ist.
* Enthaltene Menge an API-Computestunden: Umfasst bei Resource Manager-basierten Webdiensten die enthaltene Menge von API-Computestunden.
* Enthaltene Menge an API-Transaktionen (in 1.000): Umfasst bei Resource Manager-basierten Webdiensten die enthaltene Menge von API-Transaktionen.

**Wie registriere ich mich für den Free-Tarif von Azure Machine Learning?**

Dazu benötigen Sie nur ein Microsoft-Konto. Wechseln Sie zur [Azure Machine Learning-Startseite](https://azure.microsoft.com/services/machine-learning/), und klicken Sie dann auf **Jetzt starten**. Melden Sie sich mit Ihrem Microsoft-Konto an. Daraufhin wird für Sie im Free-Tarif ein Arbeitsbereich erstellt. Sie können Machine Learning sofort erkunden und Experimente erstellen.

**Wie registriere ich mich für den Standard-Tarif von Azure Machine Learning?**

Zunächst benötigen Sie Zugriff auf ein Azure-Abonnement, um einen Machine Learning-Arbeitsbereich vom Typ „Standard“ erstellen zu können. Sie können sich für ein 30-tägiges, kostenloses Azure-Testabonnement registrieren und später ein Upgrade auf ein kostenpflichtiges Azure-Abonnement durchführen oder direkt ein kostenpflichtiges Azure-Abonnement erwerben. Sobald Sie Zugriff auf das Abonnement haben, können Sie über das Microsoft Azure-Portal einen Machine Learning-Arbeitsbereich erstellen. Lesen Sie die [Schritt-für-Schritt-Anleitungen](https://azure.microsoft.com/trial/get-started-machine-learning-b/).

Alternativ können Sie auch von einem Besitzer eines Machine Learning-Arbeitsbereichs vom Typ „Standard“ dazu eingeladen werden, auf den Arbeitsbereich des Besitzers zuzugreifen.

**Kann ich für die Verwendung im Free-Tarif mein eigenes Azure Blob Storage-Konto angeben?**

Nein. Der Standard-Tarif entspricht der Version des Machine Learning-Diensts, die vor der Einführung der Tarife verfügbar war.

**Kann ich meine Machine Learning-Modelle im Free-Tarif als APIs bereitstellen?**

Ja. Sie können Machine Learning-Modelle im Rahmen des Free-Tarifs mit Staging-API-Diensten operationalisieren. Um den Staging-API-Dienst in die Produktion zu übergeben und einen Produktionsendpunkt für den standardisierten Dienst abzurufen, müssen Sie den Standard-Tarif verwenden.

**Worin besteht der Unterschied zwischen der kostenlosen Testversion von Azure und dem Free-Tarif von Azure Machine Learning?**

Die [kostenlose Testversion von Microsoft Azure](https://azure.microsoft.com/free/) bietet Gutschriften, die einen Monat lang für jeden Azure-Dienst genutzt werden können. Der Free-Tarif von Azure Machine Learning hingegen stellt vor allem einen kontinuierlichen Zugriff auf Azure Machine Learning für produktionsfremde Workloads sicher.

**Wie verschiebe ich ein Experiment vom Free-Tarif in den Standard-Tarif?**

Gehen Sie wie folgt vor, um Ihre Experimente aus dem Free-Tarif in den Standard-Tarif zu kopieren:

1. Melden Sie sich bei Azure Machine Learning Studio an, und vergewissern Sie sich, dass Ihnen in der Arbeitsbereichauswahl in der oberen Navigationsleiste der Free- und der Standard-Arbeitsbereich angezeigt werden.
2. Wechseln Sie zum Free-Arbeitsbereich, wenn Sie sich im Standard-Arbeitsbereich befinden.
3. Wählen Sie in der Experimentlistenansicht ein zu kopierendes Experiment aus, und klicken Sie dann auf die Befehlsschaltfläche **Kopieren**.
4. Wählen Sie im angezeigten Dialogfeld den Standard-Arbeitsbereich aus, und klicken Sie dann auf die Schaltfläche **Kopieren**.
   Alle zugehörigen Datasets, Trainingsmodelle usw. werden zusammen mit dem Experiment in den Standard-Arbeitsbereich kopiert.
5. Sie müssen das Experiment erneut ausführen und Ihren Webdienst erneut im Standard-Arbeitsbereich veröffentlichen.

### <a name="studio-workspace"></a>Studio-Arbeitsbereich
**Bekomme ich verschiedene Rechnungen für unterschiedliche Arbeitsbereiche?**

Die Gebühren für den Arbeitsbereich werden separat für jede anwendbare Messgröße auf einer Gesamtrechnung ausgewiesen.

**Auf welcher Art von Computeressourcen werden meine Experimente ausgeführt?**

Der Machine Learning-Dienst ist ein mehrinstanzenfähiger Dienst. Die eigentlichen Computeressourcen, die auf dem Back-End verwendet werden, variieren und wurden in Bezug auf die Leistung und die Vorhersagbarkeit optimiert.

### <a name="guest-access"></a>Gastzugriff
**Was umfasst der Gastzugriff für Azure Machine Learning Studio?**

Über den Gastzugriff können Sie Azure Machine Learning Studio in begrenztem Umfang testen. Sie können die Umgebung kostenlos und ohne Authentifizierung nutzen, um in Azure Machine Learning Studio Experimente zu erstellen und auszuführen. Gastsitzungen sind nicht persistent (können nicht gespeichert werden) und auf acht Stunden begrenzt. Außerdem werden R und Python nicht unterstützt, es können keine Staging-APIs verwendet werden, und sowohl die Größe von Datasets als auch die Speicherkapazität sind beschränkt. Im Gegensatz dazu haben Benutzer, die sich mit einem Microsoft-Konto anmelden, vollen Zugriff auf den oben beschriebenen Funktionsumfang von Machine Learning Studio im Free-Tarif, der einen persistenten Arbeitsbereich und umfangreichere Optionen bietet. Wenn Sie Machine Learning kostenlos nutzen möchten, können Sie unter [https://studio.azureml.net](https://studio.azureml.net) einfach auf **Erste Schritte** klicken und dann entweder den **Gastzugriff** oder die Anmeldung über ein Microsoft-Konto wählen.

<!-- Module References -->
[image-reader]: https://msdn.microsoft.com/library/azure/893f8c57-1d36-456d-a47b-d29ae67f5d84/
[join]: https://msdn.microsoft.com/library/azure/124865f7-e901-4656-adac-f4cb08248099/
[machine-learning-modules]: https://msdn.microsoft.com/library/azure/6d9e2516-1343-4859-a3dc-9673ccec9edc/
[partition-and-sample]: https://msdn.microsoft.com/library/azure/a8726e34-1b3e-4515-b59a-3e4a475654b8/
[import-data]: https://msdn.microsoft.com/library/azure/4e1b0fe6-aded-4b3f-a36f-39b8862b9004/
[export-data]: https://msdn.microsoft.com/library/azure/7A391181-B6A7-4AD4-B82D-E419C0D6522C
[split]: https://msdn.microsoft.com/library/azure/70530644-c97a-4ab6-85f7-88bf30a8be5f/
[python]: https://msdn.microsoft.com/library/azure/CDB56F95-7F4C-404D-BDE7-5BB972E6F232
[counts]: https://msdn.microsoft.com/library/azure/dn913056.aspx
