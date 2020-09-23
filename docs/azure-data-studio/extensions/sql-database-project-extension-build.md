---
title: Générer et publier un projet
description: Générer et publier un projet à l’aide de l’extension SQL Server Database Projects
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.reviewer: maghan, sstein
ms.custom: ''
ms.date: 06/25/2020
ms.openlocfilehash: 4320873affdab74a31d1e666a84bc744b1c00385
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91123173"
---
# <a name="build-and-publish-a-project"></a>Générer et publier un projet

Le processus de génération dans l’extension SQL Database Projects pour Azure Data Studio permet la création de *dacpac* dans les environnements Windows, macOS et Linux. Le projet peut être déployé dans un environnement local ou cloud à l’aide du processus de publication.

## <a name="prerequisites"></a>Prérequis

- Installez et configurez l’[extension SQL Database Projects pour Azure Data Studio](sql-database-project-extension.md).

## <a name="build-a-database-project"></a>Générer un projet de base de données

 Dans la viewlet **Projets** sous **Explorateur**, cliquez avec le bouton droit sur le nœud racine *.sqlproj*, puis sélectionnez **Générer**.

 Le volet de sortie s’affiche automatiquement avec la sortie du processus de génération.  Le message suivant apparaît à la fin d’une génération réussie : 

 ``` ... exited with code: 0 ```

## <a name="publish-a-database-project"></a>Publier un projet de base de données

Une fois qu’un projet a été compilé via le processus de génération, la base de données peut être publiée sur une instance SQL Server. Pour publier un projet de base de données, dans la viewlet **Projets** sous **Explorateur**, cliquez avec le bouton droit sur le nœud racine *.sqlproj*, puis sélectionnez **Publier**.

Dans la boîte de dialogue **Publier la base de données** qui s’affiche, spécifiez une connexion serveur et le nom de la base de données à créer.

## <a name="next-steps"></a>Étapes suivantes

- [Extension SQL Database Projects pour Azure Data Studio](sql-database-project-extension.md)
- [Générer des projets de base de données SQL à partir de la ligne de commande](sql-database-project-extension-build-from-command-line.md)
