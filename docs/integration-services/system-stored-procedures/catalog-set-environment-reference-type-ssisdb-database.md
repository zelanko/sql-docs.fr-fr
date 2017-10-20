---
title: "Catalog.set_environment_reference_type (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b79e3a06-22c0-40e5-8933-1b3414db3329
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e83d9979ee4736528efb4851848ea3eac717fab8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetenvironmentreferencetype-ssisdb-database"></a>catalog.set_environment_reference_type (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Définit le type de référence et le nom de l'environnement associés à une référence environnementale existante pour un projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
set_environment_reference_location [ @reference_id = reference_id  
    , [ @reference_type = ] reference_type  
 [  , [ @environment_folder_name = ] environment_folder_name ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @reference_id =] *reference_id*  
 Identificateur unique de la référence environnementale qui sera mise à jour. Le *reference_id* est **bigint**.  
  
 [ @reference_type =] *reference_type*  
 Indique si l'environnement peut se trouver dans le même dossier que le projet (référence relative) ou dans un dossier différent (référence absolue). Utilisez la valeur `R` pour indiquer une référence relative. Utilisez la valeur `A` pour indiquer une référence absolue. Le *reference_type* est **char (1)**.  
  
 [ @environment_folder_name =] *environment_folder_name*  
 Dossier dans lequel l'environnement se trouve. Cette valeur est obligatoire pour les références absolues. Le *environment_folder_name* est **nvarchar (128)**.  
  
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
  
-   Le nom du dossier, le nom de l’environnement ou l’ID de référence n’est pas valide  
  
-   L'utilisateur n'a pas les autorisations appropriées  
  
-   Une référence absolue est spécifiée à l’aide de la `A` dans les *reference_location* paramètre, mais le nom du dossier n’a pas été spécifié avec la *environment_folder_name* paramètre.  
  
## <a name="remarks"></a>Notes  
 Un projet peut avoir des références environnementales relatives ou absolues. Les références relatives font référence à l'environnement par nom et requièrent qu'il réside dans le même dossier que le projet. Les références absolues font référence à l'environnement par nom et par dossier et peuvent faire référence aux environnements qui résident dans un dossier différent que le projet. Un projet peut référencer plusieurs environnements.  
  
> [!IMPORTANT]  
>  Si une référence relative est spécifiée, le *environment_folder_name* la valeur du paramètre n’est pas utilisée, et le nom de dossier d’environnement est automatiquement défini sur **NULL**. Si une référence absolue est spécifiée, le nom de dossier d’environnement doit être fourni dans le *environment_folder_name* paramètre.  
  
  
