---
title: Membres de la dimension inférés (Assistant Dimension à variation lente) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2c505bf78acc4293e68f0f2222dd9fbf7f9e01e2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62900135"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>Membres de la dimension inférés (Assistant Dimension à variation lente)
  La boîte de dialogue **Membres de la dimension inférés** vous permet de spécifier les options d'utilisation des membres inférés. Des membres inférés existent lorsqu'une table de faits fait référence à des membres de la dimension qui ne sont pas encore chargés. Lorsque les données du membre inféré sont chargées, vous pouvez mettre à jour l'enregistrement existant au lieu d'en créer un.  
  
 Pour en savoir plus sur cet Assistant, consultez [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
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
 [Configurer les sorties à l'aide de l'Assistant Dimension à variation lente](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
