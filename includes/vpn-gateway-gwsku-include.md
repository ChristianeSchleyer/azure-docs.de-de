---
title: Includedatei
description: Includedatei
services: vpn-gateway
author: cherylmc
ms.service: vpn-gateway
ms.topic: include
ms.date: 03/21/2018
ms.author: cherylmc
ms.custom: include file
ms.openlocfilehash: 05dc8ae48a9164e4f7118d378ab0eb7c30a4249e
ms.sourcegitcommit: 59914a06e1f337399e4db3c6f3bc15c573079832
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
ms.locfileid: "30196799"
---
Beim Erstellen eines Gateways des virtuellen Netzwerks müssen Sie die gewünschte Gateway-SKU angeben. Wählen Sie die SKU aus, die Ihre Anforderungen im Bezug auf Workloadtypen, Durchsätze, Funktionen und SLAs erfüllt.

###  <a name="benchmark"></a>Gateway-SKUs nach Tunnel, Verbindung und Durchsatz

[!INCLUDE [Aggregated throughput by SKU](./vpn-gateway-table-gwtype-aggtput-include.md)]

[!INCLUDE [classic SKU](./vpn-gateway-classic-sku-support-include.md)]

###  <a name="feature"></a>Gateway-SKUs nach Featuregruppe

Die neuen VPN-Gateway-SKUs optimieren die für die Gateways bereitgestellten Features:

| **SKU**| **Funktionen**|
| ---    | ---         |
|**Basic** (\*\*)   | **Routenbasiertes VPN**: Zehn Tunnel mit P2S; keine RADIUS-Authentifizierung für P2S; kein IKEv2 für P2S<br>**Richtlinienbasiertes VPN**: (IKEv1): 1 Tunnel; kein P2S|
| **VpnGw1, VpnGw2 und VpnGw3** | **Routenbasiertes VPN**: bis zu 30 Tunnel (\*), P2S, BGP, Aktiv/Aktiv, benutzerdefinierte IPsec-/IKE-Richtlinie, Koexistenz von ExpressRoute/VPN |
|        |             |

( * ) Sie können „PolicyBasedTrafficSelectors“ konfigurieren, um eine Verbindung zwischen einem routenbasierten VPN-Gateway (VpnGw1, VpnGw2, VpnGw3) und mehreren lokalen richtlinienbasierten Firewallgeräten herzustellen. Ausführliche Informationen finden Sie unter [Connect VPN gateways to multiple on-premises policy-based VPN devices using PowerShell](../articles/vpn-gateway/vpn-gateway-connect-multiple-policybased-rm-ps.md) (Herstellen einer Verbindung zwischen VPN-Gateways und mehreren lokalen richtlinienbasierten VPN-Geräten mit PowerShell).

(\*\*) Die Basic-SKU wird als Legacy-SKU betrachtet. Für die Basic-SKU gelten bestimmte Featurebeschränkungen. Die Größe eines Gateways mit einer Basic-SKU kann nicht auf eine der neuen Gateway-SKUs festgelegt werden. Stattdessen müssen Sie zu einer neuen SKU wechseln und dazu Ihr VPN-Gateway löschen und neu erstellen.

###  <a name="workloads"></a>Gateway-SKUs: Gegenüberstellung von Produktions- und Dev-Test-Workloads

Aufgrund der Unterschiede bei SLAs und Features werden die folgenden SKUs für die Produktion bzw. für Dev-Test-Workloads empfohlen:

| **Workload**                       | **SKUs**               |
| ---                                | ---                    |
| **Produktion, kritische Workloads** | VpnGw1, VpnGw2, VpnGw3 |
| **Dev-Test oder Proof of Concept**   | Basic (\*\*)                 |
|                                    |                        |

(\*\*) Die Basic-SKU wird als Legacy-SKU betrachtet und bietet eingeschränkte Features. Vergewissern Sie sich vor der Verwendung der Basic-SKU, dass das von Ihnen benötigte Feature unterstützt wird.

Wenn Sie die alten SKUs (Legacy-SKUs) verwenden, werden für die Produktion die SKUs „Standard“ und „HighPerformance“ empfohlen. Informationen und Anweisungen für alte SKUs finden Sie unter [Arbeiten mit SKUs für virtuelle Netzwerkgateways (Legacy-SKUs)](../articles/vpn-gateway/vpn-gateway-about-skus-legacy.md).