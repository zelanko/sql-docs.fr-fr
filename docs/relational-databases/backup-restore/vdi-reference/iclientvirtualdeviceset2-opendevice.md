---
title: IClientVirtualDeviceSet2::OpenDevice
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IClientVirtualDeviceSet2::OpenDevice.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f28a7547d16a03e5be963b3cfeb837e7ab78c007
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896876"
---
# <a name="iclientvirtualdeviceset2opendevice-vdi"></a>IClientVirtualDeviceSet2::OpenDevice (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

La fonction **OpenDevice** ouvre un des appareils de l’ensemble d’appareils virtuels.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IClientVirtualDeviceSet2::OpenDevice (
   LPCWSTR                  lpName,
   IClientVirtualDevice**   ppVirtualDevice

);
```

## <a name="parameters"></a>Paramètres

*lpName* : identifie l’appareil virtuel.

*ppVirtualDevice* : quand la fonction réussit, un pointeur d’interface vers l’appareil virtuel est retourné. Cette interface est utilisée pour GetCommand et CompleteCommand.

## <a name="return-value"></a>Valeur de retour

|Valeur de retour | Explication |
|---|---|
| NOERROR | La fonction a réussi. |
| VD_E_ABORT | L’annulation a été demandée. |
| VD_E_OPEN |Tous les appareils sont ouverts. |
| VD_E_PROTOCOL | L’ensemble n’est pas dans l’état d’initialisation ou cet appareil particulier est déjà ouvert. |
| VD_E_INVALID | Le nom de l’appareil n’est pas valide. Il ne s’agit pas d’un des noms connus pour inclure l’ensemble. |

## <a name="remarks"></a>Notes

VD_E_OPEN peut être retourné sans problème. Le client peut appeler OpenDevice au moyen d’une boucle jusqu’à ce que ce code soit retourné.
Si plusieurs appareils sont configurés (par exemple n appareils), l’ensemble d’appareils virtuels retourne n interfaces d’appareil uniques. Le premier appareil a le même nom que l’ensemble d’appareils virtuels. Les autres appareils sont nommés comme spécifié avec les clauses VIRTUAL_DEVICE de l’instruction BACKUP/RESTORE.

La fonction GetConfiguration peut être utilisée pour attendre jusqu’à ce que les appareils puissent être ouverts.

Si cette fonction échoue, une valeur null est retournée par le biais de ppVirtualDevice.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).