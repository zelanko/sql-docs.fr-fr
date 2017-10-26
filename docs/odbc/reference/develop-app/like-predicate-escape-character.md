---
title: "COMME caractère d’échappement de prédicat | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 132359972cebd3dded36fb911a2ee8e561e5ca64
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="like-predicate-escape-character"></a>COMME caractère d’échappement de prédicat
Dans un **comme** prédicat, le symbole de pourcentage (%) correspond zéro ou plusieurs caractères et le trait de soulignement (_) correspond à n’importe quel caractère. Pour rechercher un signe de pourcentage réel ou de traits de soulignement dans un **comme** prédicat, un caractère d’échappement doit être placée avant le signe de pourcentage ou un trait de soulignement. La séquence d’échappement qui définit les **comme** caractère d’échappement de prédicat est :  
  
 **{escape '** *-caractère d’échappement* **'}**  
  
 où *-caractère d’échappement* est n’importe quel caractère pris en charge par la source de données.  
  
 Pour plus d’informations sur le type des séquence d’échappement, consultez [comme séquence d’échappement](../../../odbc/reference/appendixes/like-escape-sequence.md) dans l’annexe c : SQL grammaire.  
  
 Par exemple, les instructions SQL suivantes créent le même jeu de résultats du client des noms qui commencent par les caractères « % AAA ». La première instruction utilise la syntaxe de la séquence d’échappement. La deuxième instruction utilise la syntaxe native pour Microsoft® Access et n’est pas interopérable. Notez que le deuxième caractère de pourcentage dans chaque **comme** prédicat est un caractère générique qui correspond à zéro ou plus de n’importe quel caractère.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Pour déterminer si le **comme** caractère d’échappement de prédicat est pris en charge par une source de données, une application appelle **SQLGetInfo** avec l’option SQL_LIKE_ESCAPE_CLAUSE.

