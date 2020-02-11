---
title: sys. fn_trace_getinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_trace_getinfo
- fn_trace_getinfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- traces [SQL Server], status information
- status information [SQL Server], traces
- sys.fn_trace_getinfo function
- fn_trace_getinfo function
ms.assetid: 04b140fe-110a-47b8-98b5-e4c161beb6c9
author: rothja
ms.author: jroth
ms.openlocfilehash: 041f651fb34c486cebc589f119f3e5f220314dd2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68059235"
---
# <a name="sysfn_trace_getinfo-transact-sql"></a>sys.fn_trace_getinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur une trace spécifiée ou toutes les traces existantes.  
  
> **PRÉCIEUSE!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt des événements étendus.    
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_trace_getinfo ( { trace_id | NULL | 0 | DEFAULT } )  
```  
  
## <a name="arguments"></a>Arguments  
 *trace_id*  
 ID de la trace. *trace_id* est de **type int**.  Les entrées valides sont le numéro d’identification d’une trace, NULL, 0 ou DEFAULT. Les valeurs NULL, 0 et DEFAULT sont des valeurs équivalentes dans ce contexte. Spécifiez NULL, 0 ou DEFAULT pour retourner les informations de toutes les traces de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="tables-returned"></a>Tables retournées  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|traceid|**int**|Identificateur de la trace.|  
|propriété|**int**|Propriété de la trace :<br /><br /> 1 = options de trace. Pour plus d’informations, @options consultez dans [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md).<br /><br /> 2 = nom de fichier<br /><br /> 3 = taille maxi<br /><br /> 4 = heure d'arrêt<br /><br /> 5 = statut de trace actuel. 0 = arrêtée. 1 = exécution.|  
|value|**sql_variant**|Informations sur la propriété de la trace spécifiée.|  
  
## <a name="remarks"></a>Notes  
 Lorsque l'identificateur d'une trace spécifique lui est passé, la fonction fn_trace_getinfo retourne les informations relatives à cette trace. Lorsqu'un identificateur non valide lui est passé, cette fonction renvoie un ensemble de lignes vide.  
  
 La fonction fn_trace_getinfo ajoute une extension .trc au nom de tous les fichiers de trace inclus dans son jeu de résultats. Pour plus d’informations sur la définition d’une trace, consultez [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md). Pour obtenir des informations similaires sur les filtres de trace, consultez [sys. fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md).  
  
 Pour obtenir un exemple complet d’utilisation de procédures stockées de trace, consultez [créer une trace &#40;&#41;Transact-SQL ](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER TRACE sur le serveur.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne des informations sur toutes les traces actives.  
  
```  
SELECT * FROM sys.fn_trace_getinfo(0) ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une trace &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys. fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys. fn_trace_gettable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
