---
title: Sqlasyncnotificationcallback, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b78764e1dccb7118d43cc967f3b03838366d6eb0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758047"
---
# <a name="sqlasyncnotificationcallback-function"></a>SQLAsyncNotificationCallback, fonction
**Conformité**  
 Version introduite : ODBC 3.8  
  
 Conformité aux normes : aucun  
  
 **Résumé**  
 **SQLAsyncNotificationCallback** permet à un pilote appeler le Gestionnaire de pilotes lorsqu’il existe la progression de l’opération asynchrone actuelle une fois que le pilote retourne SQL_STILL_EXECUTING. **SQLAsyncNotificationCallback** peut uniquement être appelé par le pilote.  
  
 Pilotes n’appellent pas **SQLAsyncNotificationCallback** avec le nom de la fonction **SQLAsyncNotificationCallback**. Au lieu de cela, le Gestionnaire de pilotes transmet un pointeur de fonction à un pilote comme valeur pour l’attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK ou SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK du descripteur d’instruction, ou handle de connexion correspondante respectivement. Handles différents peuvent être affectés à des valeurs de pointeur fonction différente. Le type du pointeur de fonction est défini comme SQL_ASYNC_NOTIFICATION_CALLBACK.  
  
 **SQLAsyncNotificationCallback** est thread-safe. Un pilote peut choisir d’utiliser plusieurs threads appelant **SQLAsyncNotificationCallback** sur différents gère simultanément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>Arguments  
 *pContex*  
 Pointeur vers une structure de données définie par le Gestionnaire de pilote. La valeur est passée au pilote via SQLSetConnectAttr(SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) ou SQLSetStmtAttr(SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT).  Le pilote n’a pas accès à la valeur.  
  
 *fLast*  
 Utilisé par un pilote pour indique que cet appel de fonction de rappel est la dernière pour l’opération asynchrone actuelle. Le pilote retournera un code de retour différent de SQL_STILL_EXECUTING lorsque le Gestionnaire de pilotes appelle la fonction à nouveau. Le Gestionnaire de pilote peut utiliser ces informations, par exemple, pour informer l’application à l’avance que l’opération asynchrone se termine.  
  
 Si *gérer* n’est pas un handle valide du type spécifié par *HandleType*, **SQLCancelHandle** retourne SQL_INVALID_HANDLE.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS ou SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLAsyncNotificationCallback** peut retourner SQL_ERROR pour deux situations suivantes (celles-ci indiquent un problème d’implémentation dans le pilote ou le Gestionnaire de pilotes.  
  
|Error|Description|  
|-----------|-----------------|  
|Connexion ou l’instruction n’a pas demandé de notification.||  
|Non valide *gérer*|Le pilote est passé dans un handle non valide, ce qui a échoué les tests de validation interne du Gestionnaire de pilotes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
