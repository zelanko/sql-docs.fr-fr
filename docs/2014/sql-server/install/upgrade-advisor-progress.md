---
title: Progression du conseiller de mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 692b06051872084ff5e1b16dfaf1f8198a649d62
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062339"
---
# <a name="upgrade-advisor-progress"></a>Progression du Conseiller de mise à niveau
  L'analyse du Conseiller de mise à niveau commence par une analyse de chaque composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sélectionné exécutée par un analyseur dédié. À mesure que les composants sont analysés, la progression est signalée dans la boîte de dialogue de **progression** .  
  
## <a name="options"></a>Options  
 **Action**  
 Spécifie le composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est sélectionné pour l'analyse.  
  
 **État**  
 Affiche la valeur d'état retournée par l'interface de progression du composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Message**  
 Affiche les messages d'erreur, d'échec ou de réussite retournés par l'analyseur individuel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Si l'analyse dure trop longtemps, vous pouvez l'arrêter, quitter l'Assistant Analyse du Conseiller de mise à niveau, puis réexécuter l'Assistant. Pour réduire le temps d'analyse, limitez le nombre de composants à analyser.  
  
 À la fin de l'analyse, le rapport est écrit dans un fichier. Vous pouvez afficher le rapport en cliquant sur **lancer le rapport** pour lancer la visionneuse de rapports à partir de cette page. Si vous souhaitez afficher le rapport ultérieurement, vous pouvez ouvrir la **visionneuse de rapports du conseiller de mise à niveau** à partir de la page de démarrage du conseiller de mise à niveau.  
  
> [!NOTE]  
>  Les rapports précédents sont enregistrés chaque fois que vous analysez un serveur. Les rapports sont enregistrés en utilisant le timestamp pour le nom de fichier. La visionneuse de rapports affiche les cinq derniers rapports enregistrés.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : lancer le conseiller de mise à niveau](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [Procédure : exécuter l’Assistant analyse du conseiller de mise à niveau](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Composants SQL Server](../../../2014/sql-server/install/sql-server-components.md)   
 [Référence de l’interface utilisateur du conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
