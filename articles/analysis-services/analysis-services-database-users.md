---
title: Verwalten von Datenbankrollen und Benutzern in Azure Analysis Services | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Datenbankrollen und Benutzer auf einem Analysis Services-Server in Azure verwalten.
author: minewiskan
manager: kfile
ms.service: analysis-services
ms.topic: conceptual
ms.date: 04/12/2018
ms.author: owend
ms.reviewer: minewiskan
ms.openlocfilehash: 3c35fb1ee70544b8b01bbadaf72ee38145179b27
ms.sourcegitcommit: 9cdd83256b82e664bd36991d78f87ea1e56827cd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="manage-database-roles-and-users"></a>Verwalten von Datenbankrollen und Benutzern

Auf Modelldatenbankebene müssen alle Benutzer einer Rolle zugewiesen sein. Rollen definieren Benutzer mit bestimmten Berechtigungen für die Modelldatenbank. Alle einer Rolle hinzugefügten Benutzer oder Sicherheitsgruppen müssen über ein Konto in einem Azure AD-Mandanten im gleichen Abonnement wie der Server verfügen.

Wie Sie Rollen definieren, hängt jeweils vom verwendeten Tool ab, das Ergebnis ist jedoch gleich.

Folgende Rollenberechtigungen stehen zur Verfügung:
*  **Administrator:** Benutzer verfügen über uneingeschränkte Berechtigungen für die Datenbank. Datenbankrollen mit Administratorberechtigungen unterscheiden sich von Serveradministratoren.
*  **Verarbeiten:** Benutzer können eine Verbindung mit Verarbeitungsvorgängen in der Datenbank herstellen und diese durchführen sowie Daten der Modelldatenbank analysieren.
*  **Lesen:** Benutzer können über eine Clientanwendung eine Verbindung mit Daten der Modelldatenbank herstellen und diese analysieren.

Wenn Sie ein Projekt für ein tabellarisches Modell erstellen, erstellen Sie mit dem Rollen-Manager in SSDT Rollen und fügen diesen Rollen Benutzer oder Gruppen hinzu. Bei Bereitstellung auf einem Server verwenden Sie SSMS, [Analysis Services-PowerShell-Cmdlets](https://msdn.microsoft.com/library/hh758425.aspx) oder [Tabular Model Scripting Language](https://msdn.microsoft.com/library/mt614797.aspx) (TMSL), um Rollen und Benutzermitglieder hinzuzufügen oder zu entfernen.

## <a name="to-add-or-manage-roles-and-users-in-ssdt"></a>So fügen Sie Rollen und Benutzer in SSDT hinzu oder verwalten diese  
  
1.  Klicken Sie in SSDT > **Explorer für tabellarische Modelle** mit der rechten Maustaste auf **Rollen**.  
  
2.  Klicken Sie im **Rollen-Manager** auf **Neu**.  
  
3.  Geben Sie einen Namen für die Rolle ein.  
  
     Standardmäßig wird der Name der Standardrolle bei jeder neuen Rolle fortlaufend nummeriert. Es wird empfohlen, dass Sie einen Namen eingeben, aus dem der Mitgliedstyp deutlich hervorgeht, z.B. „Finance Managers“ oder „Human Resources Specialists“.  
  
4.  Wählen Sie eine der folgenden Berechtigungen aus:  
  
    |Berechtigung|BESCHREIBUNG|  
    |----------------|-----------------|  
    |**Keine**|Mitglieder können das Modellschema nicht ändern und keine Daten abfragen.|  
    |**Lesen**|Mitglieder können (basierend auf Zeilenfiltern) Daten abfragen, jedoch das Modellschema nicht ändern.|  
    |**Lesen und Verarbeiten**|Mitglieder können Daten (basierend auf Zeilenfiltern) abfragen sowie Prozesse ausführen und alle Vorgänge verarbeiten, jedoch das Modellschema nicht ändern.|  
    |**Prozess**|Mitglieder können Prozesse ausführen und alle Vorgänge verarbeiten. Sie können das Modellschema nicht ändern und keine Daten abfragen.|  
    |**Administrator**|Mitglieder können das Modellschema ändern und alle Daten abfragen.|   
  
5.  Wenn die erstellte Rolle über die Berechtigung „Lesen“ oder „Lesen und Verarbeiten“ verfügt, können Sie mit einer DAX-Formel Zeilenfilter hinzufügen. Klicken Sie auf die Registerkarte **Zeilenfilter**, und wählen Sie eine Tabelle aus. Klicken Sie dann auf das Feld **DAX-Filter**, und geben Sie eine DAX-Formel ein.
  
6.  Klicken Sie auf **Mitglieder** > **Extern hinzufügen**.  
  
8.  Geben Sie in **Externes Element hinzufügen** Benutzer oder Gruppen nach E-Mail-Adresse in Ihrem Azure AD-Mandanten ein. Nachdem Sie auf „OK“ geklickt und den Rollen-Manager geschlossen haben, werden Rollen und Rollenmitglieder im Explorer für tabellarische Modelle angezeigt. 
 
     ![Rollen und Benutzer im Explorer für tabellarische Modelle](./media/analysis-services-database-users/aas-roles-tmexplorer.png)

9. Führen Sie die Bereitstellung auf dem Azure Analysis Services-Server durch.


## <a name="to-add-or-manage-roles-and-users-in-ssms"></a>So fügen Sie Rollen und Benutzer in SSMS hinzu oder verwalten diese
Zum Hinzufügen von Rollen und Benutzern zu einer bereitgestellten Modelldatenbank müssen Sie als Serveradministrator oder bereits in einer Datenbankrolle mit Administratorberechtigungen eine Verbindung mit dem Server hergestellt haben.

1. Klicken Sie im Objekt-Exporer mit der rechten Maustaste auf **Rollen** > **Neue Rolle**.

2. Geben Sie in **Rolle erstellen** einen Rollennamen und eine Beschreibung ein.

3. Wählen Sie eine Berechtigung aus.
   |Berechtigung|BESCHREIBUNG|  
   |----------------|-----------------|  
   |**Vollzugriff (Administrator)**|Mitglieder können das Modellschema ändern, Prozesse ausführen und alle Daten abfragen.| 
   |**Datenbank verarbeiten**|Mitglieder können Prozesse ausführen und alle Vorgänge verarbeiten. Sie können das Modellschema nicht ändern und keine Daten abfragen.|  
   |**Lesen**|Mitglieder können (basierend auf Zeilenfiltern) Daten abfragen, jedoch das Modellschema nicht ändern.|  
  
4. Klicken Sie auf **Mitgliedschaft**, und geben Sie einen Benutzer oder eine Gruppe nach E-Mail-Adresse in Ihrem Azure AD-Mandanten ein.

     ![Benutzer hinzufügen](./media/analysis-services-database-users/aas-roles-adduser-ssms.png)

5. Wenn die erstellte Rolle über die Berechtigung „Lesen“ verfügt, können Sie mit einer DAX-Formel Zeilenfilter hinzufügen. Klicken Sie auf **Zeilenfilter**, wählen Sie eine Tabelle aus, und geben Sie dann im Feld **DAX-Filter** eine DAX-Formel ein. 

## <a name="to-add-roles-and-users-by-using-a-tmsl-script"></a>So fügen Sie Rollen und Benutzer mit einem TMSL-Skript hinzu oder verwalten diese
Sie können ein TMSL-Skript im XMLA-Fenster in SSMS oder mithilfe von PowerShell ausführen. Verwenden Sie den Befehl [CreateOrReplace](https://docs.microsoft.com/sql/analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl) und das Objekt [Roles](https://docs.microsoft.com/sql/analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl).

**TMSL-Beispielskript**

In diesem Beispiel werden der Rolle „Analyst“ ein externer B2B-Benutzer und eine Gruppe mit Berechtigungen zum Lesen für die SalesBI-Datenbank hinzugefügt. Der externe Benutzer und die Gruppe müssen sich im gleichen Azure AD-Mandanten befinden.

```
{
  "createOrReplace": {
    "object": {
      "database": "SalesBI",
      "role": "Analyst"
    },
    "role": {
      "name": "Users",
      "description": "All allowed users to query the model",
      "modelPermission": "read",
      "members": [
        {
          "memberName": "user1@contoso.com",
          "identityProvider": "AzureAD"
        },
        {
          "memberName": "group1@adventureworks.com",
          "identityProvider": "AzureAD"
        }
      ]
    }
  }
}
```

## <a name="to-add-roles-and-users-by-using-powershell"></a>So fügen Sie Rollen und Benutzer mit PowerShell hinzu oder verwalten diese
Das [SqlServer](https://msdn.microsoft.com/library/hh758425.aspx)-Modul bietet aufgabenspezifische Cmdlets für die Datenbankverwaltung und das allgemeine Cmdlet „Invoke-ASCmd“, das TMSL-Abfragen (Tabular Model Scripting Language) und -Skripts akzeptiert. Die folgenden Cmdlets werden zum Verwalten von Datenbankrollen und Benutzern verwendet.
  
|Cmdlet|BESCHREIBUNG|
|------------|-----------------| 
|[Add-RoleMember](https://msdn.microsoft.com/library/hh510167.aspx)|Hinzufügen eines Mitglieds zu einer Datenbankrolle.| 
|[Remove-RoleMember](https://msdn.microsoft.com/library/hh510173.aspx)|Entfernen eines Mitglieds aus einer Datenbankrolle.|   
|[Invoke-ASCmd](https://msdn.microsoft.com/library/hh479579.aspx)|Ausführen eines TMSL-Skripts.|

## <a name="row-filters"></a>Zeilenfilter  
Zeilenfilter definieren, welche Zeilen in einer Tabelle von Mitgliedern einer bestimmten Rolle abgefragt werden können. Zeilenfilter werden mithilfe von DAX-Formeln für jede Tabelle in einem Modell definiert.  
  
Zeilenfilter können nur für Rollen mit den Berechtigungen „Lesen“ und „Lesen und Verarbeiten“ definiert werden. Wenn für eine bestimmte Tabelle kein Zeilenfilter definiert ist, können Mitglieder standardmäßig alle Zeilen in der Tabelle abfragen, sofern keine Kreuzfilterung aus einer anderen Tabelle gilt.
  
 Zeilenfilter erfordern eine DAX-Formel, die als TRUE- oder FALSE-Wert ausgewertet werden muss, um die Zeilen zu definieren, die von Mitgliedern dieser bestimmten Rolle abgefragt werden können. Zeilen, die in der DAX-Formel nicht enthalten sind, können nicht abgefragt werden. Bei der Tabelle „Customers“ mit dem Zeilenfilterausdruck *=Customers[Country]="USA"* können Mitglieder der Rolle „Sales“ beispielsweise nur Kunden in den USA anzeigen.  
  
Zeilenfilter gelten für die angegebenen Zeilen und zugehörige Zeilen. Wenn für eine Tabelle mehrere Beziehungen definiert sind, wenden Filter Sicherheitseinstellungen für die jeweils aktive Beziehung an. Zeilenfilter überschneiden sich mit anderen für zugehörige Tabellen definierte Zeilenfiltern, z.B.:  
  
|Table|DAX-Ausdruck|  
|-----------|--------------------|  
|Region|=Region[Country]="USA"|  
|ProductCategory|=ProductCategory[Name]="Bicycles"|  
|Transaktionen|=Transactions[Year]=2016|  
  
 Hier können Mitglieder Datenzeilen abfragen, bei denen der Kunde sich in den USA befindet, als Produktkategorie Fahrräder und als Jahr 2016 definiert ist. Benutzer können keine Transaktionen außerhalb der USA, keine Transaktionen, die keine Fahrräder betreffen, und keine Transaktionen abfragen, die nicht 2016 erfolgt sind, es sei denn, sie sind Mitglied einer anderen Rolle, mit der diese Berechtigungen erteilt werden.
  
 Mit dem Filter *=FALSE()* können Sie den Zugriff auf alle Zeilen für eine gesamte Tabelle verweigern.

## <a name="next-steps"></a>Nächste Schritte
  [Verwalten von Serveradministratoren](analysis-services-server-admins.md)   
  [Verwalten von Azure Analysis Services mit PowerShell](analysis-services-powershell.md)  
  [TMSL-Referenz (Tabular Model Scripting Language)](https://docs.microsoft.com/sql/analysis-services/tabular-model-scripting-language-tmsl-reference)

