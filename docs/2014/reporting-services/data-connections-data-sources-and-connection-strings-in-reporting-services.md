---
title: Connexions de données, Sources de données et chaînes de connexion dans Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [Reporting Services], data sources
- reports [Reporting Services], data
- expressions [Reporting Services], data sources
- data sources [Reporting Services], connections
- connection strings [Reporting Services]
- shared data sources [Reporting Services]
- Reporting Services, data sources
- logins [Reporting Services]
ms.assetid: 4d8f0ae1-102b-4b3d-9155-fa584c962c9e
caps.latest.revision: 112
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 021028f9c5039c04de522fe98b23f93a3b529eba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292259"
---
# <a name="data-connections-data-sources-and-connection-strings-in-reporting-services"></a>Connexions de données, sources de données et chaînes de connexion dans Reporting Services
  Pour inclure des données dans un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] de rapports, vous devez d’abord créer *des sources de données* et *jeux de données*. Cette rubrique explique le type des sources de données, comment créer les sources de données et les informations importantes liées aux informations d'identification de source de données. Une source de données inclut le type de source de données, les informations de connexion et le type d'informations d'identification à utiliser. Il existe deux types de sources de données : incorporée et partagée. Une source de données incorporée est définie dans le rapport et utilisée uniquement par ce rapport. Une source de données partagée est définie indépendamment d'un rapport et peut être utilisée par plusieurs rapports. Pour plus d’informations, consultez [Connexions de données ou sources de données incorporées et partagées &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) et [Datasets incorporés et partagés &#40;Générateur de rapports et SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode natif &#124; [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint|  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  

  
##  <a name="bkmk_data_sources"></a> Sources de données incorporées et partagées  
 La différence entre les deux sources de données réside dans leur mode de création, de stockage et de gestion.  
  
-   Dans le Concepteur de rapports, créer des sources de données incorporée ou partagée dans le cadre d’un [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] projet. Vous pouvez choisir de les utiliser localement pour l'aperçu ou de les déployer dans le cadre du projet sur un serveur de rapports ou sur un site SharePoint. Vous pouvez utiliser les extensions de données personnalisées qui ont été installées sur votre ordinateur et sur le serveur de rapports ou le site SharePoint sur lequel vous déployez vos rapports.  
  
     Les administrateurs système peuvent installer et configurer des extensions supplémentaires pour le traitement des données, ainsi que des fournisseurs de données .NET Framework. Pour plus d’informations, consultez [Extensions pour le traitement des données et fournisseurs de données .NET Framework &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md).  
  
     Les développeurs peuvent utiliser l’API <xref:Microsoft.ReportingServices.DataProcessing> pour créer des extensions pour le traitement des données permettant de prendre en charge d’autres types de sources de données.  
  
-   Dans le Générateur de rapports, accédez à un serveur de rapports ou à un site SharePoint et sélectionnez les sources de données partagées ou créez des sources de données incorporées dans le rapport. Vous ne pouvez pas créer de source de données partagée dans le Générateur de rapports. Vous ne pouvez pas utiliser les extensions de données personnalisées dans le Générateur de rapports.  
  
##  <a name="bkmk_DataConnections"></a> Extensions de données intégrées  
 Les extensions de données par défaut dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] comprennent les types de connexions de données suivants :  
  
-   Microsoft SQL Server  
  
-   Microsoft SQL Server Analysis Services  
  
-   Liste Microsoft SharePoint  
  
-   [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]  
  
-   Microsoft SQL Server Parallel Data Warehouse  
  
-   OLE DB  
  
-   Oracle  
  
-   SAP NetWeaver BI  
  
-   Hyperion Essbase  
  
-   Teradata  
  
-   XML  
  
-   ODBC  
  
-   Modèle sémantique Microsoft BI pour Power View : sur un site SharePoint qui a été configuré pour une galerie PowerPivot et [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], ce type de source de données est disponible. Ce type de source de données est utilisé uniquement pour les présentations [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]. Pour plus d'informations, consultez [Création de modèles tabulaires sémantiques BI pour Power View parfaits](http://technet.microsoft.com/video/building-the-perfect-bi-semantic-tabular-models-for-power-view.aspx).  
  
 Pour obtenir la liste complète des sources de données et des versions prises en charge par [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
##  <a name="bkmk_create_data_source"></a> Créer une source de données  
 Pour créer une source de données, vous devez indiquer les informations suivantes :  
  
-   **Type de source de données** le type de connexion, par exemple, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Choisissez cette valeur dans la liste déroulante des types de connexion.  
  
-   **Informations sur la connexion** Les informations de connexion comportent le nom et l'emplacement de la source de données, ainsi que les propriétés de connexion spécifiques à chaque fournisseur de données. La *chaîne de connexion* est la représentation textuelle des informations de connexion. Par exemple, si la source de données est une base de données SQL Server, vous pouvez spécifier le nom de cette base de données. Pour les sources de données incorporées, vous pouvez également écrire des chaînes de connexion basées sur des expressions qui sont évaluées au moment de l'exécution. Pour plus d'informations, consultez [Chaînes de connexion basées sur des expressions](#Expressions) plus loin dans cette rubrique.  
  
-   **Informations d'identification** Vous fournissez les informations d'identification nécessaires pour accéder aux données. Le propriétaire de la source de données doit vous avoir accordé les autorisations appropriées pour accéder à la fois à la source de données et aux données spécifiques de la source de données. Par exemple, pour vous connecter à l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] installée sur un serveur réseau, vous devez être autorisé non seulement à vous connecter à ce serveur, mais aussi à accéder en lecture seule à cette base de données.  
  
    > [!NOTE]  
    >  Par défaut, les informations d'identification sont gérées indépendamment des sources de données. Les informations d'identification que vous utilisez pour afficher un aperçu de votre rapport sur un système local peuvent être différentes de celles dont vous avez besoin pour afficher votre rapport publié. Après avoir enregistré une source de données sur le serveur de rapports ou le site SharePoint, vous devrez peut-être modifier les informations d'identification pour travailler à partir de cet emplacement. Pour plus d'informations, consultez [Informations d'identification pour sources de données](#bkmk_credentials).  
  
> [!NOTE]  
>  Lorsque vous créez une source de données incorporée pour un rapport dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], vous devez créer la source de données dans le Concepteur de rapports dans l’Explorateur de solutions ou dans le volet de données de rapport, mais pas dans l’Explorateur de serveurs. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Le Concepteur de rapports ne prend pas en charge [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sources de données créées dans l’Explorateur de serveurs.  
  
 Le volet des données de rapport affiche les sources de données incorporées et les références aux sources de données partagées qui ont été ajoutées au rapport. Dans le Générateur de rapports, une référence à une source de données partagée pointe vers une source de données partagée sur un serveur de rapports ou un site SharePoint. Dans le Concepteur de rapports, une référence de source de données partagée pointe vers une source de données partagée dans l'Explorateur de solutions dans le dossier de source de données partagée.  
  
##  <a name="bkmk_credentials"></a> Informations d’identification pour sources de données  
 Par défaut, les informations d'identification peuvent être enregistrées et gérées indépendamment des informations de connexion. Les informations d'identification sont utilisées pour créer une source de données, exécuter une requête de dataset et afficher un aperçu d'un rapport.  
  
> [!NOTE]  
>  Nous vous recommandons de ne pas inclure les informations de connexion, telles que les noms de connexion et les mots de passe, aux propriétés de connexion de la source de données. Utilisez les sources de données partagées avec les informations d'identification stockées dans la mesure du possible. Dans un environnement de création, utilisez la page Informations d'identification de la boîte de dialogue **Source de données** pour entrer des informations d'identification lorsque vous créez une connexion de données ou exécutez une requête de dataset.  
  
 Les informations d'identification que vous entrez pour l'accès aux données à partir de votre ordinateur sont stockées en sécurité dans le fichier local de configuration du projet et sont spécifiques à votre ordinateur. Si vous copiez les fichiers de projet sur un autre ordinateur, vous devez redéfinir les informations d'identification de la source de données.  
  
 Lorsque vous déployez un rapport sur le serveur de rapports ou sur le site SharePoint, ses sources de données incorporées et partagées sont gérées de manière indépendante. Les informations d'identification nécessaires à la source de données pour accéder aux données de votre ordinateur peuvent être différentes de celles dont le serveur de rapports a besoin pour accéder aux données.  
  
 ![Remarque](media/rs-fyinote.png "Remarque")une bonne pratique consiste à vérifier que les connexions de source de données continuent à fonctionner une fois que vous publiez un rapport. Si vous devez modifier les informations d'identification, vous pouvez les modifier directement sur le serveur de rapports.  
  
 Pour modifier les sources de données utilisées par un rapport, vous pouvez modifier les propriétés de rapport dans Report Manager en mode natif ou à partir de bibliothèques de documents en mode SharePoint. Pour plus d'informations, consultez les documents suivants :  
  
-   [Store les informations d’identification dans une Source de données Reporting Services](report-data/store-credentials-in-a-reporting-services-data-source.md) [Store les informations d’identification dans une Source de données Reporting Services](report-data/store-credentials-in-a-reporting-services-data-source.md)  
  
-   [Spécifier des informations d'identification et de connexion pour les sources de données de rapports](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
-   [Spécifier des connexions pour des extensions de traitement de données personnalisées](report-data/specify-connections-for-custom-data-processing-extensions.md)  
  
-   [Spécifier des informations d’identification dans le Générateur de rapports](../../2014/reporting-services/specify-credentials-in-report-builder.md)  
  
-   [Ajouter et vérifier une connexion de données ou d’une Source de données &#40;Générateur de rapports et SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
##  <a name="bkmk_connection_examples"></a> Exemples de chaîne de connexion courante  
 Les chaînes de connexion constituent la représentation textuelle des propriétés de connexion pour un fournisseur de données. Le tableau suivant présente des exemples de chaînes de connexion pour différents types de connexion de données.  
  
|**Source de données**|**Exemple**|**Description**|  
|---------------------|-----------------|---------------------|  
|Base de données SQL Server sur le serveur local|`data source="(local)";initial catalog=AdventureWorks`|Définir le type de source de données `Microsoft SQL Server`. Pour plus d’informations, consultez [Type de connexion SQL Server &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md).|  
|Base de données SQL Server sur le serveur local|`data source="(local)";initial catalog=AdventureWorks`|Définir le type de source de données `Microsoft SQL Server`.|  
|Instance SQL Server<br /><br /> base de données|`Data Source=localhost\MSSQL10_50.InstanceName; Initial Catalog=AdventureWorks`|Définir le type de source de données `Microsoft SQL Server`.|  
|Base de données SQL Server Express|`Data Source=localhost\MSSQL10_50.SQLEXPRESS; Initial Catalog=AdventureWorks`|Définir le type de source de données `Microsoft SQL Server`.|  
|[!INCLUDE[ssSDS](../includes/sssds-md.md)] dans le cloud|`Data Source=<host>;Initial Catalog=AdventureWorks; Encrypt=True`|Définir le type de source de données `Windows Azure SQL Database`. Pour plus d’informations, consultez [Type de connexion SQL Azure &#40;SSRS&#41;](report-data/sql-azure-connection-type-ssrs.md).|  
|SQL Server Parallel Data Warehouse|`HOST=<IP address>;database= AdventureWorks; port=<port>`|Définir le type de source de données `Microsoft SQL Server Parallel Data Warehouse`. Pour plus d’informations, consultez [Type de connexion SQL Server Parallel Data Warehouse &#40;SSRS&#41;](report-data/sql-server-parallel-data-warehouse-connection-type-ssrs.md).|  
|Base de données Analysis Services sur le serveur local|`data source=localhost;initial catalog=Adventure Works DW`|Définir le type de source de données `Microsoft SQL Server Analysis Services`. Pour plus d’informations, consultez [Type de connexion Analysis Services pour MDX &#40;SSRS&#41;](report-data/analysis-services-connection-type-for-mdx-ssrs.md) ou [Type de connexion Analysis Services pour DMX &#40;SSRS&#41;](report-data/analysis-services-connection-type-for-dmx-ssrs.md).|  
|Base de données de modèles tabulaires Analysis Services avec une perspective Ventes|`Data source=<servername>;initial catalog= Adventure Works DW;cube='Sales’`|Définir le type de source de données `Microsoft SQL Server Analysis Services`. Spécifiez le nom de la perspective dans le paramètre cube=. Pour plus d’informations, consultez [Perspectives &#40;SSAS Tabular&#41;](../analysis-services/tabular-models/perspectives-ssas-tabular.md).|  
|Source de données de modèle de rapport sur un serveur de rapports configuré en mode natif|`Server=http://myreportservername/reportserver; datasource=/models/Adventure Works`|Spécifiez l'URL du serveur de rapports ou de la bibliothèque de documents, ainsi que le chemin d'accès au modèle publié dans l'espace de noms du dossier du serveur de rapports ou du dossier de la bibliothèque de documents. Pour plus d’informations, consultez [Connexion à un modèle de rapport &#40;SSRS&#41;](report-data/report-model-connection-ssrs.md).|  
|Source de données de modèle de rapport sur un serveur de rapports configuré en mode intégré SharePoint|`Server=http://server; datasource=http://server/site/documents/models/Adventure Works.smdl`|Spécifiez l'URL du serveur de rapports ou de la bibliothèque de documents, ainsi que le chemin d'accès au modèle publié dans l'espace de noms du dossier du serveur de rapports ou du dossier de la bibliothèque de documents.|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server|`provider=MSOLAP.2;data source=<remote server name>;initial catalog=FoodMart 2000`|Définissez le type de source de données `OLE DB Provider for OLAP Services 8.0`.<br /><br /> Vous pouvez obtenir une connexion plus rapide aux sources de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en affectant à la propriété `ConnectTo` la valeur `8.0`. Pour définir cette propriété, utilisez l'onglet **Propriétés avancées** de la boîte de dialogue **Propriétés de connexion** .|  
|Serveur Oracle|`data source=myserver`|Définissez le type de source de données `Oracle`. Les outils clients Oracle doivent être installés sur l'ordinateur hébergeant le Concepteur de rapports et sur le serveur de rapports. Pour plus d’informations, consultez [Type de connexion Oracle &#40;SSRS&#41;](report-data/oracle-connection-type-ssrs.md).|  
|Source de données SAP NetWeaver BI|`DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla`|Définissez le type de source de données `SAP NetWeaver BI`. Pour plus d’informations, consultez [Type de connexion SAP NetWeaver BI &#40;SSRS&#41;](report-data/sap-netweaver-bi-connection-type-ssrs.md).|  
|Source de données Hyperion Essbase|`Data Source=http://localhost:13080/aps/XMLA; Initial Catalog=Sample`|Définissez le type de source de données `Hyperion Essbase`. Pour plus d’informations, consultez [Type de connexion Hyperion Essbase &#40;SSRS&#41;](report-data/hyperion-essbase-connection-type-ssrs.md).|  
|Source de données Teradata|`data source=`\<NNN>.\<NNN>.\<NNN>.\<NNN>`;`|Définissez le type de source de données `Teradata`. La chaîne de connexion est une adresse IP (Internet Protocol) se présentant sous la forme de quatre champs, chaque champ pouvant comporter de un à trois chiffres. Pour plus d’informations, consultez [Type de connexion Teradata &#40;SSRS&#41;](report-data/teradata-connection-type-ssrs.md).|  
|Source de données XML, service Web|`data source=http://adventure-works.com/results.aspx`|Définissez le type de source de données `XML`. La chaîne de connexion est une URL pour un service Web prenant en charge le langage de définition de services Web (WSDL, Web Services Definition Language). Pour plus d’informations, consultez [Type de connexion XML &#40;SSRS&#41;](report-data/xml-connection-type-ssrs.md).|  
|Source de données XML, document XML|`http://localhost/XML/Customers.xml`|Définissez le type de source de données `XML`. La chaîne de connexion est une URL vers le document XML.|  
|Source de données XML, document XML incorporé|*Vide*|Définissez le type de source de données `XML`. Les données XML sont incorporées dans la définition de rapport.|  
  
 Si vous ne parvenez pas à vous connecter à un serveur de rapports en utilisant `localhost`, vérifiez que le protocole réseau pour le protocole TCP/IP est activé. Pour plus d’informations, consultez [configurer des protocoles clients](../database-engine/configure-windows/configure-client-protocols.md).  
  
 Pour plus d’informations sur les configurations nécessaires pour se connecter à ces types de sources de données, consultez la rubrique spécifique aux connexions de données sous [Ajouter des données à partir de sources de données externes &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) ou [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
##  <a name="bkmk_special_password_characters"></a> Caractères spéciaux dans un mot de passe  
 Si vous configurez votre source de données ODBC ou SQL de manière à demander un mot de passe ou à inclure le mot de passe dans la chaîne de connexion, et si l'utilisateur entre le mot de passe avec des caractères spéciaux tels que des marques de ponctuation, certains pilotes de sources de données sous-jacents ne peuvent pas valider les caractères spéciaux. Lors du traitement du rapport, le message « Mot de passe non valide » peut s'afficher et signaler ce problème. Si le changement du mot de passe s'avère impossible, vous pouvez demander à votre administrateur de base de données de stocker les informations d'identification appropriées sur le serveur en tant que nom de sources de données (DSN) ODBC. Pour plus d'informations, consultez « OdbcConnection.ConnectionString » dans la documentation du Kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
##  <a name="bkmk_Expressions_in_connection_strings"></a> Chaînes de connexion basées sur des expressions  
 Les chaînes de connexion basées sur des expressions sont évaluées au moment de l'exécution. Par exemple, vous pouvez spécifier la source de données comme paramètre, inclure la référence de paramètre dans la chaîne de connexion et permettre à l'utilisateur de choisir une source de données pour le rapport. Par exemple, supposons qu'une société multinationale possède des serveurs de données dans plusieurs pays. Grâce à une chaîne de connexion basée sur une expression, un utilisateur peut sélectionner une source de données pour un pays particulier avant d'exécuter un rapport de ventes.  
  
 L'exemple suivant illustre l'utilisation d'une expression de source de données dans une chaîne de connexion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Il repose sur l'hypothèse que vous avez créé un paramètre de rapport nommé `ServerName`:  
  
```  
="data source=" & Parameters!ServerName.Value & ";initial catalog=AdventureWorks"  
```  
  
 Les expressions de source de données sont traitées au moment de l'exécution ou lors de l'affichage de l'aperçu d'un rapport. L’expression doit être écrit en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Suivez les règles suivantes lorsque vous définissez une expression de source de données :  
  
-   Créez le rapport à l'aide d'une chaîne de connexion statique. Une chaîne de connexion statique désigne une chaîne de connexion qui n'est pas définie par le biais d'une expression (ce qui est par exemple le cas lorsque vous suivez la procédure de création d'une source de données partagée ou spécifique aux rapports). L'utilisation d'une chaîne de connexion statique vous permet de vous connecter à la source de données dans le Concepteur de rapports afin d'obtenir les résultats de requête nécessaires à la création du rapport.  
  
-   Lorsque vous définissez la connexion de source de données, n'utilisez pas une source de données partagée. Vous ne pouvez pas utiliser une expression de source de données dans une source de données partagée. Vous devez définir une source de données incorporée pour le rapport.  
  
-   Spécifiez les informations d'identification indépendamment de la chaîne de connexion. Vous pouvez utiliser des informations d'identification stockées, des informations d'identification saisies ou la sécurité intégrée.  
  
-   Ajoutez un paramètre de rapport pour spécifier une source de données. Pour les valeurs du paramètre, vous pouvez fournir une liste statique de valeurs disponibles, qui doivent être des sources de données utilisables avec le rapport, ou définir une requête qui extrait une liste de sources de données au moment de l'exécution.  
  
-   Vérifiez que la liste de sources de données partage le même schéma de base de données. Toute conception de rapport commence par les informations relatives au schéma. Si le schéma permettant de définir le rapport ne correspond pas au schéma effectivement utilisé par le rapport au moment de l'exécution, celle-ci peut échouer.  
  
-   Avant de publier le rapport, remplacez la chaîne de connexion statique par une expression. N'effectuez cette opération qu'une fois la création du rapport achevée. Dès que vous utilisez une expression, vous ne pouvez pas exécuter la requête dans le Concepteur de rapports. De plus, la liste de champs du volet des données de rapport et la liste Paramètres ne sont pas automatiquement mises à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Incorporée et partagée des connexions de données ou Sources de données &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Gérer les Sources de données de rapport](report-data/manage-report-data-sources.md)   
 [Boîte de dialogue Propriétés données Source, informations d’identification](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)   
 [Boîte de dialogue Propriétés des données partagées Source, informations d’identification](../../2014/reporting-services/shared-data-source-properties-dialog-box-credentials.md)   
 [Créer, modifier et supprimer des Sources de données partagées &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
 [Définir les propriétés de déploiement &#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md)   
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapport](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Ajouter et vérifier une connexion de données ou d’une Source de données &#40;Générateur de rapports et SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
  
