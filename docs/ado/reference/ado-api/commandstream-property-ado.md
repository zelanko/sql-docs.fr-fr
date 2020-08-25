---
description: CommandStream, propriété (ADO)
title: CommandStream, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::CommandStream
helpviewer_keywords:
- CommandStream property [ADO]
ms.assetid: f78f61b6-87e0-48dc-961e-83d0e20da58e
author: rothja
ms.author: jroth
ms.openlocfilehash: 20b52a91429e2db6478aab36f2db5928bc2d30f5
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776148"
---
# <a name="commandstream-property-ado"></a>CommandStream, propriété (ADO)
Indique le flux utilisé comme entrée pour un objet [Command](./command-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne le flux utilisé comme entrée pour un objet **Command** . Le format de ce flux est spécifique au fournisseur ; Pour plus d’informations, consultez la documentation de votre fournisseur. Cette propriété est similaire à la propriété [CommandText](./commandtext-property-ado.md) , qui permet de spécifier une chaîne pour l’entrée d’une **commande**.  
  
## <a name="remarks"></a>Notes  
 **CommandStream** et **CommandText** s’excluent mutuellement. Lorsque l’utilisateur définit la propriété **CommandStream** , la propriété **CommandText** est définie sur la chaîne vide (""). Si l’utilisateur définit la propriété **CommandText** , la propriété **CommandStream** est définie sur **Nothing**.  
  
 Les comportements des méthodes **Command. Parameters. Refresh** et **Command. Prepare** sont définis par le fournisseur. Les valeurs des paramètres d’un flux ne peuvent pas être actualisées.  
  
 Le flux d’entrée n’est pas disponible pour les autres objets ADO qui retournent la source d’une **commande**. Par exemple, si la [source](./source-property-ado-recordset.md) d’un [jeu d’enregistrements](./recordset-object-ado.md) est définie sur un objet de **commande** qui a un flux comme entrée, **Recordset. source** continue à retourner la propriété **CommandText** , qui contient une chaîne vide (""), au lieu du contenu du flux de la propriété **CommandStream** .  
  
 Lors de l’utilisation d’un flux de commande (comme spécifié par **CommandStream**), les seules valeurs [CommandTypeEnum](./commandtypeenum.md) valides pour la propriété [CommandType](./commandtype-property-ado.md) sont **adCmdText** et **adCmdUnknown**. Toute autre valeur générera une erreur.  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CommandText, propriété (ADO)](./commandtext-property-ado.md)   
 [Dialect, propriété](./dialect-property.md)   
 [CommandTypeEnum](./commandtypeenum.md)