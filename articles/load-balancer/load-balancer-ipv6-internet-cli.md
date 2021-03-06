---
title: Erstellen eines öffentlichen Lastenausgleichs mit IPv6 – Azure CLI | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie einen öffentlichen Lastenausgleich mit IPv6 in Azure Resource Manager über die Azure-Befehlszeilenschnittstelle erstellen.
services: load-balancer
documentationcenter: na
author: KumudD
manager: timlt
tags: azure-resource-manager
keywords: IPv6, Azure Load Balancer, dualer Stapel, öffentliche IP, natives IPv6, mobil, IoT
ms.assetid: a1957c9c-9c1d-423e-9d5c-d71449bc1f37
ms.service: load-balancer
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 09/25/2017
ms.author: kumud
ms.openlocfilehash: 62f22ccadfabd2f3d6906beb3c241703d4e6383f
ms.sourcegitcommit: c3d53d8901622f93efcd13a31863161019325216
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2018
---
# <a name="create-a-public-load-balancer-with-ipv6-in-azure-resource-manager-by-using-azure-cli"></a>Erstellen eines öffentlichen Lastenausgleichs mit IPv6 in Azure Resource Manager über die Azure-Befehlszeilenschnittstelle

> [!div class="op_single_selector"]
> * [PowerShell](load-balancer-ipv6-internet-ps.md)
> * [Azure-Befehlszeilenschnittstelle](load-balancer-ipv6-internet-cli.md)
> * [Vorlage](load-balancer-ipv6-internet-template.md)


Ein Azure Load Balancer ist ein Layer-4-Load Balancer (TCP, UDP). Lastenausgleichsmodule sorgen für Hochverfügbarkeit, indem sie eingehenden Datenverkehr zwischen funktionierenden Dienstinstanzen in Clouddiensten oder auf virtuelle Computer in einer Lastenausgleichsgruppe verteilen. Lastenausgleichsmodule können diese Dienste auch auf mehreren Ports, mehreren IP-Adressen oder beidem leisten.

## <a name="example-deployment-scenario"></a>Beispielszenario für die Bereitstellung

Das folgende Diagramm veranschaulicht die Lösung mit Lastenausgleich, die mithilfe der in diesem Artikel beschriebenen Beispielvorlage bereitgestellt wird.

![Load Balancer-Szenarios](./media/load-balancer-ipv6-internet-cli/lb-ipv6-scenario-cli.png)

In diesem Szenario erstellen Sie die folgenden Azure-Ressourcen:

* zwei virtuelle Computer (VMs)
* eine virtuelle Netzwerkschnittstelle für jeden virtuellen Computer mit zugewiesenen IPv4- und IPv6-Adressen
* einen öffentlichen Lastenausgleich mit je einer öffentlichen IPv4- und IPv6-IP-Adresse
* eine Verfügbarkeitsgruppe, die die zwei virtuellen Computer enthält
* zwei Lastenausgleichsregeln, um die öffentlichen virtuellen IP-Adressen den privaten Endpunkten zuzuordnen

## <a name="deploy-the-solution-by-using-azure-cli"></a>Bereitstellen der Lösung mithilfe der Azure-Befehlszeilenschnittstelle

Die folgenden Schritte zeigen, wie Sie einen öffentlichen Lastenausgleich mit Azure Resource Manager und der Azure-Befehlszeilenschnittstelle erstellen. Mit Azure Resource Manager werden die einzelnen Teilobjekte erstellt sowie individuell konfiguriert und dann zusammengeführt, um eine Ressource zu erstellen.

Erstellen und konfigurieren Sie die folgenden Objekte, um einen Lastenausgleich bereitzustellen:

* **Front-End-IP-Konfiguration**: Enthält öffentliche IP-Adressen für eingehenden Netzwerkdatenverkehr.
* **Back-End-Adresspool**: Enthält Netzwerkschnittstellen (NICs), die virtuellen Computern den Empfang von Netzwerkdatenverkehr des Lastenausgleichs ermöglichen.
* **Lastenausgleichsregeln**: Enthält Regeln, die einen öffentlichen Port des Lastenausgleichs einem Port im Back-End-Adresspool zuordnen.
* **NAT-Eingangsregeln**: Enthält Netzwerkadressübersetzungs-Regeln (Network Address Translation, NAT), die einen öffentlichen Port des Lastenausgleichs einem Port für einen bestimmten virtuellen Computer im Back-End-Adresspool zuordnen.
* **Tests**: Enthält Integritätstests zum Prüfen der Verfügbarkeit von VM-Instanzen im Back-End-Adresspool.

Weitere Informationen finden Sie unter [Unterstützung des Azure Resource Managers für Load Balancer](load-balancer-arm.md).

## <a name="set-up-your-azure-cli-environment-to-use-azure-resource-manager"></a>Einrichten der Azure CLI-Umgebung zur Verwendung von Azure Resource Manager

In diesem Beispiel führen Sie die Azure CLI-Tools in einem PowerShell-Befehlsfenster aus. Sie verwenden nicht die Azure PowerShell-Cmdlets, sondern die PowerShell-Skriptfunktionen, um Lesbarkeit und Wiederverwendung zu verbessern.

1. Wenn Sie die Azure-Befehlszeilenschnittstelle noch nie verwendet haben, ziehen Sie [Installieren von Azure CLI 1.0](../cli-install-nodejs.md) zurate, und folgen Sie den Anweisungen bis zu dem Punkt, an dem Sie Ihr Azure-Konto und Ihr Abonnement auswählen.

2. Führen Sie den Befehl **azure config mode** aus, um in den Resource Manager-Modus zu wechseln:

    ```azurecli
    azure config mode arm
    ```

    Erwartete Ausgabe:

        info:    New mode is arm

3. Melden Sie sich bei Azure an, und rufen Sie eine Liste der Abonnements ab:

    ```azurecli
    azure login
    ```

4. Geben Sie an der Eingabeaufforderung Ihre Azure-Anmeldeinformationen ein:

    ```azurecli
    azure account list
    ```

5. Wählen Sie das Abonnement aus, das Sie verwenden möchten, und notieren Sie sich die Abonnement-ID für den nächsten Schritt.

6. Richten Sie PowerShell-Variablen für die Verwendung mit den Azure CLI-Befehlen ein:

    ```powershell
    $subscriptionid = "########-####-####-####-############"  # enter subscription id
    $location = "southcentralus"
    $rgName = "pscontosorg1southctrlus09152016"
    $vnetName = "contosoIPv4Vnet"
    $vnetPrefix = "10.0.0.0/16"
    $subnet1Name = "clicontosoIPv4Subnet1"
    $subnet1Prefix = "10.0.0.0/24"
    $subnet2Name = "clicontosoIPv4Subnet2"
    $subnet2Prefix = "10.0.1.0/24"
    $dnsLabel = "contoso09152016"
    $lbName = "myIPv4IPv6Lb"
    ```

## <a name="create-a-resource-group-a-load-balancer-a-virtual-network-and-subnets"></a>Erstellen einer Ressourcengruppe, eines Load Balancers, eines virtuellen Netzwerks und der Subnetze

1. Erstellen Sie eine Ressourcengruppe:

    ```azurecli
    azure group create $rgName $location
    ```

2. Erstellen Sie einen Lastenausgleich:

    ```azurecli
    $lb = azure network lb create --resource-group $rgname --location $location --name $lbName
    ```

3. Erstellen Sie ein virtuelles Netzwerk:

    ```azurecli
    $vnet = azure network vnet create  --resource-group $rgname --name $vnetName --location $location --address-prefixes $vnetPrefix
    ```

4. Erstellen Sie in diesem virtuellen Netzwerk zwei Subnetze:

    ```azurecli
    $subnet1 = azure network vnet subnet create --resource-group $rgname --name $subnet1Name --address-prefix $subnet1Prefix --vnet-name $vnetName
    $subnet2 = azure network vnet subnet create --resource-group $rgname --name $subnet2Name --address-prefix $subnet2Prefix --vnet-name $vnetName
    ```

## <a name="create-public-ip-addresses-for-the-front-end-pool"></a>Erstellen öffentlicher IP-Adressen für den Front-End-Pool

1. Richten Sie die PowerShell-Variablen ein:

    ```powershell
    $publicIpv4Name = "myIPv4Vip"
    $publicIpv6Name = "myIPv6Vip"
    ```

2. Erstellen Sie eine öffentliche IP-Adresse für den Front-End-IP-Pool:

    ```azurecli
    $publicipV4 = azure network public-ip create --resource-group $rgname --name $publicIpv4Name --location $location --ip-version IPv4 --allocation-method Dynamic --domain-name-label $dnsLabel
    $publicipV6 = azure network public-ip create --resource-group $rgname --name $publicIpv6Name --location $location --ip-version IPv6 --allocation-method Dynamic --domain-name-label $dnsLabel
    ```

    > [!IMPORTANT]
    > Der Lastenausgleich verwendet die Domänenbezeichnung der öffentlichen IP-Adresse als seinen vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN). Dies ist eine Abkehr von der klassischen Bereitstellung, bei der der Clouddienstname als FQDN des Load Balancers verwendet wird.
    >
    > In diesem Beispiel lautet der FQDN *contoso09152016.southcentralus.cloudapp.azure.com*.

## <a name="create-front-end-and-back-end-pools"></a>Erstellen von Front-End- und Back-End-Pools

In diesem Abschnitt erstellen Sie die folgenden IP-Pools:
* Front-End-IP-Pool, der den eingehenden Netzwerkdatenverkehr für den Lastenausgleich empfängt
* Back-End-IP-Pool, an den der Front-End-Pool den Netzwerkdatenverkehr sendet, für den ein Lastenausgleich durchgeführt wurde

1. Richten Sie die PowerShell-Variablen ein:

    ```powershell
    $frontendV4Name = "FrontendVipIPv4"
    $frontendV6Name = "FrontendVipIPv6"
    $backendAddressPoolV4Name = "BackendPoolIPv4"
    $backendAddressPoolV6Name = "BackendPoolIPv6"
    ```

2. Erstellen Sie einen Front-End-IP-Adresspool, und ordnen Sie ihn der im vorherigen Schritt erstellten öffentlichen IP-Adresse und dem Lastenausgleich zu.

    ```azurecli
    $frontendV4 = azure network lb frontend-ip create --resource-group $rgname --name $frontendV4Name --public-ip-name $publicIpv4Name --lb-name $lbName
    $frontendV6 = azure network lb frontend-ip create --resource-group $rgname --name $frontendV6Name --public-ip-name $publicIpv6Name --lb-name $lbName
    $backendAddressPoolV4 = azure network lb address-pool create --resource-group $rgname --name $backendAddressPoolV4Name --lb-name $lbName
    $backendAddressPoolV6 = azure network lb address-pool create --resource-group $rgname --name $backendAddressPoolV6Name --lb-name $lbName
    ```

## <a name="create-the-probe-nat-rules-and-load-balancer-rules"></a>Erstellen des Tests, der NAT-Regeln und der Lastenausgleichsregeln

In diesem Beispiel werden die folgenden Elemente erstellt:

* Testregel, um die Verbindung mit TCP-Port 80 zu überprüfen
* NAT-Regel, um sämtlichen eingehenden Datenverkehr an Port 3389 für Port 3389 für RDP zu übersetzen\*
* NAT-Regel, um sämtlichen eingehenden Datenverkehr an Port 3391 für Port 3389 für Remotedesktopprotokoll (RDP) zu übersetzen\*
* Lastenausgleichsregel für die gleichmäßige Verteilung des gesamten an Port 80 eingehenden Datenverkehrs an Port 80 der Adressen im Back-End-Pool

\* NAT-Regeln sind einer bestimmten Instanz eines virtuellen Computers hinter dem Lastenausgleichsmodul zugeordnet. Der an Port 3389 eingehende Netzwerkdatenverkehr wird an einen bestimmten virtuellen Computer und einen Port gesendet, die mit dieser NAT-Regel verknüpft sind. Sie müssen ein Protokoll (UDP oder TCP) für eine NAT-Regel angeben. Sie können nicht beide Protokolle dem gleichen Port zuweisen.

1. Richten Sie die PowerShell-Variablen ein:

    ```powershell
    $probeV4V6Name = "ProbeForIPv4AndIPv6"
    $natRule1V4Name = "NatRule-For-Rdp-VM1"
    $natRule2V4Name = "NatRule-For-Rdp-VM2"
    $lbRule1V4Name = "LBRuleForIPv4-Port80"
    $lbRule1V6Name = "LBRuleForIPv6-Port80"
    ```

2. Erstellen Sie den Test.

    Das folgende Beispiel erstellt einen TCP-Test, der alle 15 Sekunden die Verbindung mit Back-End-TCP-Port 80 überprüft. Nach zwei aufeinanderfolgenden Fehlern wird die Back-End-Ressource als nicht verfügbar markiert.

    ```azurecli
    $probeV4V6 = azure network lb probe create --resource-group $rgname --name $probeV4V6Name --protocol tcp --port 80 --interval 15 --count 2 --lb-name $lbName
    ```

3. Erstellen Sie eingehende NAT-Regeln, die RDP-Verbindungen mit Back-End-Ressourcen zulassen:

    ```azurecli
    $inboundNatRuleRdp1 = azure network lb inbound-nat-rule create --resource-group $rgname --name $natRule1V4Name --frontend-ip-name $frontendV4Name --protocol Tcp --frontend-port 3389 --backend-port 3389 --lb-name $lbName
    $inboundNatRuleRdp2 = azure network lb inbound-nat-rule create --resource-group $rgname --name $natRule2V4Name --frontend-ip-name $frontendV4Name --protocol Tcp --frontend-port 3391 --backend-port 3389 --lb-name $lbName
    ```

4. Erstellen Sie Lastenausgleichsregeln, die Datenverkehr abhängig davon, welches Front-End die Anforderung empfangen hat, an verschiedene Back-End-Ports senden.

    ```azurecli
    $lbruleIPv4 = azure network lb rule create --resource-group $rgname --name $lbRule1V4Name --frontend-ip-name $frontendV4Name --backend-address-pool-name $backendAddressPoolV4Name --probe-name $probeV4V6Name --protocol Tcp --frontend-port 80 --backend-port 80 --lb-name $lbName
    $lbruleIPv6 = azure network lb rule create --resource-group $rgname --name $lbRule1V6Name --frontend-ip-name $frontendV6Name --backend-address-pool-name $backendAddressPoolV6Name --probe-name $probeV4V6Name --protocol Tcp --frontend-port 80 --backend-port 8080 --lb-name $lbName
    ```

5. Überprüfen Sie Ihre Einstellungen:

    ```azurecli
    azure network lb show --resource-group $rgName --name $lbName
    ```

    Erwartete Ausgabe:

        info:    Executing command network lb show
        info:    Looking up the load balancer "myIPv4IPv6Lb"
        data:    Id                              : /subscriptions/########-####-####-####-############/resourceGroups/pscontosorg1southctrlus09152016/providers/Microsoft.Network/loadBalancers/myIPv4IPv6Lb
        data:    Name                            : myIPv4IPv6Lb
        data:    Type                            : Microsoft.Network/loadBalancers
        data:    Location                        : southcentralus
        data:    Provisioning state              : Succeeded
        data:
        data:    Frontend IP configurations:
        data:    Name             Provisioning state  Private IP allocation  Private IP   Subnet  Public IP
        data:    ---------------  ------------------  ---------------------  -----------  ------  ---------
        data:    FrontendVipIPv4  Succeeded           Dynamic                                     myIPv4Vip
        data:    FrontendVipIPv6  Succeeded           Dynamic                                     myIPv6Vip
        data:
        data:    Probes:
        data:    Name                 Provisioning state  Protocol  Port  Path  Interval  Count
        data:    -------------------  ------------------  --------  ----  ----  --------  -----
        data:    ProbeForIPv4AndIPv6  Succeeded           Tcp       80          15        2
        data:
        data:    Backend Address Pools:
        data:    Name             Provisioning state
        data:    ---------------  ------------------
        data:    BackendPoolIPv4  Succeeded
        data:    BackendPoolIPv6  Succeeded
        data:
        data:    Load Balancing Rules:
        data:    Name                  Provisioning state  Load distribution  Protocol  Frontend port  Backend port  Enable floating IP  Idle timeout in minutes
        data:    --------------------  ------------------  -----------------  --------  -------------  ------------  ------------------  -----------------------
        data:    LBRuleForIPv4-Port80  Succeeded           Default            Tcp       80             80            false               4
        data:    LBRuleForIPv6-Port80  Succeeded           Default            Tcp       80             8080          false               4
        data:
        data:    Inbound NAT Rules:
        data:    Name                 Provisioning state  Protocol  Frontend port  Backend port  Enable floating IP  Idle timeout in minutes
        data:    -------------------  ------------------  --------  -------------  ------------  ------------------  -----------------------
        data:    NatRule-For-Rdp-VM1  Succeeded           Tcp       3389           3389          false               4
        data:    NatRule-For-Rdp-VM2  Succeeded           Tcp       3391           3389          false               4
        info:    network lb show

## <a name="create-nics"></a>Erstellen von NICs

Erstellen Sie NICs, und ordnen Sie diese NAT-Regeln, Lastenausgleichsregeln und Tests zu.

1. Richten Sie die PowerShell-Variablen ein:

    ```powershell
    $nic1Name = "myIPv4IPv6Nic1"
    $nic2Name = "myIPv4IPv6Nic2"
    $subnet1Id = "/subscriptions/$subscriptionid/resourceGroups/$rgName/providers/Microsoft.Network/VirtualNetworks/$vnetName/subnets/$subnet1Name"
    $subnet2Id = "/subscriptions/$subscriptionid/resourceGroups/$rgName/providers/Microsoft.Network/VirtualNetworks/$vnetName/subnets/$subnet2Name"
    $backendAddressPoolV4Id = "/subscriptions/$subscriptionid/resourceGroups/$rgname/providers/Microsoft.Network/loadbalancers/$lbName/backendAddressPools/$backendAddressPoolV4Name"
    $backendAddressPoolV6Id = "/subscriptions/$subscriptionid/resourceGroups/$rgname/providers/Microsoft.Network/loadbalancers/$lbName/backendAddressPools/$backendAddressPoolV6Name"
    $natRule1V4Id = "/subscriptions/$subscriptionid/resourceGroups/$rgname/providers/Microsoft.Network/loadbalancers/$lbName/inboundNatRules/$natRule1V4Name"
    $natRule2V4Id = "/subscriptions/$subscriptionid/resourceGroups/$rgname/providers/Microsoft.Network/loadbalancers/$lbName/inboundNatRules/$natRule2V4Name"
    ```

2. Erstellen Sie eine NIC für jedes Back-End, und fügen Sie eine IPv6-Konfiguration hinzu:

    ```azurecli
    $nic1 = azure network nic create --name $nic1Name --resource-group $rgname --location $location --private-ip-version "IPv4" --subnet-id $subnet1Id --lb-address-pool-ids $backendAddressPoolV4Id --lb-inbound-nat-rule-ids $natRule1V4Id
    $nic1IPv6 = azure network nic ip-config create --resource-group $rgname --name "IPv6IPConfig" --private-ip-version "IPv6" --lb-address-pool-ids $backendAddressPoolV6Id --nic-name $nic1Name

    $nic2 = azure network nic create --name $nic2Name --resource-group $rgname --location $location --subnet-id $subnet1Id --lb-address-pool-ids $backendAddressPoolV4Id --lb-inbound-nat-rule-ids $natRule2V4Id
    $nic2IPv6 = azure network nic ip-config create --resource-group $rgname --name "IPv6IPConfig" --private-ip-version "IPv6" --lb-address-pool-ids $backendAddressPoolV6Id --nic-name $nic2Name
    ```

## <a name="create-the-back-end-vm-resources-and-attach-each-nic"></a>Erstellen der Back-End-VM-Ressourcen und Anfügen der NICs

Um VMs zu erstellen, benötigen Sie ein Speicherkonto. Für den Lastenausgleich müssen die VMs zu einer Verfügbarkeitsgruppe gehören. Weitere Informationen zum Erstellen von VMs finden Sie unter [Erstellen eines virtuellen Windows-Computers mit PowerShell](../virtual-machines/virtual-machines-windows-ps-create.md?toc=%2fazure%2fload-balancer%2ftoc.json).

1. Richten Sie die PowerShell-Variablen ein:

    ```powershell
    $storageAccountName = "ps08092016v6sa0"
    $availabilitySetName = "myIPv4IPv6AvailabilitySet"
    $vm1Name = "myIPv4IPv6VM1"
    $vm2Name = "myIPv4IPv6VM2"
    $nic1Id = "/subscriptions/$subscriptionid/resourceGroups/$rgname/providers/Microsoft.Network/networkInterfaces/$nic1Name"
    $nic2Id = "/subscriptions/$subscriptionid/resourceGroups/$rgname/providers/Microsoft.Network/networkInterfaces/$nic2Name"
    $disk1Name = "WindowsVMosDisk1"
    $disk2Name = "WindowsVMosDisk2"
    $osDisk1Uri = "https://$storageAccountName.blob.core.windows.net/vhds/$disk1Name.vhd"
    $osDisk2Uri = "https://$storageAccountName.blob.core.windows.net/vhds/$disk2Name.vhd"
    $imageurn "MicrosoftWindowsServer:WindowsServer:2012-R2-Datacenter:latest"
    $vmUserName = "vmUser"
    $mySecurePassword = "PlainTextPassword*1"
    ```

    > [!WARNING]
    > Dieses Beispiel verwendet den Benutzernamen und das Kennwort für die virtuellen Computer in Klartext. Bei Anmeldeinformationen in Klartext müssen Sie entsprechend vorsichtig vorgehen. Eine sicherere Methode zur Handhabung der Anmeldeinformationen in PowerShell finden Sie in den Informationen zum Cmdlet [`Get-Credential`](https://technet.microsoft.com/library/hh849815.aspx).

2. Erstellen Sie das Speicherkonto und die Verfügbarkeitsgruppe.

    Sie können beim Erstellen der virtuellen Computer ein vorhandenes Speicherkonto verwenden. Erstellen Sie mit dem folgenden Befehl ein neues Speicherkonto:

    ```azurecli
    $storageAcc = azure storage account create $storageAccountName --resource-group $rgName --location $location --sku-name "LRS" --kind "Storage"
    ```

3. Erstellen Sie die Verfügbarkeitsgruppe:

    ```azurecli
    $availabilitySet = azure availset create --name $availabilitySetName --resource-group $rgName --location $location
    ```

4. Erstellen Sie die virtuellen Computer mit den zugehörigen NICs:

    ```azurecli
    $vm1 = azure vm create --resource-group $rgname --location $location --availset-name $availabilitySetName --name $vm1Name --nic-id $nic1Id --os-disk-vhd $osDisk1Uri --os-type "Windows" --admin-username $vmUserName --admin-password $mySecurePassword --vm-size "Standard_A1" --image-urn $imageurn --storage-account-name $storageAccountName --disable-bginfo-extension

    $vm2 = azure vm create --resource-group $rgname --location $location --availset-name $availabilitySetName --name $vm2Name --nic-id $nic2Id --os-disk-vhd $osDisk2Uri --os-type "Windows" --admin-username $vmUserName --admin-password $mySecurePassword --vm-size "Standard_A1" --image-urn $imageurn --storage-account-name $storageAccountName --disable-bginfo-extension
    ```

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte zum Konfigurieren des internen Lastenausgleichs](load-balancer-get-started-ilb-arm-cli.md)  
[Konfigurieren eines Lastenausgleichs-Verteilungsmodus](load-balancer-distribution-mode.md)  
[Konfigurieren von TCP-Leerlauftimeout-Einstellungen für den Lastenausgleich](load-balancer-tcp-idle-timeout.md)
