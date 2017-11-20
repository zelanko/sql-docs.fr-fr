---
title: "Catalog.move_environment (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
ms.assetid: b3fb5242-3c4c-4a87-b3e5-beb22fbab053
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e08328e0baccaa9098d8647b50c6133de2504912
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogmoveenvironment-ssisdb-database"></a>catalog.move_environment (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Déplace un environnement d'un dossier vers un autre dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.move_environment [ @source_folder = ] source_folder  
    , [ @environment_name = ] environment_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>Arguments  
 [ @source_folder =] *source_folder*  
 Nom du dossier source, où l'environnement réside avant le déplacement. Le *source_folder* est **nvarchar (128)**.  
  
 [ @environment_name =] *environment_name*  
 Nom de l'environnement qui sera supprimé. Le *environment_name* est **nvarchar (128)**.  
  
 [ @destination_folder =] *destination_folder*  
 Nom du dossier de destination, où l'environnement réside après le déplacement. Le *destination_folder* est **nvarchar (128)**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur l'environnement  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L'environnement n'existe pas dans le dossier source  
  
-   Le dossier de destination a déjà un environnement avec le même nom  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
## <a name="remarks"></a>Notes  
 Les références environnementales des projets ne suivent pas l'environnement pendant le déplacement. Les références environnementales doivent être mises à jour en conséquence. Cette procédure stockée réussira même si les références environnementales sont arrêtées en déplaçant un environnement. Les références environnementales doivent être mises à jour après que cette procédure stockée s'est achevée.  
  
> [!NOTE]  
>  Un projet peut avoir des références environnementales relatives ou absolues. Les références relatives font référence à l'environnement par nom et requièrent que l'environnement réside dans le même dossier que le projet. Les références absolues font référence à l'environnement par nom et dossier, et aux environnements qui résident dans un dossier différent de celui du projet.  
  
  

