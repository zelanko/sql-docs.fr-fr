---
title: IServerVirtualDeviceSet2::SignalAbort
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IServerVirtualDeviceSet2::SignalAbort.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee70ef059e80d9c8a31281ce50f451e7787f637a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895938"
---
# <a name="iservervirtualdeviceset2signalabort-vdi"></a>IServerVirtualDeviceSet2::SignalAbort (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

La fonction **SignalAbort** signale qu’un arrêt anormal doit se produire.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IServerVirtualDeviceSet2::SignalAbort ();
```

## <a name="return-value"></a>Valeur de retour

Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur NOERROR indique que l’appel de la méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.

## <a name="remarks"></a>Notes

À tout moment, le serveur peut choisir d’abandonner l’opération BACKUP ou RESTORE.

Cette routine signale que toutes les opérations doivent cesser. L’interface globale entre dans un état Abort (Abandon). Aucune autre commande n’est acceptée sur les appareils. L’agent d’achèvement retourne ERROR_OPERATION_ABORTED pour chaque demande en suspens et retourne à son appelant. Tous les achèvements enregistrés sur le client sont ignorées.

Le serveur vérifie qu’il n’y a pas d’autre utilisation nécessaire des mémoires tampons ou des appareils retournée depuis l’interface VDI. Le serveur effectue ensuite un nettoyage de l’arrêt anormal, qui doit inclure un appel de la fonction IServerVirtualDeviceSet2::Close.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).