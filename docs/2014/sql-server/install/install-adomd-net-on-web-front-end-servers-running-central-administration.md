---
title: Installez ADOMD.NET sur des serveurs Web frontaux exécutant l’Administration centrale | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2d8a3c6a47a9f353f44a9ec9c4a0cbb2c3cd3505
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66094694"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a>Installer ADOMD.NET sur des serveurs Web frontaux exécutant l'Administration centrale
  Si vous installez PowerPivot pour SharePoint dans une batterie de serveurs qui a la topologie de l'Administration centrale, sans Excel Services ou PowerPivot pour SharePoint, téléchargez et installez la bibliothèque cliente Microsoft ADOMD.NET si vous voulez disposer d'un accès total aux rapports intégrés dans le tableau de bord de gestion PowerPivot. Certains rapports du tableau de bord utilisent ADOMD.NET pour accéder aux données internes qui fournissent les données de création de rapports sur le traitement des requêtes PowerPivot et l'intégrité des serveurs de la batterie.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010  
  
 Pour SharePoint 2013, le fournisseur est inclus dans le Feature Pack SQL Server. Pour plus d’informations sur le téléchargement de spPowerPivot.msi, consultez [Microsoft SQL Server 2014 Feature Pack](https://www.microsoft.com/download/details.aspx?id=35577)  
  
### <a name="download-and-install-the-client-library"></a>Télécharger et installer la bibliothèque cliente  
  
1.  Sur le [page SQL Server 2014 Feature Pack](https://go.microsoft.com/fwlink/?LinkID=296473), recherchez Microsoft ADOMD.NET.  
  
2.  Téléchargez le package x64 du programme d'installation `SQL_AS_ADOMD.msi`.  
  
3.  Exécutez le fichier .msi pour installer la bibliothèque.  
  
4.  Réinitialisez IIS une fois l'installation finie. Ouvrez une invite de commandes d’administration et le type **IISRESET**.  
  
### <a name="verify-installation"></a>Vérifier l'installation  
  
1.  Accédez à Windows\Assembly.  
  
2.  Cliquez sur Microsoft.AnalysisServices.AdomdClient, puis sélectionnez **propriétés**.  
  
3.  Cliquez sur **Version**.  
  
4.  Vérifiez que la version inclut 12.00. \<numéro de build > et que la description est Microsoft.AnalysisService.AdomdClient.  
  
## <a name="see-also"></a>Voir aussi  
 [Tableau de bord de gestion PowerPivot et données d’utilisation](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)  
  
  
