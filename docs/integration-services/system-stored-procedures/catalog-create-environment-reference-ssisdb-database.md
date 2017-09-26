---
title: "Catalog.create_environment_reference (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 48069bea-31cb-4a0e-9849-a07edc94088f
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 496136e8a0073ba93f003d8dfa539afb48d2c5dc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreateenvironmentreference-ssisdb-database"></a>catalog.create_environment_reference (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crée une référence environnementale pour un projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
create_environment_reference [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @environment_name = ] environment_name  
     , [ @reference_location = ] reference_location  
  [  , [ @environment_folder_name = ] environment_folder_name ]  
  [  , [ @reference_id = ] reference_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier du projet qui référence l'environnement. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nom du projet qui référence l'environnement. Le *project_name* est **nvarchar (128)**.  
  
 [ @environment_name =] *environment_name*  
 Nom de l'environnement référencé. Le *environment_name* est **nvarchar (128)**.  
  
 [ @reference_location =] *reference_location*  
 Indique si l'environnement peut se trouver dans le même dossier que le projet (référence relative) ou dans un dossier différent (référence absolue). Utilisez la valeur `R` pour indiquer une référence relative. Utilisez la valeur `A` pour indiquer une référence absolue. Le *reference_location* est **char (1)**.  
  
 [ @environment_folder_name =] *environment_folder_name*  
 Nom du dossier dans lequel l'environnement référencé se trouve. Cette valeur est obligatoire pour les références absolues. Le *environment_folder_name* est **nvarchar (128)**.  
  
 [ @reference_id =] *reference_id*  
 Retourne l'identificateur unique de la nouvelle référence. Ce paramètre est facultatif. Le *reference_id* est **bigint**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur le projet, et autorisation READ sur l'environnement  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   Le nom du dossier n'est pas valide.  
  
-   Le nom du projet n'est pas valide.  
  
-   L'utilisateur n'a pas les autorisations appropriées  
  
-   Une référence absolue est spécifiée à l’aide de la `A` dans les *reference_location* paramètre, mais le nom du dossier n’a pas été spécifié avec la *environment_folder_name* paramètre.  
  
## <a name="remarks"></a>Notes  
 Un projet peut avoir des références environnementales relatives ou absolues. Les références relatives font référence à l'environnement par nom et requièrent qu'il réside dans le même dossier que le projet. Les références absolues font référence à l'environnement par nom et par dossier et peuvent faire référence aux environnements qui résident dans un dossier différent que le projet. Un projet peut référencer plusieurs environnements.  
  
  
