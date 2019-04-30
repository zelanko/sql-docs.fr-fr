---
title: Extension de l’Agent SQL Server
titleSuffix: Azure Data Studio
description: Installer et utiliser l’extension de l’Agent SQL Server (version préliminaire) pour Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 077a3ae072c8a9f680162de5eb1813c15b1e7199
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63309305"
---
# <a name="sql-server-agent-extension-preview"></a>Extension de l’Agent SQL Server (version préliminaire)

L’extension de l’Agent SQL Server (version préliminaire) est une extension pour la gestion et résolution des problèmes de configuration et les travaux de l’Agent SQL. Cette extension est actuellement en version préliminaire.

Actions clés sont les suivantes :
- Travaux d’Agent liste SQL Server configurés sur un serveur SQL Server
- Afficher l’historique de travail avec les résultats de la tâche d’exécution
- Contrôle de travail de base pour démarrer et arrêter les travaux

## <a name="install-the-sql-server-agent-extension"></a>Installer l’extension de l’Agent SQL Server

1. Pour ouvrir le Gestionnaire d’extensions et accéder aux extensions disponibles, sélectionnez l’icône des extensions ou **Extensions** dans le **vue** menu.
2. Sélectionner une extension disponible pour afficher ses détails.

   ![Installer l’agent](media/extensions/sql-server-agent-extension/install-sql-agent.png)

1. Sélectionnez l’extension souhaitée et **installer** il.
2. Sélectionnez **recharger** pour activer l’extension (uniquement obligatoire la première fois que vous installez une extension).
1. Accédez à votre tableau de bord de gestion en double-cliquant sur votre serveur ou la base de données et en sélectionnant **gérer**.
2. Extensions installées s’affichent sous forme d’onglets sur votre tableau de bord de gestion :

   ![Agent de vue](media/extensions/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>Afficher les tâches

Lorsque vous vous connectez à l’extension de l’Agent SQL Server, la première chose que vous voyez est une liste de tous vos travaux de l’Agent.

   ![Afficher les tâches](media/extensions/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur SQL Server Agent, [consultez notre documentation.](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent?view=sql-server-2017)


