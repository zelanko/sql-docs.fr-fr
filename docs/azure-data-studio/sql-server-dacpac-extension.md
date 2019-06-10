---
title: Extension de fichier dacpac de SQL Server
titleSuffix: Azure Data Studio
description: Installer et utiliser l’extension de fichier dacpac de SQL Server (version préliminaire) pour Azure Data Studio
ms.custom: seodec18
ms.date: 03/18/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: jroth
ms.openlocfilehash: 70b06749d1cbecc2127c70fee28b60f49583d5ce
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797989"
---
# <a name="sql-server-dacpac-extension-preview"></a>Extension dacpac SQL Server (préversion)

**L’Assistant d’Application de couche données** fournit une expérience facile à utiliser pour déployer et extrayez les fichiers .dacpac et importer et exporter des fichiers .bacpac.

Cette expérience est actuellement dans sa version préliminaire. Veuillez signaler des problèmes et demandes de fonctionnalités [ici.](https://github.com/microsoft/azuredatastudio/issues)

![actions de données](media/sql-server-dacpac-extension/data-tier-application-actions.png)

 ### <a name="requirements"></a>Configuration requise
 * Cet Assistant requiert une connexion active à une instance de SQL Server pour démarrer.

 ### <a name="how-do-i-start-the-data-tier-application-wizard"></a>Comment pour démarrer l’Assistant Application de couche données ?
 * Le point d’entrée principal pour l’Assistant consiste à cliquez avec le bouton droit sur une base de données dans l’Explorateur d’objets, puis cliquez sur **Assistant d’Application de couche données**.
 * Si un utilisateur est connecté à une instance de SQL Server, l’utilisateur peut également démarrer l’Assistant à partir de la palette de commandes (Ctrl + Maj + P) en recherchant **Assistant d’Application de couche données.**

 ### <a name="why-would-i-use-the-data-tier-application-wizard"></a>Pourquoi utiliser l’Assistant d’Application de couche données ?
 Cet Assistant a été créé pour ajouter la possibilité d’extraire et déployer des fichiers .dacpac et importer et exporter des fichiers .bacpac dans Azure Data Studio.

## <a name="install-the-sql-server-dacpac-extension"></a>Installer l’extension de fichier dacpac de SQL Server

1. Pour ouvrir le Gestionnaire d’extensions et accéder aux extensions disponibles, sélectionnez l’icône des extensions ou **Extensions** dans le **vue** menu.
2. Sélectionnez l’extension de fichier dacpac de SQL Server et cliquez sur **installer**.
1. Sélectionnez **recharger** pour activer l’extension (uniquement obligatoire la première fois que vous installez une extension).
2. Accédez à votre tableau de bord de gestion en double-cliquant sur votre serveur ou la base de données et en sélectionnant **gérer**.
3. Extensions installées s’affichent sous forme d’onglets sur votre tableau de bord de gestion :

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les fichiers dacpac, [consultez notre documentation.](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017)