---
description: Erreurs (ADO)
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
ms.openlocfilehash: 392d1f2fdfc0a7fe2e0cf9e1e14efb77f396acfd
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806131"
---
# <a name="errors-ado"></a>Erreurs (ADO)
Toute opération impliquant des objets ADO peut générer une ou plusieurs erreurs de fournisseur. À mesure que chaque erreur se produit, un ou plusieurs objets **Error** sont placés dans la collection **Errors** de l’objet **Connection** . Pour plus d’informations sur la gestion des avertissements et des erreurs dans votre application ADO, consultez [gestion des erreurs](./error-handling.md).  
  
 Les erreurs d’application peuvent être déclenchées par un mécanisme distinct. Par exemple, dans Visual Basic, l’objet **Err** contient des erreurs au niveau de l’application.