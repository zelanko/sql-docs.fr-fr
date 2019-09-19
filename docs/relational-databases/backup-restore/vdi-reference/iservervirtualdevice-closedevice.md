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
ms.openlocfilehash: c73649e2a4301e94f8e68504222cc0122061f25f
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847430"
---
# <a name="iservervirtualdeviceclosedevice-vdi"></a>IServerVirtualDevice::CloseDevice (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonction **CloseDevice** ferme un appareil virtuel qui avait été ouvert avec IServerVirtualDeviceSet2::OpenDevice

## <a name="syntax"></a>Syntaxe

```c
HRESULT IServerVirtualDevice::CloseDevice ();
```

## <a name="return-value"></a>Valeur retournée

|Valeur retournée | Explication |
|---|---|
| VD_E_CLOSE | L’appareil est déjà fermé. |
| VD_E_ABORT | L’interface est dans un état Abort (Abandon). |

## <a name="remarks"></a>Notes

CloseDevice n’est pas obligatoire après l’utilisation de SignalAbort pour forcer un arrêt anormal. Si CloseDevice est appelé après l’utilisation de SignalAbort, aucune action n’est effectuée.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).