---
title: "Syntaxe de littéral numérique | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 317b9753912c937399480473bca78bc7e11b7ce8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="numeric-literal-syntax"></a>Syntaxe de littéral numérique
La syntaxe suivante est utilisée pour les littéraux numériques dans ODBC :  
  
 *littéral numérique* :: = *littéral numérique signé &#124; littéral numérique non signé*  
  
 *littéral numérique signé* :: = [*signe*] *littéral numérique non signé*  
  
 *littéral numérique non signée* :: = *littéral numérique exact &#124; littéral numérique approximative*  
  
 *littéral numérique exact* :: = *entier non signé* [*période*[*entier non signé*]] *&#124; période en entier non signé*  
  
 *signe* :: = *signe &#124; signe moins*  
  
 *littéral numérique approximatif* :: = *exposant de la mantisse E*  
  
 *mantisse* :: = *littéral numérique exacte*  
  
 *exposant* :: = *entier signé*  
  
 *entier signé* :: = [*signe*] *entier non signé*  
  
 *entier non signé* :: = *chiffre...*  
  
 *signe* :: =*+*  
  
 *signe moins-* :: = -  
  
 *chiffre* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *période* :: =.
