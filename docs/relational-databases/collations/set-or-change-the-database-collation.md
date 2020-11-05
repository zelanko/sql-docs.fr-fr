---
description: Définir ou changer le classement de la base de données
title: Définir ou changer le classement de la base de données | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], database
- database collations [SQL Server]
ms.assetid: 1379605c-1242-4ac8-ab1b-e2a2b5b1f895
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9ea1926c2e54135277dd486976dda7ebe4ae6086
ms.sourcegitcommit: ea0bf89617e11afe85ad85309e0ec731ed265583
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907373"
---
# <a name="set-or-change-the-database-collation"></a>Définir ou changer le classement de la base de données
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette rubrique explique comment définir et modifier le classement de base de données à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)]. Si aucun classement n'est spécifié, celui du serveur est utilisé.  
  
> [!IMPORTANT]
> L’instruction `ALTER DATABASE COLLATE` n’est pas prise en charge dans Azure SQL Database.

 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour définir ou modifier le classement de base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Les classements Windows Unicode seulement peuvent être utilisés uniquement avec la clause COLLATE pour appliquer des classements aux types de données **nchar** , **nvarchar** et **ntext** sur les données de niveau de colonne et de niveau d’expression. Ils ne peuvent pas être utilisés avec la clause COLLATE pour modifier le classement d'une instance de serveur ou de base de données.  
  
-   Si le classement spécifié ou le classement utilisé par l'objet référencé utilise une page de codes non gérée par Windows, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] affiche une erreur.  

-   Le classement ne peut pas être modifié avec [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] une fois la base de données créée sur [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Il ne peut être modifié qu’à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
Vous trouverez les noms des classements pris en charge dans [Nom de classement Windows &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md) et [Nom du classement SQL Server &#40;Transact-SQL&#41;](../../t-sql/statements/sql-server-collation-name-transact-sql.md). Vous pouvez également utiliser la fonction système [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md) .  
  
Lorsque vous modifiez le classement d'une base de données, vous changez les éléments suivants :  
  
-   Toutes les colonnes **char** , **varchar** , **text** , **nchar** , **nvarchar** ou **ntext** présentes dans les tables système sont modifiées en fonction du nouveau classement.  
  
-   Tous les paramètres **char** , **varchar** , **text** , **nchar** , **nvarchar** ou **ntext** existants et les valeurs de retour scalaires destinés aux procédures stockées et aux fonctions définies par l’utilisateur sont modifiés en fonction du nouveau classement.  
  
-   Les types de données système **char** , **varchar** , **text** , **nchar** , **nvarchar** ou **ntext** et tous les types de données définis par l’utilisateur sur la base de ces types de données système sont modifiés en fonction du nouveau classement par défaut.  
  
Vous pouvez modifier le classement de tous les objets créés dans une base de données utilisateur à l'aide de la clause `COLLATE` de l'instruction [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md). Cette instruction **ne modifie pas** le classement des colonnes dans les tables définies par l'utilisateur existantes. Celles-ci peuvent être modifiées à l'aide de la clause `COLLATE` de l'instruction [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  

> [!IMPORTANT]
> Le changement du classement d’une base de données ou de colonnes individuelles **ne modifie pas** les données sous-jacentes déjà stockées dans les tables existantes. À moins que votre application ne gère explicitement la comparaison et la conversion des données entre les différents classements, nous vous recommandons de transférer les données existantes de la base de données vers le nouveau classement. Cette opération supprime le risque que les applications modifient incorrectement les données, ce qui peut entraîner des résultats incorrects ou une perte de données silencieuse.   

En cas de modification du classement d’une base de données, seules les nouvelles tables héritent par défaut du nouveau classement de la base de données. Il existe plusieurs alternatives pour convertir les données existantes vers le nouveau classement :
-  Convertir les données sur place. Pour convertir le classement d’une colonne dans une table existante, consultez [Définir ou changer le classement des colonnes](../../relational-databases/collations/set-or-change-the-column-collation.md). Cette opération est facile à implémenter, mais peut devenir un problème bloquant pour les grandes tables et les applications occupées. Voici un exemple qui illustre une conversion sur place de la colonne `MyString` vers un nouveau classement :

   ```sql
   ALTER TABLE dbo.MyTable
   ALTER COLUMN MyString VARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC_UTF8;
   ```

-  Copier les données dans de nouvelles tables qui utilisent le nouveau classement, puis remplacer les tables d’origine dans la même base de données. Créez, dans la base de données actuelle, une table qui héritera du classement de la base de données, copiez les données entre l’ancienne table et la nouvelle table, supprimez la table d’origine et renommez la nouvelle table d’après le nom de la table d’origine. Il s’agit d’une opération plus rapide qu’une conversion sur place, mais qui peut s’avérer difficile lors de la gestion de schémas complexes comportant des dépendances telles que des contraintes de clé étrangère, des contraintes de clé primaire et des déclencheurs. Elle nécessiterait également une synchronisation finale des données entre la table d’origine et la nouvelle table avant la suppression finale, si les données continuent d’être changées par les applications. Voici un exemple qui illustre une conversion de type « copier et remplacer » de la colonne `MyString` vers un nouveau classement :

   ```sql
   CREATE TABLE dbo.MyTable2 (MyString VARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC_UTF8); 
   
   INSERT INTO dbo.MyTable2 
   SELECT * FROM dbo.MyTable; 
   
   DROP TABLE dbo.MyTable; 
   
   EXEC sp_rename 'dbo.MyTable2', 'dbo.MyTable’;
   ```

-  Copier les données dans une nouvelle base de données qui utilise le nouveau classement et remplacer la base de données d’origine. Créez une base de données utilisant le nouveau classement, puis transférez les données de la base de données d’origine via des outils comme [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou l’Assistant Importation/exportation dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Il s’agit d’une approche plus simple pour les schémas complexes. Elle nécessiterait également une synchronisation finale des données entre la base de données d’origine et la nouvelle base de données avant la suppression finale, si les données continuent d’être changées par les applications.
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 La création d’une base de données requiert l’autorisation `CREATE DATABASE` dans la base de données **MASTER** ou bien l’autorisation `CREATE ANY DATABASE` ou `ALTER ANY DATABASE`.  
  
 La modification du classement d’une base de données existante, requiert l’autorisation `ALTER` sur la base de données.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-or-change-the-database-collation"></a>Pour définir ou modifier le classement de base de données  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], développez cette instance, puis développez **Bases de données**.  
  
2.  Si vous créez une base de données, cliquez avec le bouton droit sur **Bases de données** , puis sélectionnez **Nouvelle base de données**. Si vous ne souhaitez pas définir le classement par défaut, cliquez sur la page **Options** , puis sélectionnez un classement dans la liste déroulante **Classement** .  
  
     Sinon, si la base de données existe déjà, cliquez avec le bouton droit sur la base de données de votre choix et sélectionnez **Propriétés**. Cliquez sur la page **Options** , puis sélectionnez un classement dans la liste déroulante **Classement** .  
  
3.  Une fois que vous avez terminé, cliquez sur **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-set-the-database-collation"></a>Pour définir le classement de base de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser la clause [COLLATE](~/t-sql/statements/collations.md) pour spécifier un nom de classement. L'exemple crée la base de données `MyOptionsTest` qui utilise le classement `Latin1_General_100_CS_AS_SC` . Après avoir créé la base de données, exécutez l'instruction `SELECT` pour vérifier le paramètre.  
  
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
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser la clause [COLLATE](~/t-sql/statements/collations.md) dans une instruction [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) pour modifier le nom du classement. Exécutez l'instruction `SELECT` pour vérifier la modification.  
  
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
 [Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [Nom du classement SQL Server &#40;Transact-SQL&#41;](../../t-sql/statements/sql-server-collation-name-transact-sql.md)   
 [Nom de classement Windows &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md)   
 [COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md)   
 [Priorité de classement &#40;Transact-SQL&#41;](../../t-sql/statements/collation-precedence-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
