---
title: Suppression d’une extension de rendu | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4e9abf2254d9c9710e68df9b488321b4ae4c1b16
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132959"
---
# <a name="removing-a-rendering-extension"></a>Suppression d'une extension de rendu
  Pour supprimer un [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extension de rendu, supprimez simplement le `Extension` élément pour votre extension de rendu à partir du fichier rsreportserver.config, situé dans **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\< Nom de l’instance > \Reporting** dossier. Si vous avez apporté des entrées pour un concepteur de rapports ainsi que sur un serveur de rapports, supprimez le `Extension` élément à partir de la [fichier de Configuration RSReportDesigner](../../report-server/rsreportdesigner-configuration-file.md) également. Une fois les informations de configuration supprimées, l'extension de rendu n'est plus accessible au composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de configuration de Reporting Services](../../report-server/reporting-services-configuration-files.md)   
 [Implémentation d’une extension de rendu](implementing-a-rendering-extension.md)   
 [Vue d’ensemble des extensions de rendu](rendering-extensions-overview.md)   
 [Mise en œuvre de l’interface IRenderingExtension](implementing-the-irenderingextension-interface.md)   
 [Considérations sur la sécurité pour les extensions](../security-considerations-for-extensions.md)   
 [Déploiement d'une extension de rendu](deploying-a-rendering-extension.md)  
  
  
