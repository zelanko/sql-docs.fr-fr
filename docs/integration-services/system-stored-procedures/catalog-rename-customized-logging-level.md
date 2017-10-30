---
title: Catalog.rename_customized_logging_level | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b1a57d5e-3f03-4901-8b2b-bb8b371b595b
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 00c2cd8fa5f8423a7791d663d02aecbf27b8ab41
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrenamecustomizedlogginglevel"></a>Catalog.rename_customized_logging_level
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Renomme un niveau de journalisation personnalisé existant. Pour plus d’informations sur les niveaux de journalisation personnalisés, consultez [Integration Services &#40; SSIS &#41; Journalisation](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.rename_customized_logging_level [ @old_name = ] old_name  
    , [ @new_name = ] new_name  
```  
  
## <a name="arguments"></a>Arguments  
 [ @old_name =] *ancien_nom*  
 Le nom existants personnalisés de niveau de journalisation à renommer.  
  
 Le *ancien_nom* est **nvarchar (128)**.  
  
 [ @new_name =] *nouveau_nom*  
 Le nouveau nom de l’élément spécifié de niveau de journalisation personnalisé.  
  
 Le *nouveau_nom* est **nvarchar (128)**.  
  
## <a name="remarks"></a>Notes  
  
## <a name="return-codes"></a>Codes de retour  
 0 (succès)  
  
 Lorsque la procédure stockée échoue, elle génère une erreur.  
  
## <a name="result-set"></a>Jeu de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   L’appartenance au rôle de base de données **ssis_admin**  
  
-   L’appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit les conditions provoquant l'échec de la procédure stockée.  
  
-   L’utilisateur n’a pas les autorisations requises.  
  
  

