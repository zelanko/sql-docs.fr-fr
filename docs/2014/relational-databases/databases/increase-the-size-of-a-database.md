---
title: Augmenter la taille d’une base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], size
- increasing database size
- database size [SQL Server], increasing
- size [SQL Server], databases
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 02a34ba1e0f441b665c239d60f6398afa4247102
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62917233"
---
# <a name="increase-the-size-of-a-database"></a>Augmenter la taille d'une base de données
  Cette rubrique explique comment augmenter la taille d'une base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Cette base de données peut être étendue de deux manières : en augmentant la taille d'un fichier de données ou d'un fichier journal existant ou en ajoutant un fichier à la base de données.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour augmenter la taille d'une base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Vous ne pouvez pas ajouter ou supprimer de fichier tant qu'une instruction BACKUP est en cours d'exécution.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'autorisation ALTER sur la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-increase-the-size-of-a-database"></a>Pour augmenter la taille d'une base de données  
  
1.  Dans **l’Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], puis développez-la.  
  
2.  Développez le dossier **Bases de données**, cliquez avec le bouton droit sur la base de données dont vous souhaitez augmenter la taille, puis cliquez sur **Propriétés**.  
  
3.  Dans **Propriétés de la base de données**, sélectionnez la page **Fichiers** .  
  
4.  Pour augmenter la taille d’un fichier existant, entrez une valeur plus grande dans la colonne **Taille initiale (Mo)** correspondant au fichier. Vous devez augmenter la taille de la base de données d'au moins 1 mégaoctet (Mo).  
  
5.  Pour augmenter la taille de la base de données en ajoutant un fichier, cliquez sur **Ajouter** et entrez les valeurs correspondant au nouveau fichier. Pour plus d’informations, consultez [Ajouter des fichiers de données ou journaux à une base de données](add-data-or-log-files-to-a-database.md).  
  
6.  Cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-increase-the-size-of-a-database"></a>Pour augmenter la taille d'une base de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple augmente la taille du fichier `test1dat3`.  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase5)]  
  
 Pour plus d’exemples, consultez [Options de fichiers et de groupes de fichiers ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des fichiers de données ou journaux à une base de données](add-data-or-log-files-to-a-database.md)   
 [Réduire une base de données](shrink-a-database.md)  
  
  
