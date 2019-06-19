---
title: Administrateurs (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 146834648164e49632a62352d684a6da66a09e12
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65480017"
---
# <a name="administrators-master-data-services"></a>Administrateurs (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], il existe deux types d'administrateurs : les administrateurs de modèle et l'administrateur système [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
## <a name="model-administrators"></a>Administrateurs de modèle  
 Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], un administrateur de modèle est un utilisateur qui a **mise à jour** autorisation affectée à l’objet de modèle de niveau supérieur sur la **objets de modèle** onglet et aucun autre des autorisations affectées.  
  
-   Si l'utilisateur a accès à la zone fonctionnelle **Explorateur** , il peut ajouter, supprimer et mettre à jour toutes les données de référence dans cette zone.  
  
-   Si l'utilisateur a accès à d'autres zones fonctionnelles, il peut effectuer toutes les tâches d'administration disponibles dans la zone fonctionnelle.  
  
 Chaque modèle peut avoir plusieurs administrateurs. Chaque utilisateur peut être un administrateur de modèle pour un, plusieurs ou tous les modèles du déploiement [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Un utilisateur peut être configuré en tant qu'administrateur de modèle dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ou par programme. Pour plus d’informations, consultez [Créer un administrateur de modèle &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md).  
  
## <a name="master-data-services-system-administrator"></a>Administrateur système Master Data Services  
 Il n'existe qu'un seul administrateur système [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. L’administrateur système est l’utilisateur spécifié pour le **compte d’administrateur** lorsque vous créez le [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données.  
  
 L'administrateur système [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] :  
  
-   Accès automatique à toutes les zones fonctionnelles.  
  
-   Peut ajouter, supprimer et mettre à jour toutes les données de référence pour tous les modèles dans le **Explorer** zone fonctionnelle.  
  
 Vous pouvez modifier l'utilisateur affecté en tant qu'administrateur système. Pour plus d’informations, consultez [modifier le compte d’administrateur système &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
## <a name="comparing-administrator-types"></a>Comparaison des types d'administrateur  
  
|Type d'administrateur|Description|  
|------------------------|-----------------|  
|Administrateur système [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Les autorisations affectées dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] n’ont aucun effet sur l’accès de l’administrateur.<br /><br /> A automatiquement **mise à jour** autorisation à tous les modèles.<br /><br /> Accès automatique à toutes les zones fonctionnelles.<br /><br /> Dans mdm.tblUser, la valeur dans le **ID** colonne est **1**.|  
|Administrateur de modèle|Les autorisations affectées dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] déterminent si l'utilisateur est ou non un administrateur de modèle.<br /><br /> Peut être administrateur de modèle en fonction des autorisations qui lui sont affectées explicitement ou de celles héritées d'un groupe.<br /><br /> Est un administrateur uniquement pour les modèles qui ont **mise à jour** autorisation affectée à l’objet de modèle de niveau supérieur et aucune autre autorisation.<br /><br /> Accès uniquement aux zones fonctionnelles auxquelles l'accès est accordé.<br /><br /> Dans mdm.tblUser, la valeur dans le **ID** colonne n’est pas **1**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un administrateur de modèle &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md)   
 [Modifier le compte d’administrateur système &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)   
 [Créer une base de données Master Data Services](install-windows/create-a-master-data-services-database.md)   
 [Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)  
  
  
