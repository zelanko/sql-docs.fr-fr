---
title: Migrer de données Sybase ASE dans SQL Server - base de données SQL Azure | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Migrating data,Client Side Data Migration
- Migrating data,Server Side Data Migration
ms.assetid: 54a39f5e-9250-4387-a3ae-eae47c799811
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e39d74143e21d6b75a5a35a1f8dbde4f62f285f4
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392777"
---
# <a name="migrating-sybase-ase-data-into-sql-server---azure-sql-db--sybasetosql"></a>Migration de données ASE Sybase vers SQL Server - Azure SQL DB (SybaseToSQL)
Une fois que vous avez correctement chargé les objets de base de données Sybase Adaptive Server Enterprise (ASE) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de la base de données SQL Azure, vous pouvez migrer des données à partir de l’ASE à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.  
  
> [!IMPORTANT]  
> Si le moteur utilisé est le moteur de Migration de données côté serveur, puis avant de migrer des données, vous devez installer SSMA pour Sybase ASE Extension Pack et les fournisseurs de Sybase ASE sur l’ordinateur qui est en cours d’exécution SSMA. Le service SQL Server Agent doit également être en cours d’exécution. Pour plus d’informations sur la façon d’installer le pack d’extension, consultez [installation des composants SSMA sur SQL Server (SybaseToSQL)](http://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
## <a name="setting-migration-options"></a>Définition des Options de Migration  
Avant de migrer des données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Azure SQL DB, passez en revue les options de migration de projet dans le **paramètres du projet** boîte de dialogue.  
  
-   À l’aide de cette boîte de dialogue vous pouvez définir des options telles que la taille de lot de migration, verrouillage de table, la vérification des contraintes, gestion des valeurs null et la gestion de valeur d’identité. Pour plus d’informations sur les paramètres de Migration de projet, consultez [paramètres du projet (Migration) (Sybase)](http://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924).  
  
    Pour plus d’informations sur **paramètres de Migration de données étendus**, consultez [les paramètres de Migration de données](data-migration-settings-sybasetosql.md)  
  
-   Le **moteur de Migration** dans le **paramètres du projet** boîte de dialogue permet à l’utilisateur effectuer le processus de migration à l’aide de deux types de moteurs de migration de données, reportages. :  
  
    1.  Moteur de Migration de données côté client  
  
    2.  Moteur de Migration de données côté serveur  
  
**Migration des données côté client :**  
  
-   Pour lancer la migration des données côté client, sélectionnez l’option **moteur de Migration de données côté Client** dans le **paramètres du projet** boîte de dialogue.  
  
-   Dans **paramètres du projet**, le **moteur de Migration de données côté Client** option a la valeur par défaut.  
  
    > [!NOTE]  
    > Le moteur de Migration de données côté Client se trouve à l’intérieur de l’application de SSMA et, par conséquent, n’est pas dépendant de la disponibilité du pack d’extension.  
  
**Migration des données côté serveur :**  
  
-   Pendant la migration de données côté serveur, le moteur se trouve sur la base de données cible. Il est installé par le pack d’extension. Pour plus d’informations sur la façon d’installer le pack d’extension, consultez [installation des composants SSMA sur SQL Server (SybaseToSQL)](http://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
-   Pour lancer une migration sur le côté serveur, sélectionnez le **moteur de Migration de données côté serveur** option dans le **paramètres du projet** boîte de dialogue.  
  
> [!NOTE]  
> Quand Azure SQL DB est utilisée comme base de données cible, uniquement **migration des données côté Client** est autorisée et la migration des données côté serveur n’est pas pris en charge.  
  
## <a name="migrating-data-to-sql-server-or-azure-sql-db"></a>Migration de données vers SQL Server ou de la base de données SQL Azure  
Migration de données sont une opération de chargement en masse qui déplace les lignes de données à partir des tables ASE dans des tables SQL Server dans des transactions. Le nombre de lignes chargées dans SQL Server ou de la base de données SQL Azure dans chaque transaction est configuré dans les paramètres du projet.  
  
Pour afficher les messages de la migration, assurez-vous que le volet de sortie est visible. Sinon, sélectionnez **sortie** à partir de la **vue** menu.  
  
**Pour migrer des données**  
  
1.  Vérifiez les éléments suivants :  
  
    -   Les fournisseurs ASE sont installés sur l’ordinateur qui est en cours d’exécution SSMA.  
  
    -   Vous avez synchronisé les objets convertis avec la base de données cible (SQL Server ou la base de données SQL Azure).  
  
2.  Dans l’Explorateur de métadonnées de Sybase, sélectionnez les objets qui contiennent les données que vous souhaitez migrer :  
  
    -   Pour migrer des données pour tous les schémas, sélectionnez la case à cocher à côté **schémas**.  
  
    -   Pour migrer des données, ou omettre des tables individuelles, tout d’abord développer le schéma, développez **Tables**, puis sélectionnez ou désactivez la case à cocher en regard du tableau.  
  
3.  Pour migrer des données, deux arriver :  
  
    **Migration des données côté client :**  
  
    Pour effectuer des **Migration des données côté Client**, sélectionnez le **moteur de Migration de données côté Client** option dans le **paramètres du projet** boîte de dialogue.  
  
    **Migration des données côté serveur :**  
  
    -   Avant d’effectuer la migration des données côté serveur, vérifiez :  
  
        1.  SSMA pour Sybase Extension Pack est installé sur l’instance de SQL Server.  
  
        2.  Le service SQL Server Agent est en cours d’exécution sur l’instance de SQL Server  
  
    -   Pour effectuer des **Migration des données côté serveur**, sélectionnez le **moteur de Migration de données côté serveur** option dans le **paramètres du projet** boîte de dialogue.  
  
4.  Avec le bouton droit **schémas** dans l’Explorateur de métadonnées de Sybase, puis cliquez sur **migrer des données**. Vous pouvez également migrer des données pour des objets individuels ou des catégories d’objets : cliquez sur l’objet ou son dossier parent, puis sélectionnez le **migrer des données** option.  
  
    > [!NOTE]  
    > Si l’Assistant SSMA pour Sybase Extension Pack n’est pas installé sur l’instance de SQL Server et si **moteur de Migration de données côté serveur** est sélectionnée, puis lors de la migration des données à la base de données cible, l’erreur suivante survient : « SSMA Composants de Migration de données sont introuvables sur SQL Server, migration de données côté serveur ne sera pas possible. Vérifiez si le Pack d’Extension est correctement installé ». Cliquez sur **Annuler** pour mettre fin à la migration des données.  
  
5.  Dans le **se connecter à Sybase ASE** boîte de dialogue, entrez les informations d’identification de connexion, puis cliquez sur **Connect**. Pour plus d’informations sur la connexion à Sybase ASE, consultez [se connecter à Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md)  
  
    Si la base de données cible est SQL Server, puis, entrez les informations d’identification de connexion dans le **se connecter à SQL Server** boîte de dialogue, puis cliquez sur **Connect**. Pour plus d’informations sur la connexion à SQL Server, consultez [connexion à SQL Server(SybaseToSQL)](http://msdn.microsoft.com/dd368a1a-45b0-40e9-b4d3-5cdb48c26606)  
  
    Si la base de données cible est la base de données SQL Azure, puis entrez les informations d’identification de connexion dans le **se connecter à la base de données SQL Azure** boîte de dialogue, puis cliquez sur **Connect**. Pour plus d’informations sur la connexion à la base de données SQL Azure, consultez [connexion à Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
    Messages seront affichés dans le **sortie** volet. Une fois la migration terminée, le **rapport de Migration de données** s’affiche. Si aucune donnée n’a pas été migré, cliquez sur la ligne qui contient les erreurs, puis cliquez sur **détails**. Lorsque vous avez terminé avec le rapport, cliquez sur **fermer**. Pour plus d’informations sur le rapport de Migration de données, consultez [rapport de Migration de données (SSMA courant)](http://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Lors de l’édition de SQL Express est utilisée en tant que la base de données cible, uniquement les migration de données côté client est autorisée et la migration des données côté serveur n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
[Migration des bases de données de Sybase ASE pour SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
