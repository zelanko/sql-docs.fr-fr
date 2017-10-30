---
title: Catalog.set_customized_logging_level_description | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 6ceaa39f-2439-457b-b99f-f12d88a1be32
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3899e02c6b1eaa2cc76ad4411d9be3aded817728
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetcustomizedloggingleveldescription"></a>Catalog.set_customized_logging_level_description
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Modifie la description d’un niveau de journalisation personnalisé existant. Pour plus d’informations sur les niveaux de journalisation personnalisés, consultez [Integration Services &#40; SSIS &#41; Journalisation](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.set_customized_logging_level_description [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
```  
  
## <a name="arguments"></a>Arguments  
 [ @level_name =] *nom_niveau*  
 Le nom d’un objet de niveau de journalisation personnalisé.  
  
 Le *nom_niveau* est **nvarchar (128)**.  
  
 [ @level_description =] *level_description*  
 Nouvelle description spécifié le niveau de journalisation personnalisé.  
  
 Le *level_description* est **nvarchar (1024)**.  
  
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
  
  

