---
title: "Catalog.configure_catalog (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
ms.assetid: 72690c61-f462-4c25-9fce-08a687b0bd41
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 15bec231bf1de825cea952e07827074d56751386
ms.contentlocale: fr-fr
ms.lasthandoff: 10/20/2017

---
# <a name="catalogconfigurecatalog-ssisdb-database"></a>catalog.configure_catalog (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Configure le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en définissant une propriété de catalogue sur une valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql
catalog.configure_catalog [ @property_name = ] property_name , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>Arguments  
 [ @property_name =] *property_name*  
 Nom de la propriété de catalogue. Le *property_name* est **nvarchar (255)**. Pour plus d’informations sur les propriétés disponibles, consultez [catalog.catalog_properties &#40; Base de données SSISDB &#41; ](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md).  
  
 [ @property_value =] *property_value*  
 Valeur de la propriété de catalogue. Le *property_value* est **nvarchar (255)**. Pour plus d’informations sur les valeurs de propriété, consultez [catalog.catalog_properties &#40; Base de données SSISDB &#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="remarks"></a>Notes  
 Cette procédure stockée détermine si le *property_value* n’est valide pour chaque *property_name*.  
  
 Cette procédure stockée peut être effectuée uniquement lorsqu'il n'y a pas d'exécution active, c'est-à-dire pas d'exécutions en attente, en file d'attente, en cours d'exécution ou suspendues.  
  
 Pendant que le catalogue est en cours de configuration, tous les autres catalogue stockées échouent de procédures avec le message d’erreur « Serveur est en cours de configuration. »
  
 Lorsque le catalogue est configuré, une entrée est écrite dans le journal des opérations.  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   La propriété n'existe pas  
  
-   La valeur de la propriété n'est pas valide  
  
  

