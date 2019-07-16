---
title: Notification de fin de la fonction asynchrone | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129323"
---
# <a name="notification-of-asynchronous-function-completion"></a>Notification de la fin d’une fonction asynchrone
Dans le Kit de développement Windows 8, ODBC ajouté un mécanisme pour informer les applications lors de l’opération asynchrone terminée, nous appellerons « notification en cas d’opération ». (Consultez [exécution asynchrone (méthode de Notification)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md) pour plus d’informations.) Cette rubrique décrit certains des problèmes pour les développeurs de pilotes.  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>L’Interface entre le Gestionnaire de pilotes et le pilote  
 Le Gestionnaire de pilotes fournit en interne une fonction de rappel [sqlasyncnotificationcallback, fonction](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md). **SQLAsyncNotificationCallback** peut uniquement être appelée par le pilote--une application ne peut pas l’appeler directement. Le pilote appelle **SQLAsyncNotificationCallback** chaque fois que les nouvelles données reçues à partir du serveur après la dernière SQL_STILL_EXECUTING de retour.  
  
 Le Gestionnaire de pilotes fournit un mécanisme de rappel pour un pilote peut informer le Gestionnaire de pilotes quand la progression a été effectuée lors de l’exécution d’une opération asynchrone après le retour de la fonction correspondante SQL_STILL_EXECUTING  
  
 Le Gestionnaire de pilotes définit l’attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK sur un handle de connexion de pilote avec un pointeur fonction non NULL, ce qui est de type SQL_ASYNC_NOTIFICATION_CALLBACK, pour le pilote fonctionne en mode de notification pour toute asynchrone opérations sur ce descripteur. De même, le Gestionnaire de pilotes définit l’attribut SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK sur un descripteur d’instruction pilote avec un pointeur fonction non NULL, ce qui est également de type SQL_ASYNC_NOTIFICATION_CALLBACK, pour le pilote fonctionne en mode de notification pour toutes les opérations asynchrones sur ce descripteur.  
  
 Si une opération asynchrone est effectuée sur un handle de pilote, les fonctions de pilote asynchrone doivent fonctionner dans un style non bloquant. Si l’opération ne peut pas se termine immédiatement, la fonction de pilote doit retourner SQL_STILL_EXECUTING. Cela est vrai pour le mode d’interrogation et le mode de notification.  
  
 Si un handle est en mode asynchrone de notification, le pilote doit appeler la fonction de rappel de notification, dont l’adresse est la valeur de l’attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK ou SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK, une seule fois après retour de SQL_STILL_EXECUTING. En d’autres termes, une SQL_STILL_EXECUTING de retour doit être associé à un appel de la fonction de rappel de notification. Le pilote doit utiliser la valeur actuelle de l’attribut de handle SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT ou SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT comme valeur pour le paramètre d’appel de fonction de rappel *pContext*.  
  
 Le pilote ne doit pas effectuer de rappel dans le thread qui appelle la fonction de pilote ; Il est inutile pour notifier les cours avant le retour de la fonction. Le pilote doit utiliser son propre thread au rappel. Le Gestionnaire de pilotes n’utilisera pas de thread de rappel du pilote pour l’exécution de logiques d’un traitement complet.  
  
 Le Gestionnaire de pilotes appelle à nouveau la fonction d’origine une fois que le pilote envoie un rappel. Le Gestionnaire de pilote peut utiliser un thread qui n’est ni un thread d’application ni à un thread de pilote. Si le pilote utilise certaines informations associées au thread (par exemple, identificateur utilisateur ou le jeton de sécurité), le pilote doit enregistrer les informations requises dans l’appel asynchrone initiale et utiliser la valeur enregistrée avant l’opération asynchrone entière se termine. En règle générale, seuls **SQLDriverConnect**, **SQLConnect**, ou **SQLBrowseConnect** devez utiliser ce type d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
