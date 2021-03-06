---
title: 'Schnellstart: Erstellen eines Analysis Services-Servers mithilfe des Azure-Portals | Microsoft-Dokumentation'
description: Informationen zum Erstellen einer Analysis Services-Serverinstanz in Azure.
author: minewiskan
manager: kfile
ms.service: azure-analysis-services
ms.topic: quickstart
ms.date: 04/01/2019
ms.author: owend
ms.reviewer: minewiskan
ms.openlocfilehash: e54c18eb405ffa36260e9980705784130bc0ca4c
ms.sourcegitcommit: c174d408a5522b58160e17a87d2b6ef4482a6694
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "58803004"
---
# <a name="quickstart-create-a-server---portal"></a>Schnellstart: Erstellen eines Servers – Portal

Diese Schnellstartanleitung erläutert, wie eine Analysis Services-Serverressource in Ihrem Azure-Abonnement mithilfe des Portals erstellt wird.

## <a name="prerequisites"></a>Voraussetzungen 

* **Azure-Abonnement:** Besuchen Sie die Webseite [Kostenlose Azure-Testversion](https://azure.microsoft.com/offers/ms-azr-0044p/), und erstellen Sie ein Konto.
* **Azure Active Directory**: Ihr Abonnement muss einem Azure Active Directory-Mandanten zugeordnet sein. Und Sie müssen bei Azure mit einem Konto in diesem Azure Active Directory angemeldet sein. Weitere Informationen finden Sie unter [Authentifizierung und Benutzerberechtigungen](analysis-services-manage-users.md).

## <a name="sign-in-to-the-azure-portal"></a>Melden Sie sich auf dem Azure-Portal an. 

[Anmelden beim Portal](https://portal.azure.com)


## <a name="create-a-server"></a>Erstellen eines Servers

1. Klicken Sie auf **+ Ressource erstellen** > **Analysen** > **Analysis Services**.

    ![Portal](./media/analysis-services-create-server/aas-create-server-portal.png)

2. Füllen Sie in **Analysis Services** die erforderlichen Felder aus, und klicken Sie dann auf **Erstellen**.
   
   * **Servername**: Geben Sie einen eindeutigen Namen ein, mit dem auf den Server verwiesen wird.
   * **Abonnement**: Wählen Sie das Abonnement aus, das diesem Server zugeordnet wird.
   * **Ressourcengruppe**: Erstellen Sie eine neue Ressourcengruppe, oder wählen Sie eine bereits vorhandene Ressourcengruppe aus. Ressourcengruppen sind darauf ausgelegt, Sie beim Verwalten einer Sammlung von Azure-Ressourcen zu unterstützen. Weitere Informationen finden Sie unter [Ressourcengruppen](../azure-resource-manager/resource-group-overview.md).
   * **Standort**: An diesem Standort des Azure-Rechenzentrums wird der Server gehostet. Wählen Sie einen Standort in der Nähe Ihrer größten Benutzerbasis aus.
   * **Tarif**: Wählen Sie einen Tarif. Wenn Sie Tests durchführen und die Beispielmodelldatenbank installieren möchten, wählen Sie den kostenlosen Tarif **D1** aus. Weitere Informationen finden Sie unter [Azure Analysis Services – Preise](https://azure.microsoft.com/pricing/details/analysis-services/). 
   * **Administrator**: Dies ist standardmäßig das Konto, mit dem Sie angemeldet werden. Sie können ein anderes Konto aus Ihrem Azure Active Directory auswählen.
   * **Einstellung „Sicherungsspeicher“**: Optional. Wenn Sie bereits über ein [Speicherkonto](../storage/common/storage-introduction.md), verfügen, können Sie es als Standardkonto für die Sicherung der Modelldatenbank angeben. Sie können später auch Einstellungen zum [Sichern und Wiederherstellen](analysis-services-backup.md) angeben.
   * **Speicherschlüssel-Ablaufdatum**: Optional. Geben Sie einen Ablaufzeitraum für den Speicherschlüssel an.

Das Erstellen des Servers dauert normalerweise weniger als eine Minute. Wenn Sie **Add to Portal** (Zu Portal hinzufügen) ausgewählt haben, navigieren Sie zu Ihrem Portal, um den neuen Server anzuzeigen. Oder navigieren Sie zu **Alle Dienste** > **Analysis Services**, um zu überprüfen, ob der Server bereit ist. Server unterstützen tabellarische Modelle mit dem Kompatibilitätsgrad 1200 oder höher. Der Modellkompatibilitätsgrad wird in SSDT oder SSMS angegeben.

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Löschen Sie Ihren Server, wenn Sie ihn nicht mehr benötigen. Klicken Sie auf der Seite **Übersicht** Ihres Servers auf **Löschen**. 

 ![Cleanup](./media/analysis-services-create-server/aas-create-server-cleanup.png)


## <a name="next-steps"></a>Nächste Schritte
In diesem Schnellstart haben Sie gelernt, wie Sie einen Server in Ihrem Azure-Abonnement erstellen. Da Sie nun über einen Server verfügen, können Sie durch Konfigurieren einer (optionalen) Serverfirewall zur Sicherheit beitragen. Außerdem können Sie Ihrem Server direkt über das Portal ein einfaches Beispieldatenmodell hinzufügen. Ein Beispielmodell ist hilfreich, wenn Sie sich mit dem Konfigurieren von Modelldatenbankrollen und dem Testen von Clientverbindungen vertraut machen. Fahren Sie mit dem Tutorial zum Hinzufügen eines Beispielmodells fort, um mehr zu erfahren.

> [!div class="nextstepaction"]
> [Schnellstart: Konfigurieren der Serverfirewall – Portal](analysis-services-qs-firewall.md)   
> [!div class="nextstepaction"]
> [Tutorial: Hinzufügen eines Beispielmodells zu Ihrem Server](analysis-services-create-sample-model.md)
