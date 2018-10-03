---
title: Prise en charge les combinaisons de SharePoint et Reporting Services serveur et complément (SQL Server 2014) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6b2335e06f5821bedefad8aeb558a3528632ad1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102719"
---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server-and-add-in-sql-server-2014"></a>Combinaisons de serveur et composant SharePoint et Reporting Services prises en charge (SQL Server 2014)
  Les serveurs de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peuvent être installés en mode SharePoint et intégrés à un déploiement SharePoint. Certaines fonctionnalités ne sont pas prises en charge dans toutes les combinaisons de serveur de rapports, complément Reporting Services pour SharePoint et produits SharePoint. Cette rubrique résume les combinaisons prises en charge. Dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] l’intégration est le résultat de la combinaison des éléments suivants :  
  
-   Une version d'un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuré pour le mode SharePoint.  
  
-   Un produit SharePoint.  
  
-   Le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint, que vous installez sur les serveurs SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010 &#124; SharePoint 2007|  
  
## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>Combinaisons de composants SharePoint et Reporting Services prises en charge  
 Le tableau suivant résume les combinaisons prises en charge de serveur de rapports, complément Reporting Services pour les produits SharePoint et produits SharePoint. Les associations qui ne sont pas répertoriées dans le tableau suivant ne sont pas prises en charge  
  
### <a name="supported-combinations"></a>Combinaisons prises en charge  
  
||Serveur de rapports|Complément|Version SharePoint|Pris en charge|  
|-|-------------------|-------------|------------------------|---------------|  
|1|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2013|Oui|  
|2|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Oui|  
|3|[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2013|Oui|  
|4|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Oui<br /><br /> Exception : l'intégration de Power View n'est pas prise en charge.|  
|5|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|SharePoint 2010|Oui|  
|6|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Oui|  
|7|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2010|Oui|  
|8|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|SharePoint 2010|Oui|  
|9|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|Oui|  
|10|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] R2|SharePoint 2010|Oui|  
|11|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|Oui|  
  
 Pour plus d’informations sur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fonctionnalités et modes de serveur de rapports, consultez [Reporting Services Report Server](../reporting-services-report-server.md).  
  
 **Remarques supplémentaires :**  
  
-   La prise en charge de SharePoint 2013, comprenant l'intégration de Power View, nécessite le serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et la version complémentaire [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de SQL Server 2012 SP1, ou une version ultérieure.  
  
-   Power View a été introduit dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Par conséquent, l'intégration de Power View dans SharePoint 2010 requiert [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , ou une version ultérieure du complément.  
  
-   Le complément SQL Server 2008 R2 n'est pas pris en charge par les serveurs de rapports SQL Server 2012 (ou versions ultérieures). Le programme d'installation de SharePoint 2010 installe automatiquement le complément SQL Server 2008 R2. Il doit être désinstallé avant d'installer les nouvelles versions du complément. La mise à niveau sur place du complément n'est pas prise en charge.  
  
-   **Mise à niveau :** SharePoint 2010 avec le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé ne peut pas être mis à niveau sur place vers SharePoint 2013. SharePoint 2013 requiert [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ou une version ultérieure du complément et du serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations sur la mise à niveau, consultez [mise à niveau et migrer Reporting Services](upgrade-and-migrate-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Où trouver le complément Reporting Services pour les produits SharePoint](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Mettre à niveau et migrer Reporting Services](upgrade-and-migrate-reporting-services.md)  
  
  
