---
title: "Source OData | Microsoft Docs"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.DTS.DESIGNER.ODATASOURCE.F1"
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Source OData
  Utilisez le composant source OData dans un package SSIS pour consommer les données provenant d’un service OData (Open Data Protocol). Le composant prend en charge les protocoles OData v3 et v4.  
  
-   Pour le protocole OData V3, le composant prend en charge les formats de données JSON et ATOM.  
  
-   Pour le protocole OData V4, le composant prend en charge le format de données JSON.  
  
> [!NOTE]  
>  Vous pouvez également utiliser la source OData pour lire des listes SharePoint. Pour visualiser toutes les listes d’un serveur SharePoint, utilisez l’URL suivante : http://\<serveur>/_vti_bin/ListData.svc. Pour plus d'informations sur les conventions d'URL SharePoint, consultez [Interface REST de SharePoint Foundation](http://msdn.microsoft.com/library/ff521587.aspx).  La source OData prend désormais en charge les produits Microsoft Dynamics AX Online et Microsoft Dynamics CRM Online.
  
## <a name="odata-format"></a>Format OData  
 La plupart des services ODatas retournent les résultats dans plusieurs formats. Vous pouvez spécifier le format du jeu de résultats à l'aide de l'option de requête $format. Les formats comme JSON et JSON Light sont plus efficaces qu’ATOM ou XML, et peuvent offrir un gain de performances en cas de transfert d’un grand volume de données. Le tableau suivant fournit les résultats des tests. Comme vous pouvez le voir, le passage d’ATOM à JSON s’est traduit par un gain de performances de 30 à 53 %, et le passage d’ATOM au nouveau format JSON Light (disponible dans WCF Data Services 5.1) a entraîné un gain de performances de 67 %.  
  
|||||  
|-|-|-|-|  
|Lignes|ATOM|JSON|JSON (Light)|  
|10000|113 secondes|74 secondes|68 secondes|  
|1000000|1110 secondes|853 secondes|665 secondes|  
  
> [!NOTE]  
>  La source OData SSIS utilise 5.6.1 pour analyser les flux OData V3 et ODataLib 6.12.0 pour analyser les flux OData V4.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Didacticiel : Utiliser la source OData](../../integration-services/data-flow/tutorial-using-the-odata-source.md)  
  
-   [Modifier la requête de la source OData à l’exécution](../../integration-services/data-flow/modify-odata-source-query-at-runtime.md)  
  
-   [Éditeur de la source OData &#40;page Connexion&#41;](../../integration-services/data-flow/odata-source-editor-connection-page.md)  
  
-   [Éditeur de la source OData &#40;page Colonnes&#41;](../../integration-services/data-flow/odata-source-editor-columns-page.md)  
  
-   [Éditeur de la source OData &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/odata-source-editor-error-output-page.md)  
  
-   [Propriétés de la source OData](../../integration-services/data-flow/odata-source-properties.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions OData](../../integration-services/connection-manager/odata-connection-manager.md)  
  
  