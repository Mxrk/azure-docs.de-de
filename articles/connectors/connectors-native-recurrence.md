---
title: Planen von wiederkehrenden Aufgaben mit dem Serientrigger – Azure Logic Apps
description: Planen und Ausführen von wiederkehrenden automatisierten Aufgaben und Workflows mit dem Serientrigger in Azure Logic Apps
services: logic-apps
ms.service: logic-apps
ms.suite: integration
author: ecfan
ms.author: estfan
ms.reviewer: deli, klam, LADocs
ms.topic: conceptual
ms.date: 05/25/2019
ms.openlocfilehash: f5fc778ee4d8f91232bc732cc276f642f748b29d
ms.sourcegitcommit: d4dfbc34a1f03488e1b7bc5e711a11b72c717ada
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2019
ms.locfileid: "66297525"
---
# <a name="create-schedule-and-run-recurring-tasks-and-workflows-with-the-recurrence-trigger-in-azure-logic-apps"></a>Erstellen, Planen und Ausführen von wiederkehrenden Aufgaben und Workflows mit dem Serientrigger in Azure Logic Apps

Um Aufgaben, Prozesse oder Aufträge nach einem bestimmten Zeitplan regelmäßig auszuführen, können Sie Ihren Logik-App-Workflow mit dem integrierten Trigger **Serie – Zeitplan starten**. Sie können ein Datum, eine Uhrzeit und eine Zeitzone zum Starten des Workflows sowie eine Serie zum Wiederholen dieses Workflows festlegen. Wenn Wiederholungen aus irgendeinem Grund nicht ausgeführt werden, setzt dieser Trigger die Wiederholungen beim nächsten geplanten Intervall fort. Weitere Informationen zu den integrierten Zeitplantriggern und -aktionen finden Sie unter [Planen und Ausführen von wiederkehrenden automatisierten Aufgaben und Workflows mit Azure Logic Apps](../logic-apps/concepts-schedule-automated-recurring-tasks-workflows.md).

Im Folgenden finden Sie einige Muster, die dieser Trigger neben erweiterten Serien und komplexen Zeitplänen unterstützt:

* Sofortige Ausführung und Wiederholung jeweils nach *n* Sekunden, Minuten, Stunden, Tagen, Wochen oder Monaten.

* Start an einem bestimmten Datum zu einer bestimmten Uhrzeit und anschließende Ausführung und Wiederholung jeweils nach *n* Sekunden, Minuten, Stunden, Tagen, Wochen oder Monaten.

* Ausführung und Wiederholung einmal oder mehrmals pro Tag, z.B. 8:00 und 17:00 Uhr.

* Ausführung und Wiederholung einmal pro Woche, aber nur an bestimmten Tagen, z.B. Samstag und Sonntag.

* Ausführung und Wiederholung einmal pro Woche, aber nur an bestimmten Tagen und zu festen Uhrzeiten, z.B. Montag bis Freitag um 8:00 und 17:00 Uhr.

Die Unterschiede zwischen diesem Trigger und dem Trigger „Gleitendes Fenster“ sowie weitere Informationen zum Planen von wiederkehrenden Workflows finden Sie unter [Planen und Ausführen von wiederkehrenden automatisierten Aufgaben, Prozessen und Workflows in Azure Logic Apps](../logic-apps/concepts-schedule-automated-recurring-tasks-workflows.md).

> [!TIP]
> Unter [Nur einmaliges Ausführen eines Auftrags](../logic-apps/concepts-schedule-automated-recurring-tasks-workflows.md#run-once) erfahren Sie, wie Sie Ihre Logik-App auslösen und danach nur einmal ausführen.

## <a name="prerequisites"></a>Voraussetzungen

* Ein Azure-Abonnement. Falls Sie kein Abonnement besitzen, können Sie sich [für ein kostenloses Azure-Konto registrieren](https://azure.microsoft.com/free/).

* Grundlegende Kenntnisse zu [Logik-Apps](../logic-apps/logic-apps-overview.md). Falls Sie noch nicht mit Logik-Apps gearbeitet haben, sollten Sie zunächst die Schnellstartanleitung zum [Erstellen Ihrer ersten Logik-App](../logic-apps/quickstart-create-first-logic-app-workflow.md) lesen.

## <a name="add-recurrence-trigger"></a>Hinzufügen eines Serientriggers

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an. Erstellen einer leeren Logik-App

1. Wenn der Designer für Logik-Apps angezeigt wird, geben Sie im Suchfeld „Serie“ als Filter ein. Wählen Sie aus der Triggerliste den folgenden Trigger als ersten Schritt Ihres Logik-App-Workflows aus: **Serie**

   ![Auswählen des Serientriggers](./media/connectors-native-recurrence/add-recurrence-trigger.png)

1. Legen Sie das Intervall und die Häufigkeit für die Wiederholung fest. Legen Sie in diesem Beispiel diese Eigenschaften fest, um Ihren Workflow jede Woche auszuführen.

   ![Festlegen von Intervall und Häufigkeit](./media/connectors-native-recurrence/recurrence-trigger-details.png)

   | Eigenschaft | Erforderlich | JSON-Name | Type | BESCHREIBUNG |
   |----------|----------|-----------|------|-------------|
   | **Intervall** | Ja | interval | Integer | Eine positive ganze Zahl, die beschreibt, wie oft der Workflow basierend auf der Häufigkeit ausgeführt wird. Zulässige Mindest- und Maximalintervalle: <p>– Monat: 1–16 Monate </br>– Tag: 1–500 Tage </br>– Stunde: 1–12.000 Stunden </br>– Minute: 1–72.000 Minuten </br>- Sekunde: 1–9.999.999 Sekunden<p>Wenn das Intervall also beispielsweise auf „6“ und die Häufigkeit auf „Month“ festgelegt ist, erfolgt die Wiederholung alle sechs Monate. |
   | **Frequency** | Ja | frequency | string | Die Zeiteinheit für die Wiederholung: **Sekunde**, **Minute**, **Stunde**, **Tag**, **Woche** oder **Monat** |
   ||||||

   Um weitere Optionen für die Planung zu erhalten, öffnen Sie die Liste **Neuen Parameter hinzufügen**. 
   Alle von Ihnen ausgewählten Optionen werden nach der Auswahl im Trigger angezeigt.

   ![Erweiterte Planungsoptionen](./media/connectors-native-recurrence/recurrence-trigger-more-options-details.png)

   | Eigenschaft | Erforderlich | JSON-Name | Type | BESCHREIBUNG |
   |----------|----------|-----------|------|-------------|
   | **Zeitzone** | Nein | timeZone | Zeichenfolge | Nur relevant, wenn Sie eine Startzeit angeben, da dieser Trigger keine [UTC-Abweichung](https://en.wikipedia.org/wiki/UTC_offset) akzeptiert. Wählen Sie die anzuwendende Zeitzone aus. |
   | **Startzeit** | Nein | startTime | string | Geben Sie Startdatum und -uhrzeit im folgenden Format an: <p>JJJJ-MM-TTThh:mm:ss (bei Auswahl einer Zeitzone) <p>Oder <p>JJJJ-MM-TTThh:mm:ssZ (wenn keine Zeitzone ausgewählt wird) <p>Für den 18. September 2017 um 14:00 Uhr würden Sie also „2017-09-18T14:00:00“ angeben und eine Zeitzone (z.B. „Pacific Standard Time“) auswählen. Alternativ können Sie „2017-09-18T14:00:00Z“ ohne Zeitzone angeben. <p>**Hinweis:** Diese Startzeit muss dem [ISO 8601-Format für Datums-/Uhrzeitangaben](https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations) entsprechen und im [UTC-Datums-/Zeitformat](https://en.wikipedia.org/wiki/Coordinated_Universal_Time) angegeben werden, jedoch ohne [UTC-Abweichung](https://en.wikipedia.org/wiki/UTC_offset). Wenn Sie keine Zeitzone auswählen, müssen Sie den Buchstaben „Z“ ohne Leerzeichen anhängen. „Z“ bezieht sich auf die entsprechende [nautische Zeit](https://en.wikipedia.org/wiki/Nautical_time). <p>Bei einfachen Zeitplänen ist die Startzeit das erste Vorkommen. Bei komplexeren Zeitplänen wird der Trigger nicht vor der Startzeit ausgelöst. [*Wie kann ich Startdatum und -uhrzeit verwenden?* ](../logic-apps/concepts-schedule-automated-recurring-tasks-workflows.md#start-time) |
   | **An diesen Tagen** | Nein | weekDays | Zeichenfolge oder Zeichenfolgenarray | Wenn Sie „Woche“ auswählen, können Sie einen oder mehrere Tage auswählen, an denen der Workflow ausgeführt werden soll: **Montag**, **Dienstag**, **Mittwoch**, **Donnerst**, **Freitag**, **Samstag** und **Sonntag** |
   | **Zu diesen Stunden** | Nein | hours | Ganze Zahl oder Ganzzahlarray | Bei Auswahl von „Tag“ oder „Woche“ können Sie eine oder mehrere ganze Zahlen zwischen 0 und 23 als Stunden des Tages angeben, zu denen der Workflow ausgeführt werden soll. <p><p>Wenn Sie z.B. „10“, „12“ und „14“ angeben, erhalten Sie 10 Uhr, 12 Uhr bzw. 14 Uhr als Stundenangabe. Die Minuten werden jedoch basierend auf dem Start der Wiederholung berechnet. Um die Minuten festzulegen, geben Sie den Wert für die Eigenschaft **Zu diesen Minuten** an. |
   | **Zu diesen Minuten** | Nein | minutes | Ganze Zahl oder Ganzzahlarray | Bei Auswahl von „Day“ (Tag) oder „Week“ (Woche) können Sie eine oder mehrere ganze Zahlen zwischen 0 und 59 als Minuten der Stunden angeben, in denen der Workflow ausgeführt werden soll. <p>Wenn Sie also beispielsweise „30“ als Minutenwert angeben und das vorherige Beispiel für Stunden des Tages verwenden, erhalten Sie „10:30 Uhr“, „12:30 Uhr“ und „14:30 Uhr“. |
   |||||

   Angenommen, heute ist Montag, der 4. September 2017. Der folgende Serientrigger wird *frühestens* am festgelegten Startdatum zur festgelegten Startzeit ausgelöst, also am Montag, den 18. September 2017, um 8:00 Uhr (PST). Der Wiederholungszeitplan ist aber für die Uhrzeiten 10:30, 12:30 und 14:30 ausschließlich an Montagen festgelegt. Also wird um 10:30 Uhr zum ersten Mal der Trigger ausgelöst und eine Instanz des Logik-App-Workflows erstellt. Weitere Informationen zur Funktionsweise von Startzeiten finden Sie in diesen [Beispielen zu Startzeiten](../logic-apps/concepts-schedule-automated-recurring-tasks-workflows.md#start-time).

   Die zukünftigen Ausführungen erfolgen um 12:30 und 14:30 Uhr an demselben Tag. Für jede Wiederholung wird eine eigene Workflowinstanz erstellt. Anschließend wird der gesamte Zeitplan am nächsten Montag wiederholt. [*Welche anderen Beispiele für Wiederholungen gibt es?* ](../logic-apps/concepts-schedule-automated-recurring-tasks-workflows.md#example-recurrences)

   ![Beispiel für erweiterte Planung](./media/connectors-native-recurrence/recurrence-trigger-more-options-advanced-schedule.png)

   > [!NOTE]
   > Für den Trigger wird nur dann eine Vorschau für Ihre angegebene Wiederholung angezeigt, wenn Sie als Häufigkeit „Tag“ oder „Woche“ wählen.

1. Nun erstellen Sie den restlichen Workflow mit weiteren Aktionen. Weitere Aktionen, die Sie hinzufügen können, finden Sie unter [Connectors für Azure Logic Apps](../connectors/apis-list.md).

## <a name="workflow-definition---recurrence"></a>Workflowdefinition – Wiederholung

In der zugrunde liegenden Workflowdefinition – im JSON-Format – können Sie die [Definition des Serientriggers](../logic-apps/logic-apps-workflow-actions-triggers.md#recurrence-trigger) mit den von Ihnen ausgewählten Optionen anzeigen. Um diese Definition anzuzeigen, wählen Sie auf der Designer-Symbolleiste die Option **Codeansicht** aus. Um zum Designer zurückzukehren, wählen Sie auf der Designer-Symbolleiste die Option **Designer** aus.

Dieses Beispiel zeigt, wie die Definition eines Serientriggers in einer zugrunde liegenden Workflowdefinition aussehen kann:

``` json
"triggers": {
   "Recurrence": {
      "type": "Recurrence",
      "recurrence": {
         "frequency": "Week",
         "interval": 1,
         "schedule": {
            "hours": [
               10,
               12,
               14
            ],
            "minutes": [
               30
            ],
            "weekDays": [
               "Monday"
            ]
         },
         "startTime": "2017-09-07T14:00:00Z",
         "timeZone": "Pacific Standard Time"
      }
   }
}
```

## <a name="next-steps"></a>Nächste Schritte

* [Anhalten von Workflows mit Verzögerungsaktionen](../connectors/connectors-native-delay.md)
* [Connectors für Logic Apps](../connectors/apis-list.md)
