---
title: Propriété Description | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Description
- Error::GetDescription
- Error::get_Description
helpviewer_keywords:
- Description property
ms.assetid: 4b5d6790-6c29-42aa-bf78-d9cfb8ad7965
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbf735e766e6ff4e058aee7c8c7f1ee9682b0339
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="description-property"></a>Description (propriété)
Décrit un [erreur](../../../ado/reference/ado-api/error-object.md) objet.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un **chaîne** valeur qui contient une description de l’erreur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **Description** propriété pour obtenir une brève description de l’erreur. Afficher cette propriété pour avertir l’utilisateur d’une erreur que vous ne pouvez pas ou ne souhaitez pas gérer. La chaîne proviennent d’ADO ou d’un fournisseur.  
  
 Les fournisseurs sont chargés de transmettre le texte d’erreur spécifique à ADO. ADO ajoute un [erreur](../../../ado/reference/ado-api/error-object.md) de l’objet à la **erreurs** collection pour chaque fournisseur d’erreur ou avertissement reçoit. Énumérer les **erreurs** collection pour les erreurs transmises par le fournisseur de trace.  
  
## <a name="applies-to"></a>S'applique à  
 [Error, objet](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, Native Error, nombre, Source et SQLState, propriétés-exemple (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, Native Error, nombre, Source et SQLState, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [HelpContext, HelpFile, propriétés](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number, propriété (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source, propriété (objet Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
