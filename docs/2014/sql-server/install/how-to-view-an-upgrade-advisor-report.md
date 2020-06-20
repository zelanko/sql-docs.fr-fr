---
title: 'Procédure : afficher un rapport du conseiller de mise à niveau | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
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
ms.openlocfilehash: 0cbe8746faeba10fa023aa51e7d91a6fb074776e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85042440"
---
# <a name="how-to-view-an-upgrade-advisor-report"></a>Procédure : afficher un rapport du Conseiller de mise à niveau
  Le Conseiller de mise à niveau crée des rapports pour chaque composant que vous sélectionnez pour analyse. Cette rubrique décrit comment afficher un rapport du Conseiller de mise à niveau à partir de la page de démarrage du Conseiller de mise à niveau.  
  
> [!IMPORTANT]  
>  La visionneuse de rapports charge les fichiers en fonction des noms de fichiers standard. Si les fichiers ont été renommés, la visionneuse de rapports ne les charge pas.  
  
### <a name="to-view-a-report"></a>Pour afficher un rapport  
  
1.  Cliquez sur **Démarrer**, sur **tous les programmes**, sur **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]** , puis sur conseiller de ** [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mise à niveau**.  
  
2.  Sur la page de démarrage du conseiller de mise à niveau, cliquez sur **lancer le conseiller de mise à niveau**.  
  
3.  Pour sélectionner un rapport dans l'emplacement par défaut sur votre ordinateur :  
  
    1.  Dans la liste **serveur** , sélectionnez un serveur.  
  
    2.  Dans la liste **instance ou composant** , sélectionnez une combinaison composant ou composant/instance.  
  
     Pour sélectionner un rapport dans un autre emplacement :  
  
    1.  Cliquez sur le lien **ouvrir le rapport** .  
  
    2.  Naviguez jusqu'à l'emplacement du rapport, puis double-cliquez sur le fichier XML.  
  
     Le Conseiller de mise à niveau stocke jusqu'à cinq rapports d'une analyse précédente comme historique. Pour afficher ces rapports, cliquez sur la zone de liste déroulante **rapport** , puis sélectionnez un rapport. Les rapports sont répertoriés selon le horodateur à partir du moment où ils ont été générés.  
  
     Le rapport contient les détails suivants pour tous les problèmes détectés :  
  
    -   **Importance**, qui indique à quel point il est important de résoudre le problème.  
  
    -   **Quand corriger**, ce qui indique si vous devez corriger le problème avant ou après la mise à niveau vers [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , avant ou après la migration de l’application ou des données, ou à tout moment.  
  
    -   Brève description du problème.  
  
4.  Si le rapport contient plus de 20 éléments, cliquez sur la flèche Suivant verte en haut ou en bas du rapport pour afficher l'ensemble d'éléments suivant. Cliquez sur le bouton Précédent vert pour afficher les 20 éléments précédents.  
  
5.  Pour trier les données du rapport, cliquez sur l'en-tête d'une colonne.  
  
6.  Pour afficher des détails pour un élément spécifique, cliquez sur l'élément. Une description du problème apparaît, ainsi que des options supplémentaires :  
  
    -   Pour afficher les objets où ce problème a été trouvé, cliquez sur **afficher les objets affectés**.  
  
    -   Pour afficher l’aide pour le problème, cliquez sur en **savoir plus sur ce problème et sur la manière de le résoudre**.  
  
    -   Pour marquer le problème comme résolu, ce qui masque le problème lorsque vous affichez de nouveau le rapport, sélectionnez **ce problème a été résolu**.  
  
> [!NOTE]  
>  Le rapport peut contenir un élément pour les problèmes indétectables. Ce sont des problèmes qui ne peuvent pas être détectés ou qui généreraient trop de résultats faux positifs. Cliquez sur le lien en **savoir plus sur ce problème et sur la manière de le résoudre** pour afficher une liste des problèmes non détectables pour le composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : exporter des rapports](../../../2014/sql-server/install/how-to-export-reports.md)   
 [Procédure : exécuter l’Assistant analyse du conseiller de mise à niveau](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Résolution des problèmes de mise à niveau](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Rubriques de procédures relatives au conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md)   
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
