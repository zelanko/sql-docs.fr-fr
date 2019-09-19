---
title: IClientVirtualDeviceSet2::CreateEx
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IClientVirtualDeviceSet2::CreateEx.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 90165738dfcea8818353d602f72390bb08eea792
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847350"
---
# <a name="iclientvirtualdeviceset2createex-vdi"></a>IClientVirtualDeviceSet2::CreateEx (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonction **CreateEx** crée l’ensemble d’appareils virtuels.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IClientVirtualDeviceSet2::CreateEx (
   LPCWSTR         lpInstanceName,
   LPCWSTR         lpName,
   VDConfig*      pCfg
);
```

## <a name="parameters"></a>Paramètres

*lpInstanceName* : cette chaîne identifie l’instance SQL Server à laquelle la commande SQL sera envoyée.

*lpName* : identifie l’ensemble d’appareils virtuels. Les règles pour les noms utilisés par CreateFileMapping() doivent être suivies. N’importe quel caractère à l’exception de la barre oblique inverse (\) peut être utilisé. Il s’agit d’une chaîne Unicode à caractères larges. Il est recommandé de préfixer la chaîne avec le nom de la société ou du produit de l’utilisateur et le nom de la base de données.

*pCfg* : la configuration pour l’ensemble d’appareils virtuels. Pour plus d’informations, consultez Configuration.

## <a name="return-value"></a>Valeur retournée

|Valeur retournée | Explication |
|---|---|
| NOERROR | La fonction a réussi. |
| VD_E_NOTSUPPORTED | Un ou plusieurs champs de la configuration ne sont pas valides ou ne sont pas pris en charge. |
| VD_E_PROTOCOL | L’ensemble d’appareils virtuels a été créé. |

## <a name="remarks"></a>Notes

La méthode CreateEx ne doit être appelée qu’une seule fois par opération BACKUP ou RESTORE. Après l’appel de la méthode Close, le client peut réutiliser l’interface pour créer un autre ensemble d’appareils virtuels.

Le nom de l’instance doit identifier l’instance à destination de laquelle le Transact-SQL est émis. NULL identifie l’instance par défaut. Aucun préfixe "machineName\" n’est accepté.

Les appels de CreateEx (et de Create) modifient la liste DACL de sécurité sur le descripteur de processus dans le processus client. Pour cette raison, toute autre modification du descripteur de processus doit être sérialisée avec l’appel de CreateEx. CreateEx va sérialiser avec d’autres appels à CreateEx, mais il ne peut pas être sérialisé avec un traitement externe. L’accès est accordé au compte exécutant le service SQL Server.

La méthode CreateEx remplace la méthode Create définie dans le IClientVirtualDeviceSet d’origine. La méthode Create d’origine est dépréciée et ne doit pas être utilisée dans des développements futurs. La méthode Create d’origine implémente une forme de prise en charge du nom d’instance avec la variable d’environnement _VIRTUAL_SERVER_NAME_. Si cette variable est définie dans l’environnement, la méthode Create appelle en interne CreateEx, en passant la valeur de _VIRTUAL_SERVER_NAME_ comme nom d’instance.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).