---
title: Changements de comportement apportés à SQL Server Reporting Services dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 91fa7a66981f3e36c7e25babffbf73dc2519a0c2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109940"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a>Changements de comportement apportés à SQL Server Reporting Services dans SQL Server 2014
  Cette rubrique décrit les changements de comportement dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Les modifications de comportement affectent le mode de fonctionnement ou d'interaction des fonctionnalités de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] par rapport aux versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Dans cette rubrique :  
  
-   [SQL Server 2014 Reporting Services modification du comportement](#bkmk_sql14)  
  
-   [Changements de comportement apportés à SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
-   [Changements de comportement apportés à SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-behavior-changes"></a><a name="bkmk_sql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services les changements de comportement  
 Il n'existe aucun changement de comportement dans les fonctionnalités [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] de [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="sssql11-reporting-services-behavior-changes"></a><a name="bkmk_rc0"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services les changements de comportement  
 Cette section décrit les changements de comportement en mode [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint.  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a>L'autorisation d'afficher les éléments ne télécharge pas les datasets partagés (mode SharePoint)  
 **Nouveau comportement :** Les utilisateurs disposant de l’autorisation SharePoint « afficher les éléments » ne peuvent plus télécharger le contenu de Reporting Services datasets partagés. Ce changement de comportement est désormais cohérent avec les autorisations « afficher les éléments » pour les rapports, les sources de données et les modèles. Les utilisateurs disposant de l’autorisation « Afficher les éléments » peuvent afficher et exécuter des rapports, des sources de données et des modèles, mais ils ne peuvent pas télécharger leur contenu.  
  
 **Comportement précédent :** Les utilisateurs disposant de l’autorisation SharePoint « afficher les éléments » peuvent télécharger le contenu de Reporting Services datasets partagés.  
  
 Pour plus d'informations sur les niveaux d'autorisation SharePoint, consultez [Autorisations utilisateur et niveaux d'autorisation](https://technet.microsoft.com/library/cc721640.aspx)  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a>Les journaux de trace du serveur de rapports sont dans un nouvel emplacement en mode SharePoint (mode SharePoint)  
 **Nouveau comportement :** Pour un serveur de rapports installé en mode SharePoint, les journaux de trace du serveur de rapports se trouvent sous le dossier %Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles.  
  
 **Comportement précédent :** Les journaux de suivi du serveur de rapports se trouvent sous un chemin d’accès similaire\\ à ce qui suit :%Programfilesdir%\Microsoft SQL Server<RS_instance> \Reporting Services\LogFiles  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a>L'API SOAP GetServerConfigInfo n'est plus prise en charge (mode SharePoint)  
 **Nouveau comportement**: utilisez l’applet de commande PowerShell « SPRSServiceApplicationServers »  
  
 **Comportement précédent :** Les clients peuvent développer le code client SOAP pour communiquer directement avec le point de terminaison [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et appeler GetReportServerConfigInfo().  
  
### <a name="report-server-configuration-and-management-tools"></a>Configuration de Report Server et Outils d'administration  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a>Le gestionnaire de configuration n'est pas utilisé pour le mode SharePoint  
 **Nouveau comportement :** Le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend plus en charge les serveurs de rapports en mode SharePoint. La configuration du mode SharePoint [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] peut maintenant être exécutée à l'aide de l'Administration centrale SharePoint et, par conséquent, le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend plus en charge le mode SharePoint. Le gestionnaire de configuration est maintenant utilisé uniquement pour les serveurs de rapports en mode natif.  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a>Vous ne pouvez pas modifier le serveur d'un mode en un autre.  
 **Nouveau comportement :** Vous ne pouvez pas modifier les modes serveur. Si vous installez un serveur de rapports en mode natif, vous ne pouvez pas le reconfigurer ou le modifier en mode SharePoint. Si vous l'installez en mode SharePoint, vous pouvez modifier le serveur de rapports en mode natif.  
  
 **Comportement précédent :** Le client installe un serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint. Si le client souhaite configurer le serveur de rapports en mode natif, il peut ouvrir le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour passer en mode natif en créant une base de données ou en se connectant à une base de données existante en mode natif. Le client peut également utiliser le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour passer du mode SharePoint en mode natif.  
  
##  <a name="sql-server-2008-r2-reporting-services-behavior-changes"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services modification du comportement  
 Cette section décrit les changements de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]comportement dans.  
  
> [!NOTE]  
>  SQL Server 2008 R2 étant une mise à niveau de version secondaire de SQL Server 2008, nous vous recommandons d'examiner également le contenu de la section SQL Server 2008.  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a>Propriété SecureConnectionLevel dans la bibliothèque du fournisseur WMI de Reporting Services  
 Dans la bibliothèque du fournisseur WMI [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]pour, la propriété **SecureConnectionLevel** autorise les `0`valeurs`1`de`2`,`3`,, `0` , avec pour indiquer que le protocole SSL (Secure Socket Layer) n’est pas requis pour `3` les méthodes de service Web, ce qui indique que le protocole SSL `1` est `2` requis pour toutes les méthodes de service Web et et indique des sous-ensembles de méthodes de service Web qui requièrent SSL. Dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], ces valeurs n’ont que deux significations possibles :  
  
-   `0` indique que le protocole SSL n'est pas obligatoire pour les méthodes de service Web.  
  
-   Un entier positif indique que le protocole SSL est obligatoire pour toutes les méthodes de service Web.  
  
 Cette modification affecte la manière dont le serveur de rapports répond aux appels de service Web. Par exemple, <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> retourne désormais Nothing si **SecureConnectionLevel** a la valeur 0 et que toutes les méthodes <xref:ReportService2005.ReportingService2005> dans si **SecureConnectionLevel** a la `1`valeur `2`, ou `3`.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Fonctionnalités dépréciées dans SQL Server Reporting Services dans SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Fonctionnalités supprimées pour SQL Server Reporting Services dans SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [Modifications importantes de SQL Server Reporting Services dans SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
