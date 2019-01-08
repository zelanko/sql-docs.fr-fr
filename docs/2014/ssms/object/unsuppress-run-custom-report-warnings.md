---
title: Annuler la suppression des avertissements d’exécution de rapports personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ed653b16fe524f364ba89f13e00715b725080033
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52772771"
---
# <a name="unsuppress-run-custom-report-warnings"></a>Annuler la suppression des avertissements d'exécution de rapports personnalisés
  Il existe deux boîtes de dialogue d'avertissement pour les rapports personnalisés. Cette rubrique décrit comment annuler la suppression de l'affichage de ces zones dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Par défaut, la boîte de dialogue **Exécuter le rapport personnalisé** apparaît avant l’exécution d’un rapport personnalisé. Elle n’apparaît plus si vous cochez la case **Ne plus afficher ce message** . De même, toujours par défaut, la boîte de dialogue **Exécuter le rapport personnalisé** s’affiche quand vous ouvrez un rapport personnalisé, puis cliquez sur un lien pour en ouvrir un autre. Cette boîte de dialogue affiche le chemin du fichier de rapport d'extraction personnalisé. Elle n’apparaît plus si vous cochez la case **Ne plus afficher ce message** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>Pour annuler la suppression de la boîte de dialogue d'avertissement principale des rapports personnalisés  
  
1.  Se connecter à \< *Server*>\\<*partage*>|\<*lecteur*> \ Documents and Settings\\< UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.  
  
2.  Avec le bouton droit `reports.xml`, puis cliquez sur **modifier**.  
  
3.  Modification**\<SuppressWarning > true\</SuppressWarning > à \<SuppressWarning > false\</SuppressWarning >**.  
  
4.  Redémarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>Pour annuler la suppression de la boîte de dialogue d'avertissement principale des rapports d'extraction personnalisés  
  
1.  Se connecter à \< *Server*>\\<*partage*>|\<*lecteur*> \ Documents and Settings\\< UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.  
  
2.  Avec le bouton droit `reports.xml`, puis cliquez sur **modifier**.  
  
3.  Modification  **\<SuppressDrillthroughWarning > true\</SuppressDrillthroughWarning > à \<SuppressDrillthroughWarning > false\</SuppressDrillthroughWarning >**.  
  
4.  Redémarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Rapports personnalisés dans Management Studio](custom-reports-in-management-studio.md)   
 [Ajouter un rapport personnalisé à Management Studio](add-a-custom-report-to-management-studio.md)   
 [Utiliser des rapports personnalisés avec les propriétés de nœud de l’Explorateur d’objets](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
