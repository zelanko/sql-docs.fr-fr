---
description: Moniteur d'activité des travaux (Paramètres du filtre)
title: Moniteur d’activité des travaux (Paramètres du filtre) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.jobactivitymon.filter.f1
ms.assetid: 89cb0055-5262-447f-8464-7203d4caba78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f7533366a28517fcc2fdb8ca5c2e4ad0c0dd01c5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424051"
---
# <a name="job-activity-monitor-filter-settings"></a>Moniteur d'activité des travaux (Paramètres du filtre)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette page vous permet de réduire le nombre de lignes visibles dans le Moniteur d'activité des travaux. Entrez des critères dans une ou plusieurs des zones disponibles, pour afficher uniquement les lignes qui correspondent aux valeurs spécifiées. Certaines zones, telles que **État** ou **Type de blocage** , proposent un nombre défini de valeurs possibles, fournies dans une liste déroulante. D’autres, telles que **Application** , permettent d’entrer n’importe quelle valeur et autant de valeurs que vous le souhaitez, sous la forme d’une liste dont les valeurs sont séparées par une virgule. Les icônes de la barre d'outils vous permettent de trier les zones disponibles par catégorie ou par ordre alphabétique. Cliquez sur des critères pour afficher une brève description de chacun d'eux.  
  
 Pour filtrer le Moniteur d’activité des travaux, fournissez autant de critères de filtre que vous le souhaitez, cliquez sur **Appliquer le filtre**, puis sur **OK**.  
  
## <a name="all-jobs"></a>Tous les travaux  
 Ce groupe de critères de filtre est disponible lors du filtrage du Moniteur d'activité des travaux.  
  
 **Nom**  
 Permet de filtrer les travaux par leur nom.  
  
 **Prochaine exécution**  
 Permet de filtrer par la date de prochaine exécution planifiée.  
  
 **Exécutable**  
 Permet d'afficher les travaux qui peuvent être exécutés ou les travaux qui ne le peuvent pas. Sélectionnez **Oui** pour visualiser uniquement les travaux exécutables, **Non** pour visualiser uniquement les travaux non exécutables ou **Tous** pour visualiser les deux types de travaux.  
  
 **Dernière exécution**  
 Permet de filtrer par la date de dernière exécution.  
  
 **Résultats de la dernière exécution**  
 Permet de filtrer les travaux par l'état de leur dernière exécution.  
  
 **Activé**  
 Permet d'afficher uniquement les travaux activés ou non activés  
  
 **Catégorie**  
 Permet de filtrer les travaux par catégorie.  
  
 **Planifié**  
 Permet d'afficher tous les travaux avec planification ou sans planification.  
  
 **État**  
 Permet de filtrer les travaux par leur état.  
  
## <a name="description-area"></a>Zone Description  
 **Zone de description**  
 Cette zone sans nom fournit une brève description des critères lors de leur sélection.  
  
 **Appliquer le filtre**  
 Pour appliquer le filtre, cliquez sur **Appliquer le filtre**, puis sur **OK**. Pour conserver les paramètres du filtre dans la boîte de dialogue **Paramètres du filtre**, sans les appliquer, désactivez l’option **Appliquer le filtre**, puis cliquez sur **OK** pour afficher toutes les lignes.  
  
 **Clear**  
 Rétablit les paramètres par défaut du filtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller l'activité des travaux](../../ssms/agent/monitor-job-activity.md)  
  
  
