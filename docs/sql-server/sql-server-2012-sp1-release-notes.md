---
title: "Notes de publication de SQL Server 2012 SP1 | Microsoft Docs"
ms.prod: sql-server-2012
ms.technology: server-general
ms.custom: 
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72171357-28de-4edd-bdfd-194f97225a6f
caps.latest.revision: 49
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 978e780dd19e34c27ceef49ff8388f6ae1f155ed
ms.openlocfilehash: bb97a542834adce9221b55f54c4bf5657586f187
ms.contentlocale: fr-fr
ms.lasthandoff: 09/02/2017

---
# <a name="sql-server-2012-sp1-release-notes"></a>Notes de publication de SQL Server 2012 SP1
Ces notes de publication décrivent des problèmes connus que vous devez examiner avant d’installer ou de résoudre les problèmes de [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1. Ce document Notes de publication, uniquement disponible en ligne (absent du support d'installation), est régulièrement mis à jour.  
  
## <a name="bkmk_top"></a>Sommaire  
[1.0 Avant l’installation](#bmk_Install)  
  
[2.0 Analysis Services et PowerPivot](#bkmk_AS)  
  
[3.0 Reporting Services](#bkmk_RS)  
  
[4.0 Data Quality Services](#bkmk_DQS)  
  
[5.0 SQL Server Express](#bkmk_Express)  
  
[6.0 Service et concepteur de capture de données modifiées pour Oracle par Attunity](#bkmk_CDC)  
  
[7.0 Infrastructure d'application de couche Données (DACFx) de SQL Server](#DACFx)  
  
[8.0 Problèmes connus résolus dans ce Service Pack](#bkmk_known_issues_fixed)  
  
## <a name="bmk_Install"></a>1.0 Avant l’installation  
Lisez les informations répertoriées ci-dessous avant d'installer SQL Server 2012 SP1.  
  
### <a name="11-reinstalling-an-instance-of-sql-server-failover-custer-fails-if-you-use-the-same-ip-address"></a>1.1 Échec de la réinstallation d'une instance de cluster de basculement SQL Server si vous utilisez la même adresse IP  
**Problème :** si vous spécifiez une adresse IP incorrecte lors de l’installation d’une instance de cluster de basculement SQL Server, l’installation échoue. Après avoir désinstallé l'instance en échec, si vous tentez de réinstaller l'instance de cluster de basculement SQL Server avec le même nom d'instance et une adresse IP correcte, l'installation échoue. Cet échec est dû au groupe de ressources dupliqué conservé par l'installation précédente.  
  
**Solution de contournement :** pour résoudre ce problème, utilisez un autre nom d'instance lors de la réinstallation, ou supprimez manuellement le groupe de ressources avant réinstallation. Pour plus d'informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server](http://msdn.microsoft.com/library/ms191545).  
  
### <a name="12-choose-the-correct-file-to-download-and-install"></a>1.2 Choisir le fichier approprié à télécharger et installer  
Utilisez le tableau suivant pour déterminer le fichier à télécharger et installer. Vérifiez que vous disposez de la configuration requise avant d'installer le Service Pack. La configuration requise est disponible sur les pages de téléchargement liées dans le tableau.  
  
|Si la version actuellement installée est...|Vous souhaitez…|Téléchargez et installez...|  
|-------------------------------------------|----------------------|---------------------------|  
|**Installations 32 bits :**|||  
|Une version 32 bits de n’importe quelle édition de SQL Server 2012|Effectuer la mise à niveau vers la version 32 bits de SQL Server 2012 SP1|SQLServer2012SP1-KB2674319-x86-ENU.exe à partir d’ [ici](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Une version 32 bits de SQL Server 2012 RTM Express|Effectuer la mise à niveau vers la version 32 bits de SQL Server 2012 Express SP1|SQLServer2012SP1-KB2674319-x86-ENU.exe à partir d’ [ici](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Une version 32 bits de seulement le client et les outils de gestion pour SQL Server 2012 (y compris SQL Server 2012 Management Studio)|Effectuer la mise à niveau du client et des outils de gestion vers la version 32 bits de SQL Server 2012 SP1|SQLManagementStudio_x86_ENU.exe à partir d’ [ici](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Une version 32 bits de SQL Server 2012 Management Studio Express|Effectuer la mise à niveau vers la version 32 bits de SQL Server 2012 SP1 Management Studio Express|SQLManagementStudio_x86_ENU.exe à partir d’ [ici](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Une version 32 bits d'une édition quelconque de SQL Server 2012 **et** une version 32 bits du client et des outils de gestion (y compris SQL Server 2012 RTM Management Studio)|Effectuer la mise à niveau de tous les produits vers la version 32 bits de SQL Server 2012 SP1|SQLServer2012SP1-KB2674319-x86-ENU.exe à partir d’ [ici](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Une version 32 bits d'un ou de plusieurs outils du [Feature Pack Microsoft SQL Server 2012 RTM](http://www.microsoft.com/download/details.aspx?id=16978)|Effectuer la mise à niveau des outils vers la version 32 bits du Feature Pack Microsoft SQL Server 2012 SP1|Un ou plusieurs fichiers du [Feature Pack Microsoft SQL Server 2012 SP1](http://go.microsoft.com/fwlink/p/?LinkID=268266)|  
|Pas d’installation 32 bits de SQL Server 2012|Installer SQL Server 2012 32 bits, y compris SP1 (nouvelle instance avec SP1 préinstallé)|SQLServer2012SP1-FullSlipstream-x86-ENU.exe **et** SQLServer2012SP1-FullSlipstream-x86-ENU.box à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Pas d’installation 32 bits de SQL Server 2012 Management Studio|Installer la version 32 bits de SQL Server 2012 Management Studio, y compris SP1|SQLManagementStudio_x86_ENU.exe à partir d’ [ici](http://go.microsoft.com/fwlink/p/?LinkId=267905)|  
|Pas de version 32 bits de SQL Server 2012 RTM Express|Install la version 32 bits de SQL Server 2012 Express, y compris SP1|SQLEXPR32_x86_ENU.exe à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkId=267905)|  
|Une installation 32 bits de **SQL Server 2008** ou de **SQL Server 2008 R2**|**Mise à niveau sur place** vers la version 32 bits de SQL Server 2012, y compris SP1|SQLServer2012SP1-FullSlipstream-x86-ENU.exe **et** SQLServer2012SP1-FullSlipstream-x86-ENU.box à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|**Installations 64 bits :**|||  
|Une version 64 bits d'une édition quelconque de SQL Server 2012|Effectuer la mise à niveau vers la version 64 bits de SQL Server 2012 SP1|SQLServer2012SP1-KB2674319-x64-ENU.exe à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Version 64 bits de SQL Server 2012 RTM Express|Effectuer la mise à niveau vers la version 64 bits de SQL Server 2012 SP1|SQLServer2012SP1-KB2674319-x64-ENU.exe à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Une version 64 bits uniquement du client et des outils de gestion de SQL Server 2012 (y compris SQL Server 2012 Management Studio)|Effectuer la mise à niveau du client et des outils de gestion vers la version 64 bits de SQL Server 2012 SP1|SQLManagementStudio_x64_ENU.exe à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Version 64 bits de SQL Server 2012 Management Studio Express|Effectuer la mise à niveau vers la version 64 bits de SQL Server 2012 SP1 Management Studio Express|SQLManagementStudio_x64_ENU.exe à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Une version 64 bits d'une édition quelconque de SQL Server 2012 **et** une version 64 bits du client et des outils de gestion (y compris SQL Server 2012 RTM Management Studio)|Effectuer la mise à niveau de tous les produits vers la version 64 bits de SQL Server 2012 SP1|SQLServer2012SP1-KB2674319-x64-ENU.exe à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Une version 64 bits d'un ou de plusieurs outils du [Feature Pack Microsoft SQL Server 2012 RTM](http://www.microsoft.com/download/en/details.aspx?id=16978)|Effectuer la mise à niveau des outils vers la version 64 bits du Feature Pack Microsoft SQL Server 2012 SP1|Un ou plusieurs fichiers du [Feature Pack Microsoft SQL Server 2012 SP1](http://go.microsoft.com/fwlink/p/?LinkID=268266)|  
|Aucune installation version 64 bits de SQL Server 2012|Installer une version 64 bits de Server 2012 notamment SP1 (nouvelle instance avec la version SP1 préinstallée)|SQLServer2012SP1-FullSlipstream-x64-ENU.exe **et** SQLServer2012SP1-FullSlipstream-x64-ENU.box à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Aucune installation version 64 bits de SQL Server 2012 Management Studio|Installer la version 64 bits de SQL Server 2012 Management Studio y compris le SP1|SQLManagementStudio_x64_ENU.exe à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|No version 64 bits de SQL Server 2012 RTM Express|Installer la version 64 bits de SQL Server 2012 Express y compris le SP1|SQLEXPR_x64_ENU.exe à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Une installation 64 bits de **SQL Server 2008** ou de **SQL Server 2008 R2**|**Mise à niveau sur place** vers la version 64 bits de SQL Server 2012, y compris SP1|SQLServer2012SP1-FullSlipstream-x64-ENU.exe **et** SQLServer2012SP1-FullSlipstream-x64-ENU.box à partir d' [ici](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Sommaire](#bkmk_top)  
  
## <a name="bkmk_AS"></a>2.0 Analysis Services et PowerPivot  
  
### <a name="21-powerpivot-configuration-tool-does-not-create-the-powerpivot-gallery"></a>2.1 L'outil de configuration PowerPivot ne crée pas la Galerie PowerPivot  
**Problème :** l'outil de configuration PowerPivot configure un site d'équipe, par conséquent la Galerie PowerPivot n'est pas créée.  
  
**Solution :** créez une application (bibliothèque).  
  
1.  Vérifiez que la fonctionnalité de collection de site **Fonctionnalité d'intégration PowerPivot pour les collections de sites** est active.  
  
2.  Dans la page **Contenu du site** d'un site existant, cliquez sur **Ajouter une application**.  
  
3.  Cliquez sur **Galerie PowerPivot**.  
  
### <a name="22-to-use-powerpivot-for-excel-with-excel-2013-you-must-use-the-add-in-that-is-installed-with-excel"></a>2.2 Pour utiliser PowerPivot pour Excel avec Excel 2013, vous devez utiliser le complément installé avec Excel  
**Problème :** avec Office 2010, PowerPivot pour Excel est un complément autonome qui peut être téléchargé à partir de [http://www.microsoft.com/bi/powerpivot.aspx](http://www.microsoft.com/bi/powerpivot.aspx). Sinon, vous pouvez également le télécharger depuis le [Centre de téléchargement Microsoft](http://www.microsoft.com/download/details.aspx?id=29074). Notez qu'il existe deux versions du complément PowerPivot disponible en téléchargement : un qui est livré avec SQL Server 2008 R2 et un autre qui est fourni avec SQL Server 2012. Toutefois, pour Office 2013, PowerPivot pour Excel est fourni avec Office et s'installe en même temps qu'Excel. Bien que les versions SQL Server 2008 R2 et SQL Server 2012 de PowerPivot pour Excel 2010 ne soient pas compatibles avec Excel 2013, vous pouvez toujours installer PowerPivot pour Excel 2010 sur votre ordinateur client si vous souhaitez exécuter Excel 2010 en parallèle d'Excel 2013. En d'autres termes, les deux versions d'Excel peuvent coexister, de même que les compléments PowerPivot correspondants.  
  
**Solution :** pour utiliser PowerPivot pour Excel 2013, vous devez activer le complément COM. Dans Excel 2013, sélectionnez **Fichier** | **Options** | **Compléments**. Dans la liste déroulante **Gérer** , sélectionnez **Compléments COM** , puis cliquez sur **OK**. Dans **Compléments COM**, sélectionnez **Microsoft Office PowerPivot pour Excel 2013** , puis cliquez sur **OK**.  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Sommaire](#bkmk_top)  
  
## <a name="bkmk_RS"></a>3.0 Reporting Services  
  
### <a name="31-install-and-configure-sharepoint-server-2013-prior-to-installing-reporting-services"></a>3.1 Installer et configurer SharePoint Server 2013 avant d'installer Reporting Services  
**Problème :** terminez la configuration suivante **avant** d'installer SQL Server Reporting Services (SSRS).  
  
1.  Exécutez l'Outil de préparation des produits SharePoint 2013.  
  
2.  Installez SharePoint Server 2013.  
  
3.  Exécutez l'Assistant Configuration de produit SharePoint 2013 ou terminez un ensemble équivalent d'étapes de configuration pour configurer la batterie SharePoint.  
  
**Solution de contournement :**  si vous avez installé le mode SharePoint de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] avant de configurer la batterie SharePoint, la solution de contournement requise dépend des autres composants installés.  
  
### <a name="32-power-view-in-sharepoint-server-2013-requires-microsoftanalysisservicesspclientdll"></a>3.2 Power View dans SharePoint Server 2013 nécessite Microsoft.AnalysisServices.SPClient.dll  
**Problème :** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n’installe pas un composant requis, **Microsoft.AnalysisServices.SPClient.dll**. Si vous installez SharePoint Server 2013 Preview et [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint, mais que vous ne téléchargez pas et n’installez pas le package de programme d’installation de PowerPivot pour SharePoint 2013, **spPowerPivot.msi**, Power View ne fonctionne pas et montre les symptômes suivants.  
  
**Symptômes :** Un message d'erreur semblable au suivant s'affiche lorsque vous essayez de créer un rapport Power View :  
  
-   « Impossible de créer une connexion à la source de données... »  
  
Les détails de l'erreur interne contiennent un message similaire au message suivant :  
  
-   « La valeur Principal SharePoint n'est pas prise en charge pour la propriété de chaîne de connexion Identité de l'utilisateur.  
  
**Solution de contournement :** installez le package d'installation PowerPivot pour SharePoint 2013 (**spPowerPivot.msi**) sur le serveur SharePoint 2013. Le package d'installation est disponible dans le cadre du Feature Pack [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Le Feature Pack peut être téléchargé en accédant au centre de téléchargement [!INCLUDE[msCoName](../includes/msconame-md.md)] à l'adresse [SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266).  
  
### <a name="33-power-view-sheets-in-a-powerpivot-workbook-are-deleted-after-a-scheduled-data-refresh"></a>3.3 Les feuilles Power View dans un classeur PowerPivot sont supprimées après les actualisations des données planifiées  
**Problème**: dans le complément PowerPivot pour SharePoint, les feuilles Power View seront supprimées avec l’utilisation de l’ **actualisation de données planifiée** .  
  
**Solution**: pour utiliser **Scheduled Data Refresh** avec classeurs Power View, créez un classeur PowerPivot qui est simplement le modèle de données. Créez un classeur distinct avec les feuilles Excel et Power View qui se lie au classeur PowerPivot avec le modèle de données. Seul le classeur PowerPivot avec le modèle de données doit être planifiée pour l'actualisation des données.  
  
## <a name="bkmk_DQS"></a>4.0 Data Quality Services  
  
### <a name="41-dqs-available-in-the-incorrect-edition-of-sql-server-2012"></a>4.1 DQS disponible dans la version incorrecte de SQL Server 2012  
**Problème :** dans la version commerciale de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , la fonctionnalité Data Quality Services (DQS) est disponible dans les éditions de SQL Server autres que les éditions Enterprise, Business Intelligence et Developer. Après avoir installé SQL Server 2012 SP1, DQS ne sera disponible que dans les éditions Enterprise, Business Intelligence et Developer.  
  
**Solution**: si vous utilisez DQS dans une édition non prise en charge, effectuez une mise à niveau vers une édition prise en charge ou supprimez la dépendance à cette fonctionnalité dans vos applications.  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Sommaire](#bkmk_top)  
  
## <a name="bkmk_Express"></a>5.0 SQL Server Express  
  
### <a name="51-full-version-of-sql-server-management-studio-available-in-sql-server-2012-express-sp1"></a>5.1 Version complète de SQL Server Management Studio dans SQL Server 2012 Express SP1  
La version SQL Server 2012 Express Service Pack 1 (SP1) inclut la version complète de SQL Server 2012 Management Studio (qui était précédemment disponible uniquement sur le DVD SQL Server 2012) au lieu de SQL Server 2012 Management Studio Express. Pour télécharger et installer SQL Server 2012 Express SP1, consultez [SQL Server 2012 Express Service Pack 1](http://go.microsoft.com/fwlink/p/?linkid=267905).  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Sommaire](#bkmk_top)  
  
## <a name="bkmk_CDC"></a>6.0 Service et concepteur de capture de données modifiées pour Oracle par Attunity  
  
### <a name="61-upgrading-the-cdc-service-and-designer"></a>6.1 Mise à niveau du service et du concepteur de capture de données modifiées  
**Problème :** si le concepteur de capture de données modifiées pour Oracle et le service de capture de données modifiées pour Oracle par Attunity sont installés sur votre ordinateur lorsque vous installez SQL Server 2012 SP1, ces composants ne sont pas mis à niveau lors de l'installation du SP1.  
  
**Solution :** pour mettre à niveau les composants CDC vers la version la plus récente :  
  
1.  Téléchargez les fichiers .msi pour le service de capture de données modifiées pour Oracle par Attunity à partir de la [page de téléchargement du Feature Pack SQL Server 2012 SP1](http://go.microsoft.com/fwlink/p/?LinkID=268266).  
  
2.  Exécutez le fichier .msi.  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Sommaire](#bkmk_top)  
  
## <a name="DACFx"></a>7.0 Infrastructure d'application de couche Données (DACFx) de SQL Server  
**Prise en charge de la mise à niveau sur place**  
  
Cette version de l'Infrastructure d'application de couche Données (DACFx) prend en charge la mise à niveau de versions précédentes, de sorte qu'il n'est pas nécessaire de supprimer les installations DACFx précédentes avant d'effectuer la mise à niveau de cette version. Vous pouvez trouver de versions à venir de DACFx [ici](https://msdn.microsoft.com/library/dn702988.aspx).  
  
**Prise en charge des index XML sélectifs**  
  
SQL Server 2012 SP1 inclut la prise en charge des [Index XML sélectifs (SXI)](http://msdn.microsoft.com/en-us/598ecdcd-084b-4032-81b2-eed6ae9f5d44), une nouvelle fonctionnalité SQL Server qui fournit une nouvelle façon d'indexer les données des colonnes XML avec des performances et une efficacité supplémentaires.  
  
DACFx prend maintenant en charge des index SXI dans tous les scénarios DAC et tous les outils clients. SXI n'est pris en charge que dans cette version du SSDT. Les versions RTM et de septembre 2012 de SSDT ne prennent pas en charge SXI.  
  
**Prise en charge du format natif de données BCP**  
  
Précédemment, le format de données utilisé pour stocker les données de table à l'intérieur des packages DACPAC et BACPAC était JSON. Avec cette mise à jour, le format natif de données BCP est maintenant le format de persistance des données. Cette modification permet d'améliorer la fidélité du type de données SQL Server à DACFx notamment la prise en charge des types SQL_Variant ainsi que les performances de déploiement des données pour les bases de données à grande échelle.  
  
**Conservation de l'état de la contrainte de validation dans la création et déploiement des packages**  
  
Précédemment, DACFx ne conservait pas l'état (WITH CHECK / NOCHECK) des contraintes de vérification définies sur les tables dans le schéma de la base de données et elle ne allouait pas les informations à l'intérieur des DACPAC. Ce comportement pourrait conduire à des problèmes potentiels sur le déploiement des packages quand il y a des données existantes de la table qui ne respectent pas les contraintes de vérification. Avec cette mise à jour, DACFx stocke désormais l'état actuel des contraintes de vérification au sein du DACPAC lors de son extraction d'une base de données et restaure de manière appropriée cet état lors le déploiement des packages.  
  
**Mises à jour de SqlPackage.exe (outil de ligne de commande DACFx)**  
  
-   Extraire DACPAC avec les données - Crée un fichier d'instantanés de base de données (.dacpac) à partir d'une Base de données SQL Windows Azure ou SQL Server active qui contient les données des tables d'utilisateur en plus du schéma de la base de données. Ces packages peuvent être publiés sur une nouvelle ou existante Base de données SQL Windows Azure ou SQL Server avec l'action Publier SqlPackage.exe. Les données contenues dans le package remplacent les données existantes dans la base de données cible.  
  
-   Exporter BACPAC - Crée un fichier de sauvegarde logique (.bacpac) à partir d'une Base de données SQL Windows Azure ou SQL Server active qui contient le schéma de la base de données et les données utilisateur qui peuvent être utilisés pour migrer une base de données de la Base de données SQL Server sur site à la Base de données SQL Windows Azure. Les bases de données compatibles avec Azure peuvent être exportées et importées entre les versions prises en charge de SQL Server.  
  
-   Importer BACPAC – Importe un fichier .bacpac à fin de créer une nouvelle Base de données SQL Windows Azure ou SQL Server, ou en remplir une vide.  
  
Vous trouverez la documentation complète de SqlPackage.exe sur MSDN [ici](http://msdn.microsoft.com/library/hh550080%28v=vs.103%29.aspx).  
  
**Compatibilité du package**  
  
Cette version introduit plusieurs scénarios de compatibilité ascendante des packages DAC.  
  
-   Les packages DAC créés par cette version qui ne contiennent pas d'éléments SXI ou de données de tables peuvent être consommés par les versions précédentes de DACFx (SQL Server 2012 RTM, SQL Server 2012 CU1 et DACFx de septembre 2012).  
  
-   Tous les packages DAC créés par les versions précédentes de DACFx peuvent être consommés par cette version.  
  
## <a name="bkmk_known_issues_fixed"></a>8.0 Problèmes connus résolus dans ce Service Pack  
Pour obtenir la liste complète des bogues et problèmes connus corrigés dans ce Service Pack, consultez cet [article de la Base de connaissances](http://support.microsoft.com/kb/2674319).  
  
[Sommaire](#bkmk_top)  
  
## <a name="see-also"></a>Voir aussi  
[Comment déterminer la version et l'édition de SQL Server](http://support.microsoft.com/kb/321185)  
[Fonctionnalités prises en charge par les éditions de SQL Server 2014](http://msdn.microsoft.com/en-us/5da61ff5-12b9-48e6-b3c8-0dacca1751c4)  
  

