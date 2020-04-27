---
title: Mise en œuvre d’une extension de rendu | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03deb7c818de8d875f69b585ae6015fc178e707d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62986751"
---
# <a name="implementing-a-rendering-extension"></a>Implémentation d'une extension de rendu
  Une extension de rendu est un composant ou un module d'un serveur de rapports qui transforme les données de rapport et les informations de disposition dans un format spécifique au périphérique. SQL Server Reporting Services incluent six extensions de rendu : HTML, Excel, Word, CSV ou Texte, XML, Image et PDF. Vous pouvez créer des extensions de rendu supplémentaires pour créer des rapports dans d'autres formats.  
  
> [!NOTE]  
>  Pour déterminer quelles extensions de rendu sont disponibles, vous pouvez consulter la liste des extensions installées dans le fichier RSReportServer.config.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d'ensemble des extensions de rendu](rendering-extensions-overview.md)  
 Explique comment écrire une extension de rendu personnalisée pour [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Mise en œuvre de l'interface IRenderingExtension ](implementing-the-irenderingextension-interface.md)  
 Décrit les attributs d'une extension de rendu.  
  
 [Déploiement d'une extension de rendu](deploying-a-rendering-extension.md)  
 Décrit comment déployer une extension de rendu sur un serveur de rapports.  
  
 [Suppression d'une extension de rendu](removing-a-rendering-extension.md)  
 Décrit comment supprimer une extension de rendu d'un serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../reporting-services-extensions.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
