---
title: Réception de plusieurs Recordsets | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving multiple Recordsets [ADO]
- Recordset object [ADO], receiving multiple Recordsets
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 78e6ed78e8c61a9ce14e30f0eb286d55da0e63b9
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700746"
---
# <a name="receiving-multiple-recordsets"></a>Réception de plusieurs recordsets
Le [fournisseur Microsoft OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) prend en charge de retourner plusieurs **Recordset** objets pour une commande unique contenant plusieurs instructions SQL, un **Recordset**par l’instruction SQL. L’ordre dans lequel le **Recordset**sont renvoyées suit l’ordre dans lequel les instructions SQL sont placées dans le texte de commande.  
  
 Le fournisseur Microsoft OLE DB pour SQL Server retourne également plusieurs jeux de résultats à ADO lorsque la commande contient une clause COMPUTE. Par exemple, une commande contenant l’instruction SQL suivante retournera les résultats en deux **Recordset** objets : un pour l’ensemble de lignes de (*ProductID*, *ProductName*, *UnitPrice*) et l’autre pour le prix moyen de tous les produits dans la table.  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 Vous pouvez utiliser la **Recordset.NextRecordset** méthode pour énumérer les deux objets.  
  
 Pour plus d’informations, consultez [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md).
