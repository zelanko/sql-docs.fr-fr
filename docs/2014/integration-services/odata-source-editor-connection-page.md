---
title: Éditeur de source OData (page connexion) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- Sql12.dts.designer.odatasource.connection.f1
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0e36c0a3449566db9a2acee360243c77ee548f92
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057317"
---
# <a name="odata-source-editor-connection-page"></a>Éditeur de source OData (page Connexion)
  La page **Connexion** de la boîte de dialogue **Éditeur de source OData** vous permet de sélectionner le gestionnaire de connexions OData pour la source OData. Cette page vous permet également de spécifier une collection ou un chemin d'accès de ressources et toutes les options de requête permettant de spécifier quelles données doivent être récupérées à partir de la source OData. Pour en savoir plus sur la source OData, consultez [Source OData](data-flow/odata-source.md).  
  
## <a name="static-options"></a>Options statiques  
 **Gestionnaire de connexions OData**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une nouvelle connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Éditeur du gestionnaire de connexions OData** .  
  
 **Utiliser le chemin d’accès de la collection ou de la ressource**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Option|Description|  
|------------|-----------------|  
|Collection|Extrayez les données de la source OData à l'aide d'un nom de collection.|  
|Chemin d'accès de ressource|Extrayez les données de la source OData à l'aide d'un chemin d'accès de ressource.|  
  
 **Options de requête**  
 Permet d'indiquer les options de la requête.  Par exemple : $top=5  
  
 **Feed url**  
 Affiche l'URL du flux en lecture seule en fonction des options sélectionnées dans la boîte de dialogue.  
  
 **Préversion**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Aperçu** . L' **Aperçu** peut afficher jusqu’à 20 lignes.  
  
## <a name="dynamic-options"></a>Options dynamiques  
  
### <a name="use-collection-or-resource-path--collection"></a>Utilisez une collection ou un chemin d'accès de ressource = Collection.  
 **Collecte**  
 Sélectionnez une collection dans la liste déroulante.  
  
### <a name="use-collection-or-resource-path--resource-path"></a>Utilisez une collection ou un chemin d'accès de ressource = Resource Path.  
 **Chemin de la ressource**  
 Type de chemin d'accès de ressource. Par exemple : Employees  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de source OData &#40;page colonnes&#41;](../../2014/integration-services/odata-source-editor-columns-page.md)   
 [Éditeur de source OData &#40;page sortie d’erreur&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md)   
 [Gestionnaire de connexions OData](connection-manager/odata-connection-manager.md)  
  
  
