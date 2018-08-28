---
title: Augmenter la taille d’une base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], size
- increasing database size
- database size [SQL Server], increasing
- size [SQL Server], databases
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c3c76a8a748d9387a9f936cf4094cdcd6d8971c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43102376"
---
# <a name="increase-the-size-of-a-database"></a>Augmenter la taille d'une base de données
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
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
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'autorisation ALTER sur la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-increase-the-size-of-a-database"></a>Pour augmenter la taille d'une base de données  
  
1.  Dans **l’Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], puis développez-la.  
  
2.  Développez le dossier **Bases de données**, cliquez avec le bouton droit sur la base de données dont vous souhaitez augmenter la taille, puis cliquez sur **Propriétés**.  
  
3.  Dans **Propriétés de la base de données**, sélectionnez la page **Fichiers** .  
  
4.  Pour augmenter la taille d’un fichier existant, entrez une valeur plus grande dans la colonne **Taille initiale (Mo)** correspondant au fichier. Vous devez augmenter la taille de la base de données d'au moins 1 mégaoctet (Mo).  
  
5.  Pour augmenter la taille de la base de données en ajoutant un fichier, cliquez sur **Ajouter** et entrez les valeurs correspondant au nouveau fichier. Pour plus d’informations, consultez [Ajouter des fichiers de données ou journaux à une base de données](../../relational-databases/databases/add-data-or-log-files-to-a-database.md).  
  
6.  Cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-increase-the-size-of-a-database"></a>Pour augmenter la taille d'une base de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple augmente la taille du fichier `test1dat3`.  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../relational-databases/databases/codesnippet/tsql/increase-the-size-of-a-d_1.sql)]  
  
 Pour plus d’exemples, consultez [Options de fichiers et de groupes de fichiers ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Ajouter des fichiers de données ou journaux à une base de données](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)   
 [Réduire une base de données](../../relational-databases/databases/shrink-a-database.md)  
  
  
