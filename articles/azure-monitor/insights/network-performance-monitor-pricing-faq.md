---
title: Häufig gestellte Fragen zu Preisen für den Azure-Netzwerkleistungsmonitor | Microsoft-Dokumentation
description: Häufig gestellte Fragen – Azure-Netzwerkleistungsmonitor
services: monitoring-and-diagnostics
documentationcenter: na
author: agummadi
manager: cherylmc
editor: ''
tags: azure-resource-manager
ms.assetid: ''
ms.service: log-analytics
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 04/02/2018
ms.author: ajaycode
ms.openlocfilehash: 77cacd7f94d8ddd92fcd7383d2d0a7929734eaeb
ms.sourcegitcommit: 41ca82b5f95d2e07b0c7f9025b912daf0ab21909
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2019
ms.locfileid: "60401407"
---
# <a name="pricing-changes-for-azure-network-performance-monitor"></a>Preisänderungen für Azure-Netzwerkleistungsmonitor

Wir haben Ihr Feedback berücksichtigt und vor kurzem eine [neue Preisgestaltung](https://azure.microsoft.com/blog/introducing-a-new-way-to-purchase-azure-monitoring-services/) für verschiedene Überwachungsdienste in Azure eingeführt. In diesem Artikel sind Preisänderungen im Zusammenhang mit dem Azure-[Netzwerkleistungsmonitor](https://docs.microsoft.com/azure/networking/network-monitoring-overview) in einem benutzerfreundlichen Frage-und-Antwort-Format festgehalten.

Der Netzwerkleistungsmonitor umfasst drei Komponenten:
* [Systemmonitor](https://docs.microsoft.com/azure/networking/network-monitoring-overview#performance-monitor)
* [Dienstendpunktmonitor](https://docs.microsoft.com/azure/networking/network-monitoring-overview)
* [ExpressRoute-Monitor](https://docs.microsoft.com/azure/networking/network-monitoring-overview#expressroute-monitor)

In den folgenden Abschnitten werden die Preisänderungen für diese Komponenten des Netzwerkleistungsmonitors erläutert.

## <a name="performance-monitor"></a>Systemmonitor

**Wie wurde die Verwendung des Systemmonitors im alten Modell in Rechnung gestellt?**

Die Abrechnung für den Systemmonitor basierte bisher auf der Nutzung von zwei Komponenten:
* **Knoten**: Alle synthetischen Transaktionen beginnen und enden an den Knoten. Knoten werden auch als Agents oder Microsoft-Verwaltungs-Agents bezeichnet.
* **Daten**: Die Ergebnisse der verschiedenen Netzwerktests werden im Log Analytics-Workspace gespeichert.

Unter dem alten Modell wurde die Rechnung basierend auf der Anzahl der Knoten und dem Volumen der generierten Daten berechnet. 

**Wie wird die Nutzung von Systemmonitor nach dem neuen Modell berechnet?**

Die Funktion „Systemmonitor“ im Netzwerkleistungsmonitor wird nun anhand der Kombination folgender Elemente berechnet: 

* Überwachte Subnetzlinks
* Datenvolume

**Was ist ein Subnetzlink?**

Systemmonitor überwacht die Konnektivität zwischen zwei oder mehr Orten im Netzwerk. Die Verbindung zwischen einer Gruppe von Knoten oder Agents in einem Subnetz und einer Gruppe von Knoten in einem anderen Subnetz wird als Subnetzlink bezeichnet.

**Ich verfüge über zwei Subnetze (A und B) und mehrere Agents in den einzelnen Subnetzen. Systemmonitor überwacht die Konnektivität aller Agents in Subnetz A mit allen Agents in Subnetz B. Werden Gebühren anhand der Anzahl der Verbindungen zwischen den Subnetzen berechnet?**

Nein. Zu Abrechnungszwecken werden alle Verbindungen zwischen Subnetz A und Subnetz B zu einem Subnetzlink gruppiert. Ihnen wird eine einzelne Verbindung in Rechnung gestellt. Systemmonitor überwacht weiterhin die Konnektivität zwischen den verschiedenen Agents in den einzelnen Subnetzen.

**Was sind die Kosten für die Überwachung eines Subnetzlinks?**

Im Abschnitt [Pingmesh](https://azure.microsoft.com/pricing/details/network-watcher/) finden Sie die Kosten für die Überwachung eines einzelnen Subnetzlinks für den gesamten Monat.

**Welche Gebühren werden für die von Systemmonitor generierten Daten erhoben?**

Die Gebühren für die Erfassung (Datenupload zum Log Analytics-Workspace in Azure Monitor, Verarbeitung und Indizierung) stehen auf der [Preisseite](https://azure.microsoft.com/pricing/details/log-analytics/) für Log Analytics, im Abschnitt „Datenerfassung“, zur Verfügung. Die Gebühren für die Datenaufbewahrung (d. h. Daten, die auf Kundenwunsch über den ersten Monat hinaus aufbewahrt werden) sind ebenfalls auf der [Preisseite](https://azure.microsoft.com/pricing/details/log-analytics/), im Abschnitt „Datenaufbewahrung“, aufgeführt.


## <a name="expressroute-monitor"></a>ExpressRoute-Monitor

**Was sind die Gebühren für die Verwendung von ExpressRoute-Monitor?**

Gebühren für ExpressRoute-Monitor werden basierend auf der Menge der während der Überwachung generierten Daten in Rechnung gestellt. Weitere Informationen finden Sie unter „Welche Gebühren werden für die von Systemmonitor generierten Daten erhoben?“.

**Ich verwende ExpressRoute-Monitor zum Überwachen mehrerer ExpressRoute-Verbindungen. Werden Gebühren entsprechend der Anzahl von überwachten Verbindungen berechnet?**

Die Gebühren werden weder anhand der Anzahl von Verbindungen noch anhand des Peeringtyps (z. B. privates Peering, Microsoft-Peering) berechnet. Ihnen wird, wie oben erläutert, das Datenvolumen in Rechnung gestellt.

**Wie wird das Volumen der generierten Daten berechnet, wenn ExpressRoute eine einzelne Verbindung überwacht?**

Wenn ExpressRoute eine private Peeringverbindung überwacht, wird das Volumen der pro Monat generierten Daten wie folgt berechnet:

|Perzentil      |Daten/Monat (MB)|
| :---:          |           ---:|
|50\.<sup></sup> |            192|
|60\.<sup></sup> |            256|
|70\.<sup></sup> |            360|
|80\.<sup></sup> |            498|
|90\.<sup></sup> |            870|
|95\.<sup></sup> |           1560|


Gemäß der obigen Tabelle fallen beim 50. Perzentil Kosten für eine Datenmenge von 192 MB von. Bei einem Preis von 2,30 USD pro GB für den ersten Monat belaufen sich die Kosten für die Überwachung einer Verbindung auf 0,43 USD (192 * 2,30:1024).

**Welche Gründe gibt es für Abweichungen beim Datenvolumen?**

Das Volumen der generierten Überwachungsdaten hängt von mehreren Faktoren ab:
* Anzahl der Agents. Die Genauigkeit der Fehlerisolation nimmt bei einer höheren Anzahl von Agents zu.
* Anzahl der Hops im Netzwerk.
* Anzahl der Pfade zwischen Quelle und Ziel.

Bei den höheren Perzentilen (siehe obige Tabelle) überwachen Kunden ihre Verbindungen in der Regel von mehreren Standpunkten in ihrem lokalen Netzwerk. Mehrere Agents werden auch tiefer im Netzwerk, weiter entfernt vom Edgerouter des Dienstanbieters platziert. Die Agents werden häufig an mehreren Benutzerstandorten, Branches und Racks in Rechenzentren platziert.

## <a name="service-endpoint-monitor"></a>Dienstendpunktmonitor

**Was sind die Gebühren für die Verwendung des Dienstendpunktmonitors?**

Die Gebühren für die Nutzung des Dienstendpunktmonitors werden anhand der folgenden Elemente berechnet:
* Anzahl der Verbindungen
* Datenvolumen

**Was ist eine Verbindung?**

Eine Verbindung ist ein Test der Erreichbarkeit eines Endpunkts (URL oder Netzwerkdienst) über einen einzelnen Agent für den gesamten Monat. Beispielsweise stellt die Überwachung einer Verbindung mit „bing.com“ über drei Agents drei Verbindungen dar.

**Was sind die Kosten für den Dienstendpunktmonitor?**

Im Abschnitt [Verbindungsüberwachung](https://azure.microsoft.com/pricing/details/network-watcher/) finden Sie die Kosten für die Überwachung eines Endpunkts für den gesamten Monat. Die Gebühren für Daten stehen auf der [Preisseite](https://azure.microsoft.com/pricing/details/log-analytics/) für Log Analytics, im Abschnitt „Datenerfassung“, zur Verfügung.

## <a name="references"></a>Referenzen

[Häufig gestellte Fragen zu Log Analytics-Preisen](https://azure.microsoft.com/pricing/details/log-analytics/): Der Abschnitt „FAQ“ enthält Informationen zum Free-Tarif, zu Preisen pro Knoten und weitere Preisdetails.

