---
title: À propos des réservations et de l’inscription d’URL (Gestionnaire de configuration de SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL reservations
- URL registration
- Report Server service, URL reservations
ms.assetid: c2c460c3-e749-4efd-aa02-0f8a98ddbc76
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6b72d0a263010cc82abab38ea2d6149d3492ed7b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108941"
---
# <a name="about-url-reservations-and-registration--ssrs-configuration-manager"></a>À propos des réservations et de l’inscription d’URL (Gestionnaire de configuration de SSRS)
  Les URL pour les applications Reporting Services sont définies en tant que réservations d'URL dans HTTP.SYS. Une réservation d'URL définit la syntaxe d'un point de terminaison URL à une application Web. Les réservations d'URL sont définies pour le service Web Report Server et pour le Gestionnaire de rapports lorsque vous configurez les applications sur le serveur de rapports. Les réservations d'URL sont créées automatiquement pour vous lors de la configuration d'URL par le biais du programme d'installation ou de l'outil de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
-   Le programme d'installation crée des réservations d'URL à l'aide de valeurs par défaut. Si le programme d'installation installe la configuration par défaut, il réserve deux URL : une pour le service Web Report Server et une autre pour le Gestionnaire de rapports. Vous pouvez utiliser l'outil de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour ajouter davantage d'URL ou modifier les URL par défaut créées par le programme d'installation.  
  
-   L'outil de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] crée une réservation d'URL basée sur l'URL que vous spécifiez dans les pages **URL du service Web** ou **URL du Gestionnaire de rapports** dans l'outil.  
  
 Le programme d'installation et l'outil assignent également des autorisations sur l'URL au service Report Server, vérifient s'il existe des instances en double et ajoutent la réservation d'URL à HTTP.SYS. Vous ne devez jamais créer ou modifier une réservation d'URL Reporting Services directement à l'aide de HttpCfg.exe ou d'un autre outil. Si vous ignorez une étape ou si vous avez défini une valeur non valide, vous rencontrerez des problèmes qui pourront être difficiles à diagnostiquer ou à résoudre.  
  
> [!NOTE]  
>  HTTP.SYS est un composant du système d'exploitation qui écoute les demandes réseau et les transfère vers une file d'attente de demandes. Dans cette version de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], HTTP.SYS établit et maintient la file d'attente de demandes pour le service Web Report Server et le Gestionnaire de rapports. Les services Internet (IIS) ne sont plus utilisés pour héberger ou accéder aux applications [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d'informations sur la fonctionnalité HTTP.SYS, consultez [HTTP Server API](https://go.microsoft.com/fwlink/?LinkId=92652) sur MSDN.  
  
##  <a name="ReportingServicesURLs"></a> URL dans Reporting Services  
 Dans une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous pouvez accéder aux outils, applications et éléments suivants au moyen d'URL :  
  
-   service Web Report Server  
  
-   Gestionnaire de rapports  
  
-   Générateur de rapports  
  
-   Rapports ayant été publiés sur un serveur de rapports  
  
 Les autres éléments publiés adressables par URL, tels que les modèles et sources de données partagées, ne doivent pas être accédés par le biais d'URL en tant qu'éléments autonomes. Le serveur de rapports n'affiche pas ces éléments dans un format explicite lorsqu'ils sont affichés dans une fenêtre de navigateur.  
  
> [!NOTE]  
>  Cette rubrique ne décrit pas l'accès par le biais d'URL au Générateur de rapports ou à des rapports spécifiques stockés sur le serveur de rapports. Pour plus d’informations sur l’accès à ces éléments par le biais d’URL, consultez [Accéder à des éléments de serveur de rapports à l’aide de l’accès URL](../access-report-server-items-using-url-access.md) dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="URLreservation"></a> Réservation et inscription d'URL  
 Une réservation d'URL définit les URL pouvant être utilisées pour accéder à une application [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] réserve une ou plusieurs pour le service Web Report Server et le Gestionnaire de rapports dans HTTP.SYS, puis les inscrit au démarrage du service. Les URL du Générateur de rapport et des rapports sont basés sur la réservation d'URL du service Web Report Server. En ajoutant des paramètres à l'URL, vous pouvez ouvrir le Générateur de rapport ou des rapports par le biais du service Web. Les réservations et l'inscription sont fournies par HTTP.SYS. Pour plus d'informations, consultez [Namespace Reservations, Registration, and Routing](https://go.microsoft.com/fwlink/?LinkId=92653) sur MSDN.  
  
 La*réservation d'URL* est un processus par lequel un point de terminaison URL à une application Web est créé et stocké dans HTTP.SYS. HTTP.SYS est la base de données de référentiel commune de toutes les réservations d'URL qui sont définies sur un ordinateur ; elle définit un jeu de règles communes qui garantissent des réservations d'URL uniques.  
  
 L'*inscription d'URL* se produit lorsque le service démarre. La file d'attente des demandes est créée et HTTP.SYS commence à transférer les demandes vers cette file d'attente. Un point de terminaison URL doit être inscrit pour que les demandes dirigées vers ce point de terminaison soient ajoutées à la file d'attente. Lorsque le service Report Server démarre, il enregistre toutes les URL qu'il a réservées pour toutes les applications actives. Cela signifie que le service Web doit être activé pour que l'inscription ait lieu. Si vous affectez à la propriété **WebServiceAndHTTPAccessEnabled** la valeur **False** dans la facette Configuration de la surface d'exposition pour Reporting Services de la gestion basée sur une stratégie, l'URL du service Web n'est pas inscrite au démarrage du service.  
  
 Les inscriptions des URL sont annulées si vous arrêtez le service ou si vous recyclez le service Web ou le domaine d'application du Gestionnaire de rapports. Si vous modifiez une réservation d'URL pendant que le service s'exécute, le serveur de rapports recycle immédiatement le domaine d'application afin que l'ancienne URL puisse être désinscrite et que la nouvelle puisse être utilisée.  
  
 Quelques exemples simples illustrent le concept de réservation d'URL et sa relation avec les adresses URL utilisées pour les applications [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Un point clé à noter est que la réservation d'URL a une syntaxe différente de celle de l'URL que vous utilisez pour accéder à l'application :  
  
|Réservation d'URL dans HTTP.SYS|URL|Explication|  
|---------------------------------|---------|-----------------|  
|http://+:80/reportserver|http://\<computername>/reportserver<br /><br /> http://\<IPAddress>/reportserver<br /><br /> http://localhost/reportserver|La réservation d'URL spécifie un caractère générique (+) sur le port 80. Cela met dans la file d'attente de serveur de rapports toute requête entrante qui spécifie un hôte résolu sur le serveur de rapports sur le port 80. Remarquez qu'avec cette réservation d'URL, une quantité quelconque d'URL peut être utilisée pour accéder au serveur de rapports.<br /><br /> Il s'agit de la réservation d'URL par défaut pour un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour la plupart des systèmes d'exploitation.|  
|http://123.45.67.0:80/reportserver|http://123.45.67.0/reportserver|Cette réservation d'URL spécifie une adresse IP ; elle est beaucoup plus restrictive que la réservation d'URL générique. Seules les URL qui incluent l'adresse IP peuvent être utilisées pour se connecter au serveur de rapports. Avec cette réservation d’URL, une demande à un serveur de rapports à l’adresse http://\<nom_ordinateur > / reportserver ou http://localhost/reportserver échouerait.|  
  
##  <a name="DefaultURLs"></a> URL par défaut  
 Si vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans la configuration par défaut, le programme d'installation réserve des URL pour le service Web Report Server et pour le Gestionnaire de rapports. Vous pouvez également accepter ces valeurs par défaut lorsque vous définissez des réservations d'URL dans l'outil de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les URL par défaut incluront un nom d'instance si vous installez [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] ou si vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en tant qu'instance nommée.  
  
> [!IMPORTANT]  
>  Le caractère d'instance est un trait de soulignement (`_`).  
  
 Les réservations d'URL incluent un numéro de port. Les systèmes d'exploitation suivants permettent à plusieurs applications web de partager un port :  
  
1.  [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
2.  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
3.  [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
4.  [!INCLUDE[win7](../../includes/win7-md.md)]  
  
5.  [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)]  
  
|Type d'instance|Application|URL par défaut|Réservation d'URL réelle dans HTTP.SYS|  
|-------------------|-----------------|-----------------|----------------------------------------|  
|Instance par défaut|service Web Report Server|http://\<servername>/reportserver|http://\<servername>:80/reportserver|  
|Instance par défaut|Gestionnaire de rapports|http://\<servername>/reportserver|http://\<servername>:80/reportserver|  
|Instance nommée|service Web Report Server|http://\<servername>/reportserver_\<instancename>|http://\<servername>:80/reportserver_\<instancename>|  
|Instance nommée|Gestionnaire de rapports|http://\<servername>/reports_\<instancename>|http://\<servername>:80/reports_\<instancename>|  
|SQL Server Express|service Web Report Server|http://\<servername>/reportserver_SQLExpress|http://\<servername>:80/reportserver_SQLExpress|  
|SQL Server Express|Gestionnaire de rapports|http://\<servername>/reports_SQLExpress|http://\<nom_serveur > : 80/reports_SQLExpress|  
  
##  <a name="URLPermissionsAccounts"></a> Authentification et identité de service pour les URL Reporting Services  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] spécifient le compte de service du service Report Server. Le compte sous lequel le service s'exécute est utilisé pour toutes les URL créées pour les applications [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui s'exécutent dans la même instance. L'identité de service de l'instance de serveur de rapports est stockée dans le fichier RSReportServer.config.  
  
 Le compte de service n'a aucune valeur par défaut. Toutefois, la spécification d'un compte de service est requise pendant l'installation et est spécifiée dans `URLReservation` dans RSReportServer.config même si vous installez le serveur en mode fichiers uniquement. Les valeurs valides pour le compte de service incluent un compte d'utilisateur de domaine, `LocalSystem` ou `NetworkService`.  
  
 L'accès anonyme est désactivé car la sécurité par défaut est `RSWindowsNegotiate`. Pour l'accès intranet, les URL de serveur de rapports utilisent des noms d'ordinateurs réseau. Si vous souhaitez configurer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour des connexions Internet, vous devez utiliser des paramètres différents. Pour plus d’informations sur l’authentification, consultez [Authentification avec le serveur de rapports](../security/authentication-with-the-report-server.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="URLlocalAdmin"></a> URL pour l'administration locale  
 Vous pouvez utiliser http://localhost/reportserver ou http://localhost/reports si vous avez spécifié un caractère générique fort ou faible pour la réservation d’URL.  
  
 L’URL http://localhost est interprétée comme http://127.0.0.1. Si vous avez lié la réservation d'URL à un nom d'ordinateur ou une adresse IP unique, vous ne pouvez pas utiliser localhost, à moins de créer une réservation supplémentaire pour 127.0.0.1 sur l'ordinateur local. De même, si localhost ou 127.0.0.1 est désactivé sur votre ordinateur, vous ne pouvez pas utiliser cette URL.  
  
 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] et [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] incluent de nouvelles fonctionnalités de sécurité destinées à réduire le risque d'exécution accidentelle de programmes avec des privilèges élevés. Des étapes supplémentaires sont nécessaires pour activer l'administration locale sur ces systèmes d'exploitation. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
##  <a name="URLSharePoint"></a> URL pour le serveur de rapports en Mode intégré SharePoint  
 Si un serveur de rapports autonome est configuré pour s'exécuter au sein d'un déploiement plus vaste d'un produit ou d'une technologie SharePoint, la construction d'URL et de répertoires virtuels sera affectée de plusieurs manières :  
  
-   Les URL pour les rapports et autres éléments sont adressées par le biais de l'URL d'application Web SharePoint. Pour l'accès URL à des rapports spécifiques, utilisez toujours une URL complète qui inclut le chemin d'accès au site, la bibliothèque de documents, le nom de l'article et une extension de nom de fichier (telle que .rdl pour un rapport). Vous devez spécifier des URL complètes lorsque vous faites référence à des sources de données partagées et à des modèles dans des rapports, et lorsque vous spécifiez un serveur et des dossiers cibles pour des opérations de publication sur un serveur de rapports.  
  
-   L'extension de nom de fichier est utilisée pour distinguer entre différents types d'éléments de serveur de rapports. Les extensions valides incluent .rdl pour les définitions de rapport, .smdl pour les modèles d'état et .rsds pour les sources de données partagées créées pour un site SharePoint.  
  
-   Bien que les produits et technologies SharePoint aient des réservations d'URL définies, vous pouvez ignorer la réservation lors de la publication sur le serveur. Pour les applications Web SharePoint, la réservation d'URL est une opération interne.  
  
-   Pour les déploiements de serveur unique où un serveur de rapports intégrée et l’instance de technologie SharePoint sont installés sur le même ordinateur, vous ne pouvez pas utiliser http://localhost/reportserver. Si http://localhost est utilisé pour accéder à l’application SharePoint Web, vous devez utiliser un site Web de celle par défaut ou une affectation de port unique pour accéder à un serveur de rapports. En outre, si le serveur de rapports est intégré à une batterie de serveurs SharePoint, l'accès localhost à un serveur de rapports n'est pas résolu pour les nœuds du déploiement installés sur des ordinateurs distants.  
  
-   La réservation d'URL et le point de terminaison pour le Gestionnaire de rapports ne peuvent pas être configurés pour un serveur de rapports qui s'exécute en mode intégré SharePoint. Si vous les configurez, le gestionnaire ne fonctionnera plus après le déploiement d'un serveur de rapports en mode intégré SharePoint. Le Gestionnaire de rapports n'est pas pris en charge dans ce mode.  
  
 Si vous avez intégré un déploiement de serveur de rapports avec montée en puissance parallèle pour s'exécuter au sein d'un déploiement plus vaste d'un produit ou d'une technologie SharePoint, vous devez équilibrer la charge des nœuds du serveur de rapports et définir une URL de serveur virtuel unique pour le déploiement avec montée en puissance parallèle. Les paramètres d'intégration Report Server vous permettent uniquement de spécifier une URL de serveur de rapports unique. Dans le cas d'un déploiement avec montée en puissance parallèle, l'URL doit être le point d'accès pour les nœuds de serveur dans le déploiement avec montée en puissance parallèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](configure-a-url-ssrs-configuration-manager.md)   
 [Syntaxe de réservation d’URL &#40;Gestionnaire de configuration de SSRS&#41;](url-reservation-syntax-ssrs-configuration-manager.md)  
  
  
