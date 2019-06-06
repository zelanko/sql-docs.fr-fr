---
title: HelpContext, HelpFile propriétés | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetHelpContext
- Error::GetHelpFile
- Error::get_HelpFile
- Error::get_HelpContext
- Error::HelpContext
- Error::HelpFile
helpviewer_keywords:
- HelpContext property [ADO]
- HelpFile property [ADO]
ms.assetid: 2b9ef441-993c-44d4-8f87-fac0979dac1d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c9c980e293b06e7fa9642ace7d425b7ffd3c0197
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694805"
---
# <a name="helpcontext-helpfile-properties"></a>HelpContext, HelpFile, propriétés
Indique le fichier d’aide et de la rubrique associée à un [erreur](../../../ado/reference/ado-api/error-object.md) objet.  
  
## <a name="return-values"></a>Valeurs de retour  
  
-   **HelpContextID** retourne un ID de contexte, comme un **Long** valeur, pour une rubrique dans un fichier d’aide.  
  
-   **HelpFile** retourne un **chaîne** valeur qui correspond à un chemin d’accès entièrement résolu vers un fichier d’aide.  
  
## <a name="remarks"></a>Notes  
 Si un fichier d’aide est spécifié dans le **HelpFile** propriété, le **HelpContext** propriété est utilisée pour afficher automatiquement la rubrique d’aide qu’il identifie. Si aucune rubrique d’aide pertinentes n’est disponible, le **HelpContext** propriété retourne la valeur zéro et le **HelpFile** propriété retourne une chaîne de longueur nulle (« »).  
  
## <a name="applies-to"></a>S'applique à  
 [Error, objet](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Propriété Description](../../../ado/reference/ado-api/description-property.md)   
 [Number, propriété (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source, propriété (objet Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
