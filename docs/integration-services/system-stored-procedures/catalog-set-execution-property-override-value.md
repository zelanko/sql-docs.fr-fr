---
title: Catalog.set_execution_property_override_value | Documents Microsoft
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
ms.assetid: 37cb3c01-f4c0-4978-8e40-a975456def5a
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 20f2c882a78f5e60931b0152d5877898e1972d0a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetexecutionpropertyoverridevalue"></a>catalog.set_execution_property_override_value
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Définit la valeur d'une propriété pour une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.set_execution_property_override_value [ @execution_id = execution_id  
    , [ @property_path = ] property_path  
    , [ @property_value = ] property_value  
    , [ @sensitive = ] sensitive  
```  
  
## <a name="arguments"></a>Arguments  
 [ @execution_id =] *execution_id*  
 Identificateur unique de l'instance d'exécution. Le *execution_id* est **bigint**.  
  
 [ @property_path =] *property_path*  
 Chemin d'accès à la propriété dans le package. Le *property_path* est **nvarchar (4000)**.  
  
 [ @property_value =] *property_value*  
 Valeur de remplacement à affecter à la propriété. Le *property_value* est **nvarchar (max)**.  
  
 [ @sensitive =] *sensibles*  
 Lorsque la valeur est 1, la propriété est sensible et est chiffrée lorsqu'elle est stockée. Lorsque la valeur est 0, la propriété n'est pas sensible et la valeur est stockée dans en texte en clair. Le *sensibles* argument est **bits**.  
  
## <a name="remarks"></a>Notes  
 Cette procédure effectue la même fonction que la **substitutions de propriété** section dans le **avancé** onglet de la **exécuter le Package** boîte de dialogue. Le chemin d’accès à la propriété est dérivée de la **chemin d’accès du Package** propriété de la tâche du package.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
-   L'identificateur d'exécution n'est pas valide.  
  
-   Le chemin de la propriété n'est pas valide.  
  
-   Le type de données de la valeur de propriété ne correspond pas au type de propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [catalog.set_execution_parameter_value &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
  
  

