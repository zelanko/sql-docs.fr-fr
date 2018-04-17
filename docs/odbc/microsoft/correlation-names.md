---
title: Noms de corrélation | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- correlation names [ODBC]
- SQL grammar [ODBC], correlation names
ms.assetid: 76c36c6f-f8e1-4ece-a77b-611dde3bdd8a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e3fd26a5b4601657d4f95ca629bc41666ef27309
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="correlation-names"></a>Noms de corrélation
Noms de corrélation sont entièrement pris en charge, y compris dans la liste de tables. Par exemple, dans la chaîne suivante, E1 est le nom de corrélation pour la table nommé Emp :  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
