---
title: Configurations matérielle et logicielle requises pour Reporting Services en mode SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 56ddfce4fc1812e99870c22eeb0e15be64c5decb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75245632"
---
# <a name="hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode"></a>Configurations matérielle et logicielle pour Reporting Services en mode SharePoint

  Cette rubrique décrit les conditions préalables, la configuration matérielle requise et les [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] éléments à prendre en compte pour l’exécution en mode SharePoint. Étant donné que le mode [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint nécessite un serveur SharePoint, la plupart des conditions sont basées sur l'environnement SharePoint. Pour les serveurs de rapports en mode natif, votre matériel doit correspondre aux configurations matérielle et logicielle minimales requises pour l'exécution de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d'informations, consultez [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   [Conditions préalables](#bkmk_prereq)  
  
-   [Configuration requise pour la base de données du serveur de rapports](#bkmk_report_server_database)  
  
-   [Spécifications Power View](#bkmk_powerview)  
  
-   [Plus d’informations](#bkmk_more_information)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> Conditions préalables  
  
-   Pour les installations locales, le compte connecté pendant l'installation de SharePoint et de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] doit être un membre du groupe Administrateurs dans le système d'exploitation local. Le compte utilisé pour l'installation ne doit pas être nécessairement un membre du groupe d'administrateurs de la batterie de serveurs SharePoint.  
  
     Pour plus d'informations, consultez [Autorisations de compte et paramètres de sécurité dans SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx).  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint requiert SharePoint Server. Pour plus d'informations sur les configurations requises et les configurations SharePoint, consultez les rubriques suivantes :  
  
    -   [Configuration matérielle et logicielle requise (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)  
  
    -   [Gestion et dimensionnement de la capacité pour SharePoint Server 2013](https://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [Configuration logicielle requise pour l’aide à la décision dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   [Configuration matérielle et logicielle requise (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))  
  
    -   [Capacity management and sizing for SharePoint Server 2010 (Gestion et dimensionnement de la capacité pour SharePoint Server 2010)](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))  
  
-   Si vous souhaitez mettre à niveau ou à jour une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint existante vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consultez [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
-   Vérifiez que le service **Administration SharePoint 2013** est démarré dans le Gestionnaire du serveur Windows.  
  
###  <a name="report-server-database-requirements"></a><a name="bkmk_report_server_database"></a> Configuration requise pour une base de données de serveur de rapports  
  
-   Les produits et technologies SharePoint et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilisent des bases de données relationnelles SQL Server pour stocker les données d'application.  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] requiert une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] d’une édition SQL Server compatible. Pour plus d'informations sur les configurations matérielle et logicielle requises, consultez [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Les produits SharePoint peuvent utiliser une instance de base de données existante. En l'absence d'une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] installée, le programme d'installation de produits SharePoint installe l'édition SQL Server Express pour les bases de données d'application SharePoint.  
  
-   L'instance de serveur de rapports ne peut pas utiliser l'édition SQL Server Express pour sa base de données. Toutefois, l'instance de l'édition SQL Server Express installée par le produit SharePoint peut exister côte à côte avec d'autres éditions du moteur de base de données.  
  
##  <a name="sscrescent-requirements"></a><a name="bkmk_powerview"></a>[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Configuration requise

 Consultez la [documentation liée à Power View](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) la plus récente sur le site Office.Microsoft.com. [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] est maintenant une fonctionnalité de Microsoft Excel 2013 ; elle est disponible avec le complément [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services de Microsoft SharePoint Server 2010 et 2013 Enterprise Edition.  
  
##  <a name="more-information"></a><a name="bkmk_more_information"></a> Plus d’informations

 Pour plus d’informations sur les modifications apportées à SharePoint, consultez [modifications de sharepoint 2010 à sharepoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (https://technet.microsoft.com/library/ff607742(office.15).aspx).  
  
 [Notes de publication de SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
