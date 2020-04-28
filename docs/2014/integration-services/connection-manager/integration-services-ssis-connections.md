---
title: Connexions Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, connections
- SSIS packages, connections
- sources [Integration Services], connections
- packages [Integration Services], connections
- destinations [Integration Services], connections
- tasks [Integration Services], connections
- connections [Integration Services], about connections
- connections [Integration Services]
- SQL Server Integration Services packages, connections
ms.assetid: 72f5afa3-d636-410b-9e81-2ffa27772a8c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 18575c95602f73baa959d35b176cf16220fc8e64
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "79112168"
---
# <a name="integration-services-ssis-connections"></a>Connexions Integration Services (SSIS)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent des connexions pour effectuer différentes tâches et pour implémenter des fonctionnalités [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] :  
  
-   Connexion à des banques de données sources et de destination telles que du texte, des données XML, des classeurs Excel et des bases de données relationnelles pour extraire et charger des données.  
  
-   Connexion à des bases de données relationnelles qui contiennent des données de référence pour effectuer des recherches exactes ou floues.  
  
-   Connexion à des bases de données relationnelles pour exécuter des instructions SQL telles que des commandes SELECT, DELETE et INSERT, et également des procédures stockées.  
  
-   Connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour effectuer des tâches de maintenance et de transfert telles que la sauvegarde de bases de données et le transfert de connexions.  
  
-   Écriture d'entrées de journal dans des fichiers texte, dans des fichiers XML et dans des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , écriture de configurations de package dans des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour créer des tables de travail temporaires dont certaines transformations ont besoin pour effectuer leur travail.  
  
-   Connexion à des projets et des bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour accéder à des modèles d'exploration de données, traiter des cubes et des dimensions, et exécuter du code DDL.  
  
-   Spécification de fichiers et de dossiers existants, ou création de nouveaux fichiers et dossiers à utiliser avec des énumérateurs et des tâches de boucles Foreach.  
  
-   Connexion à des files d’attente de messages, à WMI (Windows Management Instrumentation), à SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object), au web et à des serveurs de messagerie.  
  
 Pour établir ces connexions, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise des gestionnaires de connexions, comme décrit dans la section suivante.  
  
## <a name="connection-managers"></a>Gestionnaires de connexions  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise le gestionnaire de connexions comme représentation logique d'une connexion. Au moment de la conception, vous définissez les propriétés d'un gestionnaire de connexions pour décrire la connexion physique qu' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée lors de l'exécution du package. Par exemple, un gestionnaire de connexions inclut la propriété `ConnectionString` que vous définissez lors de la conception ; au moment de l'exécution, une connexion physique est créée à l'aide de la valeur de la propriété de chaîne de connexion.  
  
 Un package peut utiliser plusieurs instances d'un type de gestionnaire de connexions et vous pouvez définir les propriétés sur chaque instance. Au moment de l'exécution, chaque instance d'un type de gestionnaire de connexions crée une connexion qui possède des attributs différents.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournit différents types de gestionnaires de connexions qui permettent aux packages d’établir une connexion à divers serveurs et à diverses sources de données :  
  
-   Il y a des gestionnaires de connexions intégrés que le programme d'installation installe lorsque vous installez [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Il y a des gestionnaires de connexions qui sont téléchargeables à partir du site Web [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
-   Vous pouvez créer votre propre gestionnaire de connexions personnalisé si les gestionnaires de connexions existants ne répondent pas à vos besoins.  
  
### <a name="built-in-connection-managers"></a>Gestionnaires de connexions intégrés  
 Le tableau suivant répertorie les types de gestionnaires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de connexions fournis par.  
  
|Type|Description|Rubrique|  
|----------|-----------------|-----------|  
|ADO|Établit une connexion à des objets ADO (ActiveX Data Objects).|[Gestionnaire de connexions ADO](ado-connection-manager.md)|  
|ADO.NET|Établit une connexion à une source de données au moyen d'un fournisseur .NET.|[Gestionnaire de connexions ADO.NET](ado-net-connection-manager.md)|  
|CACHE|Lit les données du flux de données ou d'un fichier cache (.caw) et peut enregistrer des données dans le fichier cache.|[Gestionnaire de connexions du cache](cache-connection-manager.md)|  
|DQS|Établit une connexion à un serveur Data Quality Services et à une base de données Data Quality Services sur le serveur.|[Gestionnaire de connexions de nettoyage DQS](dqs-cleansing-connection-manager.md)|  
|EXCEL|Établit une connexion à un fichier de classeur Excel.|[Gestionnaire de connexions Excel](excel-connection-manager.md)|  
|FILE|Établit une connexion à un fichier ou un dossier.|[Gestionnaire de connexions de fichiers](file-connection-manager.md)|  
|FLATFILE|Établit une connexion à des données dans un fichier plat unique.|[Gestionnaire de connexions de fichiers plats](flat-file-connection-manager.md)|  
|FTP|Établit une connexion à un serveur FTP.|[Gestionnaires de connexion FTP](ftp-connection-manager.md)|  
|HTTP|Établit une connexion à un serveur Web.|[Gestionnaire de connexions HTTP](http-connection-manager.md)|  
|MSMQ|Établit une connexion à une file d'attente de messages.|[Gestionnaire de connexions MSMQ](msmq-connection-manager.md)|  
|MSOLAP100|Établit une connexion à une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à un projet.|[Gestionnaire de connexions Analysis Services](analysis-services-connection-manager.md)|  
|MULTIFILE|Établit une connexion à plusieurs fichiers et dossiers.|[Gestionnaire de connexions de fichiers multiples](multiple-files-connection-manager.md)|  
|MULTIFLATFILE|Établit une connexion à plusieurs fichiers et dossiers de données.|[Gestionnaire de connexions de fichiers plats multiples](multiple-flat-files-connection-manager.md)|  
|OLEDB|Établit une connexion à une source de données au moyen d'un fournisseur OLE DB.|[Gestionnaire de connexions OLE DB](ole-db-connection-manager.md)|  
|ODBC|Établit une connexion à une source de données au moyen d'ODBC.|[Gestionnaire de connexions ODBC](odbc-connection-manager.md)|  
|SMOServer|Établit une connexion à un serveur SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects).|[Gestionnaire de connexions SMO](smo-connection-manager.md)|  
|SMTP|Établit une connexion à un serveur de messagerie SMTP.|[Gestionnaire de connexions SMTP](smtp-connection-manager.md)|  
|SQLMOBILE|Établit une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.|[Gestionnaire de connexions de SQL Server Compact Edition](sql-server-compact-edition-connection-manager.md)|  
|WMI|Établit une connexion à un serveur et spécifie la portée de la gestion WMI (Windows Management Instrumentation) sur le serveur.|[Gestionnaire de connexions WMI](wmi-connection-manager.md)|  
  
### <a name="connection-managers-available-for-download"></a>Gestionnaires de connexions pouvant être téléchargés  
 Le tableau suivant répertorie d'autres types de gestionnaires de connexions que vous pouvez télécharger à partir du site Web [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
> [!IMPORTANT]  
>  Les gestionnaires de connexions répertoriés dans le tableau suivant fonctionnent uniquement avec [!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] et [!INCLUDE[ssDeveloperEd11](../../includes/ssdevelopered11-md.md)].  
  
|Type|Description|Rubrique|  
|----------|-----------------|-----------|  
|ORACLE|Établit une connexion à \<un serveur d’informations de version Oracle>.|Le gestionnaire de connexions Oracle est le composant de gestionnaire de connexions du Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour Oracle par Attunity. Le Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour Oracle par Attunity inclut également une source et une destination. Pour plus d'informations, consultez la page de téléchargement [Microsoft Connectors for Oracle and Teradata by Attunity](https://go.microsoft.com/fwlink/?LinkId=251526)(en anglais).|  
|SAPBI|Établit une connexion à un système SAP NetWeaver BI version 7.|Le gestionnaire de connexions SAP BI est le composant de gestionnaire de connexions du Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] for SAP BI. Le Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] for SAP BI inclut également une source et une destination. Pour plus d'informations, consultez la page de téléchargement [Microsoft SQL Server 2008 Feature Pack](https://www.microsoft.com/download/details.aspx?id=30440).|  
|TERADATA|Établit une connexion à \<un serveur d’informations de version Teradata>.|Le gestionnaire de connexions Teradata est le composant de gestionnaire de connexions du Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour Teradata par Attunity. Le Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour Teradata par Attunity inclut également une source et une destination. Pour plus d'informations, consultez la page de téléchargement [Microsoft Connectors for Oracle and Teradata by Attunity](https://go.microsoft.com/fwlink/?LinkId=251526)(en anglais).|  
  
### <a name="custom-connection-managers"></a>Gestionnaires de connexions personnalisés  
 Vous pouvez également écrire des gestionnaires de connexions personnalisés. Pour plus d'informations, consultez [Developing a Custom Connection Manager](../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur l’ajout et la suppression d’un gestionnaire de connexions dans un package, consultez [Ajouter, supprimer ou partager un gestionnaire de connexions dans un package](../add-delete-or-share-a-connection-manager-in-a-package.md).  
  
 Pour plus d’informations sur la définition des propriétés d’un gestionnaire de connexions dans un package, consultez [Définir les propriétés d’un gestionnaire de connexions](../set-the-properties-of-a-connection-manager.md).  
  
## <a name="related-content"></a>Contenu associé  
  
-   Vidéo, [Utilisez Microsoft Attunity Connector for Oracle pour améliorer les performances des packages](https://technet.microsoft.com/sqlserver/gg598963.aspx), sur technet.microsoft.com  
  
-   Articles Wiki, [Connectivité SSIS](https://social.technet.microsoft.com/wiki/contents/articles/sql-server-integration-services-ssis.aspx#Connectivity), sur social.technet.microsoft.com  
  
-   Entrée de blog, [Se connecter à MySQL SSIS](https://go.microsoft.com/fwlink/?LinkId=217669), sur blogs.msdn.com.  
  
-   Article technique [Extraction et chargement des données SharePoint dans SQL Server Integration Services](https://go.microsoft.com/fwlink/?LinkId=247826), sur msdn.microsoft.com.  
  
-   Article technique, [You get "DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER" error message when using Oracle connection manager in SSIS](https://go.microsoft.com/fwlink/?LinkId=233696)(Le message d’erreur « DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER’» s’affiche lors de l’utilisation du gestionnaire de connexions Oracle dans SSIS), sur le site support.microsoft.com.  
  
  
