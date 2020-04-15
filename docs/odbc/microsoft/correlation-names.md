---
title: Noms de corrélation Microsoft Docs
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
ms.openlocfilehash: dfe0655ace4bbd622dfb80b833f49562732394e2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280959"
---
# <a name="correlation-names"></a>Noms de corrélation
Les noms de corrélation sont entièrement pris en charge, y compris dans la liste de table. Par exemple, dans la chaîne suivante, E1 est le nom de corrélation pour le tableau nommé Emp :  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
