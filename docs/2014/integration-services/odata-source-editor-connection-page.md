---
title: Éditeur de Source OData (Page connexion) | Microsoft Docs
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
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66057317"
---
# <a name="odata-source-editor-connection-page"></a>Éditeur de source OData (page Connexion)
  La page **Connexion** de la boîte de dialogue **Éditeur de source OData** vous permet de sélectionner le gestionnaire de connexions OData pour la source OData. Cette page vous permet également de spécifier une collection ou un chemin d'accès de ressources et toutes les options de requête permettant de spécifier quelles données doivent être récupérées à partir de la source OData. Pour en savoir plus sur la source OData, consultez [Source OData](data-flow/odata-source.md).  
  
## <a name="static-options"></a>Options statiques  
 **Gestionnaire de connexions OData**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une nouvelle connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Éditeur du gestionnaire de connexions OData** .  
  
 **Utilisez une collection ou un chemin d'accès de ressource.**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Option|Description|  
|------------|-----------------|  
|Collection|Extrayez les données de la source OData à l'aide d'un nom de collection.|  
|Chemin d'accès de ressource|Extrayez les données de la source OData à l'aide d'un chemin d'accès de ressource.|  
  
 **Options de requête**  
 Permet d'indiquer les options de la requête.  Par exemple : $top=5  
  
 **URL du flux**  
 Affiche l'URL du flux en lecture seule en fonction des options sélectionnées dans la boîte de dialogue.  
  
 **Aperçu**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Aperçu** . L’**Aperçu** peut afficher jusqu’à 20 lignes.  
  
## <a name="dynamic-options"></a>Options dynamiques  
  
### <a name="use-collection-or-resource-path--collection"></a>Utilisez une collection ou un chemin d'accès de ressource = Collection.  
 **Collection**  
 Sélectionnez une collection dans la liste déroulante.  
  
### <a name="use-collection-or-resource-path--resource-path"></a>Utilisez une collection ou un chemin d'accès de ressource = Resource Path.  
 **Resource path**  
 Type de chemin d'accès de ressource. Exemple : Employees  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de source OData &#40;page Colonnes&#41;](../../2014/integration-services/odata-source-editor-columns-page.md)   
 [Éditeur de source OData &#40;page Sortie d’erreur&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md)   
 [OData Connection Manager](connection-manager/odata-connection-manager.md)  
  
  
