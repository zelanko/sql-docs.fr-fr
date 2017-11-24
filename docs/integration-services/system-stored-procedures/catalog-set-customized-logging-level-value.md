---
title: Catalog.set_customized_logging_level_value | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
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
ms.assetid: d83fb763-c7c6-4e20-bd10-0f995598b198
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 75ef405fe4550e81ec2d5178a1d3242d405755af
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetcustomizedlogginglevelvalue"></a>Catalog.set_customized_logging_level_value
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Modifie les statistiques ou les événements enregistrés par un niveau de journalisation personnalisé existant. Pour plus d’informations sur les niveaux de journalisation personnalisés, consultez [Integration Services &#40; SSIS &#41; Journalisation](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.set_customized_logging_level_value [ @level_name = ] level_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>Arguments  
 [ @level_name =] *nom_niveau*  
 Le nom d’un objet de niveau de journalisation personnalisé.  
  
 Le *nom_niveau* est **nvarchar (128)**.  
  
 [ @property_name =] *property_name*  
 Le nom de la propriété à modifier. Les valeurs valides sont **profil** et **événements**.  
  
 Le *property_name* est **nvarchar (128)**.  
  
 [ @property_value =] *property_value*  
 La nouvelle valeur pour la propriété spécifiée de l’objet de niveau de journalisation personnalisé.  
  
 Pour obtenir la liste des valeurs valides pour le profil et les événements, consultez [catalog.create_customized_logging_level](../../integration-services/system-stored-procedures/catalog-create-customized-logging-level.md).  
  
 Le *property_value* est un **bigint**.  
  
## <a name="remarks"></a>Notes  
  
## <a name="return-codes"></a>Codes de retour  
 0 (succès)  
  
 Lorsque la procédure stockée échoue, elle génère une erreur.  
  
## <a name="result-set"></a>Jeu de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   L’appartenance au rôle de base de données **ssis_admin**  
  
-   L’appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit les conditions provoquant l'échec de la procédure stockée.  
  
-   L’utilisateur n’a pas les autorisations requises.  
  
  

