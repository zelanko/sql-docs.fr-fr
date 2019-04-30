---
title: Effectuer une évaluation de migration de SQL Server (Assistant Migration de données) | Microsoft Docs
description: Découvrez comment utiliser l’Assistant de Migration de données pour évaluer un serveur local SQL Server avant de migrer vers un autre serveur SQL ou à la base de données SQL Azure
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 2e7d75b1ef9e540802457cf63e7d2f59468941f9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63155096"
---
# <a name="perform-a-sql-server-migration-assessment-with-data-migration-assistant"></a>Effectuer une évaluation de migration de SQL Server avec Data Migration Assistant

La procédure détaillée ci-dessous vous aider à effectuer votre évaluation premier pour la migration vers local SQL Server, SQL Server s’exécutant sur une machine virtuelle Azure, ou la base de données SQL Azure, à l’aide de Data Migration Assistant.

## <a name="create-an-assessment"></a>Créer une évaluation

1.  Sélectionnez le **New** (+) icône, puis sélectionnez le **évaluation** type de projet.

2.  Définissez le type de serveur source et cible.

    Si vous mettez à niveau votre instance de SQL Server locale vers une instance de SQL Server modernes en local ou à SQL Server hébergée sur une machine virtuelle Azure, définissez le type de serveur source et cible sur **SQL Server**. Si vous effectuez une migration vers Azure SQL Database, à la place la valeur est le type de serveur cible **Azure SQL Database**.

3.  Cliquez sur **Créer**.

    ![Créer une évaluation](../dma/media/NewAssessment.png)

## <a name="choose-assessment-options"></a>Choisissez les options d’évaluation

1. Sélectionnez la version de SQL Server cible que vous projetez de migrer vers.

2. Sélectionnez le type de rapport.

   Lorsque que vous évaluez votre instance de SQL Server source pour la migration vers local SQL Server ou SQL Server hébergées sur les cibles de la machine virtuelle Azure, vous pouvez choisir une ou les deux types de rapport d’évaluation suivants :

    -   **Problèmes de compatibilité**
    -   **Recommandation de nouvelles fonctionnalités**

    ![Sélectionnez un type de rapport d’évaluation pour SQL Server cible](../dma/media/AssessmentTypes.png)

   Lors de l’évaluation de votre instance de SQL Server source pour la migration vers Azure SQL Database, vous pouvez choisir une ou les deux types de rapport d’évaluation suivants :

    -   **Vérifier la compatibilité de base de données**
    -   **Vérifier la parité de fonctionnalité**

    ![Sélectionnez le type de rapport d’évaluation pour la cible de la base de données SQL](../dma/media/AssessmentTypes_Azure.png)

## <a name="add-databases-to-assess"></a>Ajouter des bases de données à évaluer

1.  Sélectionnez **ajouter des Sources de** pour ouvrir le menu volant de connexion.

2.  Entrez le nom d’instance SQL server, choisissez le type d’authentification, définissez les propriétés de connexion correctes, puis sélectionnez **Connect**.

3.  Sélectionnez les bases de données à évaluer, puis sélectionnez **ajouter**.

    > [!NOTE] 
    > Vous pouvez supprimer plusieurs bases de données en les sélectionnant tout en maintenant enfoncée la touche MAJ ou Ctrl, puis en cliquant sur **Sources supprimer**. Vous pouvez également ajouter des bases de données à partir de plusieurs instances de SQL Server à l’aide de la **ajouter des Sources de** bouton.

4.  Cliquez sur **suivant** pour démarrer l’évaluation.

    ![Ajouter des sources et de démarrer l’évaluation](../dma/media/SelectDatabase.png)

## <a name="view-results"></a>Afficher les résultats

La durée de l’évaluation varie selon le nombre de bases de données ajoutées et la taille du schéma de chaque base de données. Résultats sont affichés pour chaque base de données dès qu’elles sont disponibles.

1.  Sélectionnez la base de données qui a effectué l’évaluation et ensuite basculer entre les **les problèmes de compatibilité** et **recommandation de nouvelles fonctionnalités** en utilisant le sélecteur.

2.  Passez en revue les problèmes de compatibilité sur tous les niveaux de compatibilité pris en charge par la version de SQL Server cible que vous avez sélectionné sur la **Options** page.

Vous pouvez examiner les problèmes de compatibilité en analysant l’objet affecté, ses détails et potentiellement un correctif pour chaque problème identifié sous **modifications avec rupture**, **changements de comportement**, et  **Fonctionnalités déconseillées**.

![Afficher les résultats évaluation](../dma/media/ReviewResults.png)

De même, vous pouvez examiner la recommandation de fonctionnalité entre **performances**, **stockage**, et **sécurité** zones.

Recommandations de fonctionnalités couvrent une variété de fonctionnalités comme OLTP en mémoire, Columnstore, Stretch Database, Always Encrypted, Dynamic Data Masking et Transparent Data Encryption.

![Afficher les recommandations de fonctionnalité](../dma/media/FeatureRecommendations.png)

Pour la base de données SQL Azure, l’évaluation des problèmes bloquants de migration et les problèmes de parité de fonctionnalité. Passez en revue les résultats pour ces deux catégories en sélectionnant les options spécifiques.

- Le **parité des fonctionnalités de SQL Server** catégorie fournit un ensemble complet de recommandations, d’approches alternatives disponibles dans Azure et les procédures d’atténuation. Il vous permet de planifier cet effort dans vos projets de migration.

  ![Afficher les informations de parité des fonctionnalités de SQL Server](../dma/media/SQLFeatureParity.png)

- Le **les problèmes de compatibilité** catégorie fournit les fonctionnalités partiellement prises en charge ou non pris en charge qui bloquent la migration bases de données de SQL Server sur site aux bases de données SQL Azure. Il fournit ensuite des recommandations pour vous aider à résoudre ces problèmes.

  ![Afficher les problèmes de compatibilité](../dma/media/CompatibilityIssues.png)

## <a name="export-results"></a>Exporter les résultats

Toutes les bases de données après l’évaluation, sélectionnez **exporter le rapport** pour exporter les résultats dans un fichier JSON ou un fichier CSV. Vous pouvez ensuite analyser les données à votre convenance.

Vous pouvez exécuter plusieurs évaluations simultanément et afficher l’état des évaluations en ouvrant le **toutes les évaluations** page.
