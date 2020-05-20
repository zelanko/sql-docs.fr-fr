---
title: Mettre à niveau SQL Server à l’aide de la Assistant Migration de données
description: Découvrez comment utiliser Assistant Migration de données pour mettre à niveau un SQL Server local vers une version ultérieure de SQL Server ou pour SQL Server sur des machines virtuelles Azure
ms.custom: seo-lt-2019
ms.date: 05/18/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
author: rajeshsetlem
ms.author: rajpo
ms.openlocfilehash: 00d27decc533d33056a7cc0cb19c2584fea564fb
ms.sourcegitcommit: fb1430aedbb91b55b92f07934e9b9bdfbbd2b0c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82885867"
---
# <a name="upgrade-sql-server-using-the-data-migration-assistant"></a>Mettre à niveau SQL Server à l’aide de la Assistant Migration de données

Le Assistant Migration de données fournit des évaluations transcohérentes de SQL Server locales et des mises à niveau vers des versions ultérieures de SQL Server ou des migrations vers SQL Server sur des machines virtuelles Azure ou des Azure SQL Database.

Cet article fournit des instructions pas à pas pour la mise à niveau de SQL Server local vers des versions ultérieures de SQL Server ou vers des SQL Server sur des machines virtuelles Azure à l’aide de la Assistant Migration de données.

## <a name="create-a-new-migration-project"></a>Créer un nouveau projet de migration

1. Dans le volet gauche, sélectionnez **nouveau** (+), puis le type projet de **migration** .

2. Définissez le type de serveur source et cible sur **SQL Server** si vous effectuez une mise à niveau d’une SQL Server locale vers une version ultérieure du SQL Server local.

3. Sélectionnez **Create** (Créer).

   ![Créer un projet de migration](../dma/media/NewCreate.png)

## <a name="specify-the-source-and-target"></a>Spécifier la source et la cible

1. Pour la source, entrez le nom de l’instance SQL Server dans le champ **nom du serveur** dans la section **Détails du serveur source** . 

2. Sélectionnez le **Type d’authentification** pris en charge par l’instance SQL Server source.

3. Pour la cible, entrez le nom de l’instance SQL Server dans le champ **nom du serveur** dans la section **Détails du serveur cible** . 

4. Sélectionnez le **type d’authentification** pris en charge par l’instance de SQL Server cible.

5. Il est recommandé de chiffrer la connexion en sélectionnant **chiffrer la connexion** dans la section Propriétés de la **connexion** .

6. Cliquez sur **Suivant**.

   ![Spécifier la source et la page cible](../dma/media/SourceTarget.png)

## <a name="add-databases"></a>Ajouter des bases de données

1. Choisissez les bases de données spécifiques que vous souhaitez migrer en sélectionnant uniquement ces bases de données, dans le volet gauche de la page **Ajouter des bases de données** .

   Par défaut, toutes les bases de données utilisateur sur l’instance de SQL Server source sont sélectionnées pour la migration

2. Utilisez les paramètres de migration sur le côté droit de la page pour définir les options de migration appliquées aux bases de données, en procédant comme suit.

   > [!NOTE]
   > Vous pouvez appliquer les paramètres de migration à toutes les bases de données que vous migrez, en sélectionnant le serveur dans le volet gauche. Vous pouvez également configurer une base de données individuelle avec des paramètres spécifiques en sélectionnant la base de données dans le volet gauche.

    a. Spécifiez l' **emplacement partagé accessible par les serveurs SQL source et cible pour l’opération de sauvegarde**. Assurez-vous que le compte de service exécutant l’instance de SQL Server source possède des privilèges d’écriture sur l’emplacement partagé et que le compte de service cible possède des privilèges de lecture sur l’emplacement partagé.

    b. Spécifiez l’emplacement de restauration des données et des fichiers journaux transactionnels sur le serveur cible.

    ![Page Ajouter des bases de données](../dma/media/AddDatabases.png)

3. Entrez un emplacement partagé auquel les instances source et cible SQL Server ont accès, dans la zone **options d’emplacement du partage** .

4. Si vous ne pouvez pas fournir un emplacement partagé auquel les serveurs SQL source et cible ont accès, sélectionnez **copier les sauvegardes de la base de données vers un autre emplacement à partir duquel le serveur cible peut les lire et les restaurer**. Ensuite, entrez une valeur pour l' **option emplacement pour les sauvegardes pour la restauration** . 

   Assurez-vous que le compte d’utilisateur exécutant Assistant Migration de données a des privilèges de lecture sur l’emplacement de sauvegarde et des privilèges d’écriture sur l’emplacement à partir duquel le serveur cible est restauré.

   ![Option permettant de copier les sauvegardes de base de données vers un autre emplacement](../dma/media/CopyDatabaseDifferentLocation.png)

5. Sélectionnez **Suivant**.

L’Assistant Migration de données effectue des validations sur les dossiers de sauvegarde, les données et les emplacements des fichiers journaux. Si une validation échoue, corrigez les options, puis sélectionnez **suivant**.

## <a name="select-logins"></a>Sélectionner des connexions

1. Sélectionnez des connexions spécifiques pour la migration.

   > [!IMPORTANT]
   > Veillez à sélectionner les connexions qui sont mappées à un ou plusieurs utilisateurs dans les bases de données sélectionnées pour la migration.   

   Par défaut, toutes les connexions SQL Server et Windows qui sont éligibles à la migration sont sélectionnées pour la migration.

2. Sélectionnez **Démarrer la migration**.

   ![Sélectionner les connexions et démarrer la migration](../dma/media/SelectLogins.png)

## <a name="view-results"></a>Afficher les résultats

Vous pouvez surveiller la progression de la migration dans la page **afficher les résultats** .

![Afficher la page des résultats](../dma/media/ViewResults.png)

## <a name="export-migration-results"></a>Exporter les résultats de la migration

1. Cliquez sur **Exporter le rapport** en bas de la page afficher les **résultats** pour enregistrer les résultats de la migration dans un fichier CSV.

2. Consultez le fichier enregistré pour plus d’informations sur la migration de la connexion, puis vérifiez les modifications.

## <a name="see-also"></a>Voir aussi

- [Assistant Migration de données (DMA)](../dma/dma-overview.md)
- [Assistant Migration de données : paramètres de configuration](../dma/dma-configurationsettings.md)
- [Assistant Migration de données : meilleures pratiques](../dma/dma-bestpractices.md)
