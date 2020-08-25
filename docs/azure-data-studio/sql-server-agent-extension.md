---
title: Extension SQL Server Agent
description: Découvrez comment installer et utiliser l’extension SQL Server Agent (préversion) pour Azure Data Studio, qui permet de gérer les travaux et les configurations SQL Agent.
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 207388fed1ea2465fb965457640b5e1fb0d162cf
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88766158"
---
# <a name="sql-server-agent-extension-preview"></a>Extension SQL Server Agent (préversion)

L’extension SQL Server Agent (préversion) est une extension pour la gestion et le dépannage des travaux et de la configuration de l’agent SQL. Cette extension est actuellement en préversion.

Les actions principales sont les suivantes :
- Répertorier les travaux SQL Server Agent configurés sur SQL Server
- Afficher l’historique des travaux avec les résultats de l’exécution du travail
- Contrôle de base des travaux pour démarrer et arrêter des travaux

## <a name="install-the-sql-server-agent-extension"></a>Installer l’extension SQL Server Agent

1. Pour ouvrir le gestionnaire d’extensions et accéder aux extensions disponibles, sélectionnez l’icône d’extensions ou sélectionnez **Extensions** dans le menu **Affichage**.
2. Sélectionnez une extension disponible pour afficher ses détails.

   ![Installer l'agent](media/extensions/sql-server-agent-extension/install-sql-agent.png)

1. Sélectionnez l’extension de votre choix et **installez-la**.
2. Sélectionnez **Recharger** pour activer l’extension (nécessaire uniquement la première fois que vous installez une extension).
1. Accédez à votre tableau de bord de gestion en cliquant avec le bouton droit sur votre serveur ou votre base de données et en sélectionnant **Gérer**.
2. Les extensions installées apparaissent sous la forme d’onglets dans votre tableau de bord de gestion :

   ![Afficher l’agent](media/extensions/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>Afficher les travaux

Quand vous vous connectez à l’extension SQL Server Agent, la première chose que vous voyez est la liste de tous les travaux de l’agent.

   ![Afficher les travaux](media/extensions/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur SQL Server Agent, [consultez notre documentation.](../ssms/agent/sql-server-agent.md?view=sql-server-2017)