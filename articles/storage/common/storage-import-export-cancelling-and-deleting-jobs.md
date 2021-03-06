---
title: Abbrechen und Löschen eines Azure Import/Export-Auftrags | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Aufträge für den Microsoft Azure Import/Export-Dienst abbrechen und löschen.
author: muralikk
manager: syadav
editor: tysonn
services: storage
documentationcenter: ''
ms.assetid: fd3d66f0-1dbb-4c75-9223-307d5abaeefc
ms.service: storage
ms.workload: storage
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 01/23/2017
ms.author: muralikk
ms.openlocfilehash: 3524f1677baaa218b009b8498b851390c7b9da9a
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2018
---
# <a name="canceling-and-deleting-azure-importexport-jobs"></a>Abbrechen und Löschen von Azure Import/Export-Aufträgen

 Um anzufordern, dass ein Auftrag abgebrochen wird, bevor er den Status `Packaging` aufweist, rufen Sie den Vorgang zum Aktualisieren der Auftragseigenschaften ([Update Job Properties](/rest/api/storageimportexport/jobs#Jobs_Update)) auf und legen das `CancelRequested`-Element auf `true` fest. Der Auftrag wird auf Grundlage der besten Leistung abgebrochen. Wenn Laufwerke gerade Daten übertragen, wird die Datenübertragung möglicherweise auch nach der Abbruchanforderung fortgesetzt.

 Ein abgebrochener Auftrag wechselt in den Zustand `Completed` und wird 90 Tage lang aufbewahrt. Anschließend wird er gelöscht.

 Zum Löschen eines Auftrags rufen Sie den Vorgang zum Löschen des Auftrags ([Delete Job](/rest/api/storageimportexport/jobs#Jobs_Delete)) auf, bevor der Auftrag gesendet wird (d.h. während der Auftrag den Status `Creating` hat). Sie können einen Auftrag auch löschen, wenn er den Status `Completed` aufweist. Nachdem ein Auftrag gelöscht wurde, sind die zugehörigen Informationen und der Status nicht mehr über die REST-API oder das Azure-Portal zugänglich.

[!INCLUDE [storage-import-export-delete-personal-info.md](../../../includes/storage-import-export-delete-personal-info.md)]

## <a name="next-steps"></a>Nächste Schritte

* [Verwenden der REST-API des Import/Export-Diensts](storage-import-export-using-the-rest-api.md)
