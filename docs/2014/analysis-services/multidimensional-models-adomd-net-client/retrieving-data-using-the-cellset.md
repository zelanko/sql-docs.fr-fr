---
title: La récupération des données à l’aide de l’ensemble de cellules | Documents Microsoft
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
- CellSet object
- retrieving data
- data retrieval [ADOMD.NET], CellSet object
ms.assetid: 77e4ee58-882d-4012-91a3-0565f18a4882
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cda35dc6151d17e1dad2d341337d67ef39d9f839
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050934"
---
# <a name="retrieving-data-using-the-cellset"></a>Récupération de données à l'aide d'un ensemble de cellules
  Lors de la récupération de données analytiques, l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> procure une interactivité et une souplesse optimales. L'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> est un cache de données et métadonnées hiérarchiques en mémoire qui préserve la dimensionnalité des données. L'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> peut également être parcouru en état connecté ou déconnecté. Du fait de cette aptitude en état déconnecté, l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> peut être utilisé pour consulter les données et les métadonnées dans n'importe quel ordre et constitue le modèle objet le plus complet pour la récupération de données. Autre conséquence de cette aptitude en état déconnecté : l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> subit une charge maximale, et il s'agit du modèle objet de récupération de données ADOMD.NET le plus long à remplir.  
  
## <a name="retrieving-data-in-a-connected-state"></a>Récupération de données en état connecté  
 Pour utiliser l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> afin de récupérer des données, procédez comme suit :  
  
1.  **Créer une nouvelle instance de l’objet.**  
  
     Pour créer une nouvelle instance de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, vous devez appeler la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> ou <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
2.  **Identifiez les métadonnées.**  
  
     En plus de récupérer les données, ADOMD.NET récupère également les métadonnées pour l'ensemble de cellules. Dès que la commande a exécuté la requête et a retourné un objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, vous pouvez récupérer les métadonnées par le biais de différents objets. Ces métadonnées sont nécessaires aux applications clientes en vue d'afficher et d'interagir avec les données d'ensemble de cellules. Par exemple, de nombreuses applications clientes proposent des fonctionnalités qui permettent d'explorer vers le bas une position spécifiée dans un ensemble de cellules, c'est-à-dire, d'en afficher hiérarchiquement les positions enfants.  
  
     Dans ADOMD.NET, les propriétés <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Axes%2A> et <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.FilterAxis%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> représentent les métadonnées des axes de requête et de secteur, respectivement, dans l'ensemble de cellules retourné. Ces deux propriétés retournent des références à des objets <xref:Microsoft.AnalysisServices.AdomdClient.Axis>, qui de leur côté contiennent les positions représentées sur chaque axe.  
  
     Chaque objet <xref:Microsoft.AnalysisServices.AdomdClient.Axis> contient une collection d'objets <xref:Microsoft.AnalysisServices.AdomdClient.Position> qui représentent l'ensemble de tuples disponibles pour l'axe en question. Chaque objet <xref:Microsoft.AnalysisServices.AdomdClient.Position> représente un tuple unique qui contient un ou plusieurs membres, représenté(s) par une collection d'objets <xref:Microsoft.AnalysisServices.AdomdClient.Member>.  
  
3.  **Récupérer des données à partir de la collection de l’ensemble de cellules.**  
  
     En plus de récupérer les métadonnées, ADOMD.NET récupère également les données pour l'ensemble de cellules. Dès que la commande a exécuté la requête et a retourné un <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, vous pouvez récupérer les données en utilisant la collection <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Cells%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>. Cette collection contient les valeurs calculées pour l'intersection de tous les axes de la requête. Par conséquent, il existe plusieurs indexeurs pour accéder à chaque intersection (ou cellule). Pour obtenir une liste d'indexeurs, consultez <xref:Microsoft.AnalysisServices.AdomdClient.CellCollection.Item%2A>.  
  
### <a name="example-of-retrieving-data-in-a-connected-state"></a>Exemple de récupération de données en état connecté  
 L'exemple suivant établit une connexion au serveur local, puis exécute une commande sur la connexion. Il analyse les résultats à l'aide du modèle objet `CellSet` : les légendes (métadonnées) des colonnes sont récupérées à partir du premier axe, tandis que les légendes (métadonnées) de chaque ligne sont récupérées à partir du deuxième axe. Enfin, les données d'intersection sont récupérées par l'intermédiaire de la collection <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Cells%2A>.  
  
 [!code-csharp[Adomd.NetClient#ReturnCommandUsingCellSet](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#returncommandusingcellset)]  
  
## <a name="retrieving-data-in-a-disconnected-state"></a>Récupération de données en état déconnecté  
 En chargeant les données XML retournées par une requête précédente, vous pouvez utiliser l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> pour fournir une méthode complète d'exploration des données analytiques sans qu'il soit nécessaire de disposer d'une connexion active.  
  
> [!NOTE]  
>  En état déconnecté, certaines propriétés des objets disponibles à partir de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> ne sont pas disponibles. Pour plus d’informations, consultez <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.LoadXml%2A>.  
  
### <a name="example-of-retrieving-data-in-a-disconnected-state"></a>Exemple de récupération de données en état déconnecté  
 L'exemple suivant est similaire à l'exemple de métadonnées et de données présenté précédemment dans cette rubrique. Toutefois, dans cet exemple, la commande est exécutée avec un appel à <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>, et le résultat est retourné sous forme de `System.Xml.XmlReader`. L'exemple remplit ensuite l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> en utilisant ce `System.Xml.XmlReader` avec la méthode <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.LoadXml%2A>. Bien que cet exemple charge immédiatement le `System.Xml.XmlReader`, vous pouvez mettre en cache les données XML contenues dans le lecteur sur un disque dur ou les transporter vers une autre application par quelque moyen que ce soit avant de les charger dans un ensemble de cellules.  
  
 [!code-csharp[Adomd.NetClient#DemonstrateDisconnectedCellset](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#demonstratedisconnectedcellset)]  
  
## <a name="see-also"></a>Voir aussi  
 [La récupération des données à partir d’une Source de données analytiques](retrieving-data-from-an-analytical-data-source.md)   
 [La récupération des données à l’aide d’AdomdDataReader](retrieving-data-using-the-adomddatareader.md)   
 [Récupération de données à l’aide de XmlReader](retrieving-data-using-the-xmlreader.md)  
  
  