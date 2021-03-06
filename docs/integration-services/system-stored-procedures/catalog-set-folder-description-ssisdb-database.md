---
description: catalog.set_folder_description (base de données SSISDB)
title: catalog.set_folder_description (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 802416f6-5177-4db5-bca5-976dec5faf53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 18e7cb22f94e33328ed08968052d03b0261c73df
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96129643"
---
# <a name="catalogset_folder_description-ssisdb-database"></a>catalog.set_folder_description (base de données SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Définit la description d'un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.set_folder_description [ @folder_name = ] folder_name  
    , [ @folder_description = ] folder_description  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name = ] *folder_name*  
 Nom du dossier. *folder_name* est de type **nvarchar(128)** .  
  
 [ @folder_description = ] *folder_description*  
 Description du dossier. *folder_description* est de type **nvarchar(MAX)**.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 Aucun  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La procédure stockée retourne un message pour confirmer le paramètre de la nouvelle description du dossier.  
  
  
