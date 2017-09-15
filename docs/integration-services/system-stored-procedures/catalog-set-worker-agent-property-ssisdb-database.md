---
title: "Catalog.set_worker_agent_property (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddd2a534-6925-4d66-90e7-541c14f41de7
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: d0476bbb67cff44a05aed1441a31d679882b4cb3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/08/2017

---
# <a name="catalogsetworkeragentproperty-ssisdb-database"></a>Catalog.set_worker_agent_property (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Définit la propriété d’un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] montée en puissance des processus de travail.

## <a name="syntax"></a>Syntaxe

```tsql
set_worker_agent_property [ @WorkerAgentId = ] WorkerAgentId, [ @PropertyName = ] PropertyName, [ @PropertyValue = ] PropertyValue 
```

## <a name="arguments"></a>Arguments
[ @WorkerAgentId =] *WorkerAgentId*  
L’id de l’agent de travailleur de montée en puissance des processus de travail. Le *WorkerAgentId* est **uniqueidentifier**.

[ @PropertyName =] *PropertyName*  
Nom de la propriété. Le *PropertyName* est **nvarchar (256)**.

[ @PropertyValue =] *PropertyValue*  
La valeur de la propriété. Le *PropertyValue* est **nvarchar (max)**.

## <a name="remarks"></a>Notes
Les noms de propriétés valides sont **DisplayName**, **Description**, **balises**.

## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  

## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur

## <a name="erros-and-warnings"></a>Erreurs et avertissements
  La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L’utilisateur ne dispose pas des autorisations appropriées 

-   L’id de l’agent de travailleur n’est pas valide.

-   Le nom de propriété n’est pas valide.

-   La valeur de propriété n’est pas vilid.  
