---
title: Afficher l’historique (PowerPivot pour SharePoint) d’actualisation des données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- data refresh history [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 4c8d8aa8-794d-4f72-ace3-78d0e688e1a5
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5ecca7d87492645502e122497cc66eb54f083097
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267585"
---
# <a name="view-data-refresh-history-powerpivot-for-sharepoint"></a>Afficher l'historique d'actualisation des données (PowerPivot pour SharePoint)
  L'historique d'actualisation des données est un enregistrement de toute l'activité d'actualisation de données PowerPivot dans un classeur Excel. Dans une batterie de serveurs SharePoint, les opérations d'actualisation des données sont effectuées sur une instance du serveur Analysis Services, selon une planification que vous fournissez. Par défaut, l'historique d'actualisation des données est conservé pendant un an. Toutefois, un administrateur de batterie de serveurs peut, pour l'historique de l'utilisation et des événements, spécifier une stratégie de rétention différente qui détermine la durée de conservation des enregistrements d'actualisation des données.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010  
  
 **Dans cette rubrique :**  
  
 [Conditions préalables](#prereq)  
  
 [Afficher l'historique d'actualisation des données d'un classeur](#viewhistory)  
  
 [Afficher l'historique d'actualisation des données de tous les classeurs](#viewITOps)  
  
 [Utiliser les informations de l'historique](#pageelements)  
  
##  <a name="prereq"></a> Conditions préalables  
 Pour afficher l'historique d'actualisation des données, vous devez disposer d'autorisations Collaboration ou supérieures.  
  
 Vous avez avoir activé et planifié l'actualisation des données sur un classeur qui contient des données PowerPivot. Si vous n'avez pas planifié l'actualisation des données, la page de définition de la planification s'affichera au lieu des informations d'historique.  
  
##  <a name="viewhistory"></a> Afficher l'historique d'actualisation des données d'un classeur  
  
1.  Sur un site SharePoint, ouvrez la bibliothèque où figure un classeur Excel qui contient des données PowerPivot.  
  
     Aucun indicateur visuel ne permet d'identifier les classeurs d'une bibliothèque SharePoint qui contiennent des données PowerPivot. Vous devez savoir à l'avance quel classeur contient des données PowerPivot actualisables.  
  
2.  Sélectionnez le classeur, puis cliquez sur la flèche orientée vers le bas qui s'affiche à droite.  
  
3.  Sélectionnez **Gérer l'actualisation des données PowerPivot**.  
  
 La page d'historique s'affiche. Elle contient des informations complètes sur l'ensemble de l'activité d'actualisation des données PowerPivot du classeur Excel actif.  
  
##  <a name="viewITOps"></a> Afficher l'historique d'actualisation des données de tous les classeurs  
 Les administrateurs de batteries et d'applications de service peuvent, en utilisant le tableau de bord de gestion PowerPivot de l'Administration centrale, obtenir une vue complète de l'historique et de l'état d'actualisation des données de tous les classeurs PowerPivot. Pour plus d’informations, consultez [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
##  <a name="pageelements"></a> Utiliser les informations de l'historique  
 La page d'historique d'actualisation des données fournit des informations détaillées sur chaque opération d'actualisation. Vous pouvez utiliser les informations de cette page afin de vérifier si l'actualisation a eu lieu ou de déterminer la raison pour laquelle elle a échoué.  
  
|Élément|Description|  
|----------|-----------------|  
|Nom   |Spécifie le nom de fichier du classeur Excel qui contient les données PowerPivot.|  
|État actuel|Les valeurs possibles sont **Planifiée**, **Actualisation**, **Opération réussie**ou **Échec**.<br /><br /> **Planifiée** apparaît la première fois que vous créez la planification. Une fois la première actualisation des données effectuée, ce message d'état ne s'affiche plus.<br /><br /> **Actualisation** indique que l'actualisation des données est en cours. Une requête figure dans la file d'attente des processus ou s'exécute activement sur le serveur.<br /><br /> **Opération réussie** indique que la dernière opération d'actualisation des données est terminée et que le classeur mis à jour est archivé dans la bibliothèque SharePoint.<br /><br /> **Échec** indique que la dernière opération d'actualisation des données n'a pas réussi. Les données actualisées n'ont pas été enregistrées. Le classeur contient les mêmes données qu'avant l'opération d'actualisation des données.|  
|Dernière actualisation réussie|Spécifie la date de dernière exécution réussie de l'actualisation des données.|  
|Prochaine actualisation planifiée|Spécifie la date prévue pour la prochaine actualisation des données.<br /><br /> Le lien **Configurer la planification** vous dirige vers la page de définition de la planification. Si vous disposez d'autorisations Collaboration sur le classeur, vous pouvez cliquer sur ce lien pour afficher et modifier les informations de planification qui contrôlent l'actualisation sans assistance des données PowerPivot du classeur.|  
|Démarré|Dans la section des détails de l'historique, **Démarré** indique l'heure réelle du traitement. Celle-ci peut différer de celle que vous avez planifiée. En effet, le traitement commence lorsque le serveur dispose de suffisamment de mémoire. Si le serveur est très occupé, le traitement peut commencer plusieurs heures après l'heure de début que vous avez spécifiée.|  
|Terminé|Dans la section des détails de l'historique, **Terminé** indique quand l'opération d'actualisation de données s'est terminée. Les date et heure indiquent quand le classeur a été réarchivé dans la bibliothèque.<br /><br /> Si l'actualisation des données échoue, un ou plusieurs messages d'erreur expliquent la cause de l'échec. Vous pouvez développer chaque enregistrement pour consulter l'état détaillé. Chaque source de données apparaît individuellement, avec les messages de réussite ou d'échec indiquant le cas échéant la raison pour laquelle l'actualisation n'a pas été effectuée.|  
|Time|Indique le temps écoulé entre l'heure de début et l'heure de fin de l'opération d'actualisation.|  
|État|Fournit un enregistrement d'historique indiquant si une opération d'actualisation a réussi ou échoué.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la collecte de données d’utilisation pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)   
 [Planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)   
 [Actualisation des données PowerPivot](power-pivot-data-refresh.md)  
  
  
