---
title: ALTER FULLTEXT CATALOG (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_FULLEXT_CATALOG_TSQL
- ALTER FULLEXT CATALOG
dev_langs:
- TSQL
helpviewer_keywords:
- modifying full-text catalogs
- full-text catalogs [SQL Server], rebuilding
- accent sensitivity
- ALTER FULLTEXT CATALOG statement
- full-text catalogs [SQL Server], modifying
- full-text catalogs [SQL Server], reorganizing
ms.assetid: 31a47aaf-6c7f-48a4-a86a-d57aec66c9cb
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bd07ffa9da60ccbf38265d46a6415fe461d492f8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-fulltext-catalog-transact-sql"></a>ALTER FULLTEXT CATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifie les propriétés d'un catalogue de texte intégral.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER FULLTEXT CATALOG catalog_name   
{ REBUILD [ WITH ACCENT_SENSITIVITY = { ON | OFF } ]  
| REORGANIZE  
| AS DEFAULT   
}  
```  
  
## <a name="arguments"></a>Arguments  
 *catalog_name*  
 Spécifie le nom du catalogue à modifier. Si un catalogue avec le nom spécifié n’existe pas, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne une erreur et n’effectue pas l’opération de modification.  
  
 REBUILD  
 Indique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de reconstruire tout le catalogue. Dans ce cas, le catalogue existant est supprimé et un autre catalogue est créé à sa place. Toutes les tables qui comportent des références d'indexation de texte intégral sont associées au nouveau catalogue. La reconstruction redéfinit les métadonnées de texte intégral des tables système de la base de données.  
  
 WITH ACCENT_SENSITIVITY = {ON|OFF}  
 Indique si le catalogue à modifier respecte les accents ou non pour l'indexation et l'exécution de requêtes de texte intégral.  
  
 Pour déterminer le paramètre de propriété respect des accents en cours d’un catalogue de texte intégral, utilisez la fonction FULLTEXTCATALOGPROPERTY avec la **accentsensitivity** valeur de propriété par rapport à *catalog_name*. Si cette fonction retourne « 1 », le catalogue de texte intégral respecte les accents ; si elle retourne « 0 », il n'en tient pas compte.  
  
 Le catalogue et la base de données ont par défaut le même comportement quant au respect des accents.  
  
 REORGANIZE  
 Indique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour effectuer une *la fusion principale*, qui consiste à fusionner les plus petits index créés lors de l’indexation dans un index de grande taille. Fusionner les fragments d’index de recherche en texte intégral peut améliorer les performances et libérer des ressources disque et de mémoire. Si le catalogue de texte intégral fait l'objet de modifications fréquentes, utilisez cette commande régulièrement pour le réorganiser.  
  
 REORGANIZE optimise également les structures d'index et de catalogue internes.  
  
 N'oubliez pas que, selon la quantité de données indexées, une fusion principale peut prendre du temps. La fusion principale d'une grande quantité de données peut créer une transaction dont l'exécution est longue, ce qui retarde la troncation du journal des transactions pendant le point de contrôle. Dans ce cas, la taille du journal des transactions peut s'accroître considérablement en mode de récupération complète. Il est fortement recommandé de vous assurer que votre journal des transactions contient un espace suffisant pour une transaction dont l'exécution est longue avant de réorganiser un index de recherche en texte intégral de grande taille dans une base de données qui utilise le mode de récupération complète. Pour plus d’informations, consultez [Gérer la taille du fichier journal des transactions](../../relational-databases/logs/manage-the-size-of-the-transaction-log-file.md).  
  
 AS DEFAULT  
 Spécifie que ce catalogue est le catalogue par défaut. Lorsque des index de recherche en texte intégral sont créés sans qu'aucun catalogue n'ait été spécifié, c'est le catalogue par défaut qui est utilisé. S'il existe un catalogue de texte intégral par défaut, l'utilisation de l'argument AS DEFAULT pour ce catalogue remplace le catalogue par défaut existant.  
  
## <a name="permissions"></a>Permissions  
 Utilisateur doit avoir l’autorisation ALTER sur le catalogue de texte intégral, ou être un membre de la **db_owner**, **db_ddladmin** fixe des rôles de base de données ou rôle de serveur fixe sysadmin.  
  
> [!NOTE]  
>  Pour utiliser ALTER FULLTEXT CATALOG AS DEFAULT, l'utilisateur doit disposer de l'autorisation ALTER sur le catalogue de texte intégral et de l'autorisation CREATE FULLTEXT CATALOG sur la base de données.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant modifie la propriété `accentsensitivity` du catalogue de texte intégral par défaut `ftCatalog`, qui respecte les accents.  
  
```  
--Change to accent insensitive  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT CATALOG ftCatalog   
REBUILD WITH ACCENT_SENSITIVITY=OFF;  
GO  
-- Check Accentsensitivity  
SELECT FULLTEXTCATALOGPROPERTY('ftCatalog', 'accentsensitivity');  
GO  
--Returned 0, which means the catalog is not accent sensitive.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.fulltext_catalogs &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [CRÉER le catalogue de texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG &#40; Transact-SQL &#41;](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)   
 [Recherche en texte intégral](../../relational-databases/search/full-text-search.md)  
  
  

