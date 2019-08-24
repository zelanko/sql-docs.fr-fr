---
title: Vue d’ensemble de Assistant Migration de données (SQL Server) | Microsoft Docs
description: Découvrez comment utiliser Assistant Migration de données pour migrer des bases de données SQL Server vers d’autres bases de données SQL Server ou Azure
ms.custom: ''
ms.date: 08/23/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, overview
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.openlocfilehash: 26a8dbc4a156b8910bd35dfb7381608ec7198f78
ms.sourcegitcommit: 01c8df19cdf0670c02c645ac7d8cc9720c5db084
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000602"
---
# <a name="overview-of-data-migration-assistant"></a>Vue d’ensemble de Assistant Migration de données
Le Assistant Migration de données (DMA) vous aide à effectuer une mise à niveau vers une plateforme de données moderne en détectant les problèmes de compatibilité qui peuvent avoir un impact sur les fonctionnalités de base de données dans votre nouvelle version de SQL Server ou Azure SQL Database. DMA recommande des améliorations en matière de performances et de fiabilité pour votre environnement cible et vous permet de déplacer votre schéma, vos données et vos objets sans relation contenant-contenu de votre serveur source vers votre serveur cible.

> [!NOTE] 
> Pour les migrations volumineuses (en termes de nombre et de taille de bases de données), nous vous recommandons d’utiliser le [Azure Database Migration Service](/azure/dms/dms-overview), qui peut migrer des bases de données à grande échelle.
  
## <a name="get-data-migration-assistant"></a>Obtenir Data Migration Assistant
Pour installer DMA, téléchargez la dernière version de l’outil à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53595), puis exécutez le fichier **DataMigrationAssistant. msi** .

## <a name="capabilities"></a>Fonctionnalités
- Évaluer la ou les instances de SQL Server locales qui migrent vers la ou les bases de données SQL Azure. Le flux de travail d’évaluation vous aide à détecter les problèmes suivants qui peuvent affecter la migration d’Azure SQL Database et fournit des conseils détaillés sur la façon de les résoudre.

  - Problèmes de blocage de la migration: Détecte les problèmes de compatibilité qui bloquent la migration de la ou des bases de données locales SQL Server vers Azure SQL Database. DMA fournit des recommandations pour vous aider à résoudre ces problèmes.

  - Fonctionnalités partiellement prises en charge ou non prises en charge: Détecte les fonctionnalités partiellement prises en charge ou non prises en charge qui sont actuellement utilisées sur l’instance de SQL Server source. DMA fournit un ensemble complet de recommandations, d’approches alternatives disponibles dans Azure et de mesures d’atténuation pour vous permettre de les incorporer dans vos projets de migration.

- Détectez les problèmes qui peuvent affecter une mise à niveau vers un SQL Server local. Celles-ci sont décrites comme des problèmes de compatibilité et sont organisées dans les catégories suivantes:

  - Modifications avec rupture
  - Changements de comportement
  - Fonctionnalités dépréciées

- Découvrez les nouvelles fonctionnalités de la plateforme de SQL Server cible dont la base de données peut bénéficier après une mise à niveau. Celles-ci sont décrites comme recommandations relatives aux fonctionnalités et sont organisées dans les catégories suivantes:

  - Performances
  - Sécurité
  - Stockage

- Migrez une instance de SQL Server locale vers une instance SQL Server moderne hébergée localement ou sur une machine virtuelle Azure qui est accessible à partir de votre réseau local. Vous pouvez accéder à la machine virtuelle Azure à l’aide d’un VPN ou d’autres technologies. Le flux de travail de migration vous permet de migrer les composants suivants:

  - Schéma de bases de données
  - Données et utilisateurs
  - Rôles de serveur
  - Connexions SQL Server et Windows

- Après une migration réussie, les applications peuvent se connecter aux bases de données SQL Server cible en toute transparence.

- Évaluer les packages de SQL Server Integration Services (SSIS) locaux qui migrent vers Azure SQL Database ou Azure SQL Database Managed instance. L’évaluation permet de détecter les problèmes susceptibles d’affecter la migration. Celles-ci sont décrites comme des problèmes de compatibilité et sont organisées dans les catégories suivantes:

  - Bloqueurs de migration: détecte les problèmes de compatibilité qui bloquent la migration du ou des packages source vers Azure. DMA fournit des recommandations pour vous aider à résoudre ces problèmes.

  - Problèmes d’informations: détecte les fonctionnalités partiellement prises en charge ou déconseillées qui sont utilisées dans le ou les packages source.

  > [!NOTE]
  > L’évaluation des packages hébergés dans le système de fichiers est uniquement prise en charge.
  > L’évaluation des packages hébergés dans MSDB, le magasin de packages ou SSISDB est plus tard.

## <a name="prerequisites"></a>Prérequis
Pour exécuter une évaluation, vous devez être membre du rôle **sysadmin** SQL Server.

## <a name="supported-source-and-target-versions"></a>Versions source et cible prises en charge
DMA remplace toutes les versions précédentes de SQL Server conseiller de mise à niveau et doit être utilisé pour les mises à niveau pour la plupart des versions SQL Server. Versions source et cible prises en charge:

**Alimentation**
- SQL Server 2005
- SQL Server 2008
- SQL Server 2008 R2
- SQL Server 2012 
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017 sur Windows

**Compilé**
- SQL Server 2012
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017 sur Windows et Linux
- Azure SQL Database
- Azure SQL Database Managed Instance

## <a name="see-also"></a>Voir aussi
[Évaluer votre migration SQL Server](../dma/dma-assesssqlonprem.md)     
[Assistant Migration de données: Paramètres de configuration](../dma/dma-configurationsettings.md)     
[Migrer des SQL Server locaux à l’aide de Assistant Migration de données](../dma/dma-migrateonpremsql.md)     
[Assistant Migration de données: Meilleures pratiques](../dma/dma-bestpractices.md)     
