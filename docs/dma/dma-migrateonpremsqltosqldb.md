---
title: Migrer SQL Server sur site vers Azure SQL Database à l’aide de l’Assistant Migration des données | Microsoft Docs
description: Découvrez comment utiliser Data Migration Assistant pour migrer un serveur local SQL Server vers Azure SQL Database
ms.custom: ''
ms.date: 07/09/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 5de33f3a78a68f0afac0ead0d42b244cc78a85ad
ms.sourcegitcommit: dcd29cd2d358bef95652db71f180d2a31ed5886b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37935836"
---
# <a name="migrate-on-premises-sql-server-to-sql-server-or-sql-server-on-azure-vms-using-the-data-migration-assistant"></a>Migrer SQL Server sur site vers SQL Server ou SQL Server sur des machines virtuelles Azure à l’aide de l’Assistant Migration des données

Data Migration Assistant fournit des évaluations transparentes de SQL Server en local et mises à niveau vers des versions ultérieures de SQL Server ou des migrations vers SQL Server sur machines virtuelles Azure ou Azure SQL Database.

Cet article fournit des instructions pas à pas pour migrer SQL Server local vers Azure SQL Database à l’aide de l’Assistant Migration des données.   

## <a name="create-a-new-migration-project"></a>Créer un nouveau projet de migration

1. Dans le volet gauche, sélectionnez **New** (+), puis sélectionnez le **Migration** type de projet.

2. Définissez le type de source sur **SQL Server** et le serveur cible type **Azure SQL Database**.

3. Sélectionnez **Créer**.

   ![Créer le projet de migration](../dma/media/NewCreate1.png)

## <a name="specify-the-source-server-and-database"></a>Spécifier le serveur source et la base de données

1. Pour la source, sous **se connecter au serveur source**, dans le **nom du serveur** texte, entrez le nom de l’instance de SQL Server source.

2. Sélectionnez le **type d’authentification** pris en charge par l’instance de SQL Server source.

   > [!NOTE]
   > Il est recommedned chiffrer la connexion en sélectionnant le **chiffrer la connexion** case à cocher sous **connexion poperties**.

    ![Sélectionnez le serveur source](../dma/media/select-source-server.png)

3. Sélectionnez **Se connecter**.

4. Sélectionnez une base de données source unique pour migrer vers la base de données SQL Azure.

   > [!NOTE]
   > Si vous souhaitez évaluer la base de données et la vue et appliquer des corrections avant la migration, sélectionnez recommandées le **évaluation de base de données avant la migration ?** case à cocher.

    ![Sélectionnez la base de données source](../dma/media/select-source-database.png)

5. Sélectionnez **Suivant**.

## <a name="specify-the-target-server-and-database"></a>Spécifiez le serveur cible et la base de données

1. Pour la cible, sous **se connecter au serveur cible**, dans le **nom du serveur** texte, entrez le nom de l’instance de base de données SQL Azure. 

2. Sélectionnez le **type d’authentification** pris en charge par l’instance de base de données SQL Azure cible.

   > [!NOTE]
   > Il est recommedned chiffrer la connexion en sélectionnant le **chiffrer la connexion** case à cocher sous **connexion poperties**.

     ![Sélectionner un serveur cible](../dma/media/select-target-server.png)

3. Sélectionnez **Se connecter**.

4. Sélectionnez une base de données cible unique auquel vous souhaitez migrer.

   > [!NOTE]
   > Si vous avez l’intention de migrer des utilisateurs de Windows, dans le **nom de domaine utilisateur externe cible** texte zone, assurez-vous que le nom de domaine utilisateur externe cible est spécifié correctement.

    ![Sélectionnez la base de données cible](../dma/media/select-target-database.png)

5. Sélectionnez **Suivant**.

## <a name="select-schema-objects"></a>Sélectionnez les objets de schéma

1.  Sélectionnez les objets de schéma à partir de la base de données source que vous souhaitez migrer vers Azure SQL Database.

    ![Sélectionnez les objets de schéma](../dma/media/select-schema-objects.png)

       > [!NOTE]
       > Certains des objets qui ne peut pas être convertis en tant que-est des opportunités de correction automatique s’affiche. Cliquez sur ces objets dans le volet gauche pour afficher les suggestions de correction dans le volet droit. Passez en revue les correctifs et choisir d’appliquer ou ignorer toutes les modifications, objet par objet. Notez qu’appliquer ou ignorer toutes les modifications pour un objet n’affecte pas les modifications apportées aux autres objets de base de données. Les instructions qui ne peut pas être converties ou corrigées automatiquement sont reproduites à la base de données cible et commentées.

    ![Correctif suggéré](../dma/media/suggested-fix.png)

2. Sélectionnez **script général SQL**.
 
3. Passez en revue le script généré.

    ![Script généré](../dma/media/generated-script.png)

## <a name="deploy-schema"></a>Déploiement du schéma

1. Sélectionnez **déployer le schéma**.

2. Passez en revue les résultats du déploiement de schéma.
 
    ![Résultats de déploiement de schéma](../dma/media/schema-deployment-results.png)

3. Sélectionnez **migrer des données** pour lancer le processus de migration de données.
 
4. Sélectionnez les tables avec les données que vous souhaitez migrer.

    ![Sélectionnez les tables à migrer](../dma/media/select-tables-to-migrate.png) 

5. Sélectionnez **démarrer la migration des données**.
 
Le dernier écran indique l’état global.

   ![État de la migration](../dma/media/migration-status.png) 

## <a name="see-also"></a>Voir aussi

- [Data Migration Assistant (DMA)](../dma/dma-overview.md)
- [Data Migration Assistant : Paramètres de Configuration](../dma/dma-configurationsettings.md)
- [Assistant de Migration de données : Meilleures pratiques](../dma/dma-bestpractices.md)
