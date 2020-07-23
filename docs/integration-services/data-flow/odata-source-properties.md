---
title: Propriétés de la source OData | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fe4a3c3d1375095a4766186e1b854ea038b54ac9
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920776"
---
# <a name="odata-source-properties"></a>Propriétés de la source OData

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


Quand vous cliquez avec le bouton droit sur **Source OData** dans le flux de données, puis cliquez sur **Propriétés**, vous voyez les propriétés du composant **Source OData** dans la fenêtre **Propriétés**.  

## <a name="properties"></a>Propriétés 

|Propriété|Description|  
|-|-|  
|CollectionName|Nom de la collection à extraire du service OData. La propriété **CollectionName** est utilisée quand **UseResourcePath** a la valeur false.<br /><br /> Cette propriété utilise des expressions, ce qui vous permet de définir la valeur au moment de l’exécution. Cependant, si les métadonnées de la collection ne correspondent pas aux métadonnées utilisées au moment de la conception, une erreur de validation est générée et l’exécution du flux de données échoue.|  
|DefaultStringLength|Cette valeur spécifie la longueur par défaut des colonnes de chaîne qui n'ont pas de longueur maximale.<br /><br /> **Valeur par défaut :** 4000|  
|Requête|Paramètres de requête OData. Cette propriété utilise des expressions et peut être définie au moment de l’exécution.|  
|ResourcePath|Utilisez cette propriété lorsque vous devez spécifier un chemin d'accès de ressources complet, plutôt que sélectionner uniquement un nom de collection. Cette propriété est utilisée lorsque **UseResourcePath** a la valeur True.|  
|UseResourcePath|Lorsque la valeur est définie à True, la valeur **ResourcePath** est ajoutée à l'URL de base pour déterminer l'emplacement du flux OData. Lorsque la valeur est False, la valeur **CollectionName** est utilisée.<br /><br /> **Valeur par défaut :** False|  
  
## <a name="see-also"></a>Voir aussi
[Source OData](odata-source.md)
