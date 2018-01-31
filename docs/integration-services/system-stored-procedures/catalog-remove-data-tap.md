---
title: catalog.remove_data_tap | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b77db3e6-478c-441a-a838-82c4de750275
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d3fffcb092595785c1b84c1b45908ba9155551f4
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="catalogremovedatatap"></a>catalog.remove_data_tap
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Supprime un drainage de données d'une sortie de composant dans une exécution. L'identificateur unique du drainage de données est associé à une instance d'exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.remove_data_tap [ @data_tap_id = ] data_tap_id  
```  
  
## <a name="arguments"></a>Arguments  
 [ @data_tap_id = ] *data_tap_id*  
 Identificateur unique du drainage de données créé à l'aide de la procédure stockée catalog.add_data_tap. *data_tap_id* est de type **bigint**.  
  
## <a name="remarks"></a>Notes   
 Lorsqu'un package contient plusieurs tâches de flux de données du même nom, le drainage de données est ajouté à la première tâche de flux de données avec le nom donné.  
  
## <a name="return-codes"></a>Codes de retour  
 0 (succès)  
  
 Lorsque la procédure stockée échoue, elle génère une erreur.  
  
## <a name="result-set"></a>Jeu de résultats  
 None  
  
## <a name="remarks"></a>Notes   
 Pour supprimer des drainages de données, l’instance d’exécution doit avoir l’état Created (valeur 1 dans la colonne **status** de la vue [catalog.operations &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)).  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations MODIFY sur l'instance d'exécution  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit les conditions provoquant l'échec de la procédure stockée.  
  
-   L'utilisateur ne dispose pas des autorisations MODIFY.  
  
## <a name="see-also"></a> Voir aussi  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)   
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  
