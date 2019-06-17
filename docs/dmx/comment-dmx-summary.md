---
title: --(Commentaire) (DMX) Résumé | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: be2fc3e82e1da18a12af4bc4756811225e85a280
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62707262"
---
# <a name="---comment-dmx-summary"></a>--(Commentaire) (DMX) Résumé
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indique une chaîne de texte que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne doit pas exécuter. Vous pouvez imbriquer les commentaires dans une instruction DMX (Data Mining Extensions), les ajouter à la fin d'une ligne de code ou les insérer sur une ligne séparée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Paramètres  
 *Comment_Text*  
 Chaîne contenant le texte du commentaire.  
  
## <a name="remarks"></a>Notes  
 Utilisez cet opérateur pour un commentaire d'une seule ligne ou imbriqué. Les commentaires sont insérés à l’aide de--sont délimités par le caractère de saut de ligne.  
  
 Il n'y a pas de longueur maximale pour les commentaires.  
  
 Pour plus d’informations sur l’utilisation de différents types de commentaires dans DMX, consultez [commentaires &#40;DMX&#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Barre oblique étoile &#40;commentaire&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)   
 [Double barre oblique &#40;commentaire&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operators &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
