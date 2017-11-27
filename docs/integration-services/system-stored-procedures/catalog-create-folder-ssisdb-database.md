---
title: "Catalog.create_folder (base de données SSISDB) | Documents Microsoft"
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
ms.assetid: 06fb3549-e970-4ca2-a61f-59affb9c6dcc
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 43d128f9dcc4cea632c810a13d21eb5e1ddb61df
ms.contentlocale: fr-fr
ms.lasthandoff: 10/20/2017

---
# <a name="catalogcreatefolder-ssisdb-database"></a>catalog.create_folder (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crée un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.create_folder [@folder_name =] folder_name, [@folder_id =] folder_id OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
 [@folder_name =] *nom_dossier*  
 Nom du nouveau dossier. Le *nom_dossier* est **nvarchar (128)**.  
  
 [@folder_name =] *folder_id*  
 Identificateur (ID) unique du dossier. Le *folder_id* est **bigint**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 L'identificateur du dossier est retourné.  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
Si un dossier portant le même nom existe déjà, la procédure stockée renvoie une erreur.  
  
  

