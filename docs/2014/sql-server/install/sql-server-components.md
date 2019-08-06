---
title: Composants de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Upgrade Advisor, components
- listing components to analyze
- Upgrade Advisor [SQL Server], components
- component analysis [Upgrade Advisor]
- finding components to analyze
- locating components to analyze
- detecting components to analyze
- server names [Upgrade Advisor]
- analyzing system [Upgrade Advisor], component list
- identifying components to analyze
ms.assetid: 539b9525-ce3f-4950-9146-5527a5a297ee
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 514524f063bf78ceb4862612dd8c78ce8cf78fc4
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68811089"
---
# <a name="sql-server-components"></a>Composants SQL Server
  Vous pouvez exécuter l’Assistant analyse du conseiller de mise à niveau sur un ordinateur local [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]distant [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]sur lequel [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ,, ou est installé. La première étape de l'analyse de pré-mise à niveau consiste à identifier l'ordinateur et les composants à analyser.  
  
## <a name="options"></a>Options  
 **Nom de l’ordinateur**  
 Spécifie le nom de l'ordinateur à analyser. Le conseiller de mise à niveau remplit la zone **nom du serveur** avec le nom de l’ordinateur local. Vous pouvez également utiliser "." et "localhost" pour vous connecter à l'ordinateur local.  
  
 Pour analyser un autre ordinateur, appliquez les instructions suivantes :  
  
-   Pour analyser les instances non cluster, entrez le nom de l’ordinateur.  
  
-   Pour analyser les instances cluster, entrez le nom de l'instance de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour analyser les composants non-cluster installés sur un nœud d’un cluster, entrez le nom d’ordinateur du nœud de cluster de basculement.  
  
    > [!IMPORTANT]  
    >  N'incluez pas le nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Au lieu de spécifier le nom de l'ordinateur, vous pouvez spécifier l'adresse IP.  
  
 Lors de l'analyse de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez spécifier le nom de l'ordinateur local. Le Conseiller de mise à niveau analyse uniquement les serveurs de rapports locaux.  
  
 **Identifie**  
 Le bouton **détecter** accède à l’ordinateur spécifié et détecte les composants à analyser:  
  
-   Si vous analysez une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur distant, vous devez activer les services Registre distant sur l'ordinateur distant.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est détecté si une instance de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] se trouve dans le Registre de l'ordinateur.  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est détecté si une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] se trouve dans le Registre de l'ordinateur.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est détecté si [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] se trouve dans le Registre de l'ordinateur. Cependant, le Conseiller de mise à niveau analyse uniquement les serveurs de rapports locaux.  
  
 **Components**  
 Sélectionnez les composants à analyser. Vous pouvez cliquer sur le bouton **détecter** pour sélectionner tous les composants installés sur l’ordinateur. Une coche apparaît en regard des composants détectés comme étant installés sur l'ordinateur. Vous pouvez également sélectionner manuellement les composants à analyser en activant ou désactivant la case à cocher en regard de chaque composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Référence de l’interface utilisateur du conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
