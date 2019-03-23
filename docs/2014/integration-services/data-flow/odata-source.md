---
title: Source OData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4b6b4aeb4059ba659a3188712b1ce76f10efd030
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389577"
---
# <a name="odata-source"></a>Source OData
  Utilisez le composant source OData dans un package SSIS pour consommer les données provenant de services OData (Open Data Protocol). Le composant prend en charge les protocoles OData v2 et v3, ainsi que formats de données et ATOM de JSON.  
  
> [!NOTE]  
>  La source OData peut être utilisée pour lire des listes SharePoint. Pour afficher toutes les listes sur votre serveur SharePoint, utilisez l’URL suivante : http://\<serveur > / listData.svc. Pour plus d'informations sur les conventions d'URL SharePoint, consultez [Interface REST de SharePoint Foundation](https://msdn.microsoft.com/library/ff521587.aspx).  
  
## <a name="odata-format"></a>Format OData  
 La plupart des services ODatas retournent les résultats dans plusieurs formats. Vous pouvez spécifier le format du jeu de résultats à l'aide de l'option de requête $format. Les formats comme JSON et JSON Light sont plus efficaces qu'ATOM/XML, et peuvent offrir de meilleures performances en cas de transfert d'un grand volume de données. Le tableau suivant fournit les résultats des tests. Comme vous pouvez le voir, un gain de performances de 30-53 % a été enregistré en passant d'ATOM à JSON, et un gain de performances de 67 % a été constaté en passant d'ATOM au nouveau format JSON Light (disponible dans WCF Data Services 5.1).  
  
|||||  
|-|-|-|-|  
|Lignes|ATOM|JSON|JSON (Light)|  
|10000|113 secondes|74 secondes|68 secondes|  
|1000000|1110 secondes|853 secondes|665 secondes|  
  
> [!NOTE]  
>  La source OData SSIS utilise ODataLib 5.5.0 pour analyser les flux OData et peut lire tous les formats pris en charge par cette bibliothèque.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Installer et désinstaller le composant Source OData](../install-and-uninstall-odata-source-component.md)  
  
-   [Didacticiel : À l’aide de la Source OData &#91;SSIS&#93;](tutorial-using-the-odata-source.md)  
  
-   [Modifier la requête de la source OData à l’exécution](modify-odata-source-query-at-runtime.md)  
  
-   [Éditeur de la source OData &#40;page Connexion&#41;](../odata-source-editor-connection-page.md)  
  
-   [Éditeur de la source OData &#40;page Colonnes&#41;](../odata-source-editor-columns-page.md)  
  
-   [Éditeur de la source OData &#40;page Sortie d’erreur&#41;](../odata-source-editor-error-output-page.md)  
  
-   [Propriétés de la source OData](odata-source-properties.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions OData](../connection-manager/odata-connection-manager.md)  
  
  
