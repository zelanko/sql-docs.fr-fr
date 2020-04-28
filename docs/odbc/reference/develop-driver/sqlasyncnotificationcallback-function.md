---
title: SQLAsyncNotificationCallback fonction) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6c182c48b8e5ddb70204ddd3a94d9651f97595d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294536"
---
# <a name="sqlasyncnotificationcallback-function"></a>SQLAsyncNotificationCallback, fonction
**Conformité**  
 Version introduite : ODBC 3,8  
  
 Conformité aux normes : aucune  
  
 **Résumé**  
 **SQLAsyncNotificationCallback** permet à un pilote de rappeler le gestionnaire de pilotes lorsqu’il y a une progression pour l’opération asynchrone en cours après que le pilote a renvoyé SQL_STILL_EXECUTING. **SQLAsyncNotificationCallback** peut uniquement être appelé par le pilote.  
  
 Les pilotes n’appellent pas **SQLAsyncNotificationCallback** avec le nom de fonction **SQLAsyncNotificationCallback**. Au lieu de cela, le gestionnaire de pilotes passe un pointeur de fonction à un pilote comme valeur pour l’attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK ou SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK du handle de connexion ou du handle d’instruction correspondant, respectivement. Des valeurs de pointeur de fonction différentes peuvent être affectées à différents handles. Le type du pointeur de fonction est défini en tant que SQL_ASYNC_NOTIFICATION_CALLBACK.  
  
 **SQLAsyncNotificationCallback** est thread-safe. Un pilote peut choisir d’utiliser plusieurs threads appelant **SQLAsyncNotificationCallback** sur des handles différents simultanément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>Arguments  
 *pContex*  
 Pointeur vers une structure de données définie par le gestionnaire de pilotes. La valeur est passée au pilote via SQLSetConnectAttr (SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) ou SQLSetStmtAttr (SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT).  Le pilote n’a pas accès à la valeur.  
  
 *fLast*  
 Utilisé par un pilote pour indiquer que cet appel de fonction de rappel est le dernier pour l’opération asynchrone actuelle. Le pilote renverra un code de retour autre que SQL_STILL_EXECUTING lorsque le gestionnaire de pilotes appelle à nouveau la fonction. Le gestionnaire de pilotes peut utiliser ces informations, par exemple, pour informer à l’avance l’application que l’opération asynchrone se termine.  
  
 Si *handle* n’est pas un handle valide du type spécifié par *comme HandleType*, **SQLCancelHandle** retourne SQL_INVALID_HANDLE.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS ou SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLAsyncNotificationCallback** peut retourner SQL_ERROR pour les deux situations suivantes (cela indique un problème d’implémentation dans le pilote ou le gestionnaire de pilotes.  
  
|Error|Description|  
|-----------|-----------------|  
|La connexion ou l’instruction n’a pas demandé de notification.||  
|*Handle* non valide|Le pilote a passé un handle non valide, ce qui a échoué lors des tests de validation du gestionnaire de pilotes internes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
