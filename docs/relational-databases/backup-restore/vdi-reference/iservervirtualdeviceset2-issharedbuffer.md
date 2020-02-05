---
title: IServerVirtualDeviceSet2::IsSharedBuffer
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IServerVirtualDeviceSet2::IsSharedBuffer.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cd3e7abfd1d250a170e0de4ebc1b392bc5857468
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "70847360"
---
# <a name="iservervirtualdeviceset2issharedbuffer-vdi"></a>IServerVirtualDeviceSet2::IsSharedBuffer (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonction **IsSharedBuffer** détermine si l’adresse de la mémoire tampon donnée fait référence à une des mémoires tampons partagées rendues disponibles par la méthode AllocateBuffer.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IServerVirtualDeviceSet2::IsSharedBuffer (
   LPVOID   lpBuffer
);
```

## <a name="parameters"></a>Paramètres

*lpBuffer* : une adresse d’une mémoire tampon.

## <a name="return-value"></a>Valeur de retour

|Valeur de retour | Explication |
|---|---|
| TRUE | La mémoire tampon est une mémoire tampon partagée. |
| FALSE | La mémoire tampon ne fait pas partie de l’ensemble d’appareils virtuels. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).