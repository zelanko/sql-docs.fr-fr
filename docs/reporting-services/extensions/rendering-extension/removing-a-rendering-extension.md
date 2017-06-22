---
title: "Suppression d’une Extension de rendu | Documents Microsoft"
ms.custom: 
ms.date: 03/18/2017
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
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
caps.latest.revision: 38
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 58e9d46c17b300cda365e8b42d6442e00ffab0b9
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="removing-a-rendering-extension"></a>Suppression d'une extension de rendu
  Pour supprimer un [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extension de rendu, supprimez simplement le **Extension** élément pour votre extension de rendu à partir du fichier rsreportserver.config, situé dans **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\< Nom de l’instance > \Reporting** dossier. Si vous avez entrées pour un concepteur de rapports ainsi que sur un serveur de rapports, supprimez le **Extension** élément à partir de la [RSReportDesigner Configuration File](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md) également. Une fois les informations de configuration supprimées, l'extension de rendu n'est plus accessible au composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de configuration de Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Implémentation d’une Extension de rendu](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Vue d’ensemble des Extensions de rendu](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [Implémentation de l’Interface IRenderingExtension](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [Considérations sur la sécurité pour les Extensions](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [Déploiement d’une Extension de rendu](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
