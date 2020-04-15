---
title: ORDER BY expression-list ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [ODBC]
- SQL grammar [ODBC], order by clause
ms.assetid: 5ef88186-a99f-4e2c-a3f3-98a42d4f03a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 272fa0be844569d322679d444807f8c332b4837b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291219"
---
# <a name="order-by-expression-list"></a>ORDER BY, liste d’expressions
Les expressions peuvent être utilisées dans la clause ORDER BY. Par exemple, dans les clauses suivantes, le tableau est commandé par trois expressions clés : a-b, c-d et e.  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 Aucune commande n’est autorisée sur les fonctions définies ou une expression qui contient une fonction définie.
