---
title: Sqlcompleteasync, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
f1_keywords:
- SQLCompleteAsync
helpviewer_keywords:
- SQLCompleteAsync function [ODBC]
ms.assetid: 1b97c46a-d2e5-4540-8239-9d975e5321c6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91046e19e77d3074a8ecef2163e8d46ab528bec9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259357"
---
# <a name="sqlcompleteasync-function"></a>SQLCompleteAsync, fonction
**Conformité**  
 Version introduite : ODBC 3.8  
  
 Conformité aux normes : None  
  
 **Résumé**  
 **SQLCompleteAsync** peut être utilisé pour déterminer quand une fonction asynchrone se termine à l’aide d’un traitement en fonction de notification ou d’interrogation. Pour plus d’informations sur les opérations asynchrones, consultez [exécution asynchrone](../../../odbc/reference/develop-app/asynchronous-execution.md).  
  
 **SQLCompleteAsync** est implémentée uniquement dans le Gestionnaire de pilotes ODBC.  
  
 En mode de traitement asynchrone en fonction de notification, **SQLCompleteAsync** doit être appelée une fois que le Gestionnaire de pilotes déclenche l’objet d’événement utilisé pour la notification. **SQLCompleteAsync** fin asynchrone traitement et la fonction asynchrone génèrent un code de retour.  
  
 En mode de traitement asynchrone en fonction de l’interrogation, **SQLCompleteAsync** est une alternative à l’appel de la fonction asynchrone d’origine, sans avoir à spécifier les arguments dans l’appel de fonction asynchrone d’origine. **SQLCompleteAsync** peut être utilisé que si la bibliothèque de curseurs ODBC est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Le type du handle sur lequel compléter asynchrone de traitement. Les valeurs valides sont SQL_HANDLE_DBC ou SQL_HANDLE_STMT.  
  
 *Handle*  
 [Entrée] Traitement de la poignée sur lequel compléter asynchrone. Si *gérer* n’est pas un handle valide du type spécifié par *HandleType*, **SQLCompleteAsync** retourne SQL_INVALID_HANDLE.  
  
 Si *gérer* n’est pas un handle valide du type spécifié par *HandleType*, **SQLCompleteAsync** retourne SQL_INVALID_HANDLE.  
  
 *AsyncRetCodePtr*  
 [Sortie] Pointeur vers une mémoire tampon qui contient le code de retour de l’API asynchrone. Si *AsyncRetCodePtr* est NULL, **SQLCompleteAsync** retourne SQL_ERROR.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_ERROR, SQL_NO_DATA, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Si **SQLCompleteAsync** retourne SQL_SUCCESS, une application doit obtenir le code de retour de la fonction asynchrone à partir de la mémoire tampon vers laquelle pointe *AsyncRetCodePtr*. La valeur SQLSTATE associée, le cas échéant, peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et un descripteur d’instruction ou un *HandleType* de SQL_ HANDLE_DBC et un handle de connexion. Ces enregistrements de diagnostic sont associés à la fonction asynchrone, n’appliquez pas **SQLCompleteAsync** (fonction).  
  
 **SQLCompleteAsync** retourne un code autre que SQL_SUCCESS pour indiquer que **SQLCompleteAsync** n’est pas appelé correctement. **SQLCompleteAsync** ne publie pas dans ce cas de n’importe quel enregistrement de diagnostic. Codes de retour possibles sont :  
  
-   SQL_INVALID_HANDLE: Le handle a indiqué par *HandleType* et *gérer* n’est pas un handle valide.  
  
-   SQL_ERROR : *AsyncRetCodePtr* est NULL ou le traitement asynchrone n’est pas activé sur le handle.  
  
-   SQL_NO_DATA: En mode de notification, une opération asynchrone n’est pas en cours d’exécution ou le Gestionnaire de pilotes n’a pas notifié l’application. En mode d’interrogation, une opération asynchrone n’est pas en cours d’exécution.  
  
## <a name="comments"></a>Commentaires  
 En mode de traitement asynchrone en fonction de l’interrogation, *AsyncRetCodePtr* peut être SQL_STILL_EXECUTING lorsque **SQLCompleteAsync** retourne SQL_SUCCESS. Application continue à interroger jusqu'à ce que *AsyncRetCodePtr* n’est pas SQL_STILL_EXECUTING. En mode de traitement asynchrone en fonction de notification, *AsyncRetCodePtr* ne sera jamais SQL_STILL_EXECUTING.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
