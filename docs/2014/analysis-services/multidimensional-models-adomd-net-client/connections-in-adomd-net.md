---
title: Établissement de connexions dans ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- opening connections
- closing connections
- connections [ADOMD.NET]
- ADOMD.NET, connections
ms.assetid: 7b9610f5-6641-42cc-af4e-bd35771913d1
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d7bf4529df77545cf2d0acf69af5d0b570ef750
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165300"
---
# <a name="establishing-connections-in-adomdnet"></a>Établissement de connexions dans ADOMD.NET
  Dans ADOMD.NET, vous allez utiliser le <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> objet pour ouvrir des connexions avec les sources de données analytiques, telles que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bases de données. Lorsque vous n'avez plus besoin de la connexion, vous devez la fermer explicitement.  
  
## <a name="opening-a-connection"></a>Ouverture d'une connexion  
 Pour ouvrir une connexion dans ADOMD.NET, vous devez d'abord spécifier une chaîne de connexion à une source de données analytiques et à une base de données valides. Vous devez ensuite ouvrir explicitement la connexion à cette source de données.  
  
### <a name="specifying-a-multidimensional-data-source"></a>Spécification d'une source de données multidimensionnelles  
 Pour spécifier une source de données analytiques et une base de données, vous devez définir la propriété <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. La chaîne de connexion spécifiée pour la propriété <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> est une chaîne compatible OLE DB. ADOMD.NET utilise la chaîne de connexion spécifiée pour déterminer le mode de connexion au serveur.  
  
 La propriété <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> peut être définie sur un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> existant ou lors de la création d'une instance d'un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Le code suivant montre comment définir la propriété <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> lorsque vous créez une connexion ADOMD :  
  
```vb  
Dim advwrksConnection As New AdomdConnection("Data Source=localhost;Catalog=AdventureWorksAS")  
System.Diagnostics.Debug.Writeline(advwrksConnection.ConnectionString)  
```  
  
```csharp  
AdomdConnection advwrksConnection = new AdomdConnection("Data Source=localhost;Catalog=AdventureWorksAS");  
System.Diagnostics.Debug.Writeline(advwrksConnection.ConnectionString);  
```  
  
### <a name="opening-a-connection-to-the-data-source"></a>Ouverture d'une connexion à la source de données  
 Après avoir spécifié la chaîne de connexion, vous devez utiliser la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> pour ouvrir la connexion. Lorsque vous ouvrez un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, vous pouvez définir différents niveaux de sécurité pour la connexion. Le niveau de sécurité utilisé pour la connexion dépend de la valeur du paramètre de chaîne de connexion `ProtectionLevel`. Pour plus d’informations sur l’ouverture des connexions sécurisées dans ADOMD.NET, consultez [l’établissement des connexions sécurisées dans ADOMD.NET](connections-in-adomd-net-establishing-secure-connections.md).  
  
## <a name="working-with-a-connection"></a>Utilisation d'une connexion  
 Chaque connexion ouverte existe dans le cadre d'une session, qui fournit une prise en charge des opérations avec état. Une session peut être partagée par plusieurs connexions ouvertes. Le partage d'une session permet à plusieurs clients de partager un même contexte. Pour plus d’informations, consultez [utilisation des connexions et Sessions dans ADOMD.NET](../multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md).  
  
 Vous pouvez utiliser une connexion ouverte pour récupérer des métadonnées et des données et exécuter des commandes. Pour plus d’informations, consultez [récupération de métadonnées à partir d’une Source de données analytiques](retrieving-metadata-from-an-analytical-data-source.md), [extraction de données à partir d’une Source de données analytiques](retrieving-data-from-an-analytical-data-source.md), et [l’exécution de commandes par rapport à une données analytiques Source](executing-commands-against-an-analytical-data-source.md).  
  
 Lorsque la connexion est ouverte, vous pouvez récupérer des données, extraire des métadonnées et exécuter des commandes à partir d'une transaction validée en lecture, dans laquelle les verrous partagés sont maintenus pendant la lecture des données afin d'éviter des lectures erronées. Les données peuvent toujours être modifiées avant la fin de la transaction, ce qui provoque des lectures non renouvelables ou des données fantômes. Pour plus d’informations, consultez [exécution de Transactions dans ADOMD.NET](../../relational-databases/native-client-ole-db-transactions/transactions.md).  
  
## <a name="closing-a-connection"></a>Fermeture d'une connexion  
 Nous vous recommandons de fermer explicitement un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> dès lors que vous n'avez plus besoin de la connexion. Pour fermer explicitement la connexion, vous devez utiliser les méthodes `Close` et `Dispose` de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Une connexion qui n'est pas explicitement fermée mais qui est autorisée à se situer hors de portée risque de ne pas diffuser assez rapidement les ressources du serveur pour permettre à des applications clientes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] soumises à une forte concurrence d'accès d'ouvrir efficacement de nouvelles connexions. Selon la façon dont vous avez créé la connexion, la session utilisée par l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> peut rester active si la connexion n'est pas fermée explicitement.  
  
 Pour plus d’informations sur les sessions, consultez [utilisation des connexions et Sessions dans ADOMD.NET](../multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md).  
  
> [!IMPORTANT]  
>  Dans la méthode `Finalize` d'une classe implémentée, évitez d'appeler les méthodes `Close` ou `Dispose` d'un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> ou de tout autre objet managé. Dans un finaliseur, veillez à ne diffuser que des ressources non managées qui sont directement détenues par la classe implémentée. Si la classe implémentée n'est pas propriétaire de certaines ressources non managées, évitez d'inclure une méthode `Finalize` dans la définition de cette classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation du client ADOMD.NET](adomd-net-client-programming.md)  
  
  
