---
title: Notification de la fin de la fonction asynchrone | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 336565da-4203-4745-bce2-4f011c08e357
author: MightyPen
ms.author: genemi
ms.openlocfilehash: de3496661f2ab329e5bf662a9cb8fa749cb81bfc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68129323"
---
# <a name="notification-of-asynchronous-function-completion"></a>Notification de la fin d’une fonction asynchrone
Dans le kit de développement logiciel (SDK) Windows 8, ODBC a ajouté un mécanisme pour notifier les applications lorsqu’une opération asynchrone se termine, ce que nous appelons « notification à l’achèvement ». (Pour plus d’informations, consultez [exécution asynchrone (méthode de notification)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md) .) Cette rubrique décrit certains des problèmes rencontrés par les développeurs de pilotes.  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>Interface entre le gestionnaire de pilotes et le pilote  
 Le gestionnaire de pilotes fournit en interne une fonction de rappel [SQLAsyncNotificationCallback Function](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md). **SQLAsyncNotificationCallback** peut uniquement être appelé par le pilote : une application ne peut pas l’appeler directement. Le pilote appelle **SQLAsyncNotificationCallback** chaque fois que de nouvelles données sont reçues du serveur après le dernier renvoi de SQL_STILL_EXECUTING.  
  
 Le gestionnaire de pilotes fournit un mécanisme de rappel afin qu’un pilote puisse notifier le gestionnaire de pilotes lorsqu’une progression a été effectuée lors de l’exécution d’une opération asynchrone après le retour de la fonction correspondante SQL_STILL_EXECUTING  
  
 Le gestionnaire de pilotes définit l’attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK sur un handle de connexion de pilote avec un pointeur de fonction non NULL, qui est de type SQL_ASYNC_NOTIFICATION_CALLBACK, pour que le pilote fonctionne en mode de notification pour toute opération asynchrone opérations sur ce handle. De même, le gestionnaire de pilotes définit l’attribut SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK sur un descripteur d’instruction de pilote avec un pointeur de fonction non NULL, qui est également de type SQL_ASYNC_NOTIFICATION_CALLBACK, pour que le pilote fonctionne en mode de notification pour toutes les opérations asynchrones sur ce handle.  
  
 Si une opération asynchrone est effectuée sur un handle de pilote, les fonctions du pilote asynchrone doivent fonctionner dans un style non bloquant. Si l’opération ne peut pas se terminer immédiatement, la fonction du pilote doit retourner SQL_STILL_EXECUTING. Cette condition est vraie pour le mode d’interrogation et le mode de notification.  
  
 Si un handle est en mode de notification asynchrone, le pilote doit appeler la fonction de rappel de notification, dont l’adresse est la valeur de l’attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK ou SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK, une fois après retour de SQL_STILL_EXECUTING. En d’autres termes, un SQL_STILL_EXECUTING de retour doit être associé à un appel de la fonction de rappel de notification. Le pilote doit utiliser la valeur actuelle de l’attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT ou SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT handle comme valeur pour le paramètre de fonction de rappel *pContext*.  
  
 Le pilote ne doit pas rappeler le thread qui appelle la fonction de pilote ; Il n’y a aucune raison de notifier la progression avant le retour de la fonction. Le pilote doit utiliser son propre thread pour le rappel. Le gestionnaire de pilotes n’utilise pas le thread de rappel du pilote pour exécuter une logique de traitement extensive.  
  
 Le gestionnaire de pilotes appellera la fonction d’origine une fois le pilote rappelé. Le gestionnaire de pilotes peut utiliser un thread qui n’est ni un thread d’application, ni un thread de pilote. Si le pilote utilise des informations associées au thread (par exemple, un jeton de sécurité ou un identificateur d’utilisateur), le pilote doit enregistrer les informations requises dans l’appel asynchrone initial et utiliser la valeur enregistrée avant l’intégralité de l’opération asynchrone se termine. En règle générale, seuls **SQLDriverConnect**, **SQLConnect**ou **SQLBrowseConnect** doivent utiliser ce type d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
