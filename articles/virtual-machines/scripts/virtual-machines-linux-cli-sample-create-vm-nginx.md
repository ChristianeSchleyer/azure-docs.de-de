---
title: "Azure CLI-Skriptbeispiel – Erstellen einer Linux-VM mit NGINX | Microsoft-Dokumentation"
description: "Azure CLI-Skriptbeispiel – Erstellen einer Linux-VM mit NGINX"
services: virtual-machines-linux
documentationcenter: virtual-machines
author: neilpeterson
manager: timlt
editor: tysonn
tags: azure-resource-manager
ms.assetid: 
ms.service: virtual-machines-linux
ms.devlang: azurecli
ms.topic: sample
ms.tgt_pltfrm: vm-linux
ms.workload: infrastructure
ms.date: 02/27/2017
ms.author: nepeters
ms.custom: mvc
ms.openlocfilehash: a88077d405a662c0b5f83022209712545fea537f
ms.sourcegitcommit: 8c3267c34fc46c681ea476fee87f5fb0bf858f9e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2018
---
# <a name="create-a-vm-with-nginx"></a>Erstellen eines virtuellen Computers mit NGINX

Dieses Skript erstellt einen virtuellen Azure-Computer und verwendet die benutzerdefinierte Azure-VM-Skripterweiterung, um NGINX zu installieren. Nachdem das Skript ausgeführt wurde, können Sie die Demonstrationswebsite über die öffentliche IP-Adresse des virtuellen Computers aufrufen.

[!INCLUDE [sample-cli-install](../../../includes/sample-cli-install.md)]

[!INCLUDE [quickstarts-free-trial-note](../../../includes/quickstarts-free-trial-note.md)]

## <a name="sample-script"></a>Beispielskript

[!code-azurecli-interactive[main](../../../cli_scripts/virtual-machine/create-vm-nginx/create-vm-nginx.sh "Quick Create VM")]

## <a name="custom-script-extension"></a>Benutzerdefinierte Skripterweiterung

Die benutzerdefinierte Skripterweiterung kopiert das Skript auf den virtuellen Computer. Das Skript wird dann zum Installieren und Konfigurieren eines NGINX-Webservers ausgeführt. 

```bash
#!/bin/bash

# update package source
apt-get -y update

# install NGINX
apt-get -y install nginx
```

## <a name="clean-up-deployment"></a>Bereinigen der Bereitstellung 

Führen Sie den folgenden Befehl aus, um die Ressourcengruppe, den virtuellen Computer und alle zugehörigen Ressourcen zu entfernen.

```azurecli-interactive 
az group delete --name myResourceGroup
```

## <a name="script-explanation"></a>Erläuterung des Skripts

In diesem Skript werden die folgenden Befehle verwendet, um eine Ressourcengruppe, einen virtuellen Computer und alle zugehörigen Ressourcen zu erstellen. Jeder Befehl in der Tabelle ist mit der zugehörigen Dokumentation verknüpft.

| Get-Help | Notizen |
|---|---|
| [az group create](https://docs.microsoft.com/cli/azure/group#az_group_create) | Erstellt eine Ressourcengruppe, in der alle Ressourcen gespeichert sind. |
| [az vm create](https://docs.microsoft.com/cli/azure/vm#az_vm_create) | Erstellt den virtuellen Computer. Dieser Befehl legt außerdem das zu verwendende VM-Image und die Administratoranmeldeinformationen fest.  |
| [az vm open-port](https://docs.microsoft.com/cli/azure/network/nsg/rule#az_network_nsg_rule_create) | Erstellt eine Netzwerksicherheitsgruppenregel zum Zulassen von eingehendem Datenverkehr. In diesem Beispiel wird Port 80 für HTTP-Datenverkehr geöffnet. |
| [azure vm extension set](https://docs.microsoft.com/cli/azure/vm/extension#az_vm_extension_set) | Fügt eine VM-Erweiterung zu einem virtuellen Computer hinzu und führt diese aus. In diesem Beispiel wird die benutzerdefinierte Skripterweiterung zum Installieren von NGINX verwendet.|
| [az group delete](https://docs.microsoft.com/cli/azure/vm/extension#az_vm_extension_set) | Löscht eine Ressourcengruppe einschließlich aller geschachtelten Ressourcen. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Azure CLI finden Sie in der [Azure CLI-Dokumentation](https://docs.microsoft.com/cli/azure).

Zusätzliche VM-CLI-Skriptbeispiele finden Sie in der [Dokumentation zu Linux-VMs in Azure](../linux/cli-samples.md?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json).
