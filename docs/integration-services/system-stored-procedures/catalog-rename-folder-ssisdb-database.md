---
title: catalog.rename_folder (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 336ab467-c32f-4d2e-a79c-174dc6fab75e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5f048ff41461e719a06c20ddd08bb62ca58ca974
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65715984"
---
# <a name="catalogrenamefolder-ssisdb-database"></a>catalog.rename_folder (base de données SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Renomme un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.rename_folder [ @old_name = ] old_name , [ @new_name = ] new_name  
```  
  
## <a name="arguments"></a>Arguments  
 [ @old_name = ] *old_name*  
 Nom d'origine du dossier. *old_name* est de type **nvarchar(128)**.  
  
 [ @new_name = ] *new_name*  
 Nouveau nom du dossier. *new_name* est de type **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 None  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   Le nom du dossier d'origine n'est pas valide  
  
-   Le nouveau nom a déjà été utilisé dans un dossier existant  
  
  
