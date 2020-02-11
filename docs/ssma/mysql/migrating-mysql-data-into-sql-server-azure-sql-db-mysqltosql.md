---
title: Migration de données MySQL vers SQL Server-Azure SQL DB (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Data Migration, server side data migration
- Data Migration,client side data migration
ms.assetid: a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 83a4a2d1bea5074cc268590d4074bde631f28694
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67908836"
---
# <a name="migrating-mysql-data-into-sql-server---azure-sql-db-mysqltosql"></a>Migration de données MySQL vers SQL Server-Azure SQL DB (MySQLToSQL)
Une fois que vous avez synchronisé avec succès les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertis avec ou SQL Azure, vous pouvez migrer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données de MySQL vers ou SQL Azure.  
  
> [!IMPORTANT]  
> Si le moteur utilisé est le moteur de migration des données côté serveur, avant de migrer les données, vous devez installer le pack d’extension SSMA pour MySQL et les fournisseurs MySQL sur l’ordinateur qui exécute SSMA. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service agent doit également être en cours d’exécution. Pour plus d’informations sur l’installation du pack d’extension, consultez [installation des composants SSMA sur SQL Server (MySQL to SQL)](https://msdn.microsoft.com/6772d0c5-258f-4d7b-afb0-b5f810e71af1) .  
  
## <a name="setting-migration-options"></a>Définition des options de migration  
Avant de migrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des données vers ou SQL Azure, passez en revue les options de migration de projet dans la boîte de dialogue **paramètres du projet** .  
  
-   À l’aide de cette boîte de dialogue, vous pouvez définir des options telles que la taille de lot de migration, le verrouillage de table, la vérification des contraintes, la gestion des valeurs NULL et la gestion des valeurs d’identité. Pour plus d’informations sur les paramètres de migration de projet, consultez [paramètres du projet (migration)](https://msdn.microsoft.com/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9).  
  
    Pour plus d’informations sur les **paramètres de migration de données étendues**, consultez [paramètres de migration de données](data-migration-settings-mysqltosql.md) .  
  
-   Le **moteur de migration** de la boîte de dialogue **paramètres du projet** permet à l’utilisateur d’effectuer le processus de migration à l’aide de deux types de moteurs de migration de données :  
  
    1.  Moteur de migration de données côté client  
  
    2.  Moteur de migration de données côté serveur  
  
**Migration des données côté client :**  
  
-   Pour lancer la migration des données côté client, sélectionnez l’option **moteur de migration de données côté client** dans la boîte de dialogue **paramètres du projet** .  
  
-   Dans les **paramètres du projet**, l’option moteur de migration de **données côté client** est définie.  
  
    > [!NOTE]  
    > Le **moteur de migration de données côté client** se trouve dans l’application SSMA et n’est donc pas dépendant de la disponibilité du pack d’extension.  
  
**Migration des données côté serveur :**  
  
-   Pendant la migration des données côté serveur, le moteur réside sur la base de données cible. Il est installé par le biais du pack d’extension. Pour plus d’informations sur la façon d’installer le pack d’extension, consultez [installation de composants SSMA sur SQL Server (MySQL to SQL)](https://msdn.microsoft.com/6772d0c5-258f-4d7b-afb0-b5f810e71af1) .  
  
-   Pour lancer la migration côté serveur, sélectionnez l’option **moteur de migration de données côté serveur** dans la boîte de dialogue **paramètres du projet** .  
  
> [!IMPORTANT]  
> L’option de **migration de données côté client** est disponible uniquement pour les SQL Azure.  
  
## <a name="migrating-data-to-sql-server-or-sql-azure"></a>Migration de données vers SQL Server ou SQL Azure  
La migration des données est une opération de chargement en masse qui déplace des lignes de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de tables MySQL vers ou SQL Azure des tables dans des transactions. Le nombre de lignes chargées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans dans chaque transaction est configuré dans les paramètres du projet.  
  
Pour afficher les messages de migration, assurez-vous que le volet de sortie est visible. Dans le cas contraire, dans le menu **affichage** , sélectionnez **sortie**.  
  
**Pour migrer des données**  
  
1.  Vérifiez les points suivants :  
  
    -   Les fournisseurs MySQL sont installés sur l’ordinateur qui exécute SSMA.  
  
    -   Vous avez synchronisé les objets convertis avec la base de données cible (SQL Server/SQL Azure).  
  
2.  Dans l’Explorateur de métadonnées MySQL, sélectionnez les objets qui contiennent les données que vous souhaitez migrer :  
  
    -   Pour migrer des données pour tous les schémas, activez la case à cocher en regard de **schémas**.  
  
    -   Pour migrer des données ou omettre des tables individuelles, commencez par développer le schéma, développez **tables**, puis activez ou désactivez la case à cocher en regard de la table.  
  
3.  Pour migrer des données, deux cas se produisent :  
  
    **Migration des données côté client :**  
  
    -   Pour effectuer la **migration des données côté client**, sélectionnez l’option **moteur de migration de données côté client** dans la boîte de dialogue **paramètres du projet** .  
  
    **Migration des données côté serveur :**  
  
    -   Avant d’effectuer la migration des données côté serveur, vérifiez les éléments suivants :  
  
        1.  Le pack d’extension SSMA pour MySQL est installé sur l’instance de SQL Server.  
  
        2.  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service agent est en cours d’exécution sur l’instance de SQL Server  
  
    -   Pour effectuer la **migration des données côté serveur**, sélectionnez l’option **moteur de migration de données côté serveur** dans la boîte de dialogue **paramètres du projet** .  
  
4.  Cliquez avec le bouton droit sur **schémas** dans l’Explorateur de métadonnées MySQL, puis cliquez sur **migrer les données**. Vous pouvez également migrer des données pour des objets individuels ou des catégories d’objets : cliquez avec le bouton droit sur l’objet ou son dossier parent. Sélectionnez l’option **migrer les données** .  
  
    > [!NOTE]  
    > Si le pack d’extension SSMA pour MySQL n’est pas installé sur l’instance de SQL Server et si le **moteur de migration de données côté serveur** est sélectionné, lors de la migration des données vers la base de données cible, l’erreur suivante s’est produite : «les composants de migration de données SSMA n’ont pas été trouvés sur SQL Server, la migration des données côté serveur n’est pas possible. Vérifiez si le pack d’extension est correctement installé. Cliquez sur **Annuler** pour mettre fin à la migration des données.  
  
5.  Dans la boîte de dialogue **connexion à MySQL** , entrez les informations d’identification de connexion, puis cliquez sur **se connecter**. Pour plus d’informations sur la connexion à MySQL, consultez [se connecter à mysql &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
    Si la base de données cible est SQL Server, entrez les informations d’identification de connexion dans la boîte de dialogue **se connecter à SQL Server** , puis cliquez sur **se connecter**. Pour plus d’informations sur la connexion à SQL Server, consultez [se connecter à SQL Server](https://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    Si la base de données cible est SQL Azure, entrez les informations d’identification de connexion dans la boîte de dialogue **se connecter à SQL Azure** , puis cliquez sur **se connecter**. Pour plus d’informations sur la connexion à SQL Azure, consultez [se connecter à la base de données SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-azure-sql-db-mysqltosql.md)  
  
    Les messages s’affichent dans le volet de **sortie** . Une fois la migration terminée, le **rapport de migration des données** s’affiche. Si des données n’ont pas été migrées, cliquez sur la ligne qui contient les erreurs, puis cliquez sur **Détails**. Lorsque vous avez terminé avec le rapport, cliquez sur **Fermer**. Pour plus d’informations sur le rapport de migration de données, consultez [rapport de migration des données (SSMA commun)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Lorsque SQL Express Edition est utilisé comme base de données cible, seule la migration des données côté client est autorisée et la migration des données côté serveur n’est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données MySQL vers SQL Server-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
