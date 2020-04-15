---
title: Fonction SQLCompleteAsync (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4e09d61ef516e846798dd3af2d07dafa78af4605
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299654"
---
# <a name="sqlcompleteasync-function"></a>SQLCompleteAsync, fonction
**Conformité**  
 Version introduite: ODBC 3.8  
  
 Conformité aux normes : Aucun  
  
 **Résumé**  
 **SQLCompleteAsync** peut être utilisé pour déterminer quand une fonction asynchrone est complète en utilisant soit le traitement basé sur la notification ou le scrutin. Pour plus d’informations sur les opérations asynchrones, voir [Asynchrone Execution](../../../odbc/reference/develop-app/asynchronous-execution.md).  
  
 **SQLCompleteAsync n’est** mis en œuvre que dans le gestionnaire des chauffeurs de l’ODBC.  
  
 Dans le mode de traitement asynchrone basé sur la notification, **SQLCompleteAsync** doit être appelé après que le Gestionnaire de conducteur a soulevé l’objet d’événement utilisé pour la notification. **SQLCompleteAsync** complète le traitement asynchrone et la fonction asynchrone générera un code de retour.  
  
 Dans le sondage basé sur le mode de traitement asynchrone, **SQLCompleteAsync** est une alternative à appeler la fonction asynchrone originale, sans avoir besoin de spécifier les arguments dans l’appel de fonction asynchrone original. **SQLCompleteAsync** peut être utilisé, que la bibliothèque de cursor oDBC soit activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Le type de poignée sur laquelle compléter le traitement asynchrone. Les valeurs valides sont SQL_HANDLE_DBC ou SQL_HANDLE_STMT.  
  
 *Handle*  
 [Entrée] La poignée sur laquelle compléter le traitement asynchrone. Si *handle* n’est pas une poignée valide du type spécifié par *HandleType*, **SQLCompleteAsync** retourne SQL_INVALID_HANDLE.  
  
 Si *handle* n’est pas une poignée valide du type spécifié par *HandleType*, **SQLCompleteAsync** retourne SQL_INVALID_HANDLE.  
  
 *AsyncRetCodePtr*  
 [Sortie] Pointeur vers un tampon qui contiendra le code de retour de l’API asynchrone. Si *AsyncRetCodePtr* est NULL, **SQLCompleteAsync** revient SQL_ERROR.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_ERROR, SQL_NO_DATA ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Si **SQLCompleteAsync** retourne SQL_SUCCESS, une application doit obtenir le code de retour de la fonction asynchrone à partir du tampon pointé vers le tampon indiqué par *AsyncRetCodePtr*. Le SQLSTATE associé, le cas échéant, peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une poignée de déclaration ou un *HandleType* de SQL_HANDLE_DBC et une poignée de connexion. Ces dossiers diagnostiques sont associés à la fonction asynchrone, pas à cette fonction **SQLCompleteAsync.**  
  
 **SQLCompleteAsync renvoie** un code autre que SQL_SUCCESS pour indiquer que **SQLCompleteAsync** n’est pas appelé correctement. **SQLCompleteAsync** n’affichera aucun dossier diagnostique dans ce cas. Les codes de retour possibles sont les :  
  
-   SQL_INVALID_HANDLE : La poignée indiquée par *HandleType* et *Poignée* n’est pas une poignée valide.  
  
-   SQL_ERROR: *AsyncRetCodePtr* est NULL ou le traitement asynchrone n’est pas activé sur la poignée.  
  
-   SQL_NO_DATA : En mode notification, une opération asynchrone n’est pas en cours ou le gestionnaire de pilote n’a pas notifié l’application. En mode sondage, une opération asynchrone n’est pas en cours.  
  
## <a name="comments"></a>Commentaires  
 Dans les sondages basés sur le mode de traitement asynchrone, *AsyncRetCodePtr* pourrait être SQL_STILL_EXECUTING lorsque **SQLCompleteAsync** retourne SQL_SUCCESS. L’application doit continuer à voter jusqu’à ce *qu’AsyncRetCodePtr* ne soit pas SQL_STILL_EXECUTING. En mode de traitement asynchrone basé sur la notification, *AsyncRetCodePtr* ne sera jamais SQL_STILL_EXECUTING.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
