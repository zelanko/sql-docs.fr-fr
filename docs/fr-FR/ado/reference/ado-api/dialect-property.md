---
title: Propriété Dialect | Documents Microsoft
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
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d7f096051d1118e9fa29860c5c0d89db9f77ec3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="dialect-property"></a>Propriété Dialect
Indique le dialecte de la [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) ou [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) propriétés. Le dialecte définit la syntaxe et les règles générales que le fournisseur utilise pour analyser la chaîne ou le flux.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Le **dialecte** propriété contient un GUID valide qui représente le dialecte du texte de commande ou du flux. La valeur par défaut de cette propriété est {C8B521FB-5CF3-11CE-ADE5-00AA0044773D}, ce qui signifie que le fournisseur doit choisir comment interpréter le texte de commande ou le flux.  
  
## <a name="remarks"></a>Notes  
 ADO n’interroge pas le fournisseur lorsque l’utilisateur lit la valeur de cette propriété ; Il retourne une représentation sous forme de chaîne de la valeur actuellement stockée dans le [commande](../../../ado/reference/ado-api/command-object-ado.md) objet.  
  
 Lorsque l’utilisateur définit les **dialecte** valide le GUID de propriété, ADO et génère une erreur si la valeur fournie n’est pas un GUID valide. Consultez la documentation de votre fournisseur déterminer les valeurs GUID pris en charge par le **dialecte** propriété.  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Execute, méthode (commande ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)
