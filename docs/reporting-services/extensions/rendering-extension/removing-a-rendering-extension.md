---
title: Suppression d’une extension de rendu | Microsoft Docs
description: Découvrez comment supprimer une extension de rendu de Reporting Services afin qu’elle ne soit plus disponible pour le serveur de rapports et les Concepteur de rapports.
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f71fceddd59141516453f9f392f8f913ba20cfad
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529435"
---
# <a name="removing-a-rendering-extension"></a>Suppression d'une extension de rendu
  Pour supprimer une extension de rendu [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], supprimez simplement l’élément **Extension** pour votre extension de rendu du fichier rsreportserver.config, situé dans le dossier **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<Instance Name>\Reporting Services\ReportServer**. Si vous avez créé des entrées pour un Concepteur de rapports et un serveur de rapports, supprimez l’élément **Extension** du [fichier de configuration RSReportDesigner](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md) également. Une fois les informations de configuration supprimées, l'extension de rendu n'est plus accessible au composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de configuration de Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Implémentation d’une extension de rendu](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Vue d’ensemble des extensions de rendu](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [Mise en œuvre de l’interface IRenderingExtension](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [Considérations sur la sécurité pour les extensions](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [Déploiement d'une extension de rendu](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
