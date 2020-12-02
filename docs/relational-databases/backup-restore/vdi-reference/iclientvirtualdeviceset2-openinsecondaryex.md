---
title: IClientVirtualDeviceSet2::OpenInSecondaryEx
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IClientVirtualDeviceSet2::OpenInSecondaryEx.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: a5b2a680e34d6aa6c174cc356a2cb99bee75131f
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "96128955"
---
# <a name="iclientvirtualdeviceset2openinsecondaryex-vdi"></a>IClientVirtualDeviceSet2::OpenInSecondaryEx (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

La fonction **OpenInSecondaryEx** ouvre l’ensemble d’appareils virtuels dans un client secondaire. Le client principal doit déjà avoir utilisé CreateEx et GetConfiguration pour configurer l’ensemble d’appareils virtuels.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IClientVirtualDeviceSet2::OpenInSecondaryEx (
   LPCWSTR      lpInstanceName,
   LPCWSTR      lpSetName
);
```

## <a name="parameters"></a>Paramètres

*lpInstanceName* : cette chaîne identifie l’instance SQL Server à laquelle la commande SQL sera envoyée.

*lpSetName* : identifie l’ensemble. Ce nom respecte la casse et doit correspondre au nom utilisé par le client principal quand il a appelé IClientVirtualDeviceSet2::Create.

## <a name="return-value"></a>Valeur de retour

|Valeur de retour | Explication |
|---|---|
| NOERROR | La fonction a réussi. |
| VD_E_PROTOCOL | L’ensemble d’appareils virtuels a été ouvert ou l’ensemble d’appareils virtuels n’est pas prêt à accepter les demandes d’ouverture des clients secondaires. |
| VD_E_ABORT | L’opération est en cours d’abandon. |

## <a name="remarks"></a>Notes

Quand vous utilisez un modèle à plusieurs processus, le client principal est responsable de la détection de l’arrêt normal ou anormal des clients secondaires.

Le nom de l’instance doit identifier l’instance à destination de laquelle le T-SQL est émis. NULL identifie l’instance par défaut. Aucun préfixe "machineName\" n’est accepté.

OpenInSecondaryEx remplace la commande IClientVirtualDeviceSet::OpenInSecondary d’origine qui était définie dans l’interface SQL Server version 7.0 d’origine. Un nouveau développement doit utiliser OpenInSecondaryEx.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).