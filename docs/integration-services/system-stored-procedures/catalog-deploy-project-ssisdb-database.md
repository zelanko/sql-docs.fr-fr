---
title: "Catalog.deploy_project (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 2e3439b4-7226-4b61-a993-7a1d161eac7e
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a2e3655bedbb24f2174a62c8792cd168e7642592
ms.openlocfilehash: 9871d26467a300119c742d398ff88f87825d930c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="catalogdeployproject-ssisdb-database"></a>catalog.deploy_project (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Déploie un projet dans un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou met à jour un projet existant qui a été déployé précédemment.  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
deploy_project [ @folder_name = ] folder_name   
      , [ @project_name = ] project_name   
      , [ @project_stream = ] projectstream   
    [ , [@operation_id ] = operation_id OUTPUT ]   
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier où le projet sera déployé. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nom du nouveau projet ou du projet mis à jour dans le dossier. Le *project_name* est **nvarchar (128)**.  
  
 [ @projectstream =] *projectstream*  
 Contenu binaire du fichier de déploiement d'un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (extension .ispac).  
  
 Vous pouvez utiliser une instruction SELECT avec la fonction OPENROWSET et le fournisseur d'ensembles de lignes BULK pour récupérer le contenu binaire du fichier. Pour obtenir un exemple, consultez [Integration Services (SSIS) déployer des projets et Packages](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md). Pour plus d’informations sur OPENROWSET, consultez [OPENROWSET &#40; Transact-SQL &#41; ](../../t-sql/functions/openrowset-transact-sql.md).  
  
 Le *projectstream* est **varbinary (max)**  
  
 [ @operation_id =] *identifiant_opération*  
 Retourne l'identificateur unique de l'opération de déploiement. Le *identifiant_opération* est **bigint**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations CREATE_OBJECTS sur le dossier pour déployer un nouveau projet ou des autorisations MODIFY sur le projet pour mettre à jour un projet  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur de cette procédure stockée :  
  
-   Un paramètre fait référence à un objet qui n'existe pas, un paramètre essaie de créer un objet qui existe déjà, ou un paramètre n'est pas valide d'une autre manière  
  
-   La valeur du paramètre  *@project_name*  ne correspond pas à celui du projet dans le fichier de déploiement  
  
-   L'utilisateur n'a pas des autorisations suffisantes.  
  
## <a name="remarks"></a>Notes  
 Pendant un déploiement ou une mise à jour de projet, la procédure stockée ne vérifie pas le niveau de protection des packages individuels dans le projet.  
  
  
