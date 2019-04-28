---
title: sp_changemergefilter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergefilter_TSQL
- sp_changemergefilter
helpviewer_keywords:
- sp_changemergefilter
ms.assetid: e08fdfdd-d242-4e85-817b-9f7a224fe567
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 32facb58645e0fbb3750ca02da0d3a22b320fc67
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997043"
---
# <a name="spchangemergefilter-transact-sql"></a>sp_changemergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie certaines propriétés du filtre de fusion. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changemergefilter [ @publication= ] 'publication'  
        , [ @article= ] 'article'  
        , [ @filtername= ] 'filtername'  
        , [ @property= ] 'property'  
        , [ @value= ] 'value'  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'` Est le nom de l’article. *article* est **sysname**, sans valeur par défaut.  
  
`[ @filtername = ] 'filtername'` Est le nom actuel du filtre. *FilterName* est **sysname**, sans valeur par défaut.  
  
`[ @property = ] 'property'` Est le nom de la propriété à modifier. *propriété* est **sysname**, sans valeur par défaut.  
  
`[ @value = ] 'value'` Est la nouvelle valeur pour la propriété spécifiée. *valeur*est **nvarchar (1000)**, sans valeur par défaut.  
  
 Le tableau ci-dessous décrit les propriétés des articles et les valeurs de ces propriétés.  
  
|Propriété|Value|Description|  
|--------------|-----------|-----------------|  
|**filter_type**|**1**|Filtre de jointure.<br /><br /> Cette option est nécessaire pour la prise en charge d'Abonnés [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
||**2**|Relation d'enregistrement logique.|  
||**3**|Un filtre de jointure est également une relation d'enregistrement logique.|  
|**filtername**||Nom du filtre.|  
|**join_articlename**||Nom de l'article de jointure.|  
|**join_filterclause**||Clause Filtre.|  
|**join_unique_key**|**true**|La jointure se fait sur une clé unique.|  
||**false**|La jointure ne se fait pas sur une clé unique.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Confirme que l’action entreprise par cette procédure stockée peut invalider un instantané existant. *àce_invalidate_snapshot* est un **bits**, avec une valeur par défaut **0**.  
  
 **0** Spécifie que les modifications apportées à l’article de fusion n’invalident pas l’instantané n’est pas valide. Si la procédure stockée détecte que la modification requiert un nouvel instantané, une erreur se produit et aucune modification n'est effectuée.  
  
 **1** signifie que les modifications apportées à l’article de fusion peuvent invalider l’instantané n’est pas valide, et s’il existe des abonnements existants qui nécessitent un nouvel instantané, autorise l’instantané existant soit marqué comme obsolète et de générer un nouvel instantané.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Confirme que l’action entreprise par cette procédure stockée peut nécessiter la réinitialisation des abonnements existants. *àce_reinit_subscription* est un **bits** avec une valeur par défaut **0**.  
  
 **0** Spécifie que les modifications apportées à l’article de fusion ne provoquent pas la réinitialisation de l’abonnement. Si la procédure stockée détecte que la modification nécessite la réinitialisation des abonnements existants, une erreur se produit et aucune modification n'est effectuée.  
  
 **1** signifie que les modifications à l’article de fusion entraîne la réinitialisation des abonnements existants et autorise la réinitialisation des abonnements se produise.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changemergefilter** est utilisé dans la réplication de fusion.  
  
 La modification d'un filtre sur un article de fusion nécessite de recréer l'instantané, s'il existe. Cette opération est effectuée en définissant le **@force_invalidate_snapshot** à **1**. De même, s'il existe des abonnements à cet article, les abonnements doivent être réinitialisés. Cela est effectué en définissant le **@force_reinit_subscription** à **1**.  
  
 Pour utiliser des enregistrements logiques, la publication et les articles doivent répondre à certaines conditions. Pour plus d’informations, consultez [Regrouper les modifications apportées à des lignes connexes à l’aide d’enregistrements logiques](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_changemergefilter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Changer les propriétés des publications et des articles](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
