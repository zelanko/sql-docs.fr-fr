---
title: "Cr&#233;er une base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bases de données [SQL Server], création"
  - "création de base de données [SQL Server], SQL Server Management Studio"
  - "création de bases de données"
ms.assetid: 4c4beea2-6cbc-4352-9db6-49ea8130bb64
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Cr&#233;er une base de donn&#233;es
  Cette rubrique explique comment créer une base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Conditions préalables](#Prerequisites)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour créer une base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Vous pouvez spécifier un maximum de 32 767 bases de données sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
###  <a name="Prerequisites"></a> Configuration requise  
  
-   L'instruction CREATE DATABASE doit être exécutée en mode de validation automatique (mode de gestion des transactions par défaut) et n'est pas autorisée dans une transaction explicite ou implicite.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   La base de données [master](../../relational-databases/databases/master-database.md) doit être sauvegardée chaque fois qu'une base de données utilisateur est créée, modifiée ou supprimée.  
  
-   Lorsque vous créez une base de données, attribuez aux fichiers une taille aussi grande que possible, en tenant compte du volume maximal de données qu'est censée contenir la base de données.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'autorisation CREATE DATABASE sur la base de données master, ou l'autorisation ALTER ANY DATABASE ou VIEW ANY DEFINITION.  
  
 Pour garder le contrôle de l'utilisation du disque sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'autorisation de création de bases de données est généralement limitée à quelques comptes de connexion.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour créer une base de données  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et développez-la.  
  
2.  Cliquez avec le bouton droit sur **Bases de données**, puis cliquez sur **Nouvelle base de données**.  
  
3.  Dans **Nouvelle base de données**, entrez le nom de la base de données.  
  
4.  Pour créer la base de données en acceptant toutes les valeurs par défaut, cliquez sur **OK**, sinon effectuez les étapes facultatives ci-après.  
  
5.  Pour modifier le nom du propriétaire, cliquez sur (**…**) pour sélectionner un autre propriétaire.  
  
    > [!NOTE]  
    >  L’option **Utiliser l’indexation de texte intégral** est toujours activée et estompée, car toutes les bases de données utilisateur sont activées pour la recherche en texte intégral à compter de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
6.  Pour modifier les valeurs par défaut des données primaires et des fichiers journaux de transactions, dans la grille **Fichiers de la base de données** , cliquez sur la cellule appropriée, puis entrez la nouvelle valeur. Pour plus d’informations, consultez [Add Data or Log Files to a Database](../../relational-databases/databases/add-data-or-log-files-to-a-database.md).  
  
7.  Pour modifier le classement de la base de données, sélectionnez la page **Options** , puis sélectionnez un classement dans la liste.  
  
8.  Pour modifier le mode de récupération, sélectionnez la page **Options** , puis sélectionnez un mode de récupération dans la liste.  
  
9. Pour modifier les options de la base de données, sélectionnez la page **Options** , puis apportez les modifications de votre choix. Pour obtenir une description de chaque option, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).  
  
10. Pour ajouter un nouveau groupe de fichiers, cliquez sur la page **Groupes de fichiers** . Cliquez sur **Ajouter** , puis entrez les valeurs du groupe de fichiers.  
  
11. Pour ajouter une propriété étendue à la base de données, sélectionnez la page **Propriétés étendues** .  
  
    1.  Dans la colonne **Nom** , entrez le nom de la propriété étendue.  
  
    2.  Dans la colonne **Valeur** , entrez le texte de la propriété étendue. Par exemple, vous pouvez entrer une description de la base de données.  
  
12. Pour créer la base de données, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour créer une base de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple crée la base de données `Sales`. Le mot clé PRIMARY n'étant pas utilisé, le premier fichier (`Sales`_`dat`) devient le fichier principal. Le paramètre SIZE n'étant spécifié ni en Mo ni en Ko pour le fichier `Sales`\_`dat` , la valeur par défaut est Mo et il est alloué en mégaoctets. La base de données `Sales`\_`log` est alloué en mégaoctets car le suffixe `MB` est défini explicitement dans le paramètre `SIZE` .  
  
```tsql  
USE master ;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
 Pour obtenir plus d’exemples, consultez [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## Voir aussi  
 [Groupes de fichiers et fichiers de base de données](../../relational-databases/databases/database-files-and-filegroups.md)   
 [Attacher et détacher une base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Ajouter des fichiers de données ou journaux à une base de données](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)  
  
  