---
title: 'Beispiel: Überwachen der transparenten Datenverschlüsselung für SQL-Datenbank'
description: Mit dieser Beispielrichtliniendefinition wird überwacht, ob die transparente Datenverschlüsselung für SQL-Datenbank nicht aktiviert ist.
author: DCtheGeek
manager: carmonm
ms.service: azure-policy
ms.topic: sample
ms.date: 01/23/2019
ms.author: dacoulte
ms.openlocfilehash: e8ee800ff9f286f901a84a039e3c433442ae11b2
ms.sourcegitcommit: c174d408a5522b58160e17a87d2b6ef4482a6694
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59789577"
---
# <a name="sample---audit-sql-database-encryption"></a>Beispiel: Überwachen der SQL-Datenbankverschlüsselung

Mit dieser integrierten Richtlinie wird überwacht, wenn die transparente Datenverschlüsselung für SQL-Datenbank nicht aktiviert ist.

[!INCLUDE [quickstarts-free-trial-note](../../../../includes/quickstarts-free-trial-note.md)]

## <a name="sample-template"></a>Vorlagenbeispiel

[!code-json[main](../../../../policy-templates/samples/SQL/audit-sql-db-tde-status/azurepolicy.json "Audit TDE for SQL Database")]

Sie können diese Vorlage über das [Azure-Portal](#deploy-with-the-portal), mit [PowerShell](#deploy-with-powershell) oder mit der [Azure CLI](#deploy-with-azure-cli) bereitstellen. Verwenden Sie zum Abrufen der integrierten Richtlinie die ID `17k78e20-9358-41c9-923c-fb736d382a12`.

## <a name="deploy-with-the-portal"></a>Bereitstellen über das Portal

Wählen Sie beim Zuweisen einer Richtlinie in den verfügbaren integrierten Definitionen die Option **Transparent Data Encryption-Status überwachen** aus.

## <a name="deploy-with-powershell"></a>Bereitstellen mit PowerShell

[!INCLUDE [sample-powershell-install](../../../../includes/sample-powershell-install-no-ssh-az.md)]

```azurepowershell-interactive
$definition = Get-AzPolicyDefinition -Id /providers/Microsoft.Authorization/policyDefinitions/17k78e20-9358-41c9-923c-fb736d382a12

New-AzPolicyAssignment -name "SQL TDE Audit" -PolicyDefinition $definition -Scope <scope>
```

### <a name="clean-up-powershell-deployment"></a>Bereinigen der PowerShell-Bereitstellung

Führen Sie den folgenden Befehl aus, um die Richtlinienzuweisung zu entfernen.

```azurepowershell-interactive
Remove-AzPolicyAssignment -Name "SQL TDE Audit" -Scope <scope>
```

## <a name="deploy-with-azure-cli"></a>Bereitstellen über die Azure-Befehlszeilenschnittstelle

[!INCLUDE [sample-cli-install](../../../../includes/sample-cli-install.md)]

```azurecli-interactive
az policy assignment create --scope <scope> --name "SQL TDE Audit" --policy 17k78e20-9358-41c9-923c-fb736d382a12
```

### <a name="clean-up-azure-cli-deployment"></a>Bereinigen der Azure CLI-Bereitstellung

Führen Sie den folgenden Befehl aus, um die Richtlinienzuweisung zu entfernen.

```azurecli-interactive
az policy assignment delete --name "SQL TDE Audit" --resource-group myResourceGroup
```

## <a name="next-steps"></a>Nächste Schritte

- Unter [Azure Policy-Beispiele](index.md) finden Sie weitere Beispiele.