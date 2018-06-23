---
title: Éditeur de Destination de traitement de dimension (Page Gestionnaire de connexions) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 360810664d34244b95a6a36b20bc5c0a7098bfd3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038376"
---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a>Éditeur de destination de traitement de dimension (page Gestionnaire de connexions)
  La page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination de traitement de dimension** vous permet de spécifier une connexion à un projet [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Pour en savoir plus sur la destination de traitement de dimension, consultez [Dimension Processing Destination](data-flow/dimension-processing-destination.md).  
  
## <a name="options"></a>Options  
 **Connection manager**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou cliquez sur **Nouveau** pour créer un gestionnaire de connexions.  
  
 **Nouveau**  
 Créez une connexion à l’aide de la boîte de dialogue **Ajout d’un gestionnaire de connexions Analysis Services** .  
  
 **Liste des dimensions disponibles**  
 Sélectionnez la dimension à traiter.  
  
 **Méthode de traitement**  
 Sélectionnez la méthode de traitement à appliquer à la dimension sélectionnée dans la liste. La valeur par défaut de cette option est **Complète**.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Ajouter (incrémentiel)**|Permet d'effectuer un traitement incrémentiel de la dimension.|  
|**Complète**|Permet d'effectuer un traitement complet de la dimension.|  
|**Update**|Permet d'effectuer un traitement de mise à jour de la dimension.|  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de Destination de traitement de dimension &#40;Page mappages&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)   
 [Éditeur de Destination de traitement de dimension &#40;Page avancé&#41;](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)  
  
  