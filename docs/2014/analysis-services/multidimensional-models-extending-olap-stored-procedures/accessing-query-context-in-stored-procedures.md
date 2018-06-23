---
title: Accès au contexte de requête dans des procédures stockées | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ef60683eb410f0db5ba9e8d38ac227ca22dd9159
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043960"
---
# <a name="accessing-query-context-in-stored-procedures"></a>Accès au contexte de requête dans les procédures stockées
  Le contexte d'exécution d'une procédure stockée est disponible à l'intérieur du code de cette procédure sous la forme de l'objet `Context` du modèle d'objet serveur ADOMD.NET. Il s'agit d'un contexte en lecture seule qui ne peut pas être modifié par la procédure stockée. Les propriétés suivantes sont disponibles pour cet objet.  
  
|Propriété|Type|Description|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|Cube du contexte de requête actuel.|  
|**CurrentDatabaseName**|String|Identificateur de la base de données active.|  
|**CurrentConnection**|Connexion|Référence à l'objet de connexion dans le contexte actuel.|  
|**Passer**|Entier|Numéro de test du contexte actuel.|  
  
 L'objet `Context` existe lorsque le modèle objet MDX (Multidimensional Expressions) est utilisé dans une procédure stockée. Il n'est pas disponible lorsque le modèle objet MDX est utilisé sur un client. L'objet `Context` n'est ni explicitement transmis à la procédure stockée, ni explicitement renvoyé par celle-ci. Il est disponible pendant l'exécution de la procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèle multidimensionnel](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Définition de procédures stockées](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  