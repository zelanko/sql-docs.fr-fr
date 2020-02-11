---
title: Combinaisons de serveurs et compléments SharePoint et Reporting Services prises en charge (SQL Server 2014) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05f0997cb73a156e54b22ad280fa5d6eb0ec7d73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108652"
---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server-and-add-in-sql-server-2014"></a>Combinaisons de serveur et composant SharePoint et Reporting Services prises en charge (SQL Server 2014)
  Les serveurs de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peuvent être installés en mode SharePoint et intégrés à un déploiement SharePoint. Certaines fonctionnalités ne sont pas prises en charge dans toutes les combinaisons de serveur de rapports, complément Reporting Services pour SharePoint et produits SharePoint. Cette rubrique résume les combinaisons prises en charge. Dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , l’intégration résulte de la combinaison des éléments suivants :  
  
-   Une version d'un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuré pour le mode SharePoint.  
  
-   Un produit SharePoint.  
  
-   Le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint, que vous installez sur les serveurs SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010 &#124; SharePoint 2007|  
  
## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>Combinaisons de composants SharePoint et Reporting Services prises en charge  
 Le tableau suivant résume les combinaisons prises en charge de serveur de rapports, complément Reporting Services pour les produits SharePoint et produits SharePoint. Les associations qui ne sont pas répertoriées dans le tableau suivant ne sont pas prises en charge  
  
### <a name="supported-combinations"></a>Combinaisons prises en charge  
  
||Serveur de rapports|Complément|Version SharePoint|Prise en charge|  
|-|-------------------|-------------|------------------------|---------------|  
|1|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2013|Oui|  
|2|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Oui|  
|3|[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2013|Oui|  
|4|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Oui<br /><br /> Exception : l'intégration de Power View n'est pas prise en charge.|  
|5|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|SharePoint 2010|Oui|  
|6|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Oui|  
|7|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2010|Oui|  
|8|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|SharePoint 2010|Oui|  
|9|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|Oui|  
|10|
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]2|SharePoint 2010|Oui|  
|11|
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|Oui|  
  
 Pour plus d’informations [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur les fonctionnalités et les modes du serveur de rapports, consultez [Reporting Services serveur de rapports](../reporting-services-report-server.md).  
  
 **Remarques supplémentaires :**  
  
-   La prise en charge de SharePoint 2013, comprenant l'intégration de Power View, nécessite le serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et la version complémentaire [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de SQL Server 2012 SP1, ou une version ultérieure.  
  
-   Power View a été introduit dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Par conséquent, l'intégration de Power View dans SharePoint 2010 requiert [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , ou une version ultérieure du complément.  
  
-   Le complément SQL Server 2008 R2 n'est pas pris en charge par les serveurs de rapports SQL Server 2012 (ou versions ultérieures). Le programme d'installation de SharePoint 2010 installe automatiquement le complément SQL Server 2008 R2. Il doit être désinstallé avant d'installer les nouvelles versions du complément. La mise à niveau sur place du complément n'est pas prise en charge.  
  
-   **Mise à niveau :** SharePoint 2010 avec le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] complément installé ne peut pas être mis à niveau sur place vers SharePoint 2013. SharePoint 2013 requiert [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ou une version ultérieure du complément et du serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d'informations sur la mise à niveau, consultez [Upgrade and Migrate Reporting Services](upgrade-and-migrate-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Où trouver le complément Reporting Services pour les produits SharePoint](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Upgrade and Migrate Reporting Services](upgrade-and-migrate-reporting-services.md)  
  
  
