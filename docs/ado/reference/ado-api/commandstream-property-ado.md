---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b1048e8d243bd19d86d60c3c4f92e4e4b9d137a9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828781"
---
# <a name="commandstream-property-ado"></a>CommandStream, propriété (ADO)
Indique le flux utilisé comme entrée pour un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne le flux utilisé comme entrée pour un **commande** objet. Le format de ce flux est spécifique au fournisseur ; consultez la documentation de votre fournisseur pour plus d’informations. Cette propriété est similaire à la [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) propriété, qui permet de spécifier une chaîne pour l’entrée d’un **commande**.  
  
## <a name="remarks"></a>Notes  
 **CommandStream** et **CommandText** s’excluent mutuellement. Lorsque l’utilisateur définit le **CommandStream** propriété, le **CommandText** propriété est définie sur la chaîne vide ( » »). Si l’utilisateur définit le **CommandText** propriété, le **CommandStream** propriété sera définie **rien**.  
  
 Les comportements de la **Command.Parameters.Refresh** et **Command.Prepare** méthodes sont définies par le fournisseur. Les valeurs des paramètres dans un flux de données ne peuvent pas être actualisées.  
  
 Le flux d’entrée n’est pas disponible à d’autres objets ADO qui retournent la source d’un **commande**. Par exemple, si le [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est défini sur un **commande** objet qui a un flux comme entrée, **Recordset.Source** continue à retourner la **CommandText** propriété, qui contient une chaîne vide (« »), au lieu du contenu du flux de la **CommandStream** propriété.  
  
 Lorsque vous utilisez un flux de commandes (comme spécifié par **CommandStream**), uniquement valide [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valeurs pour le [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) propriété sont  **adCmdText** et **adCmdUnknown**. Toute autre valeur génère une erreur.  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CommandText, propriété (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Dialect, propriété](../../../ado/reference/ado-api/dialect-property.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)
