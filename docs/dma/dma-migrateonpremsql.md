---
title: Mise à niveau SQL Server vers SQL Server ou SQL Server sur des machines virtuelles Azure à l’aide de l’Assistant Migration des données sur site | Microsoft Docs
description: Découvrez comment utiliser Data Migration Assistant pour mettre à niveau un serveur local SQL Server vers une version ultérieure de SQL Server ou SQL Server sur des machines virtuelles Azure
ms.custom: ''
ms.date: 08/29/2018
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
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 2638b536cc97f53e62daf578d1249a2a62987e62
ms.sourcegitcommit: fb269accc3786715c78f8b6e2ec38783a6eb63e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43152790"
---
# <a name="upgrade-on-premises-sql-server-to-sql-server-or-sql-server-on-azure-vms-using-the-data-migration-assistant"></a>Mise à niveau de SQL Server sur site vers SQL Server ou SQL Server sur des machines virtuelles Azure à l’aide de l’Assistant Migration des données

Data Migration Assistant fournit des évaluations transparentes de SQL Server en local et mises à niveau vers des versions ultérieures de SQL Server ou des migrations vers SQL Server sur machines virtuelles Azure ou Azure SQL Database.

Cet article fournit des instructions détaillées pour la mise à niveau SQL Server local vers une version ultérieure de SQL Server ou SQL Server sur des machines virtuelles Azure à l’aide de l’Assistant Migration des données.   

## <a name="create-a-new-migration-project"></a>Créer un nouveau projet de migration

1. Dans le volet gauche, sélectionnez **New** (+), puis le **Migration** type de projet.

2. Définissez le type de serveur source et cible sur **SQL Server** si vous mettez à niveau un serveur local SQL Server vers une version ultérieure de local SQL Server.

3. Sélectionnez **Créer**.

   ![Créer le projet de migration](../dma/media/NewCreate.png)

## <a name="specify-the-source-and-target"></a>Spécifiez la source et la cible

1. Pour la source, entrez le nom de l’instance SQL Server dans le **nom du serveur** champ dans le **détails du serveur de la Source** section. 

2. Sélectionnez le **type d’authentification** pris en charge par l’instance de SQL Server source.

3. Pour la cible, entrez le nom de l’instance SQL Server dans le **nom du serveur** champ dans le **cibler les détails du serveur** section. 

4. Sélectionnez le **type d’authentification** pris en charge par l’instance de SQL Server cible.

5. Il est recommandé de chiffrer la connexion en sélectionnant **chiffrer la connexion** dans le **propriétés de connexion** section.

6. Cliquez sur **Suivant**.

   ![Spécifier la page source et cible](../dma/media/SourceTarget.png)

## <a name="add-databases"></a>Ajouter des bases de données

1. Choisissez les bases de données spécifiques que vous souhaitez migrer en sélectionnant uniquement ces bases de données, dans le volet gauche de la **ajouter des bases de données** page.

   Par défaut, toutes les bases de données utilisateur sur l’instance de SQL Server source sont sélectionnés pour la migration

2. Utilisez les paramètres de migration sur le côté droit de la page pour définir les options de migration qui sont appliquées aux bases de données, en procédant comme suit.

   > [!NOTE]
   > Vous pouvez appliquer les paramètres de migration pour toutes les bases de données que vous migrez, en sélectionnant le serveur dans le volet gauche. Vous pouvez également configurer une base de données avec des paramètres spécifiques en sélectionnant la base de données dans le volet gauche.

    A. Spécifiez le **partagé emplacement accessible par les serveurs SQL source et cible pour l’opération de sauvegarde**. Assurez-vous que le compte de service en cours d’exécution la source SQL Server instance a écrit des privilèges sur l’emplacement partagé et le compte de service cible a privilèges de lecture sur l’emplacement partagé.

    B. Spécifiez l’emplacement pour restaurer les données et les fichiers journaux transactionnels sur le serveur cible.

    ![Ajouter une page de bases de données](../dma/media/AddDatabases.png)

3. Entrez un emplacement partagé que les instances de SQL Server source et cible ont accès, dans le **partagent des options d’emplacement** boîte.

4. Si vous ne pouvez pas fournir un emplacement partagé dont les serveurs SQL source et cible ont accès, sélectionnez **copier les sauvegardes de base de données vers un autre emplacement que le serveur cible peut lire et restaurer à partir de**. Ensuite, entrez une valeur pour le **emplacement des sauvegardes pour l’option de restauration** boîte. 

   Assurez-vous que le compte d’utilisateur exécutant l’Assistant de Migration de données a des privilèges de lecture à l’emplacement de sauvegarde et en écriture à l’emplacement à partir de laquelle restaure le serveur cible.

   ![Option pour copier les sauvegardes de base de données à un autre emplacement](../dma/media/CopyDatabaseDifferentLocation.png)

5. Sélectionnez **Suivant**.

L’Assistant Migration de données effectue les validations sur les dossiers de sauvegarde, journal des fichiers de données et emplacements. Si aucune validation échoue, corrigez les options, puis sélectionnez **suivant**.

## <a name="select-logins"></a>Sélectionnez les connexions

1. Sélectionnez des connexions spécifiques pour la migration.

   > [!IMPORTANT]
   > Veillez à sélectionner les connexions qui sont mappées à un ou plusieurs utilisateurs dans les bases de données sélectionnées pour la migration.   

   Par défaut, les connexions de tous les SQL Server et Windows qui sont éligibles pour la migration sont sélectionnées pour la migration.

2. Sélectionnez **démarrer la Migration**.

   ![Sélectionnez les connexions et de démarrer la migration](../dma/media/SelectLogins.png)

## <a name="view-results"></a>Afficher les résultats

Vous pouvez surveiller la progression de la migration sur le **afficher les résultats** page.

![Page de résultats de la vue](../dma/media/ViewResults.png)

## <a name="export-migration-results"></a>Exporter les résultats de la migration

1. Cliquez sur **exporter le rapport** en bas de la **afficher les résultats** page pour enregistrer les résultats de la migration vers un fichier CSV.

2. Passez en revue le fichier enregistré pour plus d’informations sur la migration de connexion et vérifiez les modifications.

## <a name="see-also"></a>Voir aussi

- [Data Migration Assistant (DMA)](../dma/dma-overview.md)
- [Data Migration Assistant : Paramètres de Configuration](../dma/dma-configurationsettings.md)
- [Assistant de Migration de données : Meilleures pratiques](../dma/dma-bestpractices.md)
