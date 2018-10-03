---
title: Options des attributs fixes et variables (Assistant Dimension à variation lente) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 87341f7ae8c8d4d27042473a78d56c42bdf9247d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053999"
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a>Options des attributs fixes et variables (Assistant Dimension à variation lente)
  Utilisez la boîte de dialogue **Options des attributs fixes et variables** pour spécifier comment répondre aux modifications apportées aux attributs fixes et variables.  
  
 Pour en savoir plus sur cet Assistant, consultez [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Options  
 **Attributs fixes**  
 Pour les attributs fixes, indiquez si la tâche doit échouer lorsqu'un changement est détecté dans un attribut fixe.  
  
 **Modification des attributs**  
 Pour les attributs variables, spécifiez si la tâche doit modifier les enregistrements obsolètes ou expirés, en plus des enregistrements actuels, lorsqu'un changement est détecté dans un attribut variable. Un enregistrement expiré est un enregistrement qui a été remplacé par un enregistrement plus récent par une modification d'un attribut d'historique (modification de Type 2). La sélection de cette option peut imposer des exigences de traitement supplémentaires sur un objet multidimensionnel construit sur l'entrepôt de données relationnelles.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les sorties à l'aide de l'Assistant Dimension à variation lente](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
