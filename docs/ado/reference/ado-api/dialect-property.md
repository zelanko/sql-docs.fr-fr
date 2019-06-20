---
title: Dialect, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5c7e6aab3e3b33d02adcb067fff46b49973191b0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698234"
---
# <a name="dialect-property"></a>Dialect, propriété
Indique le dialecte de la [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) ou [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) propriétés. Le dialecte définit la syntaxe et les règles générales que le fournisseur utilise pour analyser la chaîne ou le flux.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Le **dialecte** propriété contient un GUID valide qui représente le dialecte du texte de commande ou du flux. La valeur par défaut de cette propriété est {C8B521FB-5CF3-11CE-ADE5-00AA0044773D}, ce qui indique que le fournisseur doit choisir comment interpréter le texte de la commande ou le flux.  
  
## <a name="remarks"></a>Notes  
 ADO n’interroge pas le fournisseur lorsque l’utilisateur lit la valeur de cette propriété ; elle retourne une représentation sous forme de chaîne de la valeur actuellement stockée dans le [commande](../../../ado/reference/ado-api/command-object-ado.md) objet.  
  
 Lorsque l’utilisateur définit le **dialecte** valide le GUID de propriété, ADO et génère une erreur si la valeur fournie n’est pas un GUID valide. Consultez la documentation de votre fournisseur déterminer les valeurs GUID pris en charge par le **dialecte** propriété.  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Execute, méthode (commande ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)
