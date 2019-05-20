---
title: catalog.create_folder (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 06fb3549-e970-4ca2-a61f-59affb9c6dcc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a5115d9c66dd7baf091635b06ff413aa8c4ca736
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65716900"
---
# <a name="catalogcreatefolder-ssisdb-database"></a>catalog.create_folder (base de données SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crée un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.create_folder [@folder_name =] folder_name, [@folder_id =] folder_id OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
 [@folder_name =] *folder_name*  
 Nom du nouveau dossier. *folder_name* est de type **nvarchar(128)**.  
  
 [@folder_name =] *folder_id*  
 Identificateur (ID) unique du dossier. *folder_id* est de type **bigint**.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 L'identificateur du dossier est retourné.  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
Si un dossier avec le même nom existe déjà, la procédure stockée retourne une erreur.  
  
  
