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
ms.openlocfilehash: 41c97cf585d1768c7aebeec2613ee8744cb220da
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062360"
---
# <a name="upgrade-advisor-prerequisites"></a>Configuration requise par le Conseiller de mise à niveau
  Cette rubrique décrit la configuration logicielle requise par le Conseiller de mise à niveau.  
  
## <a name="prerequisites"></a>Prérequis  
 La configuration requise pour l'installation et l'exécution du Conseiller de mise à niveau est la suivante :  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] depuis SP2, Windows 7 ou [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.  
  
-   Windows Installer 4.5. Vous pouvez installer Windows Installer à partir du [site Web Windows Installer](https://www.microsoft.com/download/details.aspx?id=8483).  
  
-   The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], depuis .NET Framework 4. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]Est disponible sur le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support du produit, et à partir du [Kit de développement logiciel (SDK), redistribuable et Service Pack site Web de téléchargement](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
    -   Pour installer .NET Framework 4 à partir du support de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], localisez la racine du lecteur de disque. Ensuite, double-cliquez sur le dossier \redist, sur le dossier DotNetFrameworks et exécutez dotNetFx40_Full_x86_x64.exe (pour les systèmes d'exploitation 32 bits et 64 bits).  
  
-   Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom est un composant requis pour l’installation du [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] conseiller de mise à niveau et n’est pas installé par le programme d’installation du conseiller de mise à niveau. Le programme d’installation vous demande de télécharger et d’installer le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom à partir du [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : installer le Conseiller de mise à niveau](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
