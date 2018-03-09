---
title: "Mise en œuvre d’une extension de rendu | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
caps.latest.revision: "34"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a7b8dd1c3efc550f04f3e5eff77dccbadfe305e7
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="implementing-a-rendering-extension"></a>Implémentation d'une extension de rendu
  Une extension de rendu est un composant ou un module d'un serveur de rapports qui transforme les données de rapport et les informations de disposition dans un format spécifique au périphérique. SQL Server Reporting Services incluent six extensions de rendu : HTML, Excel, Word, CSV ou Texte, XML, Image et PDF. Vous pouvez créer des extensions de rendu supplémentaires pour créer des rapports dans d'autres formats.  
  
> [!NOTE]  
>  Pour déterminer quelles extensions de rendu sont disponibles, vous pouvez consulter la liste des extensions installées dans le fichier RSReportServer.config.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d'ensemble des extensions de rendu](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
 Explique comment écrire une extension de rendu personnalisée pour [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Mise en œuvre de l'interface IRenderingExtension ](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)  
 Décrit les attributs d'une extension de rendu.  
  
 [Déploiement d'une extension de rendu](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
 Décrit comment déployer une extension de rendu sur un serveur de rapports.  
  
 [Suppression d'une extension de rendu](../../../reporting-services/extensions/rendering-extension/removing-a-rendering-extension.md)  
 Décrit comment supprimer une extension de rendu d'un serveur de rapports.  
  
## <a name="see-also"></a> Voir aussi  
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Bibliothèque d'extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
