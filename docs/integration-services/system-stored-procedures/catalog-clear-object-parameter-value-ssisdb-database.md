---
title: "Catalog.clear_object_parameter_value (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: dcbbb714-a051-4805-9e2b-2c2fb647c890
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5d0d89081a31341a8d813d9985940c0e3ce0160a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogclearobjectparametervalue-ssisdb-database"></a>catalog.clear_object_parameter_value (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Efface la valeur d'un paramètre pour un projet ou un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] existant stocké sur le serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.clear_object_parameter [ @folder_name = ] folder_name   
    , [ @project_name = ] project_name   
    , [ @object_type = ] object_type   
    , [ @object_name = ] object_name   
    , [ @parameter_ name = ] parameter_name  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier qui contient le projet. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Le nom du projet. Le *project_name* est **nvarchar (128)**.  
  
 [ @object_type =] *object_type*  
 Type de l'objet. Les valeurs valides incluent `20` pour un projet et `30` pour un package. Le *object_type* est **smallInt**.  
  
 [@ objet _ordinateur =] *_name de l’objet*  
 Nom du package. Le *objet _ordinateur* est **nvarchar (260)**.  
  
 [ @parameter_ nom =] *nom_paramètre*  
 Nom du paramètre. Le *parameter_ nom* est **nvarchar (128)**.  
  
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
 La liste suivante décrit quelques conditions qui peuvent provoquer la procédure clear_object_parameter stockées déclencher une erreur :  
  
-   Un type d'objet non valide est spécifié ou le nom d'objet est introuvable dans le projet.  
  
-   Le projet n'existe pas, n'est pas accessible ou n'est pas valide.  
  
-   Un nom de paramètre non valide est spécifié.  
  
-   L’utilisateur n’a pas les autorisations appropriées.  
  
  

