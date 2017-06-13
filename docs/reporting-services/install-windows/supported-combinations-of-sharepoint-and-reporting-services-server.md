---
title: Combinaisons de SharePoint et le serveur Reporting Services prises en charge | Documents Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 10/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
- rsSharePoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2e66cac836de44e8d2a9f23d88a600daaa26c0d1
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server"></a>Combinaisons prises en charge de SharePoint et le serveur Reporting Services
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

  Un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé en mode SharePoint nécessite une version de SharePoint et le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (rsSharePoint.msi) pour les produits SharePoint que vous installez sur les serveurs SharePoint.  Cette rubrique résume les combinaisons prises en charge.  
  
## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>Combinaisons de composants SharePoint et Reporting Services prises en charge  
 Le tableau suivant résume les combinaisons prises en charge de serveur de rapports, complément Reporting Services pour les produits SharePoint et produits SharePoint. Les associations qui ne sont pas répertoriées dans le tableau suivant ne sont pas prises en charge  
  
### <a name="supported-combinations"></a>Combinaisons prises en charge  
  
||Serveur de rapports|Complément|Version SharePoint|  
|-|-------------------|-------------|------------------------|  
|1|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|SharePoint 2016|  
|2|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|SharePoint 2013|  
|3|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2013|  
|4|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|5|SQL Server 2012 SP3|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et SQL Server 2012 SP3|SharePoint 2013|  
|6|SQL Server 2012 SP2|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et SQL Server 2012 SP2|SharePoint 2013|  
|7|[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2013|  
|8|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]*|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|9|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|SharePoint 2010|  
|10|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|11|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2010|  
|12|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|SharePoint 2010|  
|13|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|  
|14|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] R2|SharePoint 2010|  
|15|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|  
  
 *Exception : l’intégration de Power View n’est pas prise en charge.  
  
 Pour obtenir des liens vers les pages de téléchargement des compléments, consultez [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
 **Remarques supplémentaires :**  

- N’oubliez pas de mettre à niveau tous les serveurs SharePoint de la batterie de serveurs. Cela comprend les serveurs d’applications et les serveurs web frontaux.

-   La prise en charge de SharePoint 2016, comprenant l’intégration de Power View, nécessite le serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et la version du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de SQL Server 2016, ou une version ultérieure.  

-   La prise en charge de SharePoint 2013, comprenant l'intégration de Power View, nécessite le serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et la version complémentaire [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de SQL Server 2012 SP1, ou une version ultérieure.  
  
-   Power View a été introduit dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Par conséquent, l'intégration de Power View dans SharePoint 2010 requiert [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , ou une version ultérieure du complément.  
  
-   Le complément SQL Server 2008 R2 n'est pas pris en charge par les serveurs de rapports SQL Server 2012 (ou versions ultérieures). Le programme d'installation de SharePoint 2010 installe automatiquement le complément SQL Server 2008 R2. Il doit être désinstallé avant d'installer les nouvelles versions du complément. La mise à niveau sur place du complément n'est pas prise en charge.  
  
-   **Mise à niveau :** SharePoint 2010 avec le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé ne peut pas être mis à niveau sur place vers SharePoint 2013. SharePoint 2013 requiert [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ou une version ultérieure du complément et du serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d'informations sur la mise à niveau, consultez [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
  


