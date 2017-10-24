---
title: "Catalog.set_object_parameter_value (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: fb887543-f92f-404d-9495-a1dd23a6716e
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 3a5dc70b1e955b3c702dc9e9dbe4776cc4ebd5ac
ms.contentlocale: fr-fr
ms.lasthandoff: 10/20/2017

---
# <a name="catalogsetobjectparametervalue-ssisdb-database"></a>catalog.set_object_parameter_value (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Définit la valeur d'un paramètre dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Associe la valeur à une variable d’environnement ou affecte une valeur littérale qui est utilisée par défaut lorsque aucune autre valeur n’est affectés.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.set_object_parameter_value [@object_type =] object_type   
    , [@folder_name =] folder_name   
    , [@project_name =] project_name   
    , [@parameter_name =] parameter _name   
    , [@parameter_value =] parameter_value   
 [  , [@object_name =] object_name ]  
 [  , [@value_type =] value_type ]  
```  
  
## <a name="arguments"></a>Arguments  
 [@object_type =] *object_type*  
 Le type de paramètre. Utilisez la valeur `20` pour indiquer un paramètre du projet ou la valeur `30` pour indiquer un paramètre du package. Le *object_type* est **smallInt**.  
  
 [@folder_name =] *nom_dossier*  
 Nom du dossier qui contient le paramètre. Le *nom_dossier* est **nvarchar (128)**.  
  
 [@project_name =] *project_name*  
 Nom du projet qui contient le paramètre. Le *project_name* est **nvarchar (128)**.  
  
 [@parameter_name =] *nom_paramètre*  
 Nom du paramètre. Le *nom_paramètre* est **nvarchar (128)**.  
  
 [@parameter_value =] *parameter_value*  
 Valeur du paramètre. Le *parameter_value* est **sql_variant**.  
  
 [@object_name =] *nom_objet*  
 Nom du package. Cet argument est obligatoire lorsque le paramètre est un paramètre du package. Le *nom_objet* est **nvarchar (260)**.  
  
 [@value_type =] *value_type*  
 Type de valeur du paramètre. Utilisez le caractère `V` pour indiquer que *parameter_value* est une valeur littérale qui est utilisée par défaut lorsque aucune autre valeur n’est affecté avant l’exécution. Utilisez le caractère `R` pour indiquer que *parameter_value* est une valeur référencée et a été défini sur le nom d’une variable d’environnement. Cet argument est facultatif, le caractère `V` est utilisé par défaut. Le *value_type* est **char (1)**.  
  
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
 La liste suivante décrit quelques conditions qui peuvent générer une erreur de procédure stockée :  
  
-   Le type de paramètre n'est pas valide.  
  
-   Le nom du projet n'est pas valide.  
  
-   Pour les paramètres du package, le nom du package n'est pas valide  
  
-   Le type de valeur n'est pas valide.  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
## <a name="remarks"></a>Notes  
  
-   Si aucun *value_type* est spécifié, une valeur littérale pour *parameter_value* est utilisé par défaut. Lorsqu’une valeur littérale est utilisée, le *value_set* dans les [object_parameters](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md) affichage est défini sur `1`. Une valeur de paramètre NULL n'est pas autorisée.  
  
-   Si *value_type* contient le caractère `R`, qui désigne une valeur référencée, *parameter_value* fait référence au nom d’une variable d’environnement.  
  
-   La valeur `20` peuvent être utilisés pour *object_type* pour dénoter un paramètre de projet. Dans ce cas, une valeur pour *nom_objet* n’est pas nécessaire et toute valeur spécifiée pour *nom_objet* est ignoré. Cette valeur est utilisée lorsque l'utilisateur souhaite définir un paramètre du projet.  
  
-   La valeur `30` peuvent être utilisés pour *object_type* pour dénoter un paramètre de package. Dans ce cas, une valeur pour *nom_objet* sert à désigner le package correspondant. Si *nom_objet* n’est pas spécifié, la procédure stockée renvoie une erreur et s’arrête.  
  
  
