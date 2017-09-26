---
title: Catalog.remove_data_tap | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b77db3e6-478c-441a-a838-82c4de750275
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2f2c9b5d9333c201120e5f3a3e392c59012a8ac7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogremovedatatap"></a>catalog.remove_data_tap
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Supprime un drainage de données d'une sortie de composant dans une exécution. L'identificateur unique du drainage de données est associé à une instance d'exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
remove_data_tap [ @data_tap_id = ] data_tap_id  
  
```  
  
## <a name="arguments"></a>Arguments  
 [ @data_tap_id =] *data_tap_id*  
 Identificateur unique du drainage de données créé à l'aide de la procédure stockée catalog.add_data_tap. Le *data_tap_id* est **bigint**.  
  
## <a name="remarks"></a>Notes  
 Lorsqu'un package contient plusieurs tâches de flux de données du même nom, le drainage de données est ajouté à la première tâche de flux de données avec le nom donné.  
  
## <a name="return-codes"></a>Codes de retour  
 0 (succès)  
  
 Lorsque la procédure stockée échoue, elle génère une erreur.  
  
## <a name="result-set"></a>Jeu de résultats  
 Aucune  
  
## <a name="remarks"></a>Notes  
 Pour supprimer les données appuie, l’instance de l’exécution doit être dans l’état créé (une valeur de 1 dans le **état** colonne de la [catalog.operations & #40 ; Base de données SSISDB & #41 ; ](../../integration-services/system-views/catalog-operations-ssisdb-database.md)affichage).  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations MODIFY sur l'instance d'exécution  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit les conditions provoquant l'échec de la procédure stockée.  
  
-   L'utilisateur ne dispose pas des autorisations MODIFY.  
  
## <a name="see-also"></a>Voir aussi  
 [Catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)   
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  
