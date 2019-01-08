---
title: Utilisation de la classe RenderedOutputFile pour une extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5c2fa313e594dae2cfac69684770e77908c56eff
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53352609"
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a>Utilisation de la classe RenderedOutputFile pour une extension de remise
  La classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> représente un flux de données et des informations relatives aux propriétés associées du flux de données. La propriété **Data** de la classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> est utilisée pour représenter un rapport rendu ou signaler une ressource en tant qu’objet **Stream**.  
  
 La méthode <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> de l’objet **Report** retourne un tableau d’un ou plusieurs objets <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> qui constituent un rapport rendu unique. Le premier objet <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> est le rapport rendu. Les autres objets <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> sont des ressources qui doivent être remises avec les données du rapport (par exemple, un fichier HTML et les images associées). Les extensions de rendu qui sont des extensions de rendu de flux unique (IMAGE, PDF, MHTML et EXCEL) renvoient un seul objet <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> dans le tableau.  
  
 Pour un exemple d’utilisation de la classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une extension de remise](implementing-a-delivery-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
