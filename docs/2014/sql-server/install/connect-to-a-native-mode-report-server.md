---
title: Se connecter à un serveur de rapports en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5bf32c8427679b342bee89d6541b051beed2e8ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952288"
---
# <a name="connect-to-a-native-mode-report-server"></a>Se connecter à un serveur de rapports en mode natif
  Utilisez cette boîte de dialogue pour vous connecter à une instance du serveur de rapports [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou ultérieure) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , locale ou distante. Vous ne pouvez pas utiliser cet outil pour vous connecter aux versions antérieures de serveurs de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Vous ne pouvez vous connecter qu'à une instance à la fois.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode natif.  
  
> [!NOTE]  
>  Le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas nécessaire pour configurer et administrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint. Vous utilisez l'Administration centrale de SharePoint et les scripts PowerShell pour configurer un serveur de rapports en mode SharePoint. Pour plus d’informations, voir [Installer le mode SharePoint de Reporting Services pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
> [!TIP]  
>  Le[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool. exe) est installé avec un niveau de privilège « highestAvailable ». Ce comportement est normal. Le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a besoin de la communication avec des API WMI [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Une partie de la communication WMI [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requiert un niveau supérieur ou d'administration des privilèges.  
  
-   Pour vous connecter à une instance locale du serveur de rapports, utilisez les valeurs par défaut et cliquez sur **Se connecter**. Le gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit le nom du serveur local et détecte l'instance par défaut. Dans la plupart des cas, vous pouvez cliquer sur **Se connecter** sans avoir à modifier les valeurs. Si vous avez installé plusieurs instances, vous devez sélectionner celle que vous souhaitez utiliser.  
  
-   Pour vous connecter à une instance de serveur de rapports distante, tapez le nom du serveur, cliquez sur **Rechercher**, sélectionnez l'instance, puis cliquez sur **Se connecter**.  
  
 Pour ouvrir cette boîte de dialogue, démarrez le gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Cette boîte de dialogue apparaît immédiatement lorsque vous démarrez l'outil. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Options  
 **Nom du serveur**  
 Entrez le nom de réseau de l'ordinateur sur lequel [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou ultérieure) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé. Tapez simplement le nom de l'ordinateur, sans inclure de préfixe ou de barre oblique.  
  
 **Trouver**  
 Recherchez l'ordinateur spécifié dans **Nom du serveur**.  
  
 **Instance du serveur de rapports**  
 Sélectionnez l'instance à laquelle se connecter si plusieurs instances de serveur de rapports sont installées. Seules les instances valides sont disponibles pour la sélection. Si vous exécutez côte à côte des versions antérieures de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ces instances n'apparaîtront pas dans la liste.  
  
 **Connexion**  
 Connectez-vous au serveur et à l'instance que vous avez spécifiés.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
