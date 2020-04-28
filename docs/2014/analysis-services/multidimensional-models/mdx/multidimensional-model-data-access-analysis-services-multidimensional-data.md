---
title: Accès aux données de modèles multidimensionnels (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, data access interfaces
- objects [Analysis Services], data access interfaces
- Analysis Services data access interfaces
- data retrieval [Analysis Services]
- retrieving data
- metadata [Analysis Services]
- data access interfaces [Analysis Services]
- manipulating objects [Analysis Services]
- Analysis Services data access interfaces, about data access interfaces
ms.assetid: 46388efb-3c78-47a2-b5c9-5a69ff394d03
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0d6bea885a03d09da28d5f49ada36cf17375a507
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "79217148"
---
# <a name="multidimensional-model-data-access-analysis-services---multidimensional-data"></a>Accès aux données de modèles multidimensionnels (Analysis Services - Données multidimensionnelles)
  Utilisez les informations de cette rubrique pour savoir comment accéder aux données multidimensionnelles de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à l'aide des méthodes de programmation, d'un script ou d'applications clientes incluant la prise en charge intégrée pour se connecter à un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sur votre réseau.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Applications clientes](#bkmk_clientapps)  
  
 [Langages de requête](#bkmk_querylang)  
  
 [Interfaces de programmation](#bkmk_api)  
  
##  <a name="client-applications"></a><a name="bkmk_clientapps"></a>Applications clientes  
 Bien qu'Analysis Services fournisse les interfaces qui vous permettent de générer ou intégrer les bases de données multidimensionnelles par programmation, une approche plus courante consiste à utiliser des applications clientes Microsoft et d'autres fournisseurs de logiciels existantes qui ont un accès intégré aux données Analysis Services.  
  
 Les applications Microsoft suivantes prennent en charge les connexions natives aux données multidimensionnelles.  
  
### <a name="excel"></a>Excel  
 Les données multidimensionnelles Analysis Services sont souvent présentées à l'aide de contrôles de tableaux et de graphiques croisés dynamiques dans un classeur Excel. Les tableaux croisés dynamiques sont adaptés aux données multidimensionnelles car les hiérarchies, les agrégations et les éléments de navigation due modèle sont totalement compatibles avec les fonctionnalités de synthèse de données d'un tableau croisé dynamique. Un fournisseur de données OLE DB Analysis Services est inclus dans une installation d'Excel pour faciliter la configuration des connexions de données. Pour plus d'informations, consultez [Se connecter ou importer des données à partir de SQL Server Analysis Services](https://go.microsoft.com/fwlink/?linkID=215150).  
  
### <a name="reporting-services-reports"></a>Rapports Reporting Services  
 Vous pouvez utiliser le Générateur de rapports ou le Concepteur de rapports pour créer des rapports qui utilisent des bases de données Analysis Services contenant des données analytiques. Le Générateur de rapports et le Concepteur de rapports incluent un concepteur de requêtes MDX qui vous permet de taper ou concevoir des instructions MDX qui extraient des données d'une source de données disponible. Pour plus d’informations, consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md) et [Type de connexion Analysis Services pour MDX &#40;SSRS&#41;](../../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md).  
  
### <a name="performancepoint-dashboards"></a>Tableaux de bord PerformancePoint  
 Les tableaux de bord PerformancePoint servent à créer des tableaux de bord SharePoint qui communiquent les performances métier sur des mesures prédéfinies. PerformancePoint inclut la prise en charge des connexions de données aux données multidimensionnelles Analysis Services. Pour plus d’informations, consultez [Créer des connexions de données Analysis Services (PerformancePoint Services)](https://go.microsoft.com/fwlink/?linkid=232471).  
  
### <a name="sql-server-data-tools"></a>SQL Server Data Tools  
 Le modèle et les concepteurs de rapports utilisent des outils de données SQL Server pour créer des solutions qui incluent des modèles MDX. Le déploiement de la solution sur une instance Analysis Services permet de crée la base de données à laquelle vous allez vous connecter par la suite à partir d'Excel, Reporting Services et d'autres applications clientes Business Intelligence.  
  
 SQL Server Data Tools sont générés sur un shell Visual Studio et utilisent des projets pour organiser et contenir le modèle. Pour plus d’informations, consultez [Création de modèles MDX à l’aide des Outils de données SQL Server &#40;SSDT&#41;](../creating-multidimensional-models-using-sql-server-data-tools-ssdt.md).  
  
### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 Pour les administrateurs de base de données, SQL Server Management Studio est un environnement intégré qui gère vos instances de SQL Server, y compris les instances d'Analysis Services et les bases de données multidimensionnelles. Pour plus d’informations, consultez [SQL Server Management Studio](../../../ssms/sql-server-management-studio-ssms.md) et [Se connecter à Analysis Services](../../instances/connect-to-analysis-services.md).  
  
##  <a name="query-languages"></a><a name="bkmk_querylang"></a>Langages de requête  
 MDX est un langage de requête et de calcul standard utilisé pour récupérer les données des bases de données OLAP. Dans Analysis Services, MDX est le langage de requête utilisé pour récupérer les données, mais prend également en charge la définition des données et la manipulation de données. Les éditeurs MDX sont générés dans SQL Server Management Studio, Reporting Services et les outils de données SQL Server. Vous pouvez utiliser les éditeurs MDX pour créer des requêtes ad hoc ou un script réutilisable si l'opération de données est répétée.  
  
 Certains outils et applications, par exemple Excel, utilisent une instruction MDX pour interroger en interne une source de données Analysis Services. Vous pouvez également utiliser MDX par programmation en incluant l'instruction MDX dans une requête XMLA Execute.  
  
 Pour plus d'informations sur MDX, consultez les liens suivants :  
  
 [Interrogation de données multidimensionnelles à l'aide de MDX](querying-multidimensional-data-with-mdx.md)  
  
 [Concepts clés de MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)  
  
 [Principes de base des requêtes MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
 [Principes de base des scripts MDX &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)  
  
##  <a name="programmatic-interfaces"></a><a name="bkmk_api"></a>Interfaces de programmation  
 Lorsque vous développez une application personnalisée qui utilise des données multidimensionnelles, votre approche pour accéder aux données tombera très probablement dans l'une des catégories suivantes :  
  
-   **XMLA**. Utilisez XMLA lorsque vous avez besoin d'assurer la compatibilité avec une grande variété de systèmes d'exploitation et de protocoles. XMLA offre une plus grande souplesse, mais souvent au détriment des performances et de la facilité de programmation.  
  
-   **Bibliothèques clientes**. Utilisez les bibliothèques clientes Analysis Services, telles qu'ADOMD.NET, AMO et OLE DB lorsque vous souhaitez accéder aux données par programmation à partir des applications clientes qui s'exécutent sur un système d'exploitation Microsoft Windows. Les bibliothèques clientes encapsulent XMLA avec un modèle objet et des optimisations qui offrent de meilleures performances.  
  
     Les bibliothèques clientes ADOMD.NET et AMO (Analysis Management Objects) sont destinées aux applications écrites en code managé. Utilisez OLE DB pour Analysis Services si votre application est écrite en code natif.  
  
 Le tableau suivant fournit des détails supplémentaires et des liens sur les bibliothèques clientes utilisées pour connecter Analysis Services à une application personnalisée.  
  
|Interface|Description|  
|---------------|-----------------|  
|Objets AMO (Analysis Management Objects) Analysis Services|AMO est le modèle d'objet principal pour administrer des instances d'Analysis Services et des bases de données multidimensionnelles dans le code. Par exemple, SQL Server Management Studio utilise AMO pour prendre en charge l'administration de serveur et de base de données. Pour plus d’informations, consultez [Développement avec AMO &#40;Analysis Management Objects&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).|  
|ADOMD.NET|ADOMD.NET est le modèle d'objet principal de création et d'accès aux données multidimensionnelles dans les applications personnalisées. Vous pouvez utiliser ADOMD.NET dans une application cliente managée pour récupérer des informations [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à l'aide des interfaces d'accès aux données classiques de Microsoft .NET Framework. Pour plus d’informations, consultez [Développement avec ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net) et [Programmation du client ADOMD.NET](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming).|  
|Fournisseur OLE DB pour Analysis Services (MSOLAP.dll)|Vous pouvez utiliser le fournisseur OLE DB natif pour accéder à [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] par programmation à partir d'une API non-gérée. Pour plus d’informations, consultez [Fournisseur OLE DB Analysis Services &#40;Analysis Services - Données multidimensionnelles&#41;](../../dev-guide/analysis-services-ole-db-provider-analysis-services-multidimensional-data.md).|  
|Ensembles de lignes de schéma|Les tables d'ensemble de lignes de schéma sont des structures de données qui contiennent des informations descriptives sur un modèle multidimensionnel déployé sur le serveur, ainsi que des informations sur l'activité du serveur. En tant que programmeur, vous pouvez interroger les tables d'ensemble de lignes de schéma dans les applications clientes pour examiner des métadonnées stockées et récupérer des informations de support et de surveillance sur une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Vous pouvez utiliser les ensembles de lignes de schéma avec ces interfaces de programmation : OLE DB, OLE DB pour Analysis Services, OLE DB pour l'exploration de données, ou XMLA. Pour plus d’informations, consultez [Ensembles de lignes de schéma Analysis Services](https://docs.microsoft.com/bi-reference/schema-rowsets/analysis-services-schema-rowsets).<br /><br /> Voici les approches possibles pour utiliser des ensembles de lignes de schéma :<br /><br /> Exécuter des requêtes DMV dans SQL Server Management Studio ou dans des rapports personnalisés pour accéder aux ensembles de lignes de schéma à l'aide de la syntaxe SQL. Pour plus d’informations, consultez [Utiliser des vues de gestion dynamique &#40;DMVs&#41; pour surveiller Analysis Services](../../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md).<br /><br /> Écrire du code ADOMD.NET qui appelle un ensemble de lignes de schéma.<br /><br /> Exécuter directement la méthode XMLA `Discover` sur une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour récupérer les informations sur l'ensemble de lignes de schéma. Pour plus d’informations, consultez [Méthode Discover &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover).|  
|XMLA|XMLA est l'API de niveau le plus bas à la disposition d'un programmeur Analysis Services, et le dénominateur commun sous-jacent de toutes les méthodologies d'accès aux données Analysis Services. XMLA est une norme de l'industrie, un protocole XML basé sur SOAP qui prend en charge l'accès universel aux données sur n'importe quelle source de données multidimensionnelle standard disponible via une connexion HTTP. Elle utilise SOAP pour formuler les requêtes et les réponses pour les données multidimensionnelles. Si votre application s'exécute sur une plateforme autre que Windows, vous pouvez utiliser XMLA pour accéder à une base de données multidimensionnelle qui s'exécute sur un serveur Windows de votre réseau. Pour plus d’informations, consultez [Développement avec XMLA dans Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).|  
|ASSL (Analysis Services Scripting Language)|ASSL est un terme descriptif qui s'applique aux extensions Analysis Services du protocole XMLA. Les extensions ASSL permettent à Analysis Services d'utiliser des éléments XMLA dépassant les fonctions de base du protocole et autorisant la prise en charge de la définition, de la manipulation et du contrôle des données.  Alors que les méthodes Execute et Discover sont décrites par le protocole XMLA, ASSL ajoute la fonction suivante :<br /><br /> Script XMLA<br /><br /> Définition d'objets XMLA<br /><br /> Commandes XMLA<br /><br /> <br /><br /> Pour plus d'informations, consultez [Développement avec le langage de script Analysis Services &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à Analysis Services](../../instances/connect-to-analysis-services.md)   
 [Développement avec le langage de script Analysis Services &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Développement avec XMLA dans Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [Accès aux données de modèle tabulaire](../../tabular-models/tabular-model-data-access.md)  
  
  
