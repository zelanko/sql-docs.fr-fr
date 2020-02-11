---
title: Définir ou changer le classement de la base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], database
- database collations [SQL Server]
ms.assetid: 1379605c-1242-4ac8-ab1b-e2a2b5b1f895
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 38c29f8d70b3cc72baf81e2ae23082fe270ba573
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62874026"
---
# <a name="set-or-change-the-database-collation"></a>Définir ou changer le classement de la base de données
  Cette rubrique explique comment définir et modifier le classement de base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Si aucun classement n'est spécifié, celui du serveur est utilisé.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour définir ou modifier le classement de base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les classements Windows Unicode seulement peuvent être utilisés uniquement avec la clause COLLATE afin d'appliquer des classements aux types de données `nchar`, `nvarchar` et `ntext` sur les données de niveau de colonne et de niveau d'expression. Ils ne peuvent pas être utilisés avec la clause COLLATE pour modifier le classement d'une instance de serveur ou de base de données.  
  
-   Si le classement spécifié ou le classement utilisé par l'objet référencé utilise une page de codes non gérée par Windows, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] affiche une erreur.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Vous trouverez les noms des classements pris en charge dans [Nom de classement Windows &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) et [Nom du classement SQL Server &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql). Vous pouvez également utiliser la fonction système [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) .  
  
-   Lorsque vous modifiez le classement d'une base de données, vous changez les éléments suivants :  
  
    -   Toutes les colonnes `char`, `varchar`, `text`, `nchar`, `nvarchar` ou `ntext` présentes dans les tables système sont modifiées en fonction du nouveau classement.  
  
    -   Tous les paramètres `char`, `varchar`, `text`, `nchar`, `nvarchar`, ou `ntext` existants et les valeurs de retour scalaires destinés aux procédures stockées et aux fonctions définies par l'utilisateur sont modifiés en fonction du nouveau classement.  
  
    -   Les types de données système `char`, `varchar`, `text`, `nchar`, `nvarchar`, ou `ntext` et tous les types de données définis par l'utilisateur sur la base de ces types de données système sont modifiés en fonction du nouveau classement par défaut.  
  
-   Vous pouvez modifier le classement de tous les objets créés dans une base de données utilisateur à l'aide de la clause COLLATE de l'instruction [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) . Cette instruction ne modifie pas le classement des colonnes dans les tables définies par l'utilisateur existantes. Celles-ci peuvent être modifiées à l'aide de la clause COLLECT de l'instruction [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 CREATE DATABASE  
 Nécessite l’autorisation CREATE DATABASE sur la base de données **master** , ou l’autorisation ALTER ANY DATABASE ou VIEW ANY DEFINITION.  
  
 ALTER DATABASE  
 Nécessite l'autorisation ALTER sur la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-or-change-the-database-collation"></a>Pour définir ou modifier le classement de base de données  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], développez cette instance, puis développez **Bases de données**.  
  
2.  Si vous créez une base de données, cliquez avec le bouton droit sur **Bases de données** , puis sélectionnez **Nouvelle base de données**. Si vous ne souhaitez pas définir le classement par défaut, cliquez sur la page **Options** , puis sélectionnez un classement dans la liste déroulante **Classement** .  
  
     Sinon, si la base de données existe déjà, cliquez avec le bouton droit sur la base de données de votre choix et sélectionnez **Propriétés**. Cliquez sur la page **Options** , puis sélectionnez un classement dans la liste déroulante **Classement** .  
  
3.  Une fois que vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-set-the-database-collation"></a>Pour définir le classement de base de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser la clause [COLLATE](/sql/t-sql/statements/collations) pour spécifier un nom de classement. L'exemple crée la base de données `MyOptionsTest` qui utilise le classement `Latin1_General_100_CS_AS_SC` . Après avoir créé la base de données, exécutez l'instruction `SELECT` pour vérifier le paramètre.  
  
```sql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE Latin1_General_100_CS_AS_SC;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
#### <a name="to-change-the-database-collation"></a>Pour modifier le classement de la base de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser la clause [COLLATE](/sql/t-sql/statements/collations) dans une instruction [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) pour modifier le nom du classement. Exécutez l'instruction `SELECT` pour vérifier la modification.  
  
```sql  
USE master;  
GO  
ALTER DATABASE MyOptionsTest  
COLLATE French_CI_AS ;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge d'Unicode et du classement](collation-and-unicode-support.md)   
 [sys. fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql)   
 [sys. databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [Nom du classement SQL Server &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)   
 [Nom de classement Windows &#40;&#41;Transact-SQL](/sql/t-sql/statements/windows-collation-name-transact-sql)   
 [COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations)   
 [Priorité de classement &#40;&#41;Transact-SQL](/sql/t-sql/statements/collation-precedence-transact-sql)   
 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
