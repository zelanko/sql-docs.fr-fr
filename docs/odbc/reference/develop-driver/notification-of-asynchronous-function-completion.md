---
title: Notification de l’achèvement de la fonction asynchrone (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 336565da-4203-4745-bce2-4f011c08e357
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a453967f2ffdda4af2a44429737f700f4a994cf8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287819"
---
# <a name="notification-of-asynchronous-function-completion"></a>Notification de la fin d’une fonction asynchrone
Dans le Windows 8 SDK, ODBC a ajouté un mécanisme pour aviser les applications lorsqu’une opération asynchrone se termine, que nous appellerons la « notification à l’achèvement ». (Voir [Asynchrone Execution (Méthode de notification)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md) pour plus d’informations.) Ce sujet traite de quelques-unes des questions pour les développeurs de pilotes.  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>L’interface entre le Driver Manager et le Driver  
 Le Driver Manager fournit à l’interne une fonction de rappel [SQLAsyncNotificationCallback fonction](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md). **SQLAsyncNotificationCallback** ne peut être appelé que par le conducteur - une application ne peut pas l’appeler directement. Le conducteur appelle **SQLAsyncNotificationCallback** chaque fois que de nouvelles données reçues du serveur après le retour SQL_STILL_EXECUTING dernier.  
  
 Le gestionnaire de conducteur fournit un mécanisme de rappel afin qu’un conducteur puisse aviser le gestionnaire de conducteur lorsque des progrès ont été réalisés dans l’exécution d’une opération asynchrone après le retour de la fonction correspondante SQL_STILL_EXECUTING  
  
 Le gestionnaire de conducteur définit l’attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK sur une poignée de connexion du conducteur avec un pointeur de fonction non-NULL, qui est de type SQL_ASYNC_NOTIFICATION_CALLBACK, pour le conducteur de travailler en mode de notification pour toute opération asynchrone sur cette poignée. De même, le gestionnaire de conducteur définit l’attribut SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK sur une poignée de relevé de pilote avec un pointeur de fonction non-NULL, qui est également de type SQL_ASYNC_NOTIFICATION_CALLBACK, pour le conducteur de travailler en mode de notification pour toute opération asynchrone sur cette poignée.  
  
 Si une opération asynchrone est effectuée sur une poignée de conducteur, les fonctions asynchrones du conducteur doivent fonctionner dans un style non-blocage. Si l’opération ne peut pas se terminer immédiatement, la fonction du conducteur doit retourner SQL_STILL_EXECUTING. Cette exigence est valable tant pour le mode de scrutin que pour le mode notification.  
  
 Si une poignée est en mode notification asynchrone, le conducteur doit appeler la fonction de rappel de notification, dont l’adresse est la valeur pour l’attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK ou SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK, une fois après le retour SQL_STILL_EXECUTING. En d’autres termes, un SQL_STILL_EXECUTING de retour doit être jumelé à une invocation de la fonction de rappel de notification. Le conducteur doit utiliser la valeur actuelle de l’attribut de poignée SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT ou SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT de poignée comme valeur pour le paramètre de fonction de rappel *pContext*.  
  
 Le conducteur ne doit pas rappeler dans le fil qui appelle la fonction du conducteur; il n’y a aucune raison d’aviser les progrès avant le retour de la fonction. Le conducteur doit utiliser son propre thread pour rappeler. Le Gestionnaire de pilote n’utilisera pas le fil de rappel du conducteur pour l’exécution d’une logique de traitement étendue.  
  
 Le gestionnaire de conducteur appellera à nouveau la fonction d’origine après que le conducteur rappelle. Le Gestionnaire de pilote peut utiliser un thread qui n’est ni un thread d’application ni un thread de pilote. Si le conducteur utilise certaines informations associées au thread (par exemple, le jeton de sécurité ou l’identifiant de l’utilisateur), le conducteur doit enregistrer les informations requises dans l’appel asynchrone initial et utiliser la valeur enregistrée avant que l’opération asynchrone entière se termine. Habituellement, seuls **SQLDriverConnect**, **SQLConnect**, ou **SQLBrowseConnect** doivent utiliser ce genre d’information.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
