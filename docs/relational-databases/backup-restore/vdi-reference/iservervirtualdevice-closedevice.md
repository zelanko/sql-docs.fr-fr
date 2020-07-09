---
title: IServerVirtualDevice::CloseDevice
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IServerVirtualDevice::CloseDevice.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3e9ff54c500b626d667622105a39e742c5e2a339
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896837"
---
# <a name="iservervirtualdeviceclosedevice-vdi"></a>IServerVirtualDevice::CloseDevice (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

La fonction **CloseDevice** ferme un appareil virtuel qui avait été ouvert avec IServerVirtualDeviceSet2::OpenDevice

## <a name="syntax"></a>Syntaxe

```c
HRESULT IServerVirtualDevice::CloseDevice ();
```

## <a name="return-value"></a>Valeur de retour

|Valeur de retour | Explication |
|---|---|
| VD_E_CLOSE | L’appareil est déjà fermé. |
| VD_E_ABORT | L’interface est dans un état Abort (Abandon). |

## <a name="remarks"></a>Notes

CloseDevice n’est pas obligatoire après l’utilisation de SignalAbort pour forcer un arrêt anormal. Si CloseDevice est appelé après l’utilisation de SignalAbort, aucune action n’est effectuée.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).