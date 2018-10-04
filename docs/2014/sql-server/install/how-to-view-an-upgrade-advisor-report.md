---
title: 'Comment : afficher un rapport du Conseiller de mise à niveau | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- viewing reports
- Upgrade Advisor [SQL Server], reports
- SQL Server Upgrade Advisor, reports
- reports [Upgrade Advisor], viewing
ms.assetid: d13b38af-0ac3-4030-83cd-e7d7825dd09f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 90b9ca2879897bb427981e92d610a7f09916c68e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201929"
---
# <a name="how-to-view-an-upgrade-advisor-report"></a>Procédure : afficher un rapport du Conseiller de mise à niveau
  Le Conseiller de mise à niveau crée des rapports pour chaque composant que vous sélectionnez pour analyse. Cette rubrique décrit comment afficher un rapport du Conseiller de mise à niveau à partir de la page de démarrage du Conseiller de mise à niveau.  
  
> [!IMPORTANT]  
>  La visionneuse de rapports charge les fichiers en fonction des noms de fichiers standard. Si les fichiers ont été renommés, la visionneuse de rapports ne les charge pas.  
  
### <a name="to-view-a-report"></a>Pour afficher un rapport  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**, puis cliquez sur  **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.  
  
2.  Dans la page de démarrage Upgrade Advisor, cliquez sur **lancer la visionneuse de rapports**.  
  
3.  Pour sélectionner un rapport dans l'emplacement par défaut sur votre ordinateur :  
  
    1.  Dans le **Server** liste, sélectionnez un serveur.  
  
    2.  Dans le **Instance ou composant** , sélectionnez une combinaison composant/instance ou de composant.  
  
     Pour sélectionner un rapport dans un autre emplacement :  
  
    1.  Cliquez sur le **ouvrir le rapport** lien.  
  
    2.  Naviguez jusqu'à l'emplacement du rapport, puis double-cliquez sur le fichier XML.  
  
     Le Conseiller de mise à niveau stocke jusqu'à cinq rapports d'une analyse précédente comme historique. Pour afficher ces rapports, cliquez sur le **rapport** zone de liste déroulante, puis sélectionnez un rapport. Les rapports sont répertoriés selon le horodateur à partir du moment où ils ont été générés.  
  
     Le rapport contient les détails suivants pour tous les problèmes détectés :  
  
    -   **Importance**, ce qui indique combien il est important pour résoudre le problème.  
  
    -   **Date de résolution**, ce qui indique si vous devez (ou devez) corriger le problème avant ou après la mise à niveau vers [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], avant ou après la migration de l’application ou les données, ou à tout moment.  
  
    -   Brève description du problème.  
  
4.  Si le rapport contient plus de 20 éléments, cliquez sur la flèche Suivant verte en haut ou en bas du rapport pour afficher l'ensemble d'éléments suivant. Cliquez sur le bouton Précédent vert pour afficher les 20 éléments précédents.  
  
5.  Pour trier les données du rapport, cliquez sur l'en-tête d'une colonne.  
  
6.  Pour afficher des détails pour un élément spécifique, cliquez sur l'élément. Une description du problème apparaît, ainsi que des options supplémentaires :  
  
    -   Pour afficher les objets où ce problème a été trouvé, cliquez sur **afficher les objets affectés**.  
  
    -   Pour afficher l’aide pour le problème, cliquez sur **en savoir plus sur ce problème et sa résolution**.  
  
    -   Pour marquer le problème comme résolu, qui masque le problème lorsque vous affichez le rapport à nouveau, sélectionnez **ce problème a été résolu**.  
  
> [!NOTE]  
>  Le rapport peut contenir un élément pour les problèmes indétectables. Ce sont des problèmes qui ne peuvent pas être détectés ou qui généreraient trop de résultats faux positifs. Cliquez sur le **en savoir plus sur ce problème et sa résolution** lien pour afficher la liste des problèmes indétectables pour le composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : exporter des rapports](../../../2014/sql-server/install/how-to-export-reports.md)   
 [Comment : exécuter l’Assistant analyse du Conseiller de mise à niveau](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Résolution des problèmes de mise à niveau](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Les rubriques de procédures de conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md)   
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
