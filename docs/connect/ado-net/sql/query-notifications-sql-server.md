---
title: Notifications de requête dans SQL Server
description: Décrit comment les applications .NET peuvent demander une notification à partir d’SQL Server lorsque les données ont changé.
ms.date: 08/15/2019
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: d47241e3656e3ca7b4f5ea0eebe9f2cc8b571bf6
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452073"
---
# <a name="query-notifications-in-sql-server"></a>Notifications de requête dans SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Basées sur l’infrastructure de Service Broker, les notifications de requêtes permettent aux applications d’être notifiées en cas de modification des données. Cette fonctionnalité est particulièrement utile pour les applications qui fournissent un cache d'informations à partir d'une base de données, par exemple une application Web, et qui doivent être notifiées en cas de modification des données sources.  
  
Il existe trois façons d’implémenter des notifications de requête à l’aide de ADO.NET :  
  
- L’implémentation de bas niveau est fournie par la classe `SqlNotificationRequest` qui expose les fonctionnalités côté serveur, ce qui vous permet d’exécuter une commande avec une demande de notification.  
  
- L’implémentation de haut niveau est fournie par la classe `SqlDependency`, qui est une classe qui fournit une abstraction de haut niveau de la fonctionnalité de notification entre l’application source et SQL Server, ce qui vous permet d’utiliser une dépendance pour détecter les modifications apportées au serveur. Généralement, il s’agit de la manière la plus simple et la plus efficace, pour des applications clientes managées, d’exploiter les fonctionnalités de notification de SQL Server en utilisant le fournisseur de données Microsoft SqlClient pour SQL Server.  
  
- De plus, les applications web créées avec ASP.NET 2.0 ou ultérieur peuvent utiliser les classes d’assistance `SqlCacheDependency`.  
  
Les notifications de requêtes sont utilisées pour les applications qui doivent actualiser des affichages ou des caches en réponse aux modifications apportées aux données sous-jacentes. Microsoft SQL Server permet aux applications .NET d’envoyer une commande à SQL Server et de demander la génération d’une notification si l’exécution de cette commande produit des ensembles de résultats différents de ceux extraits initialement. Les notifications générées au niveau du serveur sont envoyées par l’intermédiaire de files d’attente pour un traitement ultérieur.  
  
Vous pouvez configurer des notifications pour les instructions SELECT et EXECUTe. Lors de l’utilisation d’une instruction EXECUTe, SQL Server inscrit une notification pour la commande exécutée plutôt que l’instruction EXECUTe elle-même. La commande doit satisfaire les exigences et limitations applicables aux instructions SELECT. Quand une commande qui enregistre une notification contient plusieurs instructions, le moteur de base de données crée une notification pour chaque instruction du traitement.  
  
Si vous développez une application où vous avez besoin de notifications à la fraction de seconde fiables quand les données sont modifiées, consultez les sections **Planification d’une stratégie efficace de notifications de requête** et **Alternatives aux notifications de requête** dans la rubrique [Planification des notifications](https://go.microsoft.com/fwlink/?LinkId=211984) de la Documentation en ligne de SQL Server. Pour plus d’informations sur les notifications et les SQL Server Service Brokers de requêtes, consultez les liens suivants vers les rubriques de Documentation en ligne de SQL Server.  
  
**Documentation SQL Server**  
  
- [Utilisation des notifications de requêtes](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Création d’une requête pour notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Développement (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Centre d’informations du développeur Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Guide du développeur (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>Contenu de cette section  
[Activation de notifications de requête](enable-query-notifications.md)  
Explique comment utiliser les notifications de requêtes, notamment la configuration requise pour l’activation et l’utilisation de ces notifications.  
  
[SqlDependency dans une application ASP.NET](sqldependency-aspnet-app.md)  
Montre comment utiliser des notifications de requête à partir d’une application ASP.NET.  
  
[Détection des changements avec SqlDependency](detect-changes-sqldependency.md)  
Montre comment détecter si les résultats de la requête sont différents de ceux qui ont été reçus à l’origine.  
  
[Exécution de SqlCommand avec une SqlNotificationRequest](sqlcommand-execution-sqlnotificationrequest.md)  
Illustre la configuration d’un objet <xref:Microsoft.Data.SqlClient.SqlCommand> pour qu’il fonctionne avec une notification de requête.  
  
## <a name="reference"></a>Référence  
<xref:Microsoft.Data.Sql.SqlNotificationRequest>  
Décrit la classe <xref:Microsoft.Data.Sql.SqlNotificationRequest> et tous ses membres.  
  
<xref:Microsoft.Data.SqlClient.SqlDependency>  
Décrit la classe <xref:Microsoft.Data.SqlClient.SqlDependency> et tous ses membres.  
  
<xref:System.Web.Caching.SqlCacheDependency>  
Décrit la classe <xref:System.Web.Caching.SqlCacheDependency> et tous ses membres.  
  
## <a name="next-steps"></a>Étapes suivantes
- [SQL Server et ADO.NET](index.md)
