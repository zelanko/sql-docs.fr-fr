---
title: Connexions de données, Sources de données et chaînes de connexion dans le Générateur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10421"
ms.assetid: 7e103637-4371-43d7-821c-d269c2cc1b34
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5821d8d747609abfc8433a3ff9ad0ecf2676be7d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56011011"
---
# <a name="data-connections-data-sources-and-connection-strings-in-report-builder"></a>Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports
  Pour inclure des données dans un rapport, vous devez créer des connexions de données et des datasets. Une connexion de données inclut les informations nécessaires pour accéder à une source de données externe. Un dataset inclut une commande de requête qui spécifie les données à inclure à l'aide de la connexion de données.  
  
1.  **Sources de données dans le volet des données de rapport** Une source de données s'affiche dans le volet des données de rapport une fois que vous avez créé une source de données incorporée ou que vous avez ajouté une source de données partagée.  
  
2.  **Boîte de dialogue Connexion** Utilisez la boîte de dialogue Connexion pour créer ou coller une chaîne de connexion.  
  
3.  **Informations de connexion de données** La chaîne de connexion est passée à l'extension de données.  
  
4.  **Informations d'identification** Les informations d'identification sont gérées indépendamment de la chaîne de connexion.  
  
5.  **Extension de données/Fournisseur de données** La connexion aux données peut s’effectuer via plusieurs couches d’accès aux données.  
  
6.  **Sources de données externes** Récupérez des données à partir de bases de données relationnelles, bases de données multidimensionnelles, listes SharePoint, services Web ou modèles de rapport.  
  
 Pour plus d’informations, consultez [incorporé et connexions de données partagées ou les Sources de données &#40;Générateur de rapports et SSRS&#41; ](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) et [des connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
 Il est également possible d'inclure des données dans un rapport à l'aide de sources de données partagées prédéfinies, de datasets partagés et de parties de rapports. Ces éléments possèdent déjà les informations de connexion de données dont vous avez besoin. Pour plus d’informations, consultez [ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
 ![rs_DataSourcesStory](media/rs-datasourcesstory.gif "rs_DataSourcesStory")  
  
##  <a name="ConnectionString"></a> Exemples de chaînes de connexion  
 Une connexion de données inclut une chaîne de connexion qui est généralement fournie par le propriétaire de la source de données externe. Le tableau suivant présente des exemples de chaînes de connexion pour différents types de sources de données externes.  
  
|**Source de données**|**Exemple**|**Description**|  
|---------------------|-----------------|---------------------|  
|Base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur le serveur local|`data source="(local)";initial catalog=AdventureWorks2012`|Définissez `SQL Server` comme type de source de données.|  
|Base de données d'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|`Data Source=localhost\MSSQL12.InstanceName; Initial Catalog= AdventureWorks2012`|Définissez `SQL Server` comme type de source de données.|  
|Base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express|`Data Source=localhost\MSSQL12.SQLEXPRESS; Initial Catalog= AdventureWorks2012`|Définissez `SQL Server` comme type de source de données.|  
|Base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur le serveur local|`data source=localhost;initial catalog=Adventure Works DW 2012`|Définissez `SQL Server Analysis Services` comme type de source de données.|  
|Liste SharePoint|`data source=http://MySharePointWeb/MySharePointSite/`|Définissez `SharePoint List` comme type de source de données.|  
||||  
|Modèles de rapport|Non applicable.|Vous n'avez pas besoin d'une chaîne de connexion pour un modèle de rapport. Dans le Générateur de rapports, accédez au serveur de rapports et sélectionnez le fichier .smdl correspondant au modèle de rapport.|  
|Serveur Oracle|`data source=myserver`|Définissez `Oracle` comme type de source de données. Les outils du client Oracle doivent être installés sur l'ordinateur hébergeant le Générateur de rapports et sur le serveur de rapports.|  
|Source de données SAP NetWeaver BI|`DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla`|Définissez `SAP NetWeaver BI` comme type de source de données.|  
|Source de données Hyperion Essbase|`Data Source=http://localhost:13080/aps/XMLA; Initial Catalog=Sample`|Définissez `Hyperion Essbase` comme type de source de données.|  
|Source de données Teradata|`data source=` *\<NN>.\<NNN>.\<NNN>.\<N>* `;`|Définissez `Teradata` comme type de source de données. La chaîne de connexion est une adresse IP (Internet Protocol) se présentant sous la forme de quatre champs, chaque champ pouvant comporter de un à trois chiffres.|  
|Source de données Teradata|`Database=` *\<nom_base_de_données>* `; data source=` *\<NN*N *>.\<NNN>.\<NNN>.\<N*NN*>*`;Use X Views=False;Restrict to Default Database=True`|Définissez `Teradata`, comme type de source de données, comme dans l'exemple précédent. Utilisez uniquement la base de données par défaut spécifiée dans la balise Database, et ne découvrez pas automatiquement les relations entre les données.|  
|Source de données XML, service Web|`data source=http://adventure-works.com/results.aspx`|Définissez `XML` comme type de source de données. La chaîne de connexion est une URL pour un service Web prenant en charge le langage de définition de services Web (WSDL, Web Services Definition Language).|  
|Source de données XML, document XML|`http://localhost/XML/Customers.xml`|Définissez `XML` comme type de source de données. La chaîne de connexion est une URL vers le document XML.|  
|Source de données XML, document XML incorporé|*Vide*|Définissez `XML` comme type de source de données. Les données XML sont incorporées dans la définition de rapport.|  
  
 Pour plus d’informations sur chaque type de connexion, consultez [ajouter des données à partir de Sources de données externes &#40;SSRS&#41; ](report-data/add-data-from-external-data-sources-ssrs.md) et [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).  
  

  
##  <a name="Creating"></a> Création de Sources de données  
 Pour créer une source de données incorporée, vous devez disposer d'une chaîne de connexion et des informations d'identification permettant d'accéder aux données. Ces informations proviennent généralement du propriétaire de la source de données. La connexion de données est enregistrée dans la définition de rapport en tant que partie intégrante de la source de données. Les informations d'identification sont gérées indépendamment de la connexion. Pour obtenir des instructions détaillées, consultez [ajouter et vérifier une connexion de données ou d’une Source de données &#40;Générateur de rapports et SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Certains types d'informations d'identification peuvent ne pas prendre en charge tous les scénarios utilisés par le Générateur de rapports : exécuter une requête dans le concepteur de requêtes, afficher un aperçu d'un rapport depuis votre ordinateur lorsque vous n'êtes pas connecté à un serveur de rapports et exécuter le rapport à partir du serveur de rapports. Nous recommandons d'utiliser les sources de données partagées dans la mesure du possible. Vous pouvez stocker des informations d'identification pour une source de données partagée sur le serveur de rapports. Pour plus d’informations, consultez [Spécifier des informations d’identification dans le Générateur de rapports](../../2014/reporting-services/specify-credentials-in-report-builder.md).  
  
 Pour créer une source de données partagée, vous devez utiliser le Gestionnaire de rapports pour créer la source de données directement sur le serveur de rapports, ou utiliser un environnement de création tels que le Concepteur de rapports dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [créer une Source de données partagée ou un Embedded &#40;SSRS&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md).  
  

  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Publication de parties de rapports &#40;Générateur de rapports et SSRS&#41;](report-parts-report-builder-and-ssrs.md)  
  
  
