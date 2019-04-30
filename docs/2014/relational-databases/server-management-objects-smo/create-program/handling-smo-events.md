---
title: Gestion des événements SMO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- events [SMO]
- SQL Server Management Objects, events
- SMO [SQL Server], events
- events [SMO], about events
ms.assetid: b4f120dd-ba78-46ff-99c5-e47effac8544
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d0d309103880a369a88952e19b252fc15693fdd4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63191918"
---
# <a name="handling-smo-events"></a>Gestion des événements SMO
  Il existe des types d'événement de serveur auxquels il est possible de s'abonner en utilisant un gestionnaire d'événements et l'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
 De nombreuses classes d'instance dans SMO [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects) peuvent déclencher des événements lorsque certaines actions se produisent sur le serveur.  
  
 Ces événements peuvent être contrôlés par programme en installant un gestionnaire d'événements et en s'abonnant aux événements associés. Ce type de gestion des événements est transitoire car tous les abonnements sont supprimés lorsque le programme client SMO prend fin.  
  
## <a name="connectioncontext-event-handling"></a>Gestion des événements ConnectionContext  
 L'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection> prend en charge plusieurs types d'événement. La propriété d'événement doit être définie sur une instance d'un gestionnaire d'événements approprié, et l'objet gestionnaire d'événements doit être défini comme une fonction protégée qui gère l'événement.  
  
## <a name="event-subscription"></a>Abonnement à un événement  
 Pour gérer des événements, vous devez écrire une classe de gestionnaire d'événements, créer une instance de cet événement, attribuer le gestionnaire d'événements à l'objet parent, puis vous abonner à l'événement.  
  
 La gestion d'événements requiert l'écriture d'une classe de gestionnaire d'événements. La classe de gestionnaire d'événements peut contenir plusieurs fonctions de gestionnaire d'événements et doit être installée pour les événements à gérer. Les fonctions de gestionnaire d’événements recevoir des informations sur l’événement à partir de la *ServerEventNotificatificationArgs* paramètre qui peut être utilisé pour signaler des informations sur l’événement.  
  
 Les types d’événements de base de données et de serveur qui peuvent être gérées sont répertoriés dans le <xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet> classe et la <xref:Microsoft.SqlServer.Management.Smo.ServerEventSet>classe.  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-basic"></a>Enregistrement de gestionnaires d'événements et abonnement à la gestion des événements en Visual Basic  
 Cet exemple de code montre comment configurer le gestionnaire d'événements et comment s'abonner aux événements de base de données.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEvents1](SMO How to#SMO_VBEvents1)]  -->  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-c"></a>Enregistrement de gestionnaires d'événements et abonnement à la gestion des événements en Visual C#  
 Cet exemple de code montre comment configurer le gestionnaire d'événements et comment s'abonner aux événements de base de données.  
  
```  
//Create an event handler subroutine that runs when a table is created.   
private void MyCreateEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been added to the AdventureWorks2012 database.");   
}   
//Create an event handler subroutine that runs when a table is deleted.   
private void MyDropEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been dropped from the AdventureWorks2012 database.");   
}   
public void Main()   
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Create a database event set that contains the CreateTable event only.   
DatabaseEventSet databaseCreateEventSet = new DatabaseEventSet();   
databaseCreateEventSet.CreateTable = true;   
//Create a server event handler and set it to the first event handler subroutine.   
ServerEventHandler serverCreateEventHandler;   
serverCreateEventHandler = new ServerEventHandler(MyCreateEventHandler);   
//Subscribe to the first server event handler when a CreateTable event occurs.   
db.Events.SubscribeToEvents(databaseCreateEventSet, serverCreateEventHandler);   
    //Create a database event set that contains the DropTable event only.   
DatabaseEventSet databaseDropEventSet = new DatabaseEventSet();   
databaseDropEventSet.DropTable = true;   
//Create a server event handler and set it to the second event handler subroutine.   
ServerEventHandler serverDropEventHandler;   
serverDropEventHandler = new ServerEventHandler(MyDropEventHandler);   
//Subscribe to the second server event handler when a DropTable event occurs.   
db.Events.SubscribeToEvents(databaseDropEventSet, serverDropEventHandler);   
//Start event handling.   
db.Events.StartEvents();   
//Create a table on the database.   
Table tb;   
tb = new Table(db, "Test_Table");   
Column mycol1;   
mycol1 = new Column(tb, "Name", DataType.NChar(50));   
mycol1.Collation = "Latin1_General_CI_AS";   
mycol1.Nullable = true;   
tb.Columns.Add(mycol1);   
tb.Create();   
//Remove the table.   
tb.Drop();   
//Wait until the events have occured.   
int x;   
int y;   
for (x = 1; x <= 1000000000; x++) {   
    y = x * 2;   
}   
//Stop event handling.   
db.Events.StopEvents();   
}  
```  
  
  
