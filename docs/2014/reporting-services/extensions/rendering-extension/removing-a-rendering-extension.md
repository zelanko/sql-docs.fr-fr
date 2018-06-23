---
title: Suppression d’une extension de rendu | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
caps.latest.revision: 37
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c8ad34be5d818d70b8c46d82dbf348b9d0814824
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039679"
---
# <a name="removing-a-rendering-extension"></a>Suppression d'une extension de rendu
  Pour supprimer un [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extension de rendu, supprimez simplement le `Extension` élément pour votre extension de rendu à partir du fichier rsreportserver.config, situé dans **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\< Nom de l’instance > \Reporting** dossier. Si vous avez entrées pour un concepteur de rapports ainsi que sur un serveur de rapports, supprimez le `Extension` élément à partir de la [RSReportDesigner Configuration File](../../report-server/rsreportdesigner-configuration-file.md) également. Une fois les informations de configuration supprimées, l'extension de rendu n'est plus accessible au composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de configuration de Reporting Services](../../report-server/reporting-services-configuration-files.md)   
 [Implémentation d’une extension de rendu](implementing-a-rendering-extension.md)   
 [Vue d’ensemble des extensions de rendu](rendering-extensions-overview.md)   
 [Mise en œuvre de l’interface IRenderingExtension](implementing-the-irenderingextension-interface.md)   
 [Considérations sur la sécurité pour les extensions](../security-considerations-for-extensions.md)   
 [Déploiement d'une extension de rendu](deploying-a-rendering-extension.md)  
  
  