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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 46cfbb4e2e6b60f620cd7e38272bf9308ece91bc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306240"
---
# <a name="calling-sqlsetpos"></a>Appel de SQLSetPos
Dans ODBC *2. x*, le pointeur vers le tableau d’état de ligne était un argument de **SQLExtendedFetch**. Le tableau d’état de ligne a été mis à jour ultérieurement par un appel à **SQLSetPos**. Certains pilotes s’appuient sur le fait que ce tableau ne change pas entre **SQLExtendedFetch** et **SQLSetPos**. Dans ODBC *3. x*, le pointeur vers le tableau d’État est un champ de descripteur et par conséquent, l’application peut facilement la changer pour pointer vers un autre tableau. Cela peut être un problème lorsqu’une application ODBC *3. x* utilise un pilote ODBC *2. x* , mais qu’elle appelle **SQLSetStmtAttr** pour définir le pointeur d’État du tableau et appelle **SQLFetchScroll** pour extraire des données. Le gestionnaire de pilotes le mappe comme une séquence d’appels à **SQLExtendedFetch**. Dans le code suivant, une erreur est normalement générée lorsque le gestionnaire de pilotes mappe le deuxième appel de **SQLSetStmtAttr** lorsque vous utilisez un pilote ODBC *2. x* :  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 L’erreur serait déclenchée s’il n’existait aucun moyen de modifier le pointeur d’état de ligne dans ODBC *2. x* entre les appels à **SQLExtendedFetch**. Au lieu de cela, le gestionnaire de pilotes effectue les étapes suivantes lors de l’utilisation d’un pilote ODBC *2. x* :  
  
1.  Initialise un indicateur du gestionnaire de pilotes internes *fSetPosError* à true.  
  
2.  Quand une application appelle **SQLFetchScroll**, le gestionnaire de pilotes affecte la valeur false à *fSetPosError* .  
  
3.  Lorsque l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR, le gestionnaire de pilotes définit *FSetPosError* égal à toTRUE.  
  
4.  Lorsque l’application appelle **SQLSetPos**, avec *FSETPOSERROR* égal à true, le gestionnaire de pilotes génère SQL_ERROR avec SQLSTATE HY011 (l’attribut ne peut pas être défini maintenant) pour indiquer que l’application a tenté d’appeler **SQLSetPos** après avoir modifié le pointeur d’état de ligne mais avant d’appeler **SQLFetchScroll**.
