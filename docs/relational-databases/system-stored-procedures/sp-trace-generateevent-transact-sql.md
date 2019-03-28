---
title: sp_trace_generateevent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_generateevent_TSQL
- sp_trace_generateevent
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_generateevent
ms.assetid: 3ef05bfb-b467-4403-89cc-6e77ef9247dd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a24bb05e8f10e2920bd206531723c228d6c1734
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529351"
---
# <a name="sptracegenerateevent-transact-sql"></a>sp_trace_generateevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée un événement défini par l'utilisateur dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
>**REMARQUE :**  Cette procédure stockée est **pas** déconseillée. Toutes les autres procédures stockées liées à la trace sont déconseillées.  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_trace_generateevent [ @eventid = ] event_id   
     [ , [ @userinfo = ] 'user_info' ]  
     [ , [ @userdata = ] user_data ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @eventid = ] event_id` Est l’ID de l’événement à activer. *event_id* est **int**, sans valeur par défaut. L’ID doit être un des numéros d’événements de 82 à 91, qui représentent les événements définis par l’utilisateur en tant que jeu avec [sp_trace_setevent](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md).  
  
`[ @userinfo = ] 'user_info'` Chaîne facultative définie par l’utilisateur consiste à identifier la raison de l’événement. *user_info* est **nvarchar (128)**, avec NULL comme valeur par défaut.  
  
`[ @userdata = ] user_data` Correspond aux données spécifié par l’utilisateur facultatives pour l’événement. *user_data* est **varbinary (8000)**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Le tableau suivant décrit les valeurs de code que les utilisateurs peuvent recevoir à la fin de l'exécution de la procédure stockée.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|**0**|Aucune erreur.|  
|**1**|Erreur inconnue.|  
|**3**|L'événement spécifié n'est pas valide. L'événement peut ne pas exister ou être inapproprié pour la procédure stockée.|  
|**13**|Mémoire insuffisante. Renvoyé lorsqu'il n'y a pas assez de mémoire pour exécuter l'action spécifiée.|  
  
## <a name="remarks"></a>Notes  
 **sp_trace_generateevent** effectue la plupart des actions précédemment exécutées par le **xp_trace_\***  les procédures stockées étendues. Utilisez **sp_trace_generateevent** au lieu de **xp_trace_generate_event**.  
  
 Seuls les numéros d’ID des événements définis par l’utilisateur peuvent être utilisées avec **sp_trace_generateevent**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère une erreur si d'autres numéros d'identification des événements sont utilisés.  
  
 Paramètres de Trace de SQL toutes les procédures stockées (**sp_trace_xx**) sont strictement typés. Si ces paramètres ne sont pas appelés avec des types de données appropriés pour les paramètres d'entrée tels qu'ils sont spécifiés dans la description de l'argument, la procédure stockée renvoie une erreur.  
  
## <a name="permissions"></a>Autorisations  
 L'utilisateur doit disposer de l'autorisation ALTER TRACE.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée un événement pouvant être configuré par l'utilisateur dans un exemple de table.  
  
```  
--Create a sample table.  
CREATE TABLE user_config_test(col1 int, col2 char(10));  
  
--DROP the trigger if it already exists.  
IF EXISTS  
   (SELECT * FROM sysobjects WHERE name = 'userconfig_trg')  
   DROP TRIGGER userconfig_trg;  
  
--Create an ON INSERT trigger on the sample table.  
CREATE TRIGGER userconfig_trg  
   ON user_config_test FOR INSERT;  
AS  
EXEC master..sp_trace_generateevent  
   @event_class = 82, @userinfo = N'Inserted row into user_config_test';  
  
--When an insert action happens, the user-configurable event fires. If   
you were capturing the event id=82, you will see it in the Profiler output.  
INSERT INTO user_config_test VALUES(1, 'abc');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Trace SQL](../../relational-databases/sql-trace/sql-trace.md)  
  
  
