---
title: Extension dacpac SQL Server
titleSuffix: Azure Data Studio
description: Installer et utiliser l’extension dacpac SQL Server (préversion) pour Azure Data Studio
ms.custom: seodec18
ms.date: 03/18/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: e40e377310b33034b4abecdc5e58eab17d39695d
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959196"
---
# <a name="sql-server-dacpac-extension-preview"></a>Extension dacpac SQL Server (préversion)

**L’Assistant Application de la couche Données** fournit une expérience facile à utiliser pour déployer et extraire des fichiers .dacpac et importer et exporter des fichiers .bacpac.

Cette expérience est actuellement dans sa préversion initiale. Signalez les problèmes et les demandes de fonctionnalités [ici](https://github.com/microsoft/azuredatastudio/issues).

![data-actions](media/sql-server-dacpac-extension/data-tier-application-actions.png)

 ### <a name="requirements"></a>Spécifications
 * Cet assistant nécessite une connexion active à une instance SQL Server pour démarrer.

 ### <a name="how-do-i-start-the-data-tier-application-wizard"></a>Comment démarrer l’assistant Application de la couche Données ?
 * Le point d’entrée principal de l’assistant est de cliquer avec le bouton droit sur une base de données dans l’Explorateur d’objets, puis de cliquer sur **Assistant Application de la couche Données**.
 * Si un utilisateur est connecté à une instance SQL Server, il peut également démarrer l’assistant à partir de la palette de commandes (Ctrl+Maj+P) en recherchant **l’Assistant Application de la couche Données**.

 ### <a name="why-would-i-use-the-data-tier-application-wizard"></a>Pourquoi utiliser l’Assistant Application de la couche Données ?
 Cet assistant a été créé pour permettre l’extraction et le déploiement de fichiers .dacpac, ainsi que l’importation et l’exportation de fichiers .bacpac dans Azure Data Studio.

## <a name="install-the-sql-server-dacpac-extension"></a>Installer l’extension SQL Server dacpac

1. Pour ouvrir le gestionnaire d’extensions et accéder aux extensions disponibles, sélectionnez l’icône d’extensions ou sélectionnez **Extensions** dans le menu **Affichage**.
2. Sélectionnez l’extension SQL Server dacpac, puis cliquez sur **Installer**.
1. Sélectionnez **Recharger** pour activer l’extension (nécessaire uniquement la première fois que vous installez une extension).
2. Accédez à votre tableau de bord de gestion en cliquant avec le bouton droit sur votre serveur ou votre base de données et en sélectionnant **Gérer**.
3. Les extensions installées apparaissent sous la forme d’onglets dans votre tableau de bord de gestion :

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur dacpac, [consultez notre documentation.](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017)