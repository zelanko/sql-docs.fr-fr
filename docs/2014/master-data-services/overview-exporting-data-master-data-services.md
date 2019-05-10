---
title: exportation de données (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: f92a74caa74c5cf15e917cd6c15aef9506a60180
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65482838"
---
# <a name="exporting-data-master-data-services"></a>Exportation de données (Master Data Services)
  Vous pouvez exporter des données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] vers des systèmes d'abonnement en créant des vues d'abonnement. Tout système d'abonnement peut ensuite afficher les données publiées dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations sur les vues, consultez [Vues](../relational-databases/views/views.md).  
  
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
|Créer une vue d'abonnement de vos données de référence.|[Créer une vue d’abonnement &#40;Master Data Services&#41;](create-a-subscription-view-to-export-data-master-data-services.md)|  
|Supprimer une vue d'abonnement existante.|[Supprimer une vue d’abonnement &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Formats de vue d’abonnement &#40;Master Data Services&#41;](../../2014/master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [Vues](../relational-databases/views/views.md)  
  
  
