---
title: Concepteurs de requêtes Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
caps.latest.revision: 16
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aed7304b4e7e48eff1691970da5ff68b03fd0962
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222939"
---
# <a name="reporting-services-query-designers"></a>Concepteurs de requêtes Reporting Services
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Fournit des concepteurs de requêtes graphiques et textuels pour vous aider à générer des requêtes pour chaque type de source de données dans votre rapport.  
  
 Certaines sources de données prennent en charge des concepteurs graphiques qui vous aident à générer une requête de façon interactive. D'autres sources de données utilisent un concepteur de requêtes textuel. Le concepteur de requêtes graphique vous permet de faire glisser des éléments de métadonnées qui représentent les données sous-jacentes sur une source de données vers l'aire de conception de la requête. Le concepteur de requêtes textuel vous permet de taper le texte des commandes dans un volet de requête. Vous pouvez passer d'un concepteur de requêtes graphique à un concepteur de requêtes textuel en cliquant sur l'icône du concepteur de requêtes textuel dans la barre d'outils.  
  
 Les types de sources de données disponibles dans votre rapport sont déterminés par les extensions de données de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installées sur votre client ou serveur de rapports. Pour plus d’informations, consultez [fichier de Configuration RSReportDesigner](report-server/rsreportdesigner-configuration-file.md) et [fichier de Configuration RSReportServer](report-server/rsreportserver-config-configuration-file.md).  
  
 Une extension pour le traitement des données et son concepteur de requêtes associé peuvent être différents au niveau de la prise en charge des sources de données comme suit :  
  
-   **Par type de concepteur de requêtes.** Par exemple, une source de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prend en charge à la fois les concepteurs de requêtes graphiques et textuels.  
  
-   **Par variation de langage de requête.** Par exemple, un langage de requête comme [!INCLUDE[tsql](../includes/tsql-md.md)] peut être différent du point de vue de la syntaxe selon le type de source de données. Le langage [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] et le langage Oracle SQL présentent des variantes de syntaxe pour une commande de requête.  
  
-   **Par prise en charge de la partie schéma d'un nom d'objet de base de données.** Lorsqu'une source de données utilise des schémas dans l'identificateur d'objets de la base de données, le nom du schéma doit être fourni dans la requête pour les noms qui ne font pas appel au schéma par défaut. Par exemple, `SELECT FirstName, LastName FROM [Person].[Person]`.  
  
-   **Par prise en charge des paramètres de requête.** La prise en charge des paramètres varie selon les fournisseurs de données. Certains fournisseurs de données prennent en charge des paramètres nommés ; par exemple, `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`. Certains fournisseurs de données prennent en charge des paramètres sans nom ; par exemple, `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`. L’identificateur de paramètre peut varier selon le fournisseur de données ; par exemple, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise le « au » (@) symbole, Oracle utilise le signe deux-points ( :)). Certains fournisseurs de données ne prennent pas en charge les paramètres.  
  
-   **Par capacité à importer des requêtes.** Par exemple, pour une source de données de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , vous pouvez importer une requête à partir d'un fichier de définition de rapport (.rdl) ou d'un fichier .sql.  
  
## <a name="query-designers"></a>Concepteurs de requêtes  
 Les rubriques suivantes décrivent l'interface utilisateur pour chaque concepteur de requêtes.  
  
-   [Interface utilisateur du concepteur de requêtes MDX Analysis Services](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [Interface utilisateur du concepteur de requêtes DMX Analysis Services](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [Interface utilisateur du concepteur de requêtes graphique](report-data/graphical-query-designer-user-interface.md)  
  
-   [Interface utilisateur du concepteur de requêtes relationnelles](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [Interface utilisateur du concepteur de requêtes Hyperion Essbase](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [Interface utilisateur du concepteur de requêtes de modèle de rapport](report-data/report-model-query-designer-user-interface.md)  
  
-   [Interface utilisateur du concepteur de requêtes SAP NetWeaver BI](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [Concepteur de requêtes de liste SharePoint](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [Interface utilisateur du concepteur de requêtes textuel](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Ajouter des données à partir de sources de données externes &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md)   
 [Extensions de traitement des données et les fournisseurs de données .NET Framework &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md)   
 [Extensions &#40;SSRS&#41;](extensions-ssrs.md)  
  
  
