---
title: IServerVirtualDeviceSet2::IsSharedBuffer
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IServerVirtualDeviceSet2::IsSharedBuffer.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: 5e969b4cb9bef48d11a884dd3bfec7d2fcabde88
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125330"
---
# <a name="iservervirtualdeviceset2issharedbuffer-vdi"></a>IServerVirtualDeviceSet2::IsSharedBuffer (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

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