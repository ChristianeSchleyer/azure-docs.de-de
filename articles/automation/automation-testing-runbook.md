---
title: Testen eines Runbooks in Azure Automation
description: Bevor Sie ein Runbook in Azure Automation veröffentlichen, können Sie es testen, um sicherzustellen, dass es wie erwartet funktioniert.  In diesem Artikel wird beschrieben, wie Sie ein Runbook testen und die Ausgabe anzeigen.
services: automation
ms.service: automation
ms.component: process-automation
author: georgewallace
ms.author: gwallace
ms.date: 03/16/2018
ms.topic: conceptual
manager: carmonm
ms.openlocfilehash: ebeaa8eb75373fc94f7e4e714e36d1167fd7f060
ms.sourcegitcommit: eb75f177fc59d90b1b667afcfe64ac51936e2638
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="testing-a-runbook-in-azure-automation"></a>Testen eines Runbooks in Azure Automation
Wenn Sie ein Runbook testen, wird die [Entwurfsversion](automation-creating-importing-runbook.md#publishing-a-runbook) ausgeführt, und alle darin ausgeführten Aktionen werden abgeschlossen. Es wird kein Auftragsverlauf erstellt, aber die [Ausgabe](automation-runbook-output-and-messages.md#output-stream)- sowie die [Warnungs- und Fehlerdatenströme](automation-runbook-output-and-messages.md#message-streams) werden im Testausgabebereich angezeigt. Nachrichten an den [ausführlichen Datenstrom](automation-runbook-output-and-messages.md#message-streams) werden im Ausgabebereich nur angezeigt, wenn die Variable [$VerbosePreference](automation-runbook-output-and-messages.md#preference-variables) auf „Continue“ festgelegt ist.

Auch wenn die Entwurfsversion ausgeführt wird, führt das Runbook den Workflow trotzdem normal aus und wendet alle Aktionen auf die Ressourcen in der Umgebung an. Aus diesem Grund sollten Sie nur Runbooks für Ressourcen testen, die sich nicht in der Produktionsumgebung befinden.

Das Verfahren zum Testen der verschiedenen [Runbooktypen](automation-runbook-types.md) ist identisch, und es besteht kein Unterschied zwischen Tests mit dem Text-Editor und dem grafischen Editor im Azure-Portal.  

## <a name="to-test-a-runbook-in-the-azure-portal"></a>So starten Sie ein Runbook im Azure-Portal
Sie können mit jedem [Runbooktyp](automation-runbook-types.md) im Azure-Portal arbeiten.

1. Öffnen Sie die Entwurfsversion des Runbooks entweder im [Text-Editor](automation-edit-textual-runbook.md) oder im [grafischen Editor](automation-graphical-authoring-intro.md).
2. Klicken Sie auf die Schaltfläche **Test** um das Blatt "Test" zu öffnen.
3. Wenn das Runbook über Parameter verfügt, werden diese im linken Bereich aufgeführt. Hier können Sie die für den Test zu verwendenden Werte angeben.
4. Wenn Sie den Test auf einem [Hybrid Runbook Worker](automation-hybrid-runbook-worker.md), ausführen möchten, ändern Sie die **Testlaufeinstellungen** auf **Hybrid Worker**, und wählen Sie den Namen der Zielgruppe aus.  Andernfalls behalten Sie den Standardwert **Azure** bei, um den Test in der Cloud auszuführen.
5. Klicken Sie auf die Schaltfläche **Start** , um den Test zu starten.
6. Wenn das Runbook ein [PowerShell-Workflow](automation-runbook-types.md#powershell-workflow-runbooks) oder [grafisch](automation-runbook-types.md#graphical-runbooks) ist, können Sie es während des Tests mit den Schaltflächen unterhalb des Ausgabebereichs beenden oder anhalten. Wenn Sie das Runbook anhalten, wird die aktuelle Aktivität vor der Unterbrechung abgeschlossen. Nachdem das Runbook angehalten wurde, können Sie es beenden oder erneut starten.
7. Untersuchen Sie die Ausgabe des Runbooks im Ausgabebereich.

## <a name="next-steps"></a>Nächste Schritte
* Informationen zum Erstellen oder Importieren eines Runbooks finden Sie unter [Erstellen oder Importieren eines Runbooks in Azure Automation](automation-creating-importing-runbook.md)
* Weitere Informationen zur grafischen Inhaltserstellung finden Sie unter [Grafische Erstellung in Azure Automation](automation-graphical-authoring-intro.md)
* Die ersten Schritte mit PowerShell-Workflow-Runbooks sind unter [Mein erstes PowerShell-Workflow-Runbook](automation-first-runbook-textual.md)
* Weitere Informationen zum Konfigurieren von Runbooks für die Rückgabe von Statusmeldungen und Fehlern einschließlich der empfohlenen Methoden finden Sie unter [Runbookausgabe und -meldungen in Azure Automation](automation-runbook-output-and-messages.md)

