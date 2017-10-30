---
title: "Catalog.get_project (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: f263c9e4-a7db-4888-a458-70ae99b1f729
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: adb3542d50db426d5908aa8786145406d7263ad6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="cataloggetproject-ssisdb-database"></a>catalog.get_project (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Récupère le flux binaire d'un projet déployé sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.get_project [ @folder_name = ] folder_name , [ @project_name = ] project_name   
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier qui contient le projet. *nom_dossier* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nom du projet. *PROJECT_NAME* est **nvarchar (128)**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Le flux binaire du projet est retourné en tant que **varbinary (max)**. Aucun résultat n'est retourné si le dossier ou le projet est introuvable.  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ sur le projet  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent provoquer la procédure get_project stockées déclencher une erreur :  
  
-   Le projet n'existe pas  
  
-   Le dossier n'existe pas  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
  

