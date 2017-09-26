---
title: "Catalog.get_parameter_values (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5b1aeaf7-c938-4aef-bafc-e4d7a82eb578
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4ad8f0c367e38581db696d2aa32afd5b92d635d2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="cataloggetparametervalues-ssisdb-database"></a>catalog.get_parameter_values (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Résout et extrait les valeurs de paramètre par défaut d'un projet et les packages correspondants dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
get_parameter_values [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @package_name = ] package_name  
  [  , [ @reference_id = ] reference_id  ]  
  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier qui contient le projet. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nom du projet où les paramètres résident. Le *project_name* est **nvarchar (128)**.  
  
 [ @package_name =] *package_name*  
 Nom du package. Spécifiez le nom du package pour extraire tous les paramètres du projet et les paramètres d'un package spécifique. Utilisez NULL pour extraire tous les paramètres du projet et les paramètres de tous les packages. Le *package_name* est **nvarchar (260)**.  
  
 [ @reference_id =] *reference_id*  
 Identificateur unique d’une référence d’environnement. Ce paramètre est facultatif. Le *reference_id* est **bigint**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne une table qui a le format suivant :  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|Le type de paramètre. La valeur est `20` pour un paramètre du projet et `30` pour un paramètre du package.|  
|parameter_data_type|**nvarchar (128)**|Type de données du paramètre.|  
|parameter_name|**sysname**|Nom du paramètre.|  
|parameter_value|**sql_variant**|Valeur du paramètre.|  
|sensible|**bit**|Lorsque la valeur est `1`, la valeur de paramètre est sensible. Lorsque la valeur est `0`, la valeur de paramètre n'est pas sensible.|  
|required|**bit**|Lorsque la valeur est `1`, la valeur de paramètre est obligatoire pour démarrer l'exécution. Lorsque la valeur est `0`, la valeur de paramètre n'est pas obligatoire pour démarrer l'exécution.|  
|value_set|**bit**|Lorsque la valeur est `1`, la valeur de paramètre a été affectée. Lorsque la valeur est `0`, la valeur de paramètre n'a pas été affectée.|  
  
> [!NOTE]  
>  Les valeurs littérales sont affichées en texte en clair. **NULL** s’affiche à la place des valeurs sensibles.  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ sur le projet et, si applicable, autorisations READ sur les environnements référencés  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   Le package est introuvable dans le dossier ou le projet spécifié  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
-   La référence environnementale spécifiée n'existe pas  
  
  
