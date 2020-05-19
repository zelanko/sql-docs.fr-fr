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
author: rothja
ms.author: jroth
ms.openlocfilehash: b9e4beaaa4b38a26089d1136d1b32090ea12231f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754380"
---
# <a name="maxrecords-property-ado"></a>MaxRecords, propriété (ADO)
Indique le nombre maximal d’enregistrements à retourner à un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) à partir d’une requête.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type long** qui indique le nombre maximal d’enregistrements à retourner. La valeur par défaut est zéro (**0**), ce qui signifie qu’aucune limite n’est définie.  
  
## <a name="remarks"></a>Remarques  
 Utilisez la propriété **maxRecords** pour limiter le nombre d’enregistrements renvoyés par le fournisseur à partir de la source de données. La valeur par défaut de cette propriété est zéro, ce qui signifie que le fournisseur retourne tous les enregistrements demandés.  
  
 La propriété **maxRecords** est en lecture/écriture lorsque le **Recordset** est fermé et en lecture seule lorsqu’il est ouvert.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [MaxRecords, exemple de propriété (VB)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [MaxRecords, exemple de propriété (VC++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   
