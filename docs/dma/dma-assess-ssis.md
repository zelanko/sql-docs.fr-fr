---
title: Effectuer une évaluation de la migration du service d’intégration de SQL Server (Assistant Migration de données) | Microsoft Docs
description: Découvrez comment utiliser Assistant Migration de données pour évaluer un service d’intégration de SQL Server local avant de migrer vers Azure SQL Database ou Azure SQL Database Managed instance
ms.custom: ''
ms.date: 08/23/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84b498cbaf7a2f3d1118894157c17b8270259afa
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632860"
---
# <a name="perform-a-sql-server-integration-service-migration-assessment-with-data-migration-assistant"></a>Effectuer une évaluation de la migration du service d’intégration SQL Server avec Assistant Migration de données

Les instructions pas à pas suivantes vous aident à effectuer la première évaluation de la migration de packages SQL Server Integration Service (SSIS) vers Azure SQL Database ou Azure SQL Database instance gérée, à l’aide de Assistant Migration de données.

## <a name="create-an-assessment"></a>Créer une évaluation

1. Sélectionnez l’icône **nouveau** (+), puis sélectionnez le type de projet **évaluation** en tant que **service d’intégration**.

1. Définissez le type de serveur source et cible.

    Sélectionnez la source en tant que **SQL Server**, puis définissez le type de serveur cible sur **Azure SQL Database** ou **Azure SQL Database Managed instance**.

1. Cliquez sur **Créer**.

    ![créer une évaluation](media/dma-assess-ssis/dma-assess-ssis-create.png)

## <a name="connect-to-a-server"></a>Se connecter à un serveur

1. Suivez l’option par défaut, puis cliquez sur **suivant** pour **Sélectionner les sources**.
1. Entrez le nom de l’instance SQL Server, choisissez le type d’authentification, définissez les propriétés de connexion appropriées.
1. Facultatif Entrez un chemin d’accès au dossier qui contient les packages SSIS.
1. Facultatif Entrez le mot de passe du chiffrement du package, le cas échéant.
1. Cliquez sur **se connecter** au serveur SQL Server source.
  ![ajouter une source](media/dma-assess-ssis/dma-assess-ssis-addsource.png)

## <a name="add-sources-to-assess"></a>Ajouter des sources à évaluer

1. Sélectionnez les types de stockage de package SSIS à évaluer, puis sélectionnez **Ajouter**.
![ajouter une source](media/dma-assess-ssis/dma-assess-ssis-addsource-type.png)
1. Sélectionnez **Ajouter des sources** pour ouvrir le menu contextuel connexion, si vous avez besoin d’évaluer plusieurs dossiers.
1. Cliquez sur **Démarrer l’évaluation**.
  ![](media/dma-assess-ssis/dma-assess-ssis-assess.png) d’évaluation de démarrage

## <a name="view-results"></a>Afficher les résultats

La catégorie de problèmes de compatibilité fournit des fonctionnalités partiellement prises en charge ou non prises en charge qui bloquent la migration de packages SSIS locaux vers Azure-SSIS Integration Runtime. Il fournit ensuite des recommandations pour vous aider à résoudre ces problèmes.

![Afficher les résultats](media/dma-assess-ssis/dma-assess-ssis-result.png)

## <a name="next-steps"></a>Étapes suivantes

- [Vue d’ensemble de la migration des charges de travail SSIS locales vers SSIS dans ADF](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview)
- [Migrer des packages SQL Server Integration Services vers une instance gérée Azure SQL Database](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages-managed-instance)
- [Redéployer les packages SQL Server Integration Services vers Azure SQL Database](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages)
