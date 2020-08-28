---
description: Catalog, objet (ADO MD)
title: Objet Catalogue (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog
helpviewer_keywords:
- Catalog object [ADO MD]
ms.assetid: 11f6f896-d69c-44a4-94cd-d54c93140e4a
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e62b4eedd835cff2d5bd99e054648339ffd9bc0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987300"
---
# <a name="catalog-object-ado-md"></a>Catalog, objet (ADO MD)
Contient des informations sur les schémas multidimensionnels (c’est-à-dire les cubes et les dimensions sous-jacentes, les hiérarchies, les niveaux et les membres) spécifiques à un fournisseur de données multidimensionnelles (MDP).  
  
## <a name="remarks"></a>Notes  
 Avec les collections et les propriétés d’un objet **catalogue** , vous pouvez effectuer les opérations suivantes :  
  
-   Ouvrez le catalogue en affectant à la propriété [ActiveConnection](./activeconnection-property-ado-md.md) un objet de [connexion](../ado-api/connection-object-ado.md) ADO standard ou une chaîne de connexion valide.  
  
-   Identifiez le **catalogue** à l’aide de la propriété [Name](./name-property-ado-md.md) .  
  
-   Itérer au sein des cubes dans un catalogue à l’aide de la collection [CubeDefs](./cubedefs-collection-ado-md.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements](./catalog-object-properties-methods-and-events-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de catalogue (VB)](./catalog-example-vb.md)   
 [Connection, objet (ADO)](../ado-api/connection-object-ado.md)   
 [CubeDefs, collection (ADO MD)](./cubedefs-collection-ado-md.md)