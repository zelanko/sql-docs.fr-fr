---
title: IClientVirtualDeviceSet2::SignalAbort
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IClientVirtualDeviceSet2::SignalAbort.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0a0d53421f0928b1ebf0ba557afbd29dd8680993
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "70847540"
---
# <a name="iclientvirtualdeviceset2signalabort-vdi"></a>IClientVirtualDeviceSet2::SignalAbort (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonction **SignalAbort** est utilisée pour signaler qu’un arrêt anormal doit se produire.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IClientVirtualDeviceSet2::SignalAbort ();
```

## <a name="return-value"></a>Valeur de retour

Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur NOERROR indique que l’appel de la méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.

## <a name="remarks"></a>Notes

À tout moment, le client peut choisir d’abandonner l’opération BACKUP ou RESTORE. Cette routine signale que toutes les opérations doivent cesser. L’état de l’ensemble d’appareils virtuels passe à Abort (Abandon). Aucune autre commande n’est retournée sur les appareils. Toutes les commandes incomplètes sont automatiquement terminées, en retournant ERROR_OPERATION_ABORTED comme code d’achèvement. Le client doit appeler IClientVirtualDeviceSet2::Close après avoir terminé de façon sûre toute utilisation en attente des mémoires tampons fournies au client. Pour plus d’informations, consultez Arrêt anormal.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).