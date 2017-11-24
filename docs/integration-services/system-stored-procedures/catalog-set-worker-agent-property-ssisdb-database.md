---
title: "Catalog.set_worker_agent_property (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddd2a534-6925-4d66-90e7-541c14f41de7
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: c1caf4a71e5802968d9471711b8206a26f9c28d5
ms.contentlocale: fr-fr
ms.lasthandoff: 10/20/2017

---
# <a name="catalogsetworkeragentproperty-ssisdb-database"></a>Catalog.set_worker_agent_property (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Définit la propriété d’un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] montée en puissance des processus de travail.

## <a name="syntax"></a>Syntaxe

```sql
catalog.set_worker_agent_property [@WorkerAgentId =] WorkerAgentId, [@PropertyName =] PropertyName, [@PropertyValue =] PropertyValue 
```

## <a name="arguments"></a>Arguments
[@WorkerAgentId =] *WorkerAgentId*  
L’agent de travailleur ID de montée en puissance des processus de travail. Le *WorkerAgentId* est **uniqueidentifier**.

[@PropertyName =] *PropertyName*  
Nom de la propriété. Le *PropertyName* est **nvarchar (256)**.

[@PropertyValue =] *PropertyValue*  
Valeur de la propriété. Le *PropertyValue* est **nvarchar (max)**.

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

## <a name="errors-and-warnings"></a>Erreurs et avertissements
  La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L’utilisateur ne dispose pas des autorisations appropriées 

-   L’ID de l’agent de travailleur n’est pas valide.

-   Le nom de propriété n’est pas valide.

-   La valeur de propriété n’est pas valide.  

