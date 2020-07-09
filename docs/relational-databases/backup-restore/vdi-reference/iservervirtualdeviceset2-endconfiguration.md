---
title: IServerVirtualDeviceSet2::EndConfiguration
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IServerVirtualDeviceSet2::EndConfiguration.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d2ed7365e9a0e895a7deb0ba20d57868a947b350
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896328"
---
# <a name="iservervirtualdeviceset2endconfiguration-vdi"></a>IServerVirtualDeviceSet2::EndConfiguration (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

La fonction **EndConfiguration** informe l’interface VDI que le serveur a terminé sa configuration.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IServerVirtualDeviceSet2::EndConfiguration ();
```

## <a name="return-value"></a>Valeur de retour

|Valeur de retour | Explication |
|---|---|
| NOERROR | La fonction a réussi. |
| VD_E_ABORT | L’annulation a été demandée. |
| VD_E_PROTOCOL | L’ensemble n’est pas dans l’état Configurable. |
| VD_E_MEMORY | La mémoire nécessaire via les appels « RequestBuffers » n’a pas pu être obtenue. L’ensemble reste dans l’état Configurable sans espace de mémoire tampon disponible. Le serveur peut réduire ses exigences en matière de mémoire tampon ou abandonner l’opération. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).