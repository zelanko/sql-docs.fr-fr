---
title: Sys.fn_trace_gettable (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_trace_gettable
- fn_trace_gettable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_trace_gettable function
- sys.fn_trace_gettable function
ms.assetid: c2590159-6ec5-4510-81ab-e935cc4216cd
author: rothja
ms.author: jroth
ms.openlocfilehash: 18a6225bca9539f10c4dfea61e99d147cb188d4c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059222"
---
# <a name="sysfntracegettable-transact-sql"></a>sys.fn_trace_gettable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie le contenu d'un ou plusieurs fichiers de trace dans un format tabulaire.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt des événements étendus.  
   
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn_trace_gettable ( 'filename' , number_files )  
```  
  
## <a name="arguments"></a>Arguments  
 «*filename*»  
 Spécifie le fichier de trace initial à lire. *nom de fichier* est **nvarchar (256)** , sans valeur par défaut.  
  
 *number_files*  
 Spécifie le nombre de fichiers de substitution à lire. Ce nombre inclut le fichier initial spécifié dans *filename*. *number_files* est un **int**.  
  
## <a name="remarks"></a>Notes  
 Si *number_files* est spécifié en tant que **par défaut**, **fn_trace_gettable** lit tous les fichiers de substitution jusqu'à ce qu’il atteigne la fin de la trace. **fn_trace_gettable** renvoie une table avec toutes les colonnes valides pour la trace spécifiée. Pour plus d’informations, consultez [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md).  
  
 N’oubliez pas que la fonction fn_trace_gettable ne chargera pas les fichiers de substitution (lorsque cette option est spécifiée à l’aide de la *number_files* argument) où le nom de fichier de trace d’origine se termine par un trait de soulignement et une valeur numérique. Cela ne s'applique pas au trait de soulignement et au nombre qui sont automatiquement ajoutés lors du remplacement d'un fichier. Pour résoudre ce problème, vous pouvez renommer les fichiers de trace pour supprimer les traits de soulignement dans le nom de fichier d’origine. Par exemple, si le fichier d’origine se nomme **Trace_Oct_5.trc** et le fichier de substitution est nommé **Trace_Oct_5_1.trc**, vous pouvez renommer les fichiers à **TraceOct5.trc** et  **TraceOct5_1.trc**.  
  
 Cette fonction peut lire une trace encore active sur l'instance sur laquelle elle est exécutée.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER TRACE sur le serveur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-fntracegettable-to-import-rows-from-a-trace-file"></a>R. Utilisation de fn_trace_gettable pour importer des lignes à partir d'un fichier de trace  
 L'exemple suivant appelle `fn_trace_gettable` dans la clause `FROM` d'une instruction `SELECT...INTO`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
### <a name="b-using-fntracegettable-to-return-a-table-with-an-identity-column-that-can-be-loaded-into-a-sql-server-table"></a>B. Utilisation de fn_trace_gettable pour renvoyer une table ayant une colonne IDENTITY qui peut être chargée dans une table SQL Server  
 L'exemple suivant appelle la fonction dans une instruction `SELECT...INTO` et renvoie une table avec une colonne `IDENTITY` qui peut être chargée dans la table `temp_trc`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENTITY(int, 1, 1) AS RowNumber, * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
  
