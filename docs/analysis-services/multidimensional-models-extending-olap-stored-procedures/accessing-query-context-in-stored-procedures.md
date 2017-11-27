---
title: "Accès au contexte de requête dans des procédures stockées | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d2a53ac7fb66ded14a7e79dee881755fc7ecd45e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="accessing-query-context-in-stored-procedures"></a>Accès au contexte de requête dans les procédures stockées
  Le contexte d’exécution d’une procédure stockée est disponible dans le code de la procédure stockée en tant que le **contexte** objet du modèle d’objet serveur ADOMD.NET. Il s'agit d'un contexte en lecture seule qui ne peut pas être modifié par la procédure stockée. Les propriétés suivantes sont disponibles pour cet objet.  
  
|Propriété|Type| Description|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|Cube du contexte de requête actuel.|  
|**CurrentDatabaseName**|Chaîne|Identificateur de la base de données active.|  
|**CurrentConnection**|Connexion|Référence à l'objet de connexion dans le contexte actuel.|  
|**Passer**|Entier|Numéro de test du contexte actuel.|  
  
 Le **contexte** objet existe lorsque le modèle objet MDX (Multidimensional Expressions) est utilisé dans une procédure stockée. Il n'est pas disponible lorsque le modèle objet MDX est utilisé sur un client. Le **contexte** objet n’est pas explicitement passée à ou retournée par la procédure stockée. Il est disponible pendant l'exécution de la procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèle multidimensionnel](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Définition de procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
