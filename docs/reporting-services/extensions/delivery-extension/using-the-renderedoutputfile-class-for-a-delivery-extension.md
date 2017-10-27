---
title: "À l’aide de la classe RenderedOutputFile pour une Extension de remise | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 35fa7b98c43bb20ef6df30f27ca74a5f2ada1792
ms.contentlocale: fr-fr
ms.lasthandoff: 08/14/2017

---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a>Utilisation de la classe RenderedOutputFile pour une extension de remise
  La classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> représente un flux de données et des informations relatives aux propriétés associées du flux de données. Le **données** propriété de la <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> classe est utilisée pour représenter un rapport rendu ou la ressource de rapport comme un **flux** objet.  
  
 Le <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> méthode de la **rapport** objet retourne un tableau d’un ou plusieurs <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objets qui constituent un rapport rendu unique. Le premier objet <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> est le rapport rendu. Les autres objets <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> sont des ressources qui doivent être remises avec les données du rapport (par exemple, un fichier HTML et les images associées). Les extensions de rendu qui sont des extensions de rendu de flux unique (IMAGE, PDF, MHTML et EXCEL) renvoient un seul objet <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> dans le tableau.  
  
 Pour obtenir un exemple montrant comment utiliser les <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> de classe, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une Extension de remise](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

