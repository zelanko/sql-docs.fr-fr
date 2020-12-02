---
title: IClientVirtualDeviceSet2::GetConfiguration
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IClientVirtualDeviceSet2::GetConfiguration.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: 5d46efb493dc67c38affc25f99871f3ff4617ecb
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125400"
---
# <a name="iclientvirtualdeviceset2getconfiguration-vdi"></a>IClientVirtualDeviceSet2::GetConfiguration (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

La fonction **GetConfiguration** est utilisée pour attendre que le serveur configure l’ensemble d’appareils virtuels.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IClientVirtualDeviceSet2::GetConfiguration (
   DWORD         dwTimeOut,
   VDConfig*      pCfg
);
```

## <a name="parameters"></a>Paramètres

*DwTimeOut* : le délai d’attente en millisecondes. Utilisez INFINITE pour empêcher l’expiration du délai d’attente.

*pCfg* : une fois l’exécution réussie, ceci contient la configuration sélectionnée par le serveur. Pour plus d’informations, consultez Configuration.

## <a name="return-value"></a>Valeur de retour

|Valeur de retour | Explication |
|---|---|
| NOERROR | La configuration a été retournée. |
| VD_E_ABORT | SignalAbort a été appelé. |
| VD_E_TIMEOUT | Expiration du délai d’attente de la fonction. |

## <a name="remarks"></a>Notes

Cette fonction se bloque dans un état Alertable. Une fois l’appel réussi, les appareils de l’ensemble d’appareils virtuels peuvent être ouverts.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).