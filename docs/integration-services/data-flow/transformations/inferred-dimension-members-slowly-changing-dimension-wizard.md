---
title: "Les membres de Dimension (Assistant Dimension à variation lente) inférés | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b99116c19f5ec69fcf382069a1ca3c76ee65b3d6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>Membres de la dimension inférés (Assistant Dimension à variation lente)
  La boîte de dialogue **Membres de la dimension inférés** vous permet de spécifier les options d'utilisation des membres inférés. Des membres inférés existent lorsqu'une table de faits fait référence à des membres de la dimension qui ne sont pas encore chargés. Lorsque les données du membre inféré sont chargées, vous pouvez mettre à jour l'enregistrement existant au lieu d'en créer un.  
  
 Pour en savoir plus sur cet Assistant, consultez [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Options  
 **Activer la prise en charge des membres inférés**  
 Si vous décidez d'activer les membres inférés, vous devez sélectionner l'une des deux options ci-dessous.  
  
 **Toutes les colonnes dont le type est modifié sont NULL**  
 Indique s'il convient d'entrer des valeurs NULL dans toutes les colonnes avec un type de modification dans le nouvel enregistrement de membre inféré.  
  
 **Utiliser une colonne de valeurs booléennes pour indiquer si l'enregistrement actif est un membre inféré**  
 Indique s'il convient d'utiliser une colonne de valeurs booléennes existante pour indiquer si l'enregistrement en cours est un membre inféré.  
  
 **Indicateur de membre inféré**  
 Si vous avez choisi d'utiliser une colonne de valeurs booléennes pour indiquer les membres inférés comme décrit ci-dessus, sélectionnez la colonne dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les sorties à l’aide de l’Assistant Dimension à variation lente](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  

