---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 535c169123923cdb36c355e098f6e0c55ebb9d56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68127305"
---
# <a name="correlation-names"></a>Noms de corrélation
Les noms de corrélation sont entièrement pris en charge, y compris dans la liste des tables. Par exemple, dans la chaîne suivante, E1 est le nom de corrélation pour la table nommée EMP :  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
