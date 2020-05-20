---
title: CommandType, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
author: rothja
ms.author: jroth
ms.openlocfilehash: bbc90dc2d818ca880a9f712d551fd6a98fb9ecf3
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760425"
---
# <a name="commandtype-property-ado"></a>CommandType, propriété (ADO)
Indique le type d’un objet [Command](../../../ado/reference/ado-api/command-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une ou plusieurs valeurs [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) .  
  
> [!NOTE]
>  N’utilisez pas les valeurs **CommandTypeEnum** de **adCmdFile** ou **adCmdTableDirect** avec **CommandType**. Ces valeurs ne peuvent être utilisées qu’en tant qu’options avec les méthodes d' [ouverture](../../../ado/reference/ado-api/open-method-ado-recordset.md) et de [rerequête](../../../ado/reference/ado-api/requery-method.md) d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **CommandType** pour optimiser l’évaluation de la propriété [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) .  
  
 Si la valeur de la propriété **CommandType** est définie sur la valeur par défaut, **adCmdUnknown**, vous pouvez constater une baisse des performances, car ADO doit effectuer des appels au fournisseur pour déterminer si la propriété **CommandText** est une instruction SQL, une procédure stockée ou un nom de table. Si vous connaissez le type de commande que vous utilisez, la définition de la propriété **CommandType** demande à ADO d’accéder directement au code approprié. Si la propriété **CommandType** ne correspond pas au type de commande dans la propriété **CommandText** , une erreur se produit lorsque vous appelez la méthode [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
