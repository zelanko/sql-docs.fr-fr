---
description: Caractère d’échappement du prédicat LIKE
title: Caractère d’échappement de prédicat LIKE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5304068e21dd6faf0e737a94add0cce177c4dabc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476551"
---
# <a name="like-predicate-escape-character"></a>Caractère d’échappement du prédicat LIKE
Dans un prédicat **Like** , le signe de pourcentage (%) correspond à zéro ou plusieurs caractères et le trait de soulignement (_) correspond à n’importe quel caractère. Pour mettre en correspondance un signe de pourcentage réel ou un trait de soulignement dans un prédicat **Like** , un caractère d’échappement doit précéder le signe de pourcentage ou le trait de soulignement. La séquence d’échappement qui définit le caractère d’échappement de prédicat **Like** est :  
  
 **{Escape'** *caractère d’échappement* **'}**  
  
 où *caractère d’échappement* est un caractère pris en charge par la source de données.  
  
 Pour plus d’informations sur la séquence d’échappement LIKE, voir la [séquence d’échappement like](../../../odbc/reference/appendixes/like-escape-sequence.md) dans l’annexe C : grammaire SQL.  
  
 Par exemple, les instructions SQL suivantes créent le même jeu de résultats de noms de clients qui commencent par les caractères « % AAA ». La première instruction utilise la syntaxe de séquence d’échappement. La deuxième instruction utilise la syntaxe native pour l’accès à Microsoft® et n’est pas interopérable. Notez que le deuxième caractère de pourcentage de chaque prédicat **Like** est un caractère générique qui correspond à zéro ou plusieurs caractères.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Pour déterminer si le caractère d’échappement de prédicat **Like** est pris en charge par une source de données, une application appelle **SQLGetInfo** avec l’option SQL_LIKE_ESCAPE_CLAUSE.
