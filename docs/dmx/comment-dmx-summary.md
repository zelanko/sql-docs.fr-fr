---
description: --(Commentaire) résumé (DMX)
title: --(Commentaire) résumé (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 260a3f5c8a6d1badb90349396db6f2b716380aa7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431091"
---
# <a name="---comment-dmx-summary"></a>--(Commentaire) résumé (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Indique une chaîne de texte que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne doit pas exécuter. Vous pouvez imbriquer les commentaires dans une instruction DMX (Data Mining Extensions), les ajouter à la fin d'une ligne de code ou les insérer sur une ligne séparée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Paramètres  
 *Comment_Text*  
 Chaîne contenant le texte du commentaire.  
  
## <a name="remarks"></a>Notes  
 Utilisez cet opérateur pour un commentaire d'une seule ligne ou imbriqué. Les commentaires insérés à l’aide de--sont délimités par le caractère de saut de ligne.  
  
 Il n'y a pas de longueur maximale pour les commentaires.  
  
 Pour plus d’informations sur l’utilisation de différents types de commentaires dans DMX, consultez la page [commentaires &#40;&#41;DMX ](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Barre oblique &#40;commentaire&#41; &#40;&#41;DMX ](../dmx/slash-star-comment-dmx.md)   
 [Double barre oblique &#40;commentaire&#41; &#40;&#41;DMX ](../dmx/double-slash-comment-dmx.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs &#40;&#41;DMX ](../dmx/operators-dmx.md)  
  
  
