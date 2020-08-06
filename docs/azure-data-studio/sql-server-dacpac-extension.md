---
title: Extension dacpac SQL Server
description: Découvrez comment installer et lancer l’Assistant Application de la couche Données, qui permet de déployer et d’extraire des fichiers dacpac, et d’importer et d’exporter des fichiers bacpac.
ms.custom: seodec18
ms.date: 11/04/2019
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: eeff69a65751097017383399784ea9a717f3b7e8
ms.sourcegitcommit: 7035d9471876c70b99c58bf9b46af5cce6e9c66c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87522473"
---
# <a name="sql-server-dacpac-extension"></a>Extension dacpac SQL Server

**L’Assistant Application de la couche Données**  fournit une expérience d’assistant facile à utiliser pour déployer et extraire des fichiers dacpac et importer et exporter des fichiers bacpac.


## <a name="features"></a>Fonctionnalités

* Déployer un dacpac sur une instance SQL Server
* Extraire une instance SQL Server dans un dacpac
* Créer une base de données à partir d’un bacpac
* Exporter le schéma et les données vers un bacpac

![GIF de démonstration de l’extension dacpac](media/extensions/sql-server-dacpac-extension/dacpac-extension-demo.gif)


## <a name="why-would-i-use-the-data-tier-application-wizard"></a>Pourquoi utiliser l’Assistant Application de la couche Données ?

L’Assistant facilite la gestion des fichiers dacpac et bacpac, ce qui simplifie le développement et le déploiement des éléments de la couche données qui prennent en charge votre application. Pour en savoir plus sur l’utilisation des applications de la couche Données, [consultez notre documentation.](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017)


## <a name="install-the-extension"></a>Installer l’extension

1. Sélectionnez l’icône Extensions pour voir les extensions disponibles.

    ![icône du gestionnaire d’extensions](media/extensions/extension-manager-icon.png)

2. Recherchez l’extension **SQL Server dacpac** et sélectionnez-la pour afficher ses détails. Cliquez sur **Installer** pour ajouter l’extension.

3. Une fois l’extension installée, sélectionnez **Recharger** pour l’activer dans Azure Data Studio (opération uniquement requise lors de la première installation d’une extension).


## <a name="launch-the-data-tier-application-wizard"></a>Lancer l’Assistant de l'application de la couche Données

Pour lancer l’Assistant, cliquez avec le bouton droit sur le dossier Bases de données ou cliquez avec le bouton droit sur une base de données spécifique dans l’Explorateur d’objets. Cliquez ensuite sur **Assistant de l'application de la couche Données**.

![menu de lancement de l’extension dacpac](media/extensions/sql-server-dacpac-extension/dacpac-extension-launch.png)


## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur dacpac, [consultez notre documentation.](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017)
Signalez les problèmes et les demandes de fonctionnalités [ici](https://github.com/microsoft/azuredatastudio/issues).