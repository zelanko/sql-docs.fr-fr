---
title: "Catalog.rename_folder (base de données SSISDB) | Documents Microsoft"
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
ms.assetid: 336ab467-c32f-4d2e-a79c-174dc6fab75e
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8320f1a4d4fb08e206e2dcde2e5158b5dd0729aa
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrenamefolder-ssisdb-database"></a>catalog.rename_folder (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Renomme un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.rename_folder [ @old_name = ] old_name , [ @new_name = ] new_name  
```  
  
## <a name="arguments"></a>Arguments  
 [ @old_name =] *ancien_nom*  
 Nom d'origine du dossier. Le *ancien_nom* est **nvarchar (128)**.  
  
 [ @new_name =] *nouveau_nom*  
 Nouveau nom du dossier. Le *nouveau_nom* est **nvarchar (128)**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 Aucune  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   Le nom du dossier d'origine n'est pas valide  
  
-   Le nouveau nom a déjà été utilisé dans un dossier existant  
  
  

