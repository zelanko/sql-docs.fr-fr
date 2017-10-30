---
title: "Catalog.delete_project (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: f3431445-8dd2-443b-813e-b99db893977e
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: abc0280a693be8e0f9fa9b3ec997c1d38d96ed54
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogdeleteproject-ssisdb-database"></a>catalog.delete_project (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Supprime un projet existant d'un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.delete_project [ @folder_name = ] folder_name , [ @project_name = ] project_name  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier qui contient le projet. *nom_dossier* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Le nom du projet qui doit être supprimé. *PROJECT_NAME* est **nvarchar (128)**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur le projet  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent provoquer la procédure delete_project stockées déclencher une erreur :  
  
-   Le projet n'existe pas  
  
-   Le dossier n'existe pas  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
## <a name="remarks"></a>Notes  
 Tous les objets et les références environnementales du projet correspondant sont supprimés avec le projet. Toutefois, les versions du projet et les archives d'exploitation pertinentes sont conservées jusqu'à la prochaine exécution du travail de nettoyage de l'opération.  
  
  

