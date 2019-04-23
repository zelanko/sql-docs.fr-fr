---
title: Fonctionnalités serveur ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cc127a8bafc9ad2f53465caeca013d5033e5c396
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60154375"
---
# <a name="adomdnet-server-functionality"></a>Fonctionnalités serveur ADOMD.NET
  Tous les objets serveur ADOMD.NET fournissent un accès en lecture seule aux données et aux métadonnées présentes sur le serveur. Pour récupérer les données et les métadonnées, vous devez utiliser le modèle d'objet serveur ADOMD.NET, car le modèle d'objet serveur ne prend pas en charge les ensembles de lignes de schéma.  
  
 Avec des objets serveur ADOMD.NET, vous pouvez créer une fonction définie par l’utilisateur (UDF) ou une procédure stockée pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Ces méthodes in-process sont appelées par l'intermédiaire d'instructions de requête créées dans des langages tels que MDX (Multidimensional Expressions), DMX (Data Mining Extensions) ou SQL. Ces méthodes in-process fournissent également des fonctionnalités supplémentaires sans les temps d'attente inhérents aux communications réseau.  
  
> [!NOTE]  
>  L'objet <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> ne prend en charge que le langage DMX.  
  
## <a name="what-is-a-udf"></a>Qu'est qu'une fonction définie par l'utilisateur ?  
 Un *UDF* est une méthode qui présente les caractéristiques suivantes :  
  
-   Vous pouvez appeler une fonction définie par l'utilisteur dans le contexte d'une requête.  
  
-   Une fonction définie par l'utilisateur peut prendre un nombre illimité de paramètres.  
  
-   Une fonction définie par l'utilisateur peut retourner divers types de données.  
  
 L'exemple suivant utilise la fonction définie par l'utilisateur fictive `FinalSalesNumber` :  
  
```  
SELECT SalesPerson.Name ON ROWS,  
       FinalSalesNumber() ON COLUMNS  
FROM SalesModel  
```  
  
## <a name="what-is-a-stored-procedure"></a>Qu'est-ce qu'une procédure stockée ?  
 Un *procédure stockée* est une méthode qui présente les caractéristiques suivantes :  
  
-   Vous appelez une procédure stockée sur son propre avec MDX [appeler](/sql/mdx/mdx-data-manipulation-call) instruction.  
  
-   Une procédure stockée peut prendre un nombre illimité de paramètres.  
  
-   Une procédure stockée peut retourner un jeu de données, un `IDataReader` ou un résultat vide.  
  
 L'exemple suivant utilise la procédure stockée fictive `FinalSalesNumbers` :  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation du serveur ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
