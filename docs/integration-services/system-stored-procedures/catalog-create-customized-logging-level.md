---
title: Catalog.create_customized_logging_level | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 20b3ba0a-126f-49bf-b70f-61b2a0fcb750
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 126fa0af811033bb0be035b1f4c550620c696bb3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreatecustomizedlogginglevel"></a>Catalog.create_customized_logging_level
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Crée un nouveau niveau de journalisation personnalisée. Pour plus d’informations sur les niveaux de journalisation personnalisés, consultez [Integration Services &#40; SSIS &#41; Journalisation](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.create_customized_logging_level [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
    , [ @profile_value = ] profile_value  
    , [ @event_value = ] event_value  
    , [ @level_id = ] level_id OUT   
```  
  
## <a name="arguments"></a>Arguments  
 [ @level_name =] *nom_niveau*  
 Le nom existant de nouveau le niveau de journalisation personnalisé.  
  
 Le *nom_niveau* est **nvarchar (128)**.  
  
 [ @level_description =] *level_description*  
 La description pour le nouveau le niveau de journalisation personnalisé.  
  
 Le *level_description* est **nvarchar (1024)**.  
  
 [ @profile_value =] *profile_value*  
 Les statistiques que vous souhaitez le nouveau personnalisés au niveau de journalisation pour vous connecter.  
  
 Les valeurs valides pour les statistiques sont les suivantes. Ces valeurs correspondent aux valeurs sur le **statistiques** onglet de la **gestion du niveau de journalisation personnalisé** boîte de dialogue.  
  
-   L’exécution = 0  
  
-   Volume = 1  
  
-   Performances = 2  
  
 Le *profile_value* est un **bigint**.  
  
 [ @event_value =] *event_value*  
 Les événements que vous souhaitez le nouveau personnalisés au niveau de journalisation pour vous connecter.  
  
 Les valeurs valides pour les événements sont les suivantes. Ces valeurs correspondent aux valeurs sur le **événements** onglet de la **gestion du niveau de journalisation personnalisé** boîte de dialogue.  
  
|Événements sans contexte d’événement|Événements avec un contexte d’événement|  
|----------------------------------|-------------------------------|  
|OnVariableValueChanged = 0<br /><br /> OnExecutionStatusChanged = 1<br /><br /> OnPreExecute = 2<br /><br /> OnPostExecute = 3<br /><br /> OnPreValidate = 4<br /><br /> OnPostValidate = 5<br /><br /> OnWarning = 6<br /><br /> OnInformation = 7<br /><br /> OnError = 8<br /><br /> OnTaskFailed = 9<br /><br /> OnProgress = 10<br /><br /> OnQueryCancel = 11<br /><br /> OnBreakpointHit = 12<br /><br /> OnCustomEvent = 13<br /><br /> Diagnostic = 14<br /><br /> DiagnosticEx = 15<br /><br /> NonDiagnostic = 16|OnVariableValueChanged_IncludeContext = 32<br /><br /> OnExecutionStatusChanged_IncludeContext = 33<br /><br /> OnPreExecute_IncludeContext = 34<br /><br /> OnPostExecute_IncludeContext = 35<br /><br /> OnPreValidate_IncludeContext = 36<br /><br /> OnPostValidate_IncludeContext = 37<br /><br /> OnWarning_IncludeContext = 38<br /><br /> OnInformation_IncludeContext = 39<br /><br /> OnError_IncludeContext = 40<br /><br /> OnTaskFailed_IncludeContext = 41<br /><br /> OnProgress_IncludeContext = 42<br /><br /> OnQueryCancel_IncludeContext = 43<br /><br /> OnBreakpointHit_IncludeContext = 44<br /><br /> OnCustomEvent_IncludeContext = 45<br /><br /> Diagnostic_IncludeContext = 46<br /><br /> DiagnosticEx_IncludeContext = 47<br /><br /> NonDiagnostic_IncludeContext = 48|  
  
 Le *event_value* est un **bigint**.  
  
 [ @level_id =] *level_id* OUT  
 L’id de la nouvelle le niveau de journalisation personnalisé.  
  
 Le *level_id* est un **bigint**.  
  
## <a name="remarks"></a>Notes  
 Pour combiner plusieurs valeurs dans Transact-SQL pour le *profile_value* ou *event_value* argument, suivre cet exemple. Pour capturer les OnError (8) et les événements de DiagnosticEx (15), la formule pour calculer *event_value* est `2^8 + 2^15 = 33024`.  
  
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
  
  

