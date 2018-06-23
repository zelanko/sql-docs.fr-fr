---
title: Bibliothèque d’extensions Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- namespaces [Reporting Services]
- Reporting Services, extending
- extensions [Reporting Services], library
- library [Reporting Services]
ms.assetid: e8eff470-64d6-41c3-b98b-5ec916c121c3
caps.latest.revision: 33
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4f7ec58e860d75a24eea2162639ba458a067f73b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039236"
---
# <a name="reporting-services-extension-library"></a>Bibliothèque d'extensions Reporting Services
  La bibliothèque d'extensions Reporting Services est un ensemble de classes, d'interfaces et de types de valeur inclus dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Cette bibliothèque fournit l’accès aux fonctionnalités du système ; elle est conçue pour servir de base sur laquelle les applications [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] peuvent être utilisées pour étendre les composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="namespaces"></a>Espaces de noms  
 La bibliothèque d'extensions [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit les espaces de noms suivants.  
  
 <xref:Microsoft.ReportingServices.DataProcessing>  
 Contient les classes et les interfaces qui vous permettent de créer des composants qui étendent la fonctionnalité de traitement des données de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 <xref:Microsoft.ReportingServices.Interfaces>  
 Contient les classes et les interfaces qui vous permettent de construire et d'envoyer des notifications personnalisées aux utilisateurs via vos propres extensions de remise, ainsi que de générer des extensions de sécurité personnalisées pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 `Microsoft.ReportingServices.ReportRendering`  
 Contient les classes et les interfaces qui vous permettent d'étendre les fonctionnalités de rendu de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. À l'aide des membres de cet espace de noms, ainsi que des membres de l'espace de noms <xref:Microsoft.ReportingServices.Interfaces>, vous pouvez générer vos propres extensions de rendu personnalisées pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](reporting-services-extensions.md)  
  
  