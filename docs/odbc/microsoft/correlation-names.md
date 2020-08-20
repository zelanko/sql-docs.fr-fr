---
description: Noms de corrélation
title: Noms de corrélation | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- correlation names [ODBC]
- SQL grammar [ODBC], correlation names
ms.assetid: 76c36c6f-f8e1-4ece-a77b-611dde3bdd8a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 24de7ec65b069839541cfa5cd272a221ebc96ecd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471641"
---
# <a name="correlation-names"></a>Noms de corrélation
Les noms de corrélation sont entièrement pris en charge, y compris dans la liste des tables. Par exemple, dans la chaîne suivante, E1 est le nom de corrélation pour la table nommée EMP :  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
