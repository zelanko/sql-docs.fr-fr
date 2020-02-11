---
title: Barre oblique étoile (commentaire) (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5d0b929ba60915f116d9ff6843b4f20b3105a7ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942846"
---
# <a name="slash-star-comment-dmx"></a>Barre oblique étoile (commentaire) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indique une chaîne de texte que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne doit pas exécuter. Le serveur n’évalue pas le texte entre les caractères de commentaire/ \** et/. Vous pouvez imbriquer les commentaires dans une instruction DMX (Data Mining Extensions), les ajouter à la fin d'une ligne de code ou les insérer sur une ligne séparée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
/* Comment_Text */  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Comment_Text*  
 Chaîne contenant le texte du commentaire.  
  
## <a name="remarks"></a>Notes  
 Les commentaires de plusieurs lignes doivent être signalés par /* et \*/.  
  
 Il n'y a pas de longueur maximale pour les commentaires.  
  
 Pour plus d’informations sur l’utilisation de différents types de commentaires dans DMX, consultez la page [commentaires &#40;&#41;DMX ](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Double barre oblique &#40;commentaire&#41; &#40;&#41;DMX](../dmx/double-slash-comment-dmx.md)   
 [--&#40;commentaire&#41; &#40;synthèse&#41; DMX](../dmx/comment-dmx-summary.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs &#40;&#41;DMX](../dmx/operators-dmx.md)  
  
  
