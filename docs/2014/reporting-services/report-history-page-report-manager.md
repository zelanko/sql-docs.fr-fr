---
title: Signaler la Page d’historique (Gestionnaire de rapports) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 0b0841e031ee1a98f4f678406f790996a709e90f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66104478"
---
# <a name="report-history-page-report-manager"></a>Page Historique de rapport (Gestionnaire de rapports)

La page Historique de rapport vous permet d'afficher des instantanés de rapport qui sont générés et stockés dans le temps. Selon les options définies sur le serveur de rapports, l'historique de rapport peut contenir uniquement les instantanés les plus récents.  
  

Un historique de rapport est toujours affiché dans le contexte du rapport dont il est issu. Vous ne pouvez pas afficher l'historique de tous les rapports sur un serveur de rapports dans un seul emplacement.  
  
Pour générer un historique de rapport, le rapport doit pouvoir s'exécuter sans assistance (c'est-à-dire qu'il doit utiliser les informations d'identification stockées ; les rapports paramétrables doivent contenir des valeurs de paramètres par défaut pour tous les paramètres). Un historique de rapport peut être généré manuellement ou sous forme d'opération planifiée. Les propriétés d'historique du rapport déterminent les modes de création de l'historique de rapport.  
  
Vous pouvez cliquer sur un instantané d'historique de rapport pour l'afficher. Les instantanés qui apparaissent dans l'historique de rapport ne sont différenciés que par la date et l'heure de leur création. Il n'y a aucun moyen de déterminer si un instantané a été généré par une opération manuelle ou planifiée.  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
### <a name="to-open-the-report-history-page"></a>Pour ouvrir la page Historique de rapport  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez consulter des instantanés de rapport.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Afficher l'historique du rapport**.  
  
## <a name="options"></a>Options  
 **Supprimer**  
 Cliquez pour supprimer un ou plusieurs instantanés. Avant de cliquer sur **Supprimer**, activez la case à cocher en regard de l'instantané à supprimer.  
  
 **Nouvel instantané**  
 Cliquez pour ajouter un instantané à un historique de rapport. Ce bouton est disponible lorsque vous choisissez l'option **Autoriser la création manuelle de l'historique** dans la page de propriétés de l'historique du rapport.  
  
 **Dernière exécution**  
 Affiche la date et l'heure de création de l'instantané. Cliquez sur une description pour afficher un instantané spécifique.  
  
 **Taille**  
 Affiche la taille de la définition de rapport et des données contenues dans le rapport. Cette valeur indique la quantité d'espace utilisée par la définition de rapport et les données dans la base de données du serveur de rapports. La taille du rapport rendu, qui comprend la mise en forme, est plus volumineuse. La taille totale, indiquée entre parenthèses, correspond à la taille de tous les instantanés de l'historique de rapport du rapport actif.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher ou supprimer l’historique de rapport &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md)   
 [Ajout d’un instantané à un historique de rapport &#40;Gestionnaire de rapports&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Page Propriétés générales, Rapports &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)   
 [F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Page de propriétés Options d’instantanés &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)