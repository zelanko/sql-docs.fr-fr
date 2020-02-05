---
title: Créer un schéma de base de données | Microsoft Docs
ms.custom: ''
ms.date: 07/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.schemas.general.f1
helpviewer_keywords:
- creating schemas with Management Studio
- CREATE SCHEMA [Management Studio]
- database schemas
- schemas [SQL Server], creating
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 980b179f39edc3e93e5cb0bc105b6b2f8d12bb58
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "72903746"
---
# <a name="create-a-database-schema"></a>Créer un schéma de base de données
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Cette rubrique explique comment créer un schéma dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Le nouveau schéma appartient à l'un des principaux de base de données suivants : utilisateur de base de données, rôle de base de données ou rôle d'application. Les objets créés dans un schéma appartiennent au propriétaire du schéma. La valeur **principal_id** de ces objets est NULL dans **sys.objects**. Il est possible de transférer la propriété des objets contenus dans le schéma à n'importe quel principal de base de données, mais le propriétaire du schéma conserve toujours l'autorisation CONTROL sur les objets dans le schéma.  
  
-   Quand vous créez un objet de base de données, si vous spécifiez un principal de domaine valide (utilisateur ou groupe) comme propriétaire de l'objet, le principal du domaine est ajouté à la base de données comme schéma. Le nouveau schéma appartient à ce principal de domaine.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
  
-   Nécessite l'autorisation CREATE SCHEMA sur la base de données.  
  
-   Pour spécifier un autre utilisateur comme propriétaire du schéma à créer, l'appelant doit avoir l'autorisation IMPERSONATE sur cet utilisateur. Si un rôle de base de données est spécifié comme propriétaire, l'appelant doit correspondre à l'un des critères suivants : appartenance au rôle ou autorisation ALTER pour le rôle.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
##### <a name="to-create-a-schema"></a>Pour créer un schéma  
  
1.  Dans l'Explorateur d'objets, développez le dossier **Bases de données** .  
  
2.  Développez la base de données où créer le schéma de la base de données.  
  
3.  Cliquez avec le bouton droit sur le dossier **Sécurité** , pointez sur **Nouveau**, puis sélectionnez **Schéma**.  
  
4.  Dans la boîte de dialogue **Schéma - Nouveau** , sur la page **Général** , entrez un nom pour le nouveau schéma dans la zone **Nom du schéma** .  
  
5.  Dans la zone **Propriétaire du schéma** , entrez le nom d'un utilisateur de base de données ou d'un rôle propriétaire du schéma. Vous pouvez également cliquer sur **Rechercher** pour ouvrir la boîte de dialogue **Rechercher les rôles et les utilisateurs** .  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

> [!NOTE]
> Aucune boîte de dialogue ne s’affiche si vous créez un schéma à l’aide de SSMS à partir d’**Azure SQL Database** ou d’**Azure SQL Data Warehouse**. Vous devez exécuter l’instruction T-SQL Create Schema Template qui est générée.
  
### <a name="additional-options"></a>Options supplémentaires  
 La boîte de dialogue **Schéma - Nouveau** offre également des options dans deux pages supplémentaires : **Autorisations** et **Propriétés étendues**.  
  
-   La page **Autorisations** répertorie tous les éléments sécurisables possibles et les autorisations sur les éléments sécurisables qui peuvent être accordées à la connexion.  
  
-   La page **Propriétés étendues** vous permet d'ajouter des propriétés personnalisées aux utilisateurs de base de données.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-schema"></a>Pour créer un schéma  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  L’exemple suivant crée un schéma nommé `Chains`, puis crée une table nommée `Sizes`.  
    ```sql  
    CREATE SCHEMA Chains;
    GO
    CREATE TABLE Chains.Sizes (ChainID int, width dec(10,2));
    ```

4.  Des options supplémentaires peuvent être effectuées dans une seule instruction. L’exemple suivant crée le schéma `Sprockets` détenu par Annick qui contient la table `NineProngs`. L’instruction accorde `SELECT` à Mandar et refuse `SELECT` à Prasanna.  

    ```sql  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
5. Exécutez l’instruction suivante pour consulter les schémas de cette base de données :

   ```sql
   SELECT * FROM sys.schemas;
   ```

 Pour plus d’informations, consultez [CREATE SCHEMA &#40;Transact-SQL&#41;](../../../t-sql/statements/create-schema-transact-sql.md).  
  
  
