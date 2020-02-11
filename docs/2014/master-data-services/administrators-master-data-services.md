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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65480017"
---
# <a name="administrators-master-data-services"></a>Administrateurs (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], il existe deux types d'administrateurs : les administrateurs de modèle et l'administrateur système [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
## <a name="model-administrators"></a>Administrateurs de modèle  
 Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], un administrateur de modèle est un utilisateur qui dispose de l’autorisation **mettre à jour** affectée à l’objet modèle de niveau supérieur sous l’onglet **objets de modèle** et aucune autre autorisation n’est affectée.  
  
-   Si l'utilisateur a accès à la zone fonctionnelle **Explorateur** , il peut ajouter, supprimer et mettre à jour toutes les données de référence dans cette zone.  
  
-   Si l'utilisateur a accès à d'autres zones fonctionnelles, il peut effectuer toutes les tâches d'administration disponibles dans la zone fonctionnelle.  
  
 Chaque modèle peut avoir plusieurs administrateurs. Chaque utilisateur peut être un administrateur de modèle pour un, plusieurs ou tous les modèles du déploiement [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Un utilisateur peut être configuré en tant qu'administrateur de modèle dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ou par programme. Pour plus d’informations, consultez [Créer un administrateur de modèle &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md).  
  
## <a name="master-data-services-system-administrator"></a>Administrateur système Master Data Services  
 Il n'existe qu'un seul administrateur système [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. L’administrateur système est l’utilisateur spécifié pour le **compte administrateur** lorsque vous créez la [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données.  
  
 L'administrateur système [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] :  
  
-   Accès automatique à toutes les zones fonctionnelles.  
  
-   Permet d’ajouter, de supprimer et de mettre à jour toutes les données de référence de tous les modèles dans la zone fonctionnelle **Explorateur** .  
  
 Vous pouvez modifier l'utilisateur affecté en tant qu'administrateur système. Pour plus d’informations, consultez [modifier le compte d’administrateur système &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
## <a name="comparing-administrator-types"></a>Comparaison des types d'administrateur  
  
|Type d'administrateur|Description|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]administrateur système|Les autorisations affectées dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] n’ont aucun effet sur l’accès de l’administrateur.<br /><br /> A automatiquement l’autorisation **mettre à jour** sur tous les modèles.<br /><br /> Accès automatique à toutes les zones fonctionnelles.<br /><br /> Dans MDM. tblUser, la valeur dans la colonne **ID** est **1**.|  
|Administrateur de modèle|Les autorisations affectées dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] déterminent si l'utilisateur est ou non un administrateur de modèle.<br /><br /> Peut être administrateur de modèle en fonction des autorisations qui lui sont affectées explicitement ou de celles héritées d'un groupe.<br /><br /> Est un administrateur uniquement pour les modèles qui ont l’autorisation de **mise à jour** affectée à l’objet de modèle de niveau supérieur et aucune autre autorisation.<br /><br /> Accès uniquement aux zones fonctionnelles auxquelles l'accès est accordé.<br /><br /> Dans MDM. tblUser, la valeur dans la colonne **ID** n’est pas **1**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un administrateur de modèle &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md)   
 [Modifier le compte d’administrateur système &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)   
 [Créer une base de données Master Data Services](install-windows/create-a-master-data-services-database.md)   
 [&#40;de notifications Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)  
  
  
