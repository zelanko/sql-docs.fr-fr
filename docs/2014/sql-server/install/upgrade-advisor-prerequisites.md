---
title: Conditions préalables pour le conseiller de mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- requirements [Upgrade Advisor]
- software [Upgrade Advisor]
- system requirements [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, prerequisites
- prerequisites [Upgrade Advisor]
- Upgrade Advisor [SQL Server], prerequisites
ms.assetid: d21a39e5-5f81-4096-a7dd-f244e4779992
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5875ad2268e14d6bbe276ea437c5ee201867105e
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632771"
---
# <a name="upgrade-advisor-prerequisites"></a>Configuration requise par le Conseiller de mise à niveau
  Cette rubrique décrit la configuration logicielle requise par le Conseiller de mise à niveau.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration requise pour l'installation et l'exécution du Conseiller de mise à niveau est la suivante :  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] depuis SP2, Windows 7 ou [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.  
  
-   Windows Installer 4.5. Vous pouvez installer Windows Installer à partir du [site Web Windows Installer](https://www.microsoft.com/download/details.aspx?id=8483).  
  
-   The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], depuis .NET Framework 4. Le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] est disponible sur le support produit de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], et à partir du [Kit de développement logiciel (SDK), redistribuable et Service Pack site Web de téléchargement](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
    -   Pour installer .NET Framework 4 à partir du support de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], localisez la racine du lecteur de disque. Ensuite, double-cliquez sur le dossier \redist, sur le dossier DotNetFrameworks et exécutez dotNetFx40_Full_x86_x64.exe (pour les systèmes d'exploitation 32 bits et 64 bits).  
  
-   Le [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom est un composant requis pour l’installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] le conseiller de mise à niveau, et n’est pas installé par le programme d’installation du conseiller de mise à niveau. Le programme d’installation vous demande de télécharger et d’installer le [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom à partir du Feature Pack de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour installer le Conseiller de mise à niveau](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
