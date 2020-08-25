---
description: MaxRecords, propriété (ADO)
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
ms.openlocfilehash: 4431d9a8af8623150717474cd5429a772f86be8c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774448"
---
# <a name="maxrecords-property-ado"></a>MaxRecords, propriété (ADO)
Indique le nombre maximal d’enregistrements à retourner à un [jeu d’enregistrements](./recordset-object-ado.md) à partir d’une requête.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type long** qui indique le nombre maximal d’enregistrements à retourner. La valeur par défaut est zéro (**0**), ce qui signifie qu’aucune limite n’est définie.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **maxRecords** pour limiter le nombre d’enregistrements renvoyés par le fournisseur à partir de la source de données. La valeur par défaut de cette propriété est zéro, ce qui signifie que le fournisseur retourne tous les enregistrements demandés.  
  
 La propriété **maxRecords** est en lecture/écriture lorsque le **Recordset** est fermé et en lecture seule lorsqu’il est ouvert.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [MaxRecords, exemple de propriété (VB)](./maxrecords-property-example-vb.md)   
 [MaxRecords, exemple de propriété (VC++)](./maxrecords-property-example-vc.md)