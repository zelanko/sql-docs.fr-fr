---
title: "Éditeur de Source OData (Page connexion) | Documents Microsoft"
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.odatasource.connection.f1
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6bb7a97ddbcae4868ee7b737358d4b30608e4df2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="odata-source-editor-connection-page"></a>Éditeur de source OData (page Connexion)
  La page **Connexion** de la boîte de dialogue **Éditeur de source OData** vous permet de sélectionner le gestionnaire de connexions OData pour la source OData. Cette page vous permet également de spécifier une collection ou un chemin d'accès de ressources et toutes les options de requête permettant de spécifier quelles données doivent être récupérées à partir de la source OData. Pour en savoir plus sur la source OData, consultez [Source OData](../../integration-services/data-flow/odata-source.md).  
  
## <a name="static-options"></a>Options statiques  
 **Gestionnaire de connexions OData**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 Après la sélection ou la création d’un gestionnaire de connexions, la boîte de dialogue affiche la version du protocole OData qui utilise le gestionnaire de connexions.  
  
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
 Type de chemin d'accès de ressource. Par exemple : Employees  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Source OData &#40; Page colonnes &#41;](../../integration-services/data-flow/odata-source-editor-columns-page.md)   
 [Éditeur de Source OData &#40; Page sortie d’erreur &#41;](../../integration-services/data-flow/odata-source-editor-error-output-page.md)   
 [Gestionnaire de connexions OData](../../integration-services/connection-manager/odata-connection-manager.md)  
  
  
