---
title: Fonction SQLAsyncNotificationCallback (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294536"
---
# <a name="sqlasyncnotificationcallback-function"></a>SQLAsyncNotificationCallback, fonction
**Conformité**  
 Version introduite: ODBC 3.8  
  
 Conformité aux normes : Aucun  
  
 **Résumé**  
 **SQLAsyncNotificationCallback** permet à un conducteur de rappeler au gestionnaire de conducteur quand il ya des progrès pour l’opération asynchrone actuelle après le retour du conducteur SQL_STILL_EXECUTING. **SQLAsyncNotificationCallback** ne peut appeler que par le conducteur.  
  
 Les conducteurs n’appellent pas **SQLAsyncNotificationCallback** avec le nom de fonction **SQLAsyncNotificationCallback**. Au lieu de cela, le gestionnaire de conducteur passe un pointeur de fonction à un conducteur comme valeur pour le SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK ou SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK attribut de la poignée de connexion ou de la poignée de déclaration correspondante, respectivement. Différentes poignées peuvent être attribuées à différentes valeurs de pointeur de fonction. Le type de pointeur de fonction est défini comme SQL_ASYNC_NOTIFICATION_CALLBACK.  
  
 **SQLAsyncNotificationCallback** est sans fil. Un conducteur peut choisir d’utiliser plusieurs threads appelant **SQLAsyncNotificationCallback** sur différentes poignées simultanément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>Arguments  
 *pContex (en anglais)*  
 Pointeur vers une structure de données définie par le Gestionnaire de pilote. La valeur est transmise au conducteur via SQLSetConnectAttr (SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) ou SQLSetStmtAttr (SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT).  Le conducteur n’a pas accès à la valeur.  
  
 *fLast*  
 Utilisé par un conducteur pour indique que cette invocation de la fonction de rappel est la dernière pour l’opération asynchrone actuelle. Le conducteur retournera un code de retour autre que SQL_STILL_EXECUTING lorsque le gestionnaire de conducteur appelle à nouveau la fonction. Le gestionnaire de conducteur peut utiliser ces informations, par exemple, pour informer l’application à l’avance que l’opération asynchrone sera terminée.  
  
 Si *Handle* n’est pas une poignée valide du type spécifié par *HandleType*, **SQLCancelHandle** retourne SQL_INVALID_HANDLE.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS ou SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLAsyncNotificationCallback** peut retourner SQL_ERROR pour les deux situations suivantes (celles-ci indiquent un problème de mise en œuvre chez le conducteur ou le gestionnaire de conducteur.  
  
|Error|Description|  
|-----------|-----------------|  
|La connexion ou la déclaration n’a pas demandé de notification.||  
|*Poignée* invalide|Le conducteur a passé dans une poignée invalide, qui a échoué aux tests internes de validation du gestionnaire de conducteur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
