---
title: Suivi des modifications (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: fbaf6c28b551b65473784e231716c58f974e7962
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52395362"
---
# <a name="change-tracking-master-data-services"></a>Suivi des modifications (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez utiliser des groupes de suivi des modifications pour agir lorsqu'une valeur d'attribut change. Utilisez le suivi des modifications quand vous ne savez pas ce que sera la nouvelle valeur, mais souhaitez à la place savoir si une modification est intervenue.  
  
## <a name="configuring-change-tracking"></a>Configuration du suivi des modifications  
 Pour configurer le suivi des modifications, vous ajoutez un attribut à un groupe de suivi des modifications. Le groupe peut contenir un ou plusieurs attributs. Ensuite, vous créez une règle d'entreprise pour définir l'action effectuée lorsque l'un des attributs du groupe change.  
  
> [!NOTE]  
>  Les règles d'entreprise de suivi des modifications considèrent les données (importées) mises en lots à modifier.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Ajoutez des attributs à un groupe de suivi des modifications.|[Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Créez une règle d'entreprise qui initie les actions en fonction des modifications apportées aux attributs.|[Initier des actions en fonction de modifications de valeurs d’attribut &#40;Master Data Services&#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Validation &#40;Master Data Services&#41;](../master-data-services/validation-master-data-services.md)  
  
-   [Règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Attributs &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  
