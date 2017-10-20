---
title: Catalog.deploy_packages | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 8e861df6-d103-4d84-8438-e822533f6849
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1839430dd7fb83ab16c4de46011819e3ce28e835
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogdeploypackages"></a>Catalog.deploy_packages
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Déploie un ou plusieurs packages dans un dossier sous le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalogue ou met à jour un package existant qui a été déployé précédemment.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
[catalog].[deploy_packages]     [ @folder_name = ] folder_name,    [ @project_name = ] project_name,    [ @packages_table = ] packages_table,     [ @operation_id OUTPUT ] operation_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Le nom du projet dans le dossier. Le *project_name* est **nvarchar (128)**.  
  
 [ @packages_table =] *packages_table*  
 Le contenu binaire de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package (.dtsx) fichier (s). Le *packages_table* est **[catalogue]. [ Package_Table_Type]**  
  
 [ @operation_id =] *identifiant_opération*  
 Retourne l'identificateur unique de l'opération de déploiement. Le *identifiant_opération* est **bigint**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations CREATE_OBJECTS sur le projet ou modifier les autorisations sur le package à mettre à jour un package.  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur de cette procédure stockée :  
  
-   Un paramètre fait référence à un objet qui n’existe pas, un paramètre essaie de créer un objet qui existe déjà, ou un paramètre n’est pas valide dans une autre façon.  
  
-   L'utilisateur n'a pas des autorisations suffisantes.  
  
  
