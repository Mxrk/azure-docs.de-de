---
title: 'Azure Cosmos DB: BulkExecutor – .NET-API, SDK und Ressourcen'
description: Wichtige Informationen zur .NET-API und zum SDK für Bulk Executor, einschließlich Veröffentlichungstermine, Deaktivierungstermine und Änderungen an den einzelnen Versionen des .NET SDK für Azure Cosmos DB Bulk Executor.
author: tknandu
ms.service: cosmos-db
ms.subservice: cosmosdb-sql
ms.devlang: dotnet
ms.topic: reference
ms.date: 11/19/2018
ms.author: ramkris
ms.openlocfilehash: 74eddadd7fd967daa1eebb9d7cb223fdc708025f
ms.sourcegitcommit: d4dfbc34a1f03488e1b7bc5e711a11b72c717ada
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2019
ms.locfileid: "66471421"
---
# <a name="net-bulk-executor-library-download-information"></a>.NET-BulkExecutor-Bibliothek: Informationen zum Download 

> [!div class="op_single_selector"]
> * [.NET](sql-api-sdk-dotnet.md)
> * [.NET-Änderungsfeed](sql-api-sdk-dotnet-changefeed.md)
> * [.NET Core](sql-api-sdk-dotnet-core.md)
> * [Node.js](sql-api-sdk-node.md)
> * [Async Java](sql-api-sdk-async-java.md)
> * [Java](sql-api-sdk-java.md)
> * [Python](sql-api-sdk-python.md)
> * [REST](https://docs.microsoft.com/rest/api/cosmos-db/)
> * [REST-Ressourcenanbieter](https://docs.microsoft.com/rest/api/cosmos-db-resource-provider/)
> * [SQL](sql-api-query-reference.md)
> * [Bulk Executor – .NET](sql-api-sdk-bulk-executor-dot-net.md)
> * [Bulk Executor – Java](sql-api-sdk-bulk-executor-java.md)

| |  |
|---|---|
| **Beschreibung**| Die BulkExecutor-Bibliothek ermöglicht Clientanwendungen die Ausführung von Massenvorgängen in Azure Cosmos DB-Konten. Die BulkExecutor-Bibliothek stellt die Namespaces „BulkImport“, „BulkUpdate“ und „BulkDelete“ bereit. Das BulkImport-Modul kann Dokumente auf optimierte Weise per Massenimport erfassen, sodass der für eine Sammlung bereitgestellte Durchsatz maximal genutzt wird. Das BulkUpdate-Modul kann vorhandene Daten in Azure Cosmos DB-Containern per Massenvorgang in Form von Patches aktualisieren. Das BulkDelete-Modul kann Dokumente auf optimierte Weise per Massenlöschung entfernen, sodass der für eine Sammlung bereitgestellte Durchsatz maximal genutzt wird.|
|**SDK-Download**| [NuGet](https://www.nuget.org/packages/Microsoft.Azure.CosmosDB.BulkExecutor/) |
| **BulkExecutor-Bibliothek in GitHub**| [GitHub](https://github.com/Azure/azure-cosmosdb-bulkexecutor-dotnet-getting-started)|
|**API-Dokumentation**|[.NET API-Referenzdokumentation](https://docs.microsoft.com/dotnet/api/microsoft.azure.cosmosdb.bulkexecutor?view=azure-dotnet)|
|**Erste Schritte**|[Erste Schritte mit dem .NET SDK für die Bulk Executor-Bibliothek](bulk-executor-dot-net.md)|
| **Aktuelles unterstütztes Framework**| Microsoft .NET Framework 4.5.2, 4.6.1 und .NET Standard 2.0 |

## <a name="release-notes"></a>Versionshinweise

### <a name="a-name230-preview2230-preview2"></a><a name="2.3.0-preview2"/>2.3.0-preview2

* Unterstützung für Graph-BulkExecutor wurde hinzugefügt, damit TTL für Scheitelpunkte und Kanten akzeptiert wird

### <a name="a-name220-preview2220-preview2"></a><a name="2.2.0-preview2"/>2.2.0-preview2

* Es wurde ein Problem behoben, bei dem es zu Ausnahmen während der elastischen Skalierung von Azure Cosmos DB gekommen ist, wenn die Ausführung im Modus „Gateway“ erfolgt ist. Aufgrund dieser Fehlerbehebung entspricht die Funktionalität Version 1.4.1.

### <a name="a-name210-preview2210-preview2"></a><a name="2.1.0-preview2"/>2.1.0-preview2

* Unterstützung des BulkDelete-Vorgangs wurde hinzugefügt, damit SQL-API-Konten Tupel aus Partitionsschlüssel und Dokument-ID für das Löschen akzeptieren. Aufgrund dieser Änderung entspricht die Funktionalität Version 1.4.0.

### <a name="a-name200-preview2200-preview2"></a><a name="2.0.0-preview2"/>2.0.0-preview2

* Enthält nun MongoBulkExecutor zur Unterstützung von .NET Standard 2.0. Dieses Feature stellt funktionale Gleichheit mit dem Release 1.3.0 her und unterstützt als Zielframework zusätzlich auch .NET Standard 2.0.

### <a name="a-name200-preview200-preview"></a><a name="2.0.0-preview"/>2.0.0-preview

* .NET Standard 2.0 wurde als unterstütztes Zielframework hinzugefügt, damit die BulkExecutor-Bibliothek mit .NET Core-Anwendungen verwendet werden kann.

### <a name="a-name160160"></a><a name="1.6.0"/>1.6.0

* BulkExecutor wurde aktualisiert, damit die aktuelle Version des Azure Cosmos DB .NET SDK (2.4.0) verwendet wird

### <a name="a-name150150"></a><a name="1.5.0"/>1.5.0

* Unterstützung für Graph-BulkExecutor wurde hinzugefügt, damit TTL für Scheitelpunkte und Kanten akzeptiert wird

### <a name="a-name141141"></a><a name="1.4.1"/>1.4.1

* Es wurde ein Problem behoben, bei dem es zu Ausnahmen während der elastischen Skalierung von Azure Cosmos DB gekommen ist, wenn die Ausführung im Modus „Gateway“ erfolgt ist.

### <a name="a-name140140"></a><a name="1.4.0"/>1.4.0

* Unterstützung des BulkDelete-Vorgangs wurde hinzugefügt, damit SQL-API-Konten Tupel aus Partitionsschlüssel und Dokument-ID für das Löschen akzeptieren.

### <a name="a-name130130"></a><a name="1.3.0"/>1.3.0

* Ein Problem wurde behoben, durch das ein Formatierungsproblem in dem von BulkExecutor verwendeten Benutzer-Agent verursacht wurde.

### <a name="a-name120120"></a><a name="1.2.0"/>1.2.0

* Es wurden Verbesserungen an den Import- und Update-APIs von BulkExecutor vorgenommen, um transparent die flexible Skalierung von Cosmos DB-Containern bei Überschreiten der aktuellen Speicherkapazität zu ermöglichen, ohne dass Ausnahmen ausgelöst werden.

### <a name="a-name112112"></a><a name="1.1.2"/>1.1.2

* Aktualisierung der DocumentDB .NET SDK-Abhängigkeit auf Version 2.1.3.

### <a name="a-name111111"></a><a name="1.1.1"/>1.1.1

* Ein Problem wurde behoben, durch das BulkExecutor beim Importieren in feste Sammlungen JSRT-Fehler auslöste.

### <a name="a-name110110"></a><a name="1.1.0"/>1.1.0

* Unterstützung für BulkDelete-Vorgang für die SQL-API von Azure Cosmos DB-Konten.
* Unterstützung für den BulkImport-Vorgang für Konten mit der MongoDB-API von Azure Cosmos DB.
* Aktualisierung der DocumentDB .NET SDK-Abhängigkeit auf Version 2.0.0. 

### <a name="a-name102102"></a><a name="1.0.2"/>1.0.2

* Unterstützung für BulkImport-Vorgang für die Gremlin-API von Azure Cosmos DB-Konten.

### <a name="a-name101101"></a><a name="1.0.1"/>1.0.1

* Kleinere Fehlerbehebung am BulkImport-Vorgang für die SQL-API von Azure Cosmos DB-Konten.

### <a name="a-name100100"></a><a name="1.0.0"/>1.0.0

* Unterstützung für BulkImport- und Bulkupdate-Vorgänge für die SQL-API von Azure Cosmos DB-Konten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur BulkExecutor-Java-Bibliothek finden Sie im folgenden Artikel:

[SDK und Versionshinweise zur Java-BulkExecutor-Bibliothek](sql-api-sdk-bulk-executor-java.md)
