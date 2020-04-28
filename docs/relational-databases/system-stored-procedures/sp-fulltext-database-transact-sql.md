---
title: sp_fulltext_database (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_database_TSQL
- sp_fulltext_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_database
ms.assetid: eeb1e151-eb00-484c-8fd1-5641e621ffc6
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0c27f2efcfc15cc1ff9d53f735c08fad922f9466
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68124276"
---
# <a name="sp_fulltext_database-transact-sql"></a>sp_fulltext_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  N'a aucun effet sur les catalogues de texte intégral dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures et est pris en charge uniquement à des fins de compatibilité descendante. **sp_fulltext_database** ne désactive pas le moteur de recherche en texte intégral pour une base de données donnée. Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], toutes les bases de données créées par les utilisateurs sont toujours activées pour l'indexation de texte intégral.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] à la place.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_fulltext_database [@action=] 'action'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @action = ] 'action'`Action à exécuter. **action** est de type **varchar (20)** et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**rendre**|Pris en charge pour la compatibilité descendante uniquement. N'a aucun effet sur les catalogues de texte intégral dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et versions ultérieures.|  
|**désactive**|Pris en charge pour la compatibilité descendante uniquement. N'a aucun effet sur les catalogues de texte intégral dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et versions ultérieures.|  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et versions ultérieures, l'indexation de texte intégral ne peut pas être désactivée. La désactivation de l’indexation de texte intégral ne supprime pas les lignes de **sysfulltextcatalogs** et n’indique pas que les tables activées pour la recherche en texte intégral ne sont plus marquées pour l’indexation de texte intégral. Toutes les définitions de métadonnées de texte intégral restent dans les tables système.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** et **db_owner** rôle de base de données fixe peuvent exécuter **sp_fulltext_database**.  
  
## <a name="see-also"></a>Voir aussi  
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
