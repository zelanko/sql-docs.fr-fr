---
title: "Catalog.move_project (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: ef3b0325-d8e9-472b-bf11-7d3efa6312ff
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5b091ccea1f733ebbf6e52308d17c7bdb7449cbe
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogmoveproject---ssisdb-database"></a>Catalog.move_project - base de données SSISDB
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Déplace un projet d'un dossier vers un autre dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.move_project [ @source_folder = ] source_folder  
    , [ @project_name = ] project_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>Arguments  
 [ @source_folder =] *source_folder*  
 Nom du dossier source, où le projet réside avant le déplacement. Le *source_folder* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nom du projet qui sera supprimé. Le *project_name* est **nvarchar (128)**.  
  
 [ @destination_folder =] *destination_folder*  
 Nom du dossier de destination, où le projet réside après le déplacement. Le *destination_folder* est **nvarchar (128)**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur le projet que vous souhaitez déplacer et autorisation CREATE_OBJECTS sur le dossier de destination  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur de cette procédure stockée :  
  
-   Le projet n'existe pas  
  
-   Le dossier source n'existe pas  
  
-   Le dossier de destination n'existe pas ou le dossier de destination contient déjà un projet avec le même nom  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
## <a name="remarks"></a>Notes  
 Lorsqu'un projet est déplacé d'un dossier source vers un dossier de destination, le projet dans le dossier source et les références environnementales correspondantes sont supprimés. Dans le dossier de destination, un projet et des références environnementales identiques sont créés. Les références environnementales relatives seront résolues dans un dossier différent après le déplacement. Les références absolues seront résolues dans le même dossier après le déplacement.  
  
> [!NOTE]  
>  Un projet peut avoir des références environnementales relatives ou absolues. Les références relatives font référence à l'environnement par nom et requièrent que l'environnement réside dans le même dossier que le projet. Les références absolues font référence à l'environnement par nom et dossier, et aux environnements qui résident dans un dossier différent de celui du projet.  
  
  
