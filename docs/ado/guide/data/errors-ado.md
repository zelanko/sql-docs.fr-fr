---
title: Erreurs (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 8ae6611b-3069-4155-b014-c0c9da37be39
author: rothja
ms.author: jroth
ms.openlocfilehash: b014e68bce1e0fbcbabb9c8ee314ee7a9d6e7311
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761005"
---
# <a name="errors-ado"></a>Erreurs (ADO)
Toute opération impliquant des objets ADO peut générer une ou plusieurs erreurs de fournisseur. À mesure que chaque erreur se produit, un ou plusieurs objets **Error** sont placés dans la collection **Errors** de l’objet **Connection** . Pour plus d’informations sur la gestion des avertissements et des erreurs dans votre application ADO, consultez [gestion des erreurs](../../../ado/guide/data/error-handling.md).  
  
 Les erreurs d’application peuvent être déclenchées par un mécanisme distinct. Par exemple, dans Visual Basic, l’objet **Err** contient des erreurs au niveau de l’application.
