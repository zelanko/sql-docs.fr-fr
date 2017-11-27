---
title: "CommandStream, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: _Command::CommandStream
helpviewer_keywords: CommandStream property [ADO]
ms.assetid: f78f61b6-87e0-48dc-961e-83d0e20da58e
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dacfa25b7ab9967f8c28e38c0df121063b583319
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="commandstream-property-ado"></a>CommandStream, propriété (ADO)
Indique le flux utilisé comme entrée pour un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne le flux de données utilisé comme entrée pour un **commande** objet. Le format de ce flux de données est spécifique au fournisseur ; consultez la documentation de votre fournisseur pour plus d’informations. Cette propriété est similaire à la [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) propriété, ce qui permet de spécifier une chaîne pour l’entrée d’un **commande**.  
  
## <a name="remarks"></a>Notes  
 **CommandStream** et **CommandText** s’excluent mutuellement. Lorsque l’utilisateur définit les **CommandStream** propriété, le **CommandText** propriété la valeur la chaîne vide (« »). Si l’utilisateur définit les **CommandText** propriété, le **CommandStream** propriété sera définie **rien**.  
  
 Les comportements de la **Command.Parameters.Refresh** et **Command.Prepare** méthodes sont définies par le fournisseur. Les valeurs des paramètres dans un flux de données ne peuvent pas être actualisés.  
  
 Le flux d’entrée n’est pas disponible à d’autres objets ADO qui retournent la source d’un **commande**. Par exemple, si le [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) a la valeur un **commande** objet qui a un flux de données en entrée, **Recordset.Source** continue à retourner la **CommandText** propriété, qui contient une chaîne vide (« »), au lieu du contenu du flux de la **CommandStream** propriété.  
  
 Lorsque vous utilisez un flux de commandes (tel que spécifié par **CommandStream**), valide uniquement [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) les valeurs pour le [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) propriété sont  **adCmdText** et **adCmdUnknown**. Toute autre valeur génère une erreur.  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CommandText, propriété (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Propriété Dialect](../../../ado/reference/ado-api/dialect-property.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)
