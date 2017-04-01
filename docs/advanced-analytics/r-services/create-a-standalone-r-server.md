---
title: "Cr&#233;er un serveur R autonome | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 408e2503-5c7d-4ec4-9d3d-bba5a8c7661d
caps.latest.revision: 35
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 27
---
# Cr&#233;er un serveur R autonome
  Le programme de configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre désormais la possibilité d’installer **Microsoft R Server (autonome)**. Cette option vous permet de développer des solutions R hautes performances sur Windows lors de la connexion à la base de données ou à la source de données de votre choix. Microsoft R Server est uniquement disponible dans Enterprise Edition  
  
 Lorsque vous installez Microsoft R Server, vous obtenez les mêmes packages R améliorés et outils de connectivité fournis dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], mais une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas obligatoire et l’exécution de scripts R est exécutée sur l’ordinateur autonome, pas dans la base de données.  
  
> [!NOTE]  
>  Désormais, Microsoft R Server est également disponible via une configuration simplifiée qui inscrit l’instance dans la stratégie de [cycle de vie moderne](https://support.microsoft.com/help/447912). Cette offre de support garantit que vous utilisez toujours la version la plus récente de R. Pour plus d’informations sur l’utilisation de la configuration simplifiée, consultez [Exécuter Microsoft R Server pour Windows](https://msdnstage.redmond.corp.microsoft.com/microsoft-r/rserver-install-windows?branch=r-server-nov16-dev).
>  
> Si vous installez Microsoft R Server via le programme de configuration simplifiée, vous pouvez également convertir toute instance spécifiée de R Services pour utiliser la nouvelle stratégie de support et obtenir des mises à jour plus fréquentes des composants R. Pour plus d’informations, consultez [Utilisez sqlBindR.exe pour mettre à niveau une instance R Services](http://www.bing.com).   
  
##  <a name="a-namebkmkinstallrservicesindatabasea-install-microsoft-r-server-standalone"></a><a name="bkmk_installRServicesInDatabase"></a> Installer Microsoft R Server (autonome)  
  
1.  Si vous avez installé une version précédente de Microsoft R Server, commencez par la désinstaller.  Consultez [Mise à niveau depuis une version antérieure de Microsoft R Server](#bkmk_Uninstall). 

2. Exécutez le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Dans l’onglet **Installation** , cliquez sur **Nouvelle installation de R Server (autonome)** .  
  
     ![Setup option for R Server Standalone](../../advanced-analytics/r-services/media/rsql-rstandalonesetup.png "Setup option for R Server Standalone")  
  
3.  Dans la page **Sélection de fonctionnalités** , l’option suivante doit déjà être sélectionnée :  
  
    -   **R Server (autonome)**  
  
         Cette option installe les fonctionnalités partagées, notamment les packages de base et outils R open source, ainsi que les packages et outils de connectivité R avancés fournis par Microsoft R.  
  
     Toutes les autres options peuvent être ignorées.  
  
4.  Acceptez les termes du contrat de licence pour télécharger et installer Microsoft R Open. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. L’installation de ces composants (et des autres composants éventuellement requis) peut prendre un certain temps.   
  
5.  Sur la page **Prêt pour l’installation**, vérifiez vos sélections, et cliquez sur **Installer**.  
  
> [!TIP]
> Pour plus d’informations sur l’installation automatisée ou hors connexion, consultez [Installer Microsoft R Server à partir de la ligne de commande](../../advanced-analytics/r-services/install-microsoft-r-server-from-the-command-line.md).

  
## <a name="what-is-installed-and-where-to-find-r-packages"></a>Quels sont les éléments installés et où trouver des packages R  
 Microsoft R Server inclut les packages de base R et un ensemble de packages R améliorés prenant en charge le traitement parallèle, les performances améliorées et la connectivité aux sources de données, notamment [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Hadoop.  
  
-   **Packages R**  
  
     Les bibliothèques R sont installées avec d’autres outils et utilitaires qui sont installés avec Microsoft SQL Server 2016. Par exemple :  
  
     `C:\Program Files\Microsoft SQL Server\130\R_SERVER`  
  
     En outre, dans ce dossier, vous trouverez la documentation relative aux packages de base R, des exemples de données et la documentation relative aux outils R et au runtime.  
  
    > [!NOTE]  
    >  Si vous avez installé une instance de SQL Server avec R Services (dans la base de données) sur le même ordinateur, les bibliothèques et outils R sont installés dans un dossier différent : `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`  
    >   
    >  N’utilisez pas les packages ou les utilitaires R associés à l’instance [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Utilisez toujours les outils et les packages R dans le dossier R_SERVER.  
  
-   **Outils R**  
  
     Un IDE R n’est pas installé dans le cadre de la configuration. Vous pouvez installer RStudio, [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)], ou tout autre environnement de développement de votre choix.  
  
     Toutefois, aucun outil supplémentaire n’est requis. Tous les outils R de base standard sont inclus dans `C:\Program Files\Microsoft SQL Server\130\R_SERVER\bin`.  
  
     Pour plus d’informations, consultez [Installer ou configurer les outils R](../../advanced-analytics/r-services/setup-or-configure-r-tools.md).  


 
## <a name="troubleshooting"></a>Dépannage  

### <a name="incompatible-version-of-r-client-and-r-server"></a>Version incompatible de R Client et de R Server

Si vous installez la dernière version de Microsoft R Client et l’utilisez pour exécuter R sur SQL Server à l’aide d’un contexte de calcul distant, il est possible que vous obteniez l’erreur suivante :

*Vous exécutez la version 9.0.0 de Microsoft R Client sur votre ordinateur, ce qui est incompatible avec la version 8.0.3 de Microsoft R Server. Téléchargez et installez une version compatible.*

En règle générale, la version de R installée avec SQL Server R Services est mise à jour lors de la publication des versions de service. Pour vous assurer que vous disposez toujours des versions les plus récentes des composants R, installez tous les Service Packs. Pour la compatibilité avec Microsoft R Client 9.0.0, vous devez installer les mises à jour qui sont décrites dans cet [article de support](https://support.microsoft.com/kb/3210262). 


### <a name="installing-microsoft-r-server-on-an-instance-of-sql-server-installed-on-windows-core"></a>Installation de Microsoft R Server sur une instance de SQL Server installée sur Windows Core
Dans la version SQL Server 2016, il y avait un problème connu lors de l’ajout de Microsoft R Server à une instance sur l’édition Windows Server Core. Ce problème a été résolu. 

Si vous rencontrez ce problème, vous pouvez appliquer le correctif décrit dans [KB3164398](https://support.microsoft.com/kb/3164398) pour ajouter la fonctionnalité R à l’instance existante sur Windows Server Core.   Pour plus d’informations, consultez [Impossible d’installation Microsoft R Server (autonome) sur un système d’exploitation Windows Server Core](https://support.microsoft.com/kb/3168691).


###  <a name="a-namebkmkuninstalla-upgrading-from-an-older-version-of-microsoft-r-server"></a><a name="bkmk_Uninstall"></a> Mise à niveau depuis une version antérieure de Microsoft R Server  
 Si vous avez installé une version préliminaire de Microsoft R Server, commencez par la désinstaller avant de pouvoir mettre à niveau vers une version plus récente.  
  
**Pour installer R Server (autonome)**  
  
1.  Dans le **Panneau de configuration**, cliquez sur **Ajout/Suppression de programmes**, et sélectionnez `Microsoft SQL Server 2016 <version number>`.  
  
2.  Dans la boîte de dialogue proposant les options **Ajouter**, **Réparer** ou **Supprimer** les composants, sélectionnez **Supprimer**.  
  
3.  Sur la page **Sélectionner les fonctionnalités** sous **Composants partagés**, sélectionnez **R Server (autonome)**. Cliquez sur **Suivant**, puis sur **Terminer** pour désinstaller les composants sélectionnés uniquement.  
   
### <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>L’installation échoue avec l’erreur : « Seul un produit Revolution Enterprise peut être installé à la fois. »  
Vous pouvez rencontrer cette erreur si votre installation de produits Revolution Analytics est ancienne ou si vous disposez d’une version préliminaire de SQL Server R Services. Vous devez désinstaller toute version précédente avant de pouvoir installer une version plus récente de Microsoft R Server. L’installation côte à côte avec d’autres versions des outils Revolution Enterprise n’est pas prise en charge.  

Toutefois, les installations côte à côte sont prises en charge lors de l’utilisation de R Server (autonome) avec [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] et 
  
### <a name="unable-to-uninstall-older-components"></a>Impossible de désinstaller les composants plus anciens   
  
Si vous rencontrez des problèmes de suppression d’une version antérieure, vous devrez peut-être modifier le Registre pour supprimer les clés associées.  

> [!IMPORTANT]
> Ce problème s’applique uniquement si vous avez installé une version préliminaire de Microsoft R Server ou une version CTP de SQL Server 2016 R Services.
  
1. Ouvrez le Registre Windows et recherchez cette clé : `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`.  
2. Supprimez toutes les entrées suivantes, le cas échéant, et si la clé contient uniquement la valeur `sEstimatedSize2` :  
  
    -   E0B2C29E-B8FC-490B-A043-2CAE75634972        (pour 8.0.2)  
  
    -   46695879-954E-4072-9D32-1CC84D4158F4        (pour 8.0.1)  
  
    -   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (pour 8.0.0)  
  
    -   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (pour 7.5.0)  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft R Server](../../advanced-analytics/r-services/r-server-standalone.md)  
  
  