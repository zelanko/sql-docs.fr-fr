---
title: Colonnes de dimensions à variation lente (Assistant Dimension à variation lente) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 945a9b23fd9f5850489184d89d99d4ae24350652
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71291212"
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a>Colonnes de dimensions à variation lente (Assistant Dimension à variation lente)

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Utilisez la boîte de dialogue **Colonnes de dimensions à variation lente** pour sélectionner un type de modification pour chaque colonne de dimension à variation lente.  
  
 Pour en savoir plus sur cet Assistant, consultez [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonnes de dimension**  
 Sélectionnez une colonne de dimension dans la liste.  
  
 **Modifier de type**  
 Sélectionnez un **Attribut fixe**ou sélectionnez l’un des deux types d’attributs variables. Utilisez **Attribut fixe** lorsque la valeur d'une colonne ne doit pas changer ; [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] traite alors les modifications comme des erreurs. Utilisez **Modification d'attribut** pour remplacer les valeurs existantes par des valeurs modifiées. Utilisez **Attribut d'historique** pour enregistrer les valeurs modifiées dans de nouveaux enregistrements tout en marquant comme obsolètes les anciens enregistrements.  
  
 **Supprimer**  
 Sélectionnez une colonne de dimension et supprimez-la de la liste des colonnes mappées en cliquant sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les sorties à l'aide de l'Assistant Dimension à variation lente](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
