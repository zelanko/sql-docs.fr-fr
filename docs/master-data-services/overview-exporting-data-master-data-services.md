---
title: "Vue d’ensemble : exportation de données (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
caps.latest.revision: 12
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 40f4ec6f9d1e30676dfba32288384a6f0b6fcc6e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---
# <a name="overview-exporting-data-master-data-services"></a>Vue d’ensemble : exportation de données [Master Data Services]
  Cet article présente les types de formats de vue d’abonnement et indique comment déterminer quand les vues doivent être modifiées en raison de modifications apportées aux objets de modèle.  
  
 Vous créez une vue d’abonnement pour exporter les données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] vers un système d’abonnement tel que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Vous utilisez le système d’abonnement pour afficher les données dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  Pour plus d’informations sur la création de la vue d’abonnement, consultez [Créer une vue d’abonnement pour exporter des données &#40;Master Data Services&#41;](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)  
  
 Pour plus d’informations sur les vues, consultez [Vues](../relational-databases/views/views.md).  
  
## <a name="subscription-view-formats"></a>Formats de vue d'abonnement  
 Lorsque vous créez une vue dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], vous devez choisir un format dans un ensemble de formats de vue standard fournis par [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Vous pouvez utiliser ces formats pour créer des vues qui affichent :  
  
-   Tous les membres feuille et leurs attributs.  
  
-   Tous les membres consolidés et leurs attributs.  
  
-   Toutes les collections et leurs attributs.  
  
-   Les membres qui ont été ajoutés explicitement à une collection.  
  
-   Les membres dans une hiérarchie dérivée, dans un format parent-enfant ou de niveau.  
  
-   Les membres dans toutes les hiérarchies explicites d'une entité, dans un format parent-enfant ou de niveau.  
  
## <a name="subscription-views-can-become-out-of-date"></a>Les vues d'abonnement peuvent devenir obsolètes  
 Une fois que vous avez créé une vue d'abonnement pour une entité ou une hiérarchie, les modifications apportées aux objets de modèle associés ne sont pas automatiquement répercutées dans la vue. Vous devrez peut-être régénérer une vue d'abonnement dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] pour répercuter les modifications dans les objets de modèle. La colonne **Modifié** dans la page **Exporter** est mise à jour avec la valeur **True** lorsque les objets modèle changent. **True** indique que vous devez modifier la vue d'abonnement et l'enregistrer pour régénérer la vue.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créer une vue d'abonnement de vos données de référence.|[Créer une vue d’abonnement pour exporter des données &#40;Master Data Services&#41;](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)|  
|Supprimer une vue d'abonnement existante.|[Supprimer une vue d’abonnement &#40;Master Data Services&#41;](../master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu connexe  
  
-   [Formats de vue d’abonnement &#40;Master Data Services&#41;](../master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [Vues](../relational-databases/views/views.md)  
  
  
