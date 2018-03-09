---
title: "Suppression d’une extension de rendu | Microsoft Docs"
ms.custom: 
ms.date: 03/18/2017
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
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
caps.latest.revision: "38"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0ac5e10f4ea1aa66a4acf38bd0c4b64c3eb8be72
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="removing-a-rendering-extension"></a>Suppression d'une extension de rendu
  Pour supprimer une extension de rendu [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], supprimez simplement l’élément **Extension** pour votre extension de rendu du fichier rsreportserver.config, situé dans le dossier **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<nom_instance>\Reporting Services\ReportServer**. Si vous avez créé des entrées pour un Concepteur de rapports et un serveur de rapports, supprimez l’élément **Extension** du [fichier de configuration RSReportDesigner](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md) également. Une fois les informations de configuration supprimées, l'extension de rendu n'est plus accessible au composant.  
  
## <a name="see-also"></a> Voir aussi  
 [Fichiers de configuration de Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Implémentation d’une extension de rendu](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Vue d’ensemble des extensions de rendu](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [Mise en œuvre de l’interface IRenderingExtension](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [Considérations sur la sécurité pour les extensions](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [Déploiement d'une extension de rendu](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
