---
title: Starten und Beenden von Azure Stack | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Azure Stack starten und herunterfahren.
services: azure-stack
documentationcenter: ''
author: jeffgilb
manager: femila
editor: ''
ms.assetid: 43BF9DCF-F1B7-49B5-ADC5-1DA3AF9668CA
ms.service: azure-stack
ms.workload: na
pms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 04/09/2018
ms.author: jeffgilb
ms.reviewer: misainat
ms.openlocfilehash: 53015ba5c282bbe9c7b8185b080ffb6d834b6c75
ms.sourcegitcommit: 9cdd83256b82e664bd36991d78f87ea1e56827cd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="start-and-stop-azure-stack"></a>Starten und Beenden von Azure Stack
Sie sollten die Verfahren in diesem Artikel befolgen, um Azure Stack-Dienste ordnungsgemäß herunterzufahren und neu zu starten. 

## <a name="stop-azure-stack"></a>Beenden von Azure Stack 

Fahren Sie Azure Stack mithilfe der folgenden Schritte herunter:

1. Öffnen Sie auf einem Computer mit Netzwerkzugriff auf die Azure Stack ERCS-VMs eine PEP-Sitzung (privilegierter Endpunkt). Anweisungen finden Sie unter [Verwenden des privilegierten Endpunkts in Azure Stack](azure-stack-privileged-endpoint.md).

2. Führen Sie in der PEP-Sitzung Folgendes aus:

    ```powershell
      Stop-AzureStack
    ```

3. Warten Sie, bis alle physischen Azure Stack-Knoten ausgeschaltet sind.

> [!Note]  
> Sie können den Status eines physischen Knotens überprüfen, indem Sie die Anweisungen des Originalgeräteherstellers befolgen, der Ihre Azure Stack-Hardware bereitgestellt hat. 

## <a name="start-azure-stack"></a>Starten von Azure Stack 

Starten Sie Azure Stack mithilfe der folgenden Schritte. Führen Sie diese Schritte unabhängig davon aus, wie Azure Stack beendet wurde.

1. Schalten Sie jeden der physischen Knoten in Ihrer Azure Stack-Umgebung ein. Lesen Sie zum Einschalten der physischen Knoten die Anweisungen des Originalgeräteherstellers, der die Hardware für Azure Stack bereitgestellt hat.

2. Warten Sie, bis die Azure Stack-Infrastrukturdienste gestartet wurden. Es kann zwei Stunden dauern, bis der Startvorgang der Azure Stack-Infrastrukturdienste abgeschlossen ist. Sie können den Status von Azure Stack mit dem Cmdlet [**Get-ActionStatus**](#get-the-startup-status-for-azure-stack) überprüfen.


## <a name="get-the-startup-status-for-azure-stack"></a>Abrufen des Startstatus für Azure Stack

Rufen Sie den Startstatus für die Azure Stack-Startroutine mit den folgenden Schritten ab:

1. Öffnen Sie auf einem Computer mit Netzwerkzugriff auf die Azure Stack ERCS-VMs eine PEP-Sitzung (privilegierter Endpunkt).

2. Führen Sie in der PEP-Sitzung Folgendes aus:

    ```powershell
      Get-ActionStatus Start-AzureStack
    ```

## <a name="troubleshoot-startup-and-shutdown-of-azure-stack"></a>Problembehandlung für das Starten und Herunterfahren von Azure Stack

Führen Sie die folgenden Schritte aus, wenn die Infrastruktur- und Mandantendienste zwei Stunden nach dem Einschalten der Azure Stack-Umgebung nicht erfolgreich gestartet werden. 

1. Öffnen Sie auf einem Computer mit Netzwerkzugriff auf die Azure Stack ERCS-VMs eine PEP-Sitzung (privilegierter Endpunkt).

2. Führen Sie folgenden Befehl aus: 

    ```powershell
      Test-AzureStack
      ```

3. Überprüfen Sie die Ausgabe, und lösen Sie alle Probleme in Bezug auf die Integrität. Weitere Informationen finden Sie unter [Ausführen eines Validierungstests für Azure Stack](azure-stack-diagnostic-test.md).

4. Führen Sie folgenden Befehl aus:

    ```powershell
      Start-AzureStack
    ```

5. Wenn die Ausführung von **Start-AzureStack** zu einem Fehler führt, wenden Sie sich an den Microsoft-Kundendienst. 

## <a name="next-steps"></a>Nächste Schritte 

Weitere Informationen zu Azure Stack-Diagnosetools und zur Protokollierung von Problemen finden Sie unter [Azure Stack-Diagnosetools](azure-stack-diagnostics.md).
