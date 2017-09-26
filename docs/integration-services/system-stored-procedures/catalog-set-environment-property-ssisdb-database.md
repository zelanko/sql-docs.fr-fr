---
title: "Catalog.set_environment_property (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a345675b-d32e-4624-96cf-ec656730b114
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8eedfe6919a69759cc6de3645b3e1f965dcdd0c6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetenvironmentproperty-ssisdb-database"></a>catalog.set_environment_property (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Définit la propriété d'un environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
set_environment_property [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier qui contient l'environnement. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @environment_name =] *environment_name*  
 Nom de l'environnement. Le *environment_name* est **nvarchar (128)**.  
  
 [ @property_name =] *property_name*  
 Nom d'une propriété d'environnement. Le *property_name* est **nvarchar (128)**.  
  
 [ @property_value =] *property_value*  
 Valeur de la propriété d'environnement. Le *property_value* est **nvarchar (1024)**.  
  
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
  
-   Le nom du dossier n'est pas valide.  
  
-   Le nom de la propriété n'est pas valide.  
  
-   Le nom de l'environnement n'est pas valide.  
  
## <a name="remarks"></a>Notes  
 Dans cette version finale, seule la propriété `Description` peut être définie. La valeur de la propriété `Description` ne peut pas dépasser 4000 caractères.  
  
  
