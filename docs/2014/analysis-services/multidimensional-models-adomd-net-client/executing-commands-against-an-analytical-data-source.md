---
title: L’exécution de commandes sur une Source de données analytiques | Documents Microsoft
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
- AdomdCommand object
- commands [ADOMD.NET]
- ADOMD.NET, commands
ms.assetid: 1a958e5f-fc18-480b-9706-fc44e3b1d534
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5752a4420190475e4c192cc02030892ec0f41968
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142919"
---
# <a name="executing-commands-against-an-analytical-data-source"></a>Exécution de commandes sur une source de données analytiques
  Après avoir établi une connexion à une source de données analytiques, vous pouvez utiliser un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> pour exécuter des commandes sur cette source de données et en obtenir les résultats. Ces commandes permettent de récupérer des données via MDX (Multidimensional Expressions), DMX (Data Mining Extensions), voire une syntaxe limitée de SQL. En outre, vous pouvez utiliser des commandes ASSL (Analysis Services Scripting Language) pour modifier la base de données sous-jacente.  
  
## <a name="creating-a-command"></a>Création d'une commande  
 Avant d'exécuter une commande, vous devez la créer. Pour ce faire, vous pouvez employer deux méthodes différentes :  
  
-   La première méthode consiste à utiliser le constructeur <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, qui peut prendre une commande à exécuter au niveau de la source de données, et un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> sur lequel la commande doit être exécutée.  
  
-   La deuxième méthode fait appel à la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.CreateCommand%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Le texte de la commande à exécuter peut être interrogé et modifié à l'aide de la propriété <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.CommandText%2A>. Les commandes que vous créez ne retournent pas nécessairement de données après avoir été exécutées.  
  
## <a name="running-a-command"></a>Exécution d’une commande  
 Une fois que vous avez créé un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, votre commande peut employer plusieurs méthodes <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> pour effectuer diverses actions. Le tableau ci-dessous répertorie certaines de ces actions.  
  
|Pour|Utiliser la méthode|  
|--------|---------------------|  
|Retourner les résultats sous forme de flux de données|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> pour retourner un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|  
|Retourner un objet <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A>|  
|Exécuter des commandes qui ne retournent pas de lignes|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteNonQuery%2A>|  
|Retourner un objet `XMLReader` qui contient les données dans un format compatible XMLA (XML for Analysis)|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>Exemple d'exécution d'une commande  
 Cet exemple utilise l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> pour exécuter une commande XMLA qui traitera le cube `Adventure Works DW` sur le serveur local, sans retourner de données.  
  
 [!code-csharp[Adomd.NetClient#ExecuteXMLAProcessCommand](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#executexmlaprocesscommand)]  
  
  