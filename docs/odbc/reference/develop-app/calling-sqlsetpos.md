---
title: Appel SQLSetPos (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 46cfbb4e2e6b60f620cd7e38272bf9308ece91bc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306240"
---
# <a name="calling-sqlsetpos"></a>Appel de SQLSetPos
Dans ODBC *2.x*, le pointeur du tableau d’état de la ligne était un argument à **SQLExtendedFetch**. Le tableau d’état de la ligne a ensuite été mis à jour par un appel à **SQLSetPos**. Certains conducteurs se sont fiés au fait que ce tableau ne change pas entre **SQLExtendedFetch** et **SQLSetPos**. Dans ODBC *3.x*, le pointeur du tableau d’état est un champ descripteur et donc l’application peut facilement le changer pour pointer vers un tableau différent. Cela peut être un problème quand une application ODBC *3.x* travaille avec un pilote ODBC *2.x,* mais appelle **SQLSetStmtAttr** pour définir le pointeur de statut du tableau et appelle **SQLFetchScroll** pour aller chercher des données. Le Driver Manager le décrit comme une séquence d’appels à **SQLExtendedFetch**. Dans le code suivant, une erreur serait normalement soulevée lorsque le gestionnaire de conducteur cartographie le deuxième appel **SQLSetStmtAttr** lorsqu’il travaille avec un conducteur ODBC *2.x* :  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 L’erreur serait soulevée s’il n’y avait aucun moyen de changer le pointeur de statut de ligne dans ODBC *2.x* entre les appels à **SQLExtendedFetch**. Au lieu de cela, le gestionnaire de conducteur effectue les étapes suivantes lorsqu’il travaille avec un pilote ODBC *2.x* :  
  
1.  Initialise un indicateur interne de driver Manager *fSetPosError* à VRAI.  
  
2.  Lorsqu’une application appelle **SQLFetchScroll**, le Driver Manager met *fSetPosError* à FALSE.  
  
3.  Lorsque l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR, le Driver Manager définit *fSetPosError* égal à TRUE.  
  
4.  Lorsque l’application appelle **SQLSetPos**, avec *fSetPosError* égal à VRAI, le gestionnaire de conducteur soulève SQL_ERROR avec SQLSTATE HY011 (Attribut ne peut pas être fixé maintenant) pour indiquer que l’application a tenté d’appeler **SQLSetPos** après avoir changé le pointeur de statut de la ligne, mais avant d’appeler **SQLFetchScroll**.
