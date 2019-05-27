---
title: Matérielle et logicielle requise pour Reporting Services en Mode SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5584984121403b1a70e15fb02e85b7afcc169843
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66094978"
---
# <a name="hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode"></a>Configurations matérielle et logicielle pour Reporting Services en mode SharePoint

  Cette rubrique décrit la configuration requise, la configuration matérielle requise et des considérations relatives à l'installation pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint. Étant donné que le mode [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint nécessite un serveur SharePoint, la plupart des conditions sont basées sur l'environnement SharePoint. Pour les serveurs de rapports en mode natif, votre matériel doit correspondre aux configurations matérielle et logicielle minimales requises pour l'exécution de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d'informations, consultez [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   [Conditions préalables](#bkmk_prereq)  
  
-   [Configuration requise pour une base de données de serveur de rapports](#bkmk_report_server_database)  
  
-   [Spécifications Power View](#bkmk_powerview)  
  
-   [Informations complémentaires](#bkmk_more_information)  
  
##  <a name="bkmk_prereq"></a> Conditions préalables  
  
-   Pour les installations locales, le compte connecté pendant l'installation de SharePoint et de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] doit être un membre du groupe Administrateurs dans le système d'exploitation local. Le compte utilisé pour l'installation ne doit pas être nécessairement un membre du groupe d'administrateurs de la batterie de serveurs SharePoint.  
  
     Pour plus d'informations, consultez [Autorisations de compte et paramètres de sécurité dans SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx).  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint requiert SharePoint Server. Pour plus d'informations sur les configurations requises et les configurations SharePoint, consultez les rubriques suivantes :  
  
    -   [Configuration matérielle et logicielle requises (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)  
  
    -   [Gestion et dimensionnement de la capacité pour SharePoint Server 2013](https://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [Configuration logicielle requise pour l’aide à la décision dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   [Configuration matérielle et logicielle requise (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))  
  
    -   [Capacity management and sizing for SharePoint Server 2010 (Gestion et dimensionnement de la capacité pour SharePoint Server 2010)](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))  
  
-   Si vous souhaitez mettre à niveau ou à jour une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint existante vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consultez [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
-   Vérifiez que le service **Administration SharePoint 2013** est démarré dans le Gestionnaire du serveur Windows.  
  
###  <a name="bkmk_report_server_database"></a> Configuration requise pour une base de données de serveur de rapports  
  
-   Les produits et technologies SharePoint et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilisent des bases de données relationnelles SQL Server pour stocker les données d'application.  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] requiert une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] d’une édition SQL Server compatible. Pour plus d'informations sur les configurations matérielle et logicielle requises, consultez [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Les produits SharePoint peuvent utiliser une instance de base de données existante. En l'absence d'une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] installée, le programme d'installation de produits SharePoint installe l'édition SQL Server Express pour les bases de données d'application SharePoint.  
  
-   L'instance de serveur de rapports ne peut pas utiliser l'édition SQL Server Express pour sa base de données. Toutefois, l'instance de l'édition SQL Server Express installée par le produit SharePoint peut exister côte à côte avec d'autres éditions du moteur de base de données.  
  
##  <a name="bkmk_powerview"></a> Spécifications [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]

 Consultez la [documentation liée à Power View](http://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) la plus récente sur le site Office.Microsoft.com. [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] est maintenant une fonctionnalité de Microsoft Excel 2013 ; elle est disponible avec le complément [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services de Microsoft SharePoint Server 2010 et 2013 Enterprise Edition.  
  
##  <a name="bkmk_more_information"></a> Informations supplémentaires

 Pour plus d’informations sur les modifications apportées à SharePoint, consultez [changements entre SharePoint 2010 vers SharePoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (https://technet.microsoft.com/library/ff607742(office.15).aspx).  
  
 [Notes de mise à jour de SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
  
