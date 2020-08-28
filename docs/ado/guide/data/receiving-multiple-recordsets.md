---
description: Réception de plusieurs recordsets
title: Réception de plusieurs recordsets | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving multiple Recordsets [ADO]
- Recordset object [ADO], receiving multiple Recordsets
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
author: rothja
ms.author: jroth
ms.openlocfilehash: abac183f348553f30bf0cf5ed91725ef421afb3e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979970"
---
# <a name="receiving-multiple-recordsets"></a>Réception de plusieurs recordsets
Le [fournisseur Microsoft OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) prend en charge le retour de plusieurs objets **Recordset** pour une seule commande contenant plusieurs instructions SQL, un **jeu d’enregistrements** par instruction SQL. L’ordre dans lequel les **jeux d’enregistrements**sont retournés suit l’ordre dans lequel les instructions SQL sont placées dans le texte de la commande.  
  
 Le fournisseur Microsoft OLE DB pour SQL Server retourne également plusieurs jeux de résultats à ADO lorsque la commande contient une clause COMPUTE. Par exemple, une commande contenant l’instruction SQL suivante retourne les résultats dans deux objets **Recordset** : un pour l’ensemble de lignes de (*ProductID*, *ProductName*, *UnitPrice*) et l’autre pour le prix moyen de tous les produits de la table.  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 Vous pouvez utiliser la méthode **Recordset. NextRecordset** pour énumérer les deux objets.  
  
 Pour plus d’informations, consultez [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md).
