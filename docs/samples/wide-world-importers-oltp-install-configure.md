---
title: Installer et configurer la base de données d’échantillons de WideWorldImporters
description: Suivez ces instructions pour télécharger, installer et configurer la base de données d’échantillons WideWorldImporters avec SQL Server Management Studio.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 355eaa254fcc7bb6cd4aa9a39c2cbcb269d88396
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487068"
---
# <a name="installation-and-configuration"></a>Installation et configuration
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Instructions d’installation et de configuration de base de données OLTP de Wide World Importers.

## <a name="prerequisites"></a>Prérequis

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (ou plus) ou [Azure SQL Database](https://azure.microsoft.com/services/sql-database/). Pour la version complète de l’échantillon, utilisez SQL Server Evaluation/Developer/Enterprise Edition.
- [STUDIO de gestion des serveurs SQL](../ssms/download-sql-server-management-studio-ssms.md). Pour les meilleurs résultats, utilisez la version de juin 2016 ou plus tard.

## <a name="download"></a>Téléchargement

La dernière version de l’échantillon:

[large-importateurs-libération](https://go.microsoft.com/fwlink/?LinkID=800630)

Téléchargez l’exemple de sauvegarde/bacpac de base de données WideWorldImporters qui correspond à votre édition de SQL Server ou Azure SQL Database.

Le code source pour recréer la base de données de l’échantillon est disponible à partir de l’emplacement suivant. Notez que la reconstitution de l’échantillon entraînera de légères différences dans les données, puisqu’il y a un facteur aléatoire dans la génération de données :

[importateurs du monde entier](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

## <a name="install"></a>Installer


### <a name="sql-server"></a>SQL Server

Pour restaurer une sauvegarde dans une instance SQL Server, vous pouvez utiliser Management Studio.

1. Ouvrez SQL Server Management Studio et connectez-vous à l’instance sqL Server cible.
2. Cliquez à droite sur le nœud **databases** et sélectionnez **Restore Database**.
3. Sélectionnez **l’appareil** et cliquez sur le bouton **...**
4. Dans le dialogue **Sélectionnez les périphériques de sauvegarde**, cliquez sur **Ajouter,** naviguer vers la sauvegarde de base de données dans le système de fichiers du serveur, et sélectionnez la sauvegarde. Cliquez sur **OK**.
5. Si nécessaire, modifiez l’emplacement cible des données et des fichiers journaux, dans la vitre **des fichiers.** Notez qu’il est préférable de placer des données et des fichiers de journal sur différents lecteurs.
6. Cliquez sur **OK**. Cela permettra d’initier la restauration de la base de données. Une fois qu’elle sera terminée, vous aurez installé la base de données WideWorldImporters sur votre instance SQL Server.

### <a name="azure-sql-database"></a>Azure SQL Database

Pour importer un bacpac dans une nouvelle base de données SQL, vous pouvez utiliser Management Studio.

1. (facultatif) Si vous n’avez pas encore de serveur SQL à Azure, naviguez vers le [portail Azure](https://portal.azure.com/) et créez une nouvelle base de données SQL. Dans le processus de création d’une base de données, vous allez créer un serveur. Prenez note du serveur.
   - Voir [ce tutoriel](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) pour créer une base de données en quelques minutes
2. Ouvrez SQL Server Management Studio et connectez-vous à votre serveur azure.
3. Cliquez à droite sur le nœud **databases** et sélectionnez **l’application Import Data-Tier**.
4. Dans les **Paramètres d’importation** **sélectionnez Import à partir d’un disque local** et sélectionnez le bacpac de la base de données de l’échantillon à partir de votre système de fichiers.
5. Sous **bases de données Paramètres** modifier le nom de base de données en *WideWorldImporters* et sélectionner l’édition cible et l’objectif de service à utiliser.
6. Cliquez **sur Next** and **Finish** pour lancer le déploiement. Il faudra quelques minutes pour terminer sur un P1. Si un niveau de tarification plus bas est souhaité, il est recommandé d’importer dans une nouvelle base de données P1, puis de modifier le niveau de prix au niveau souhaité.

## <a name="configuration"></a>Configuration

### <a name="full-text-indexing"></a>Indexation de texte intégral

La base de données de l’échantillon peut utiliser l’indexation intégrale. Toutefois, cette fonctionnalité n’est pas installée par défaut avec SQL Server - vous devez la sélectionner lors de la configuration SQL Server (elle est activée par défaut dans Azure SQL DB). Par conséquent, une étape post-installation est nécessaire.

1. Dans SQL Server Management Studio, connectez-vous à la base de données WideWorldImporters et ouvrez une nouvelle fenêtre de requête.
2. Exécutez la commande T-SQL suivante pour activer l’utilisation de l’indexage intégral dans la base de données :`EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>SQL Server Audit

S’applique à : SQL Server

L’activation de l’audit dans SQL Server nécessite la configuration du serveur. Pour activer l’audit SQL Server pour l’échantillon WideWorldImporters, exécutez la déclaration suivante dans la base de données :

    EXECUTE [Application].[Configuration_ApplyAuditing]

Dans la base de données Azure SQL, Audit est configuré via le [portail Azure](https://portal.azure.com/).

### <a name="row-level-security"></a>Sécurité au niveau des lignes

S’applique à: Azure SQL Database

Row-Level Security n’est pas activé par défaut dans le téléchargement bacpac de WideWorldImporters. Pour activer la sécurité au niveau des lignes dans la base de données, exécutez la procédure stockée suivante :

    EXECUTE [Application].[Configuration_ApplyRowLevelSecurity]

