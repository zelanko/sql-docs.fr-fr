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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3b0ff9e5c2a5874b5ff01e8da19fa6015e28b5e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47778557"
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
  
## <a name="permissions"></a>Permissions  
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
  
  
