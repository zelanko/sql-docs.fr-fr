---
title: sp_helparticledts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticledts
- sp_helparticledts_TSQL
helpviewer_keywords:
- sp_helparticledts
ms.assetid: cd1aed60-e056-4ff3-86ee-62b19433d890
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cac631425a43870395fa0adceb0bb041d70e1932
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797261"
---
# <a name="sphelparticledts-transact-sql"></a>sp_helparticledts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet d'obtenir des informations sur les noms de tâches personnalisés corrects à utiliser lors de la création d'un abonnement de transformation avec [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helparticledts [ @publication = ] 'publication', [ @article = ] 'article'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'` Est le nom d’un article dans la publication. *article* est **sysname**, sans valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**pre_script_ignore_error_task_name**|**sysname**|Nom de la tâche de programmation intervenant avant la copie des données d'instantané. L'exécution du programme doit se poursuivre si une erreur de script est détectée.|  
|**pre_script_task_name**|**sysname**|Nom de la tâche de programmation intervenant avant la copie des données d'instantané. L'exécution du programme s'arrête si une erreur survient.|  
|**transformation_task_name**|**sysname**|Nom de la tâche de programmation lors de l'utilisation d'une tâche Requête contrôlée par les données.|  
|**post_script_ignore_error_task_name**|**sysname**|Nom de la tâche de programmation intervenant après la copie des données d'instantané. L'exécution du programme doit se poursuivre si une erreur de script est détectée.|  
|**post_script_task_name**|**sysname**|Nom de la tâche de programmation intervenant après la copie des données d'instantané. L'exécution du programme s'arrête si une erreur survient.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helparticledts** est utilisé dans la réplication d’instantané ou transactionnelle.  
  
 Il existe des conventions de nom, requises par les agents de réplication, qui doivent être respectées lors de l'affectation de noms aux tâches dans un programme DTS (Data Transformation Services) de réplication. Dans le cas des tâches personnalisées, telles qu'une tâche d'exécution de requête SQL, le nom est une chaîne concaténée comprenant le nom de l'article, un préfixe et une partie facultative. Lors de l'écriture du code, si vous ne connaissez pas les noms de tâche à utiliser, vous pouvez les trouver dans l'ensemble de résultats.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe et le **db_owner** rôle de base de données fixe peuvent exécuter **sp_helparticledts**.  
  
  
