---
title: catalog.create_environment (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 66367092-9f6e-40e6-90bd-81efb078ab70
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2710243c72f9e245100c3fdd30a9147c89b7d4d8
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58274371"
---
# <a name="catalogcreateenvironment-ssisdb-database"></a>catalog.create_environment (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crée un environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.create_environment [@folder_name =] folder_name  
     , [@environment_name =] environment_name  
  [  , [@environment_description =] environment_description ]  
```  
  
## <a name="arguments"></a>Arguments  
 [@folder_name =] *folder_name*  
 Nom du dossier destiné à contenir l’environnement. *folder_name* est de type **nvarchar(128)**.  
  
 [@environment_name =] *environment_name*  
 Nom de l'environnement. *environment_name* est de type **nvarchar(128)**.  
  
 [@environment_description=] *environment_description*  
 Description facultative de l'environnement. *environment_description* est de type **nvarchar(1024)**.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur le dossier  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   d'un rôle de base de données ;  
  
-   Appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   Le nom du dossier est introuvable  
  
-   Un environnement qui a le même nom existe déjà dans le dossier spécifié  
  
## <a name="remarks"></a>Notes   
 Le nom de l'environnement doit être unique dans le dossier.  
  
  
