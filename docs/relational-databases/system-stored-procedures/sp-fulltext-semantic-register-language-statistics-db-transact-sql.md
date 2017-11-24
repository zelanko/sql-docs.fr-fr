---
title: sp_fulltext_semantic_register_language_statistics_db (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_register_language_statistics_db
- sp_fulltext_semantic_register_language_statistics_db_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_fulltext_semantic_register_language_statistics_db
ms.assetid: bef1b104-5a44-4327-9ae4-45eae3000f7e
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d9b280110a6105ef136db387a2cdf64607ec9c11
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="spfulltextsemanticregisterlanguagestatisticsdb-transact-sql"></a>sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Inscrit une base de données de statistiques linguistiques de sémantique pré-remplie dans l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vous pouvez initialiser l'extraction sémantique uniquement après avoir attaché cette base de données de statistiques linguistiques et l'avoir inscrite à l'aide de cette procédure stockée. Vous ne devez effectuer cette tâche qu'une fois pour chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
EXEC sp_fulltext_semantic_register_language_statistics_db  
    [ @dbname = ] ‘database_name’;  
GO  
```  
  
##  <a name="Arguments"></a> Arguments  
 [ @dbname =] '*nom_base_de_données*'  
 Nom de la base de données de statistiques linguistiques de sémantique à inscrire pour l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La base de données doit déjà être attachée. *database_name* est **sysname**, et ne peut pas être NULL.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-set"></a>Jeu de résultats  
 Aucun.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 La base de données de statistiques linguistiques de sémantique contient des statistiques propres à une langue qui sont obligatoires pour le traitement sémantique d'un contenu textuel.  
  
 **sp_fulltext_semantic_register_language_statistics_db** effectue les étapes suivantes :  
  
1.  Vérifie que l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est une version qui prend en charge le traitement sémantique.  
  
2.  Vérifie que l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas déjà de base de données de statistiques linguistiques de sémantique définie.  
  
3.  Vérifie que la base de données est une base de données de statistiques linguistiques de sémantique valide.  
  
4.  Définit des autorisations sur la base de données de statistiques linguistiques de sémantique afin de restreindre l'accès à la base de données par les utilisateurs.  
  
5.  Insère les métadonnées qui définissent le nom de la base de données de statistiques linguistiques de sémantique pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
6.  Insère les métadonnées qui définissent les mappages entre la base de données de statistiques linguistiques de sémantique installée et les tables de modèles linguistiques internes.  
  
7.  Vérifie que la base de données est prête à être utilisée.  
  
 Pour plus d’informations, consultez [Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Métadonnées  
 Pour plus d’informations sur la base de données de statistiques linguistiques de sémantique installée sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], interrogez l’affichage catalogue [sys.fulltext_semantic_language_statistics_database &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 Nécessite l'autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre comment inscrire la base de données de statistiques linguistiques de sémantique en appelant **sp_fulltext_semantic_register_language_statistics_db**.  
  
```tsql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = 'semanticsDb';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
