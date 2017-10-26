---
title: "Propriétés de la Source OData | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ee79d0f1b31963b7d13aa07bf4603246139c3a7c
ms.openlocfilehash: 64e297a37c3b6449551968b5788f8c2c0ddd4ab6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/23/2017

---
# <a name="odata-source-properties"></a>Propriétés de la source OData
Lorsque vous cliquez sur **OData Source** le flux de données, cliquez sur **propriétés**, vous consultez les propriétés pour le **OData Source** composant dans le **propriétés** fenêtre.  

## <a name="properties"></a>Propriétés 
|Propriété|Description|  
|-|-|  
|CollectionName|Nom de la collection pour récupérer à partir du service OData. La propriété **CollectionName** est utilisée quand **UseResourcePath** a la valeur false.<br /><br /> Cette propriété est expressionable, ce qui vous permet de définir la valeur lors de l’exécution. Toutefois, si les métadonnées de la collection ne correspondent pas les métadonnées qui existaient au moment du design, une erreur de validation se produit, ce à l’origine de l’exécution du flux de données échouera.|  
|DefaultStringLength|Cette valeur spécifie la longueur par défaut des colonnes de chaîne qui n'ont pas de longueur maximale.<br /><br /> **Valeur par défaut :** 4000|  
|Requête|Paramètres de requête OData. Cette propriété est expressionable et peut être définie lors de l’exécution.|  
|ResourcePath|Utilisez cette propriété lorsque vous devez spécifier un chemin d'accès de ressources complet, plutôt que sélectionner uniquement un nom de collection. Cette propriété est utilisée lorsque **UseResourcePath** a la valeur True.|  
|UseResourcePath|Lorsque la valeur est définie à True, la valeur **ResourcePath** est ajoutée à l'URL de base pour déterminer l'emplacement du flux OData. Lorsque la valeur est False, la valeur **CollectionName** est utilisée.<br /><br /> **Valeur par défaut :** False|  
  
## <a name="see-also"></a>Voir aussi
[Source OData](odata-source.md)

