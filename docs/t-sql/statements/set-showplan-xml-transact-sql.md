---
title: SET SHOWPLAN_XML (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET SHOWPLAN_XML
- SET_SHOWPLAN_XML_TSQL
dev_langs: TSQL
helpviewer_keywords:
- statements [SQL Server], estimates
- SET SHOWPLAN_XML statement
- execution information and estimates [SQL Server]
- statements [SQL Server], information without processing
- XML [SQL Server], statement execution information
- SHOWPLAN_XML option
- estimated execution information [SQL Server]
ms.assetid: a467a1b3-10a5-43c4-9085-13d8aed549c9
caps.latest.revision: "48"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bd4e6309f65bea4a71cc9e2de7d5bb5b806ab005
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="set-showplanxml-transact-sql"></a>SET SHOWPLAN_XML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Empêche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'exécuter des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. À la place, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne des informations détaillées sur le mode d'exécution des instructions, sous la forme d'un document XML correct.  
 
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET SHOWPLAN_XML { ON | OFF }  
```  
  
## <a name="remarks"></a>Notes  
 L'option SET SHOWPLAN_XML est définie lors de l'exécution, et non pas durant l'analyse.  
  
 Lorsque SET SHOWPLAN_XML ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne des informations de plan d’exécution pour chaque instruction sans toutefois l’exécuter, et [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions ne sont pas exécutées. Une fois cette option activée, des informations sur le plan d'exécution de toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes sont retournées jusqu'à sa désactivation (OFF). Par exemple, si une instruction CREATE TABLE est exécutée alors que l'option SET SHOWPLAN_XML est activée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un message d'erreur pour toute instruction SELECT ultérieure se rapportant à cette table car elle n'existe pas. Par conséquent, les prochaines références à cette table échoueront. Lorsque SET SHOWPLAN_XML a la valeur OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécute les instructions sans générer de rapport.  
  
 SET SHOWPLAN_XML est conçue pour retourner la sortie en **nvarchar (max)** pour les applications telles que la **sqlcmd** utilitaire, où la sortie XML est ensuite utilisée par d’autres outils pour afficher et traiter les informations de plan de requête.  
  
> [!NOTE]  
>  La vue de gestion dynamique **sys.dm_exec_query_plan**, retourne les mêmes informations que SET SHOWPLAN XML dans le **xml** type de données. Ces informations sont retournées à partir de la **query_plan** colonne de **sys.dm_exec_query_plan**. Pour plus d’informations, consultez [sys.dm_exec_query_plan &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md).  
  
 SET SHOWPLAN_XML ne peut pas être spécifié dans une procédure stockée. Elle doit être la seule instruction d'un traitement.  
  
 SET SHOWPLAN_XML retourne les informations sous forme d'un jeu de documents XML. Chaque traitement après l'instruction SET SHOWPLAN_XML ON est présenté dans le résultat par un document unique. Chaque document contient le texte des instructions du traitement, suivi des détails des étapes de l'exécution. Le document présente les coûts estimés, le nombre de lignes, les index accédés et les types d'opérateurs utilisés, l'ordre de jointure et d'autres informations relatives aux plans d'exécution.  
  
 Le document contenant le schéma XML pour la sortie XML provenant de SET SHOWPLAN_XML est copié pendant l'installation sur un répertoire local de l'ordinateur sur lequel Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé. Il est situé sur le lecteur contenant les fichiers d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'adresse :  
  
 \Microsoft SQL Server\130\Tools\Binn\schemas\sqlserver\2004\07\showplan\showplanxml.xsd  
  
 Le Showplan schéma également trouverez [ce site Web](http://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).  
  
> [!NOTE]  
>  Si **inclure le Plan d’exécution réel** est sélectionné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cette option SET ne produit pas de sortie du Showplan XML. Désactivez le **inclure le Plan d’exécution réel** avant d’utiliser l’option SET.  
  
## <a name="permissions"></a>Autorisations  
 Pour utiliser SET SHOWPLAN_XML, vous devez disposer des autorisations suffisantes pour exécuter les instructions sur lesquelles SET SHOWPLAN_XML est exécuté, ainsi que de l'autorisation SHOWPLAN pour toutes les bases de données contenant les objets auxquels elles font référence.  
  
 Pour SELECT, INSERT, UPDATE, DELETE, EXEC *procédure_stockée*et EXEC *user_defined_function* instructions, pour produire un plan de requête que l’utilisateur doit :  
  
-   disposer des autorisations appropriées pour exécuter les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ;  
  
-   disposer de l'autorisation SHOWPLAN sur toutes les bases de données contenant les objets auxquels les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] font référence, tels que les tables, les vues, etc.  
  
 Pour toutes les autres instructions, telles que DDL, USE *nom_base_de_données*, SET, DECLARE, dynamic SQL et ainsi de suite, seules les autorisations appropriées pour exécuter le [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions sont nécessaires.  
  
## <a name="examples"></a>Exemples  
 Les deux instructions suivantes utilisent l'option SET SHOWPLAN_XML, activée puis désactivée, pour montrer comment [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] analyse et optimise l'utilisation des index dans les requêtes.  
  
 La première requête utilise l'opérateur de comparaison Égal à (=) dans la clause WHERE sur une colonne indexée. La seconde requête utilise l'opérateur LIKE dans la clause WHERE. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit utiliser une analyse d'index cluster et rechercher les données répondant à la condition spécifiée par la clause WHERE. Les valeurs dans le **EstimateRows** et **EstimatedTotalSubtreeCost** attributs sont plus petites pour la première requête indexée, indiquant qu’il est traitée beaucoup plus rapide et utilise moins de ressources que la requête non indexée.  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_XML ON;  
GO  
-- First query.  
SELECT BusinessEntityID   
FROM HumanResources.Employee  
WHERE NationalIDNumber = '509647174';  
GO  
-- Second query.  
SELECT BusinessEntityID, JobTitle  
FROM HumanResources.Employee  
WHERE JobTitle LIKE 'Production%';  
GO  
SET SHOWPLAN_XML OFF;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
