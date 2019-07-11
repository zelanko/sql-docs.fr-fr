---
title: Appel de SQLSetPos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], calling
- upgrading applications [ODBC], SQLSetPos
- backward compatibility [ODBC], SqlSetPos
- application upgrades [ODBC], SQLSetPos
ms.assetid: 846354b8-966c-4c2c-b32f-b0c8e649cedd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f94b1191815f37728a2d8de8fc1175113644bc5a
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793887"
---
# <a name="calling-sqlsetpos"></a>Appel de SQLSetPos
Dans ODBC *2.x*, le pointeur vers le tableau d’état de ligne a été un argument à **SQLExtendedFetch**. Le tableau d’état de ligne a été ultérieurement mise à jour par un appel à **SQLSetPos**. Certains pilotes reposait sur le fait que ce tableau ne change pas entre **SQLExtendedFetch** et **SQLSetPos**. Dans ODBC *3.x*, le pointeur vers le tableau d’état est un champ de descripteur et par conséquent, l’application peut facilement le modifier pour pointer vers un tableau différent. Cela peut poser un problème lorsqu’une application ODBC *3.x* application fonctionne avec une application ODBC *2.x* pilote, mais appelle **SQLSetStmtAttr** pour définir le pointeur d’état du tableau et appelle  **SQLFetchScroll** pour extraire des données. Le Gestionnaire de pilotes est mappé comme une séquence d’appels à **SQLExtendedFetch**. Dans le code suivant, une erreur normalement est déclenchée lorsque le Gestionnaire de pilotes est mappé à la seconde **SQLSetStmtAttr** appeler lorsque vous travaillez avec une application ODBC *2.x* pilote :  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 L’erreur serait déclenchée s’il n’y avait aucun moyen de modifier le pointeur d’état de ligne d’ODBC *2.x* entre les appels à **SQLExtendedFetch**. Au lieu de cela, le Gestionnaire de pilotes effectue les étapes suivantes lorsque vous travaillez avec une application ODBC *2.x* pilote :  
  
1.  Initialise un indicateur de gestionnaire de pilotes interne *fSetPosError* sur TRUE.  
  
2.  Lorsqu’une application appelle **SQLFetchScroll**, définit le Gestionnaire de pilotes *fSetPosError* sur FALSE.  
  
3.  Lorsque l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR, définit le Gestionnaire de pilotes *fSetPosError* toTRUE égal.  
  
4.  Lorsque l’application appelle **SQLSetPos**, avec *fSetPosError* égal à TRUE, le Gestionnaire de pilotes déclenche SQL_ERROR avec SQLSTATE HY011 (attribut ne peut pas être défini maintenant) pour indiquer que l’application a essayé d’appeler **SQLSetPos** après avoir modifié le pointeur d’état de ligne, mais avant d’appeler **SQLFetchScroll**.
