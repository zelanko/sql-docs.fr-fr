---
title: MaxRecords, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MaxRecords
helpviewer_keywords:
- MaxRecords property [ADO]
ms.assetid: 20c76571-8c9a-482c-a99e-726ab1d93f8b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5acd8997af6993a49ac4cbcca6e3b4c8bd26acfd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932234"
---
# <a name="maxrecords-property-ado"></a>MaxRecords, propriété (ADO)
Indique le nombre maximal d’enregistrements à retourner à un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) à partir d’une requête.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type long** qui indique le nombre maximal d’enregistrements à retourner. La valeur par défaut est zéro (**0**), ce qui signifie qu’aucune limite n’est définie.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **maxRecords** pour limiter le nombre d’enregistrements renvoyés par le fournisseur à partir de la source de données. La valeur par défaut de cette propriété est zéro, ce qui signifie que le fournisseur retourne tous les enregistrements demandés.  
  
 La propriété **maxRecords** est en lecture/écriture lorsque le **Recordset** est fermé et en lecture seule lorsqu’il est ouvert.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [MaxRecords, exemple de propriété (VB)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [MaxRecords, exemple de propriété (VC++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   
