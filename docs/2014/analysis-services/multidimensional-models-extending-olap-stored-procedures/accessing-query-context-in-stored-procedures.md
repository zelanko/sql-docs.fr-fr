---
title: Accès au contexte de requête dans des procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f6c5a22a6bc3768e324ca45805ff510b1a86668c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142219"
---
# <a name="accessing-query-context-in-stored-procedures"></a>Accès au contexte de requête dans les procédures stockées
  Le contexte d'exécution d'une procédure stockée est disponible à l'intérieur du code de cette procédure sous la forme de l'objet `Context` du modèle d'objet serveur ADOMD.NET. Il s'agit d'un contexte en lecture seule qui ne peut pas être modifié par la procédure stockée. Les propriétés suivantes sont disponibles pour cet objet.  
  
|Propriété|Type|Description|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|Cube du contexte de requête actuel.|  
|**CurrentDatabaseName**|String|Identificateur de la base de données active.|  
|**CurrentConnection**|Connexion|Référence à l'objet de connexion dans le contexte actuel.|  
|**Pass**|Entier|Numéro de test du contexte actuel.|  
  
 L'objet `Context` existe lorsque le modèle objet MDX (Multidimensional Expressions) est utilisé dans une procédure stockée. Il n'est pas disponible lorsque le modèle objet MDX est utilisé sur un client. L'objet `Context` n'est ni explicitement transmis à la procédure stockée, ni explicitement renvoyé par celle-ci. Il est disponible pendant l'exécution de la procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèle multidimensionnel](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Définition de procédures stockées](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
