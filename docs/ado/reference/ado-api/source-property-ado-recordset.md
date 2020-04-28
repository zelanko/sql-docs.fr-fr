---
title: Source, propriété (ADO Recordset) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::putref_Source
- Recordset15::Source
- Recordset15::PutSource
- Recordset15::get_Source
- Recordset15::GetSource
- Recordset15::PutRefSource
- Recordset15::put_Source
helpviewer_keywords:
- Source property [ADO Recordset]
ms.assetid: a05ba2c9-2821-4343-8607-4de9b764ec91
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8f6ac84445272ae3657d4e25691dbbf150f32c5d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67930922"
---
# <a name="source-property-ado-recordset"></a>Source, propriété (objet Recordset ADO)
Indique la source de données d’un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit une valeur de **chaîne** ou une référence d’objet de [commande](../../../ado/reference/ado-api/command-object-ado.md) ; retourne uniquement une valeur de **chaîne** qui indique la source du **Recordset**.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **source** pour spécifier une source de données pour un objet **Recordset** à l’aide d’un des éléments suivants : une variable d’objet de **commande** , une instruction SQL, une procédure stockée ou un nom de table.  
  
 Si vous définissez la **propriété source** sur un **objet Command** , la propriété [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) de l’objet **Recordset** héritera de la valeur de la propriété **ActiveConnection** de l’objet **Command** spécifié. Toutefois, la lecture de la propriété **source** ne retourne pas d’objet **Command** . au lieu de cela, elle retourne la propriété [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) de l’objet **Command** dans lequel vous définissez la propriété **source** .  
  
 Si la propriété **source** est une instruction SQL, une procédure stockée ou un nom de table, vous pouvez optimiser les performances en passant l’argument d' *options* approprié avec l’appel de la méthode [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) .  
  
 La propriété **source** est en lecture/écriture pour les objets **Recordset** fermés et en lecture seule pour les objets **Recordset** ouverts.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Source, exemple de propriété (VB)](../../../ado/reference/ado-api/source-property-example-vb.md)   
 [Source, propriété (erreur ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Source, propriété (objet Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)
