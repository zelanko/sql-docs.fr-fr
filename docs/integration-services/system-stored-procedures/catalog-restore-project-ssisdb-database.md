---
title: "Catalog.restore_project (base de données SSISDB) | Documents Microsoft"
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
ms.assetid: 8adee525-579b-4d2f-b807-e2ecc07fb2e9
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 23074fc664591411666315036e3493e1b7b26134
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrestoreproject-ssisdb-database"></a>catalog.restore_project (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restaure un projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans une version précédente.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.restore_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project _name  
    , [ @object_version_lsn = ] object_version_lsn  
  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier qui contient le projet. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @project _name =] *project_name*  
 Nom du projet. Le *project_name* est **nvarchar (128)**.  
  
 [ @object_version_lsn =] *object_version_lsn*  
 Version du projet. Le *object_version_lsn* est **bigint**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Détails du projet sont retournés en tant que **varbinary (max)** en tant que partie du jeu de résultats si le *project_name* est trouvé.  
  
 **Aucun jeu de résultats** est retournée si le projet ne peut pas être restauré dans le dossier spécifié.  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur le projet  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   La version du projet n'existe pas ou ne correspond pas au nom du projet  
  
-   Le projet n'existe pas  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
## <a name="remarks"></a>Notes  
 Lorsqu'un projet est restauré, tous les paramètres reçoivent les valeurs par défaut et toutes les références environnementales restent inchangées. Le nombre maximal de versions de projet qui sont conservés dans le catalogue est déterminé par la propriété de catalogue **MAX_VERSIONS_PER_PROJECT**, comme illustré dans le [catalog_property](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) vue.  
  
> [!WARNING]  
>  Les références environnementales peuvent ne plus être valides une fois qu'un projet a été restauré.  
  
  

