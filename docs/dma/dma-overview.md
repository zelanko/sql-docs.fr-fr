---
title: Vue d’ensemble de l’Assistant de Migration de données (SQL Server) | Microsoft Docs
description: Découvrez comment utiliser Data Migration Assistant pour migrer des bases de données SQL Server à d’autres SQL Server ou les bases de données Azure
ms.custom: ''
ms.date: 10/20/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, overview
ms.assetid: ''
author: pochiraju
ms.author: rajpo
manager: craigg
ms.openlocfilehash: ce503f2b6cb39296d85c7e917e5600d8de44545a
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49643857"
---
# <a name="overview-of-data-migration-assistant"></a>Vue d’ensemble de l’Assistant Migration de données

Permet de Data Migration Assistant (DMA) mettre à niveau vers une plate-forme de données moderne en détectant les problèmes de compatibilité qui peuvent avoir un impact sur les fonctionnalités de base de données dans votre nouvelle version de SQL Server ou de base de données SQL Azure. DMA recommande les améliorations des performances et la fiabilité de votre environnement cible et vous permet de déplacer votre schéma, les données et les objets de relation contenant-contenus de votre serveur source à votre serveur cible.

> [!NOTE] 
> Pour les migrations de grande taille (en termes de nombre et taille des bases de données), nous vous recommandons d’utiliser le [Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview), qui peut faire migrer des bases de données à grande échelle.
  
## <a name="capabilities"></a>Fonctions

- Évaluer les instances de SQL Server sur site vers les bases de données SQL Azure. Le flux de travail d’évaluation vous aide à détecter les problèmes suivants qui peuvent affecter la migration de base de données SQL Azure et fournit des instructions détaillées sur la façon de les résoudre.

  - Problèmes de blocage de migration : détecte les problèmes de compatibilité que bloc migration locales SQL Server bases de données s pour les bases de données SQL Azure. DMA fournit des recommandations pour vous aider à résoudre ces problèmes.

  - Partiellement pris en charge ou non pris en charge des fonctionnalités : détecte les fonctionnalités partiellement prises en charge ou non pris en charge qui sont actuellement en cours d’utilisation sur l’instance de SQL Server source. DMA fournit qu'un ensemble complet de recommandations, d’approches alternatives disponibles dans Azure et les procédures d’atténuation afin que vous pouvez les incorporer dans vos projets de migration.

- Découvrez les problèmes qui peuvent affecter une mise à niveau vers un serveur local SQL Server. Ceux-ci sont décrits comme des problèmes de compatibilité et sont organisés dans les catégories suivantes :

  - Modifications avec rupture
  - Changements de comportement
  - Fonctionnalités dépréciées

- Découvrez les nouvelles fonctionnalités dans la plateforme SQL Server cible la base de données pouvant bénéficier du après une mise à niveau. Ceux-ci sont décrits en tant que recommandation de fonctionnalité et sont organisés dans les catégories suivantes :

  - Performances
  - Sécurité
  - Stockage

- Migrer une instance de SQL Server locale vers une instance de SQL Server moderne hébergée localement ou sur une machine virtuelle (VM) qui est accessible à partir de votre réseau local. La machine virtuelle Azure sont accessibles à l’aide de VPN ou autres technologies. Le workflow de migration vous aide à migrer les composants suivants :

  - Schéma des bases de données
  - Les utilisateurs et les données
  - Rôles de serveur
  - Connexions SQL Server et Windows

- Après une migration réussie, vous peuvent vous connecter des applications pour les bases de données du serveur SQL cible, en toute transparence.

## <a name="supported-source-and-target-versions"></a>Versions prises en charge de source et cible

DMA remplace toutes les versions précédentes du Conseiller de mise à niveau de SQL Server et doit être utilisé pour les mises à niveau pour la plupart des versions de SQL Server. Suivent les versions prises en charge de source et cible.

**Sources**
- SQL Server 2005
- SQL Server 2008
- SQL Server 2008 R2
- SQL Server 2012 
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017 sur Windows

**Cibles**
- SQL Server 2012
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017 sur Windows et Linux
- Azure SQL Database
- Azure SQL Database Managed Instance

## <a name="installation"></a>Installation

Pour installer le DMA, téléchargez la dernière version de l’outil à partir de la [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53595), puis exécutez le **DataMigrationAssistant.msi** fichier.

## <a name="see-also"></a>Voir aussi

[Évaluer votre migration vers SQL Server](../dma/dma-assesssqlonprem.md)

[Data Migration Assistant : Paramètres de Configuration](../dma/dma-configurationsettings.md)

[Migrate On-Premises SQL Server à l’aide de Data Migration Assistant](../dma/dma-migrateonpremsql.md)

[Assistant de Migration de données : Meilleures pratiques](../dma/dma-bestpractices.md)



