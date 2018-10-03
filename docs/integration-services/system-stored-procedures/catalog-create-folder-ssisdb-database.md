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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 24ff352e3504b07a231b300c4b68378c19fae868
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784927"
---
# <a name="catalogcreatefolder-ssisdb-database"></a>catalog.create_folder (base de données SSISDB)
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
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
Si un dossier avec le même nom existe déjà, la procédure stockée retourne une erreur.  
  
  
