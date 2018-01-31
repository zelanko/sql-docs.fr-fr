---
title: "catalog.set_worker_agent_property (base de données SSISDB) | Microsoft Docs"
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 89e5893e418de7bdd7041b5ec8e8193479205659
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="catalogsetworkeragentproperty-ssisdb-database"></a>catalog.set_worker_agent_property (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Définit la propriété d’un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Worker.

## <a name="syntax"></a>Syntaxe

```sql
catalog.set_worker_agent_property [@WorkerAgentId =] WorkerAgentId, [@PropertyName =] PropertyName, [@PropertyValue =] PropertyValue 
```

## <a name="arguments"></a>Arguments
[@WorkerAgentId =] *WorkerAgentId*  
ID d’agent de Worker de Scale Out Worker. *WorkerAgentId* est de type **uniqueidentifier**.

[@PropertyName =] *PropertyName*  
Nom de la propriété. *PropertyName* est de type **nvarchar(256)**.

[@PropertyValue =] *PropertyValue*  
Valeur de la propriété. *PropertyValue* est de type **nvarchar(max)**.

## <a name="remarks"></a>Notes 
Les noms de propriété valides sont **DisplayName**, **Description** et **Tags**.

## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  

## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**

## <a name="errors-and-warnings"></a>Erreurs et avertissements
  La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L’utilisateur n’a pas les autorisations appropriées 

-   L’ID d’agent de Worker n’est pas valide.

-   Le nom de la propriété n’est pas valide.

-   La valeur de propriété n’est pas valide.  
