---
title: IClientVirtualDevice::GetCommand
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IClientVirtualDevice::GetCommand.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a861377924b4bb3cc1c1d2a4b83eba660fbf99e0
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847590"
---
# <a name="iclientvirtualdevicegetcommand-vdi"></a>IClientVirtualDevice::GetCommand (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonction **GetCommand** est utilisée pour obtenir la commande suivante mise en file d’attente sur un appareil. Quand elle est demandée, cette fonction attend la commande suivante.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IClientVirtualDevice::GetCommand (
   DWORD               dwTimeOut,
   VDC_Command**      const ppCmd
);
```

## <a name="parameters"></a>Paramètres

*ppCmd* : quand une commande est retournée correctement, le paramètre retourne l’adresse d’une commande à exécuter. La mémoire retournée est en lecture seule. Lorsque la commande est terminée, ce pointeur est passé à la routine CompleteCommand. Pour plus d’informations sur chaque commande, consultez Commandes.

*dwTimeOut* : le délai d’attente en millisecondes. Utilisez INFINITE pour attendre indéfiniment. Utilisez 0 pour interroger une commande. VD_E_TIMEOUT est retourné si aucune commande n’est actuellement disponible. Si le délai d’expiration s’écoule, le client décide de l’action suivante.

## <a name="return-value"></a>Valeur retournée

|Valeur retournée | Explication |
|---|---|
| NOERROR | Une commande a été extraite. |
| VD_E_CLOSE | L’appareil a été fermé par le serveur. |
| VD_E_TIMEOUT | Aucune commande n’était disponible et le délai d’attente a expiré. |
| VD_E_ABORT | Le client ou le serveur a utilisé le SignalAbort pour forcer un arrêt. |

## <a name="remarks"></a>Notes

Quand VD_E_CLOSE est retourné, SQL Server a fermé l’appareil. Cela fait partie de l’arrêt normal. Une fois que tous les appareils ont été fermés, le client appelle IClientVirtualDeviceSet2::Close pour fermer l’ensemble d’appareils virtuels.

Quand cette routine doit se bloquer pour attendre une commande, le thread reste dans une condition d’attente d’alerte.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).