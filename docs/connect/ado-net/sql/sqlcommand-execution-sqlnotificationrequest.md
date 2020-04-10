---
title: Exécution de SqlCommand avec une SqlNotificationRequest
description: Illustre la configuration d’un objet SqlCommand pour travailler avec une notification de requête.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 1ad2fd2f29c7218d1da0535ca089e2648d4b0cf0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80918686"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Exécution de SqlCommand avec une SqlNotificationRequest

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Une <xref:Microsoft.Data.SqlClient.SqlCommand> peut être configurée pour générer une notification lorsque les données sont modifiées après avoir été extraites du serveur et que le jeu de résultats serait différent si la requête était exécutée à nouveau. Cela est utile dans les scénarios où vous souhaitez utiliser des files d’attente de notification personnalisées sur le serveur ou lorsque vous ne souhaitez pas conserver d’objets actifs.

## <a name="creating-the-notification-request"></a>Création de la demande de notification

Vous pouvez utiliser un objet <xref:Microsoft.Data.Sql.SqlNotificationRequest> pour créer la demande de notification en le liant à un objet `SqlCommand`. Une fois la requête créée, vous n’avez plus besoin de l’objet `SqlNotificationRequest`. Vous pouvez interroger la file d’attente pour toutes les notifications et y répondre de manière appropriée. Des notifications peuvent se produire même si l’application est arrêtée et redémarrée par la suite.

Quand la commande avec la notification associée est exécutée, toute modification du jeu de résultats déclenche l’envoi d’un message à la file d’attente SQL Server qui a été configurée dans la demande de notification.

La manière dont vous interrogez la file d’attente SQL Server et interprétez le message est propre à votre application. L’application est responsable de l’interrogation de la file d’attente et de la réaction en fonction du contenu du message.

> [!NOTE]
> Lors de l’utilisation des requêtes de notification SQL Server avec <xref:Microsoft.Data.SqlClient.SqlDependency>, créez votre propre nom de file d’attente au lieu d’utiliser le nom de service par défaut.

Il n’existe aucun nouvel élément de sécurité côté client pour <xref:Microsoft.Data.Sql.SqlNotificationRequest>. Il s’agit principalement d’une fonctionnalité serveur, et le serveur a créé des privilèges spéciaux que les utilisateurs doivent posséder pour demander une notification.

### <a name="example"></a>Exemple

Le fragment de code suivant montre comment créer une <xref:Microsoft.Data.Sql.SqlNotificationRequest> et l’associer à une <xref:Microsoft.Data.SqlClient.SqlCommand>.

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="next-steps"></a>Étapes suivantes
- [Notifications de requête dans SQL Server](query-notifications-sql-server.md)
