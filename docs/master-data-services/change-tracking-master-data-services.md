---
title: Suivi des modifications (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 0def93a0f88d19ba894508d4a5d39de59dbd7a28
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---
# <a name="change-tracking-master-data-services"></a>Suivi des modifications (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez utiliser des groupes de suivi des modifications pour agir lorsqu'une valeur d'attribut change. Utilisez le suivi des modifications lorsque vous ne savez pas ce que sera la nouvelle valeur, mais souhaitez à la place savoir si une modification est intervenue.  
  
## <a name="configuring-change-tracking"></a>Configuration du suivi des modifications  
 Pour configurer le suivi des modifications, vous ajoutez un attribut à un groupe de suivi des modifications. Le groupe peut contenir un ou plusieurs attributs. Ensuite, vous créez une règle d'entreprise pour définir l'action effectuée lorsque l'un des attributs du groupe change.  
  
> [!NOTE]  
>  Les règles d'entreprise de suivi des modifications considèrent les données (importées) mises en lots à modifier.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Ajoutez des attributs à un groupe de suivi des modifications.|[Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Créez une règle d'entreprise qui initie les actions en fonction des modifications apportées aux attributs.|[Initier des actions en fonction de modifications de valeurs d’attribut &#40;Master Data Services&#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu connexe  
  
-   [Validation &#40;Master Data Services&#41;](../master-data-services/validation-master-data-services.md)  
  
-   [Règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Attributs &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  

