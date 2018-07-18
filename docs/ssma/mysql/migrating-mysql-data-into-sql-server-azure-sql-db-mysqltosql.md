---
title: Migration de données MySQL vers SQL Server - Azure SQL DB (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Data Migration, server side data migration
- Data Migration,client side data migration
ms.assetid: a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82
caps.latest.revision: 24
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6143733af6824518b8a54ed856844c5e01702d0a
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985211"
---
# <a name="migrating-mysql-data-into-sql-server---azure-sql-db-mysqltosql"></a>Migration de données MySQL vers SQL Server - Azure SQL DB (MySQLToSQL)
Après avoir synchronisé correctement les objets convertis avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure, vous pouvez migrer les données de MySQL vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure.  
  
> [!IMPORTANT]  
> Si le moteur utilisé est le moteur de Migration de données des côté serveur, puis, avant de migrer les données, vous devez installer SSMA pour MySQL Extension Pack et les fournisseurs de MySQL sur l’ordinateur qui est en cours d’exécution SSMA. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent service doit également être exécuté. Pour plus d’informations sur la façon d’installer le pack d’extension, consultez [installation des composants SSMA sur SQL Server (MySQL to SQL)](http://msdn.microsoft.com/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
## <a name="setting-migration-options"></a>Définition des Options de Migration  
Avant de migrer les données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure, passez en revue les options de migration de projet dans le **paramètres du projet** boîte de dialogue.  
  
-   À l’aide de cette boîte de dialogue vous pouvez définir des options telles que la taille de lot de migration, verrouillage de table, la vérification des contraintes, gestion des valeurs null et la valeur-gestion d’identités. Pour plus d’informations sur les paramètres de Migration de projet, consultez [paramètres du projet (Migration)](http://msdn.microsoft.com/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9).  
  
    Pour plus d’informations sur **paramètres de Migration de données étendus**, consultez [les paramètres de Migration de données](http://msdn.microsoft.com/9c396df4-5676-4f32-9c57-70d4f15f9b7a)  
  
-   Le **moteur de Migration** dans le **paramètres du projet** boîte de dialogue permet à l’utilisateur effectuer le processus de migration à l’aide de deux types de moteurs de migration de données :  
  
    1.  Moteur de Migration de données côté client  
  
    2.  Moteur de Migration de données côté serveur  
  
**Migration des données côté client :**  
  
-   Pour lancer la migration des données côté client, sélectionnez le **moteur de Migration de données côté Client** option dans le **paramètres du projet** boîte de dialogue.  
  
-   Dans **paramètres du projet**, le **moteur de Migration de données côté Client** option est définie.  
  
    > [!NOTE]  
    > Le **moteur de Migration de données côté Client** réside à l’intérieur de l’application de SSMA et n’est, par conséquent, ne dépend pas la disponibilité du pack d’extension.  
  
**Migration des données côté serveur :**  
  
-   Pendant la migration des données côté serveur, le moteur se trouve sur la base de données cible. Il est installé par le pack d’extension. Pour plus d’informations sur la façon d’installer le pack d’extension, consultez [installation des composants SSMA sur SQL Server (MySQL to SQL)](http://msdn.microsoft.com/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
-   Pour lancer une migration sur le côté serveur, sélectionnez le **moteur de Migration de données côté serveur** option dans le **paramètres du projet** boîte de dialogue.  
  
> [!IMPORTANT]  
> **Migration des données côté client** option est uniquement disponible pour SQL Azure.  
  
## <a name="migrating-data-to-sql-server-or-sql-azure"></a>Migration de données vers SQL Server ou SQL Azure  
Migration de données sont une opération de chargement en masse qui déplace les lignes de données à partir des tables de MySQL dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou des tables SQL Azure dans des transactions. Le nombre de lignes chargées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dans chaque transaction est configuré dans les paramètres du projet.  
  
Pour afficher les messages de la migration, assurez-vous que le volet de sortie est visible. Sinon, à partir de la **vue** menu, sélectionnez **sortie**.  
  
**Pour migrer des données**  
  
1.  Vérifiez les éléments suivants :  
  
    -   Les fournisseurs de MySQL sont installés sur l’ordinateur qui est en cours d’exécution SSMA.  
  
    -   Vous avez synchronisé les objets convertis avec la base de données cible (SQL Server / SQL Azure).  
  
2.  Dans l’Explorateur de métadonnées de MySQL, sélectionnez les objets qui contiennent les données que vous souhaitez migrer :  
  
    -   Pour migrer des données pour tous les schémas, sélectionnez la case à cocher à côté **schémas**.  
  
    -   Pour migrer des données, ou omettre des tables individuelles, tout d’abord développer le schéma, développez **Tables**, puis sélectionnez ou désactivez la case à cocher en regard du tableau.  
  
3.  Pour migrer des données, deux arriver :  
  
    **Migration des données côté client :**  
  
    -   Pour effectuer des **Migration des données côté Client**, sélectionnez le **moteur de Migration de données côté Client** option dans le **paramètres du projet** boîte de dialogue.  
  
    **Migration des données côté serveur :**  
  
    -   Avant d’effectuer la migration des données côté serveur, vérifiez :  
  
        1.  SSMA pour MySQL Extension Pack est installé sur l’instance de SQL Server.  
  
        2.  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] service de l’Agent est en cours d’exécution sur l’instance de SQL Server  
  
    -   Pour effectuer des **Migration des données côté serveur**, sélectionnez le **moteur de Migration de données côté serveur** option dans le **paramètres du projet** boîte de dialogue.  
  
4.  Avec le bouton droit **schémas** dans l’Explorateur de métadonnées de MySQL, puis cliquez sur **migrer des données**. Vous pouvez également migrer des données pour des objets individuels ou des catégories d’objets : avec le bouton droit de l’objet ou son dossier parent ; Sélectionnez le **migrer des données** option.  
  
    > [!NOTE]  
    > Si l’Assistant SSMA pour le Pack d’Extension MySQL n’est pas installé sur l’instance de SQL Server et si **moteur de Migration de données côté serveur** est sélectionnée, puis lors de la migration des données à la base de données cible, l’erreur suivante survient : « SSMA Composants de Migration de données sont introuvables sur SQL Server, migration de données côté serveur ne sera pas possible. Vérifiez si le Pack d’Extension est correctement installé ». Cliquez sur **Annuler** pour mettre fin à la migration des données.  
  
5.  Dans le **se connecter à MySQL** boîte de dialogue, entrez les informations d’identification de connexion, puis cliquez sur **Connect**. Pour plus d’informations sur la connexion à MySQL, consultez [se connecter à MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
    Si la base de données cible est SQL Server, puis, entrez les informations d’identification de connexion dans le **se connecter à SQL Server** boîte de dialogue, puis cliquez sur **Connect**. Pour plus d’informations sur la connexion à SQL Server, consultez [se connecter à SQL Server](http://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    Si la base de données cible est SQL Azure, puis entrez les informations d’identification de connexion dans le **se connecter à SQL Azure** boîte de dialogue, puis cliquez sur **Connect**. Pour plus d’informations sur la connexion à SQL Azure, consultez [se connecter à la base de données SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-azure-sql-db-mysqltosql.md)  
  
    Messages seront affichés dans le **sortie** volet. Une fois la migration terminée, le **rapport de Migration de données** s’affiche. Si aucune donnée n’a pas été migré, cliquez sur la ligne qui contient les erreurs, puis cliquez sur **détails**. Lorsque vous avez terminé avec le rapport, cliquez sur **fermer**. Pour plus d’informations sur le rapport de Migration de données, consultez [rapport de Migration de données (SSMA courant)](http://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Lors de l’édition de SQL Express est utilisée en tant que la base de données cible, uniquement les migration de données côté client est autorisée et la migration des données côté serveur n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration de MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
