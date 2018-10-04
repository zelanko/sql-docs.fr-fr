---
title: Récupération des données à l’aide de XmlReader | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- retrieving data
- XmlReader object
- data retrieval [ADOMD.NET], XmlReader object
ms.assetid: 420ec40e-be2d-413a-b4b2-6d2b1756e270
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: caa8ef058839fb3c97a9e3dfdf6022dd91bc2053
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165689"
---
# <a name="retrieving-data-using-the-xmlreader"></a>Récupération de données à l'aide de XmlReader
  La classe `XmlReader`, qui fait partie de l'espace de noms `System.Xml` de la bibliothèque de classes Microsoft .NET Framework, est similaire à la classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> en ce sens que la classe `XmlReader` offre également un accès aux données rapide, sans mise en cache et avant uniquement. S'il n'est pas utile d'obtenir une vue analytique en mémoire des données avec l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, l'objet `XmlReader` est parfait pour récupérer des données XML, surtout lorsqu'il s'agit de grandes quantités de données. Étant donné que `XmlReader` transmet les données en continu, `XmlReader` n'a pas besoin de récupérer et mettre en cache l'ensemble des données avant de les exposer à l'appelant, comme ce serait le cas si un objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> était utilisé pour convertir la réponse XMLA en une représentation du modèle objet analytique.  
  
 La classe `XmlReader` fournit un accès direct à la réponse XMLA reçue par ADOMD.NET lorsque la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> est appelée. Les données étant récupérées dans un format XML brut, vous devez analyser les données et les métadonnées manuellement. Aussitôt que les données ont été récupérées, l'objet `XmlReader` doit être fermé.  
  
## <a name="retrieving-data-and-metadata"></a>Récupération de données et de métadonnées  
 Pour récupérer des données à l'aide de la classe `XmlReader`, procédez comme suit :  
  
1.  **Créer une nouvelle instance de l’objet.**  
  
     Pour créer une nouvelle instance de la classe `XmlReader`, vous devez appeler la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> ou <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
2.  **Récupérer des données.**  
  
     Une fois que la commande a exécuté la requête et qu'un `XmlReader` a été retourné, vous devez analyser les données et les métadonnées. Les données et les métadonnées XML sont présentées dans le format natif utilisé par le fournisseur XMLA. Le format natif de la plupart des fournisseurs XMLA est le format `MDDataSet`. Le format `MDDataSet` fournit les données et les métadonnées pour les ensembles de cellules dans un format bien structuré. Pour plus d'informations sur le format `MDDataSet`, consultez la spécification XML for Analysis.  
  
3.  **Fermez le lecteur.**  
  
     Vous devez toujours appeler la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> lorsque vous avez fini d'utiliser l'objet `XmlReader`. Lorsqu'un `XmlReader` est ouvert, celui-ci `XmlReader` a une utilisation exclusive de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> qui a été utilisé pour exécuter la commande. Vous ne serez pas en mesure d'exécuter des commandes par le biais de cet objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, y compris de créer un autre objet `XmlReader` ou <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, tant que vous n'aurez pas fermé le `XmlReader` initial.  
  
### <a name="example-of-retrieving-data-from-the-xmlreader"></a>Exemple de récupération de données à partir de XmlReader  
 L'exemple suivant exécute une commande et récupère les données sous forme de `XmlReader` en sortant le contenu du fichier à destination de la console.  
  
 [!code-csharp[Adomd.NetClient#OutputDataWithXML](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#outputdatawithxml)]  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération des données à partir d’une Source de données analytiques](retrieving-data-from-an-analytical-data-source.md)   
 [Récupération des données à l’aide de l’ensemble de cellules](retrieving-data-using-the-cellset.md)   
 [Récupération de données à l’aide d’AdomdDataReader](retrieving-data-using-the-adomddatareader.md)  
  
  
