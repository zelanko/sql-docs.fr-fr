---
title: Suivi des modifications (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7b4b7d9d9d153456ca471196c6480465d057e412
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483519"
---
# <a name="change-tracking-master-data-services"></a>Suivi des modifications (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez utiliser des groupes de suivi des modifications pour agir lorsqu'une valeur d'attribut change. Utilisez le suivi des modifications quand vous ne savez pas ce que sera la nouvelle valeur, mais souhaitez à la place savoir si une modification est intervenue.  
  
## <a name="configuring-change-tracking"></a>Configuration du suivi des modifications  
 Pour configurer le suivi des modifications, vous ajoutez un attribut à un groupe de suivi des modifications. Le groupe peut contenir un ou plusieurs attributs. Ensuite, vous créez une règle d'entreprise pour définir l'action effectuée lorsque l'un des attributs du groupe change.  
  
> [!NOTE]  
>  Les règles d'entreprise de suivi des modifications considèrent les données (importées) mises en lots à modifier.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Ajoutez des attributs à un groupe de suivi des modifications.|[Ajouter des attributs à un groupe de Change Tracking &#40;Master Data Services&#41;](add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Créez une règle d'entreprise qui initie les actions en fonction des modifications apportées aux attributs.|[Initier des actions en fonction des modifications de valeur d’attribut &#40;Master Data Services&#41;](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [&#40;de validation Master Data Services&#41;](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [&#40;des règles d’entreprise Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
