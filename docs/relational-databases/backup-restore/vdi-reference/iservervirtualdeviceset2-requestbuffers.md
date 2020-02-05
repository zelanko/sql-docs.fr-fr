---
title: IServerVirtualDeviceSet2::RequestBuffers
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IServerVirtualDeviceSet2::RequestBuffers.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1b941f251c9093f10abbced8c3522f1719a1580e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "70847180"
---
# <a name="iservervirtualdeviceset2requestbuffers-vdi"></a>IServerVirtualDeviceSet2::RequestBuffers (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonction **RequestBuffers** informe l’interface VDI que le serveur a besoin d’un certain nombre de mémoires tampons avec une taille et une spécification d’alignement données.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IServerVirtualDeviceSet2::RequestBuffers (
   DWORD   dwSize,
   DWORD   dwAlignment,
   DWORD   dwCount
);
```

## <a name="parameters"></a>Paramètres

*dwSize* : identifie la taille de chaque mémoire tampon. Cette taille doit inclure seulement la région nécessaire pour les données. L’interface VDI prend en charge les spécifications d’alignement et de préfixe.

*dwAlignment* : l’alignement nécessaire pour ces mémoires tampons. Une valeur plus restrictive que la valeur d’alignement de base spécifiée avec « BeginConfiguration » peut être utilisée. Si sa valeur est 0, la valeur de l’alignement de base est utilisée par défaut.

*dwCount* : nombre de mémoires tampons demandées par « AllocateBuffer » avec la taille et l’alignement spécifiés.

## <a name="return-value"></a>Valeur de retour

|Valeur de retour | Explication |
|---|---|
| NOERROR | La fonction a réussi. |
| VD_E_ABORT | L’annulation a été demandée. |
| VD_E_PROTOCOL | L’ensemble n’est pas dans un état dans lequel les allocations de mémoire tampon peuvent être déclarées (consultez la matrice de transition d’états). |
| VD_E_MEMORY | La mémoire demandée n’a pas pu être obtenue. |

## <a name="remarks"></a>Notes

Cette méthode doit être utilisée avant que les mémoires tampons soient allouées avec AllocateBuffer. Les ensembles de mémoires tampons avec une taille et un alignement donnés sont demandés avec RequestBuffers, puis les mémoires tampons individuelles sont allouées avec AllocateBuffer.

Pendant la phase de configuration, les appels de RequestBuffers sont « additionnés » pour que, lors de l’appel de EndConfiguration, une seule zone de mémoire tampon puisse être utilisée (elle est allouée à ce moment-là). Une fois la configuration terminée, tous les appels de RequestBuffers entraînent une allocation immédiate de plus d’espace de mémoire tampon.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).