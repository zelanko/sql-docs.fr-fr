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
manager: kfile
ms.openlocfilehash: 5c8f55dd0fa663d5516938e9ca39b5a6dc2caed9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014627"
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
  
  
