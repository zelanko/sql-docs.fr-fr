---
title: sp_publication_validation (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_publication_validation
- sp_publication_validation_TSQL
helpviewer_keywords:
- sp_publication_validation
ms.assetid: 06be2363-00c0-4936-97c1-7347f294a936
author: stevestein
ms.author: sstein
ms.openlocfilehash: bdfe70e3df86f792d250cd7abcc3ef3013e9df19
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056231"
---
# <a name="sp_publication_validation-transact-sql"></a>sp_publication_validation (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Lance une demande de validation pour chaque article de la publication spécifiée. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_publication_validation [ @publication = ] 'publication'  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` est le nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @rowcount_only = ] 'rowcount_only'` indique s’il faut retourner uniquement le RowCount de la table. *rowcount_only* est de type **smallint** et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Effectue une somme de contrôle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.<br /><br /> Remarque : lorsqu’un article est filtré horizontalement, une opération ROWCOUNT est exécutée à la place d’une opération de somme de contrôle.|  
|**1** (par défaut)|Effectue un contrôle du nombre de lignes uniquement.|  
|**2**|Effectue un comptage du nombre de lignes et une somme de contrôle binaire.<br /><br /> Remarque : pour les abonnés [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7,0, seule une validation ROWCOUNT est effectuée.|  
  
`[ @full_or_fast = ] 'full_or_fast'` est la méthode utilisée pour calculer le RowCount. *full_or_fast* est de **type tinyint** et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Effectue un comptage total à l'aide de COUNT(*).|  
|**1**|Effectue un comptage rapide à partir de **sysindexes. Rows**. Le comptage des lignes dans [sys. sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md) est beaucoup plus rapide que le comptage des lignes dans la table réelle. Toutefois, étant donné que [sys. sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md) est mis à jour tardivement, le ROWCOUNT peut ne pas être précis.|  
|**2** (par défaut)|Exécute un décompte rapide conditionnel en essayant d'abord la méthode rapide. Si la méthode rapide affiche des différences, revient à la méthode totale. Si *expected_rowcount* a la valeur NULL et la procédure stockée est en cours d’utilisation pour obtenir la valeur, un Count (\*) complète est toujours utilisée.|  
  
`[ @shutdown_agent = ] 'shutdown_agent'` indique si le Agent de distribution doit s’arrêter immédiatement à la fin de la validation. *shutdown_agent* est de **bit**, avec **0**comme valeur par défaut. Si la **valeur est 0**, l’agent de réplication ne s’arrête pas. Si la taille est **1**, l’agent de réplication s’arrête après la validation du dernier article.  
  
`[ @publisher = ] 'publisher'` spécifie un serveur de publication non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  l' *éditeur* ne doit pas être utilisé lors de la demande de validation sur un serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_publication_validation** est utilisé dans la réplication transactionnelle.  
  
 **sp_publication_validation** peut être appelée à tout moment une fois que les articles associés à la publication ont été activés. La procédure peut être exécutée manuellement (une fois) ou en tant que partie d'une tâche régulièrement planifiée qui valide les données.  
  
 Si votre application a des abonnés avec mise à jour immédiate, **sp_publication_validation** peut détecter des erreurs erronées. **sp_publication_validation** calcule d’abord le RowCount ou la somme de contrôle sur le serveur de publication, puis sur l’abonné. Étant donné que les déclencheurs à mise à jour immédiate peuvent propager une mise à jour de l'Abonné vers le serveur de publication une fois que le calcul du nombre de lignes ou de la somme de contrôle est terminé au niveau du serveur de publication, mais avant qu'il soit effectué au niveau de l'Abonné, les valeurs peuvent changer. Pour vous assurer que les valeurs pour l'Abonné et le serveur de publication ne changent pas au cours de la validation d'une publication, arrêtez le service Microsoft Distributed Transaction Coordinator (MS DTC) sur le serveur de publication durant cette validation.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_publication_validation**.  
  
## <a name="see-also"></a>Voir aussi  
 [Valider des données sur l’abonné](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)   
 [sp_table_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
