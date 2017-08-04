---
title: "Éditeur de Transformation d’audit | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.audittransformation.f1
helpviewer_keywords:
- Audit Transformation Editor
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c4c3cc4b661c58476a98e3528e5853cf80b9861d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="audit-transformation-editor"></a>Éditeur de transformation d'audit
  La transformation d'audit permet au flux de données d'un package de contenir des données relatives à l'environnement d'exécution du package. Par exemple, le nom du package, de l'ordinateur et de l'opérateur peuvent être ajoutés au flux de données. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] comprend des variables système qui fournissent ces informations.  
  
 Pour en savoir plus sur la transformation d'audit, consultez [Audit Transformation](../../../integration-services/data-flow/transformations/audit-transformation.md).  
  
## <a name="options"></a>Options  
 **Nom de colonne de sortie**  
 Indique le nom de la nouvelle colonne de sortie qui va contenir les informations d'audit.  
  
 **Type d'audit**  
 Sélectionne une variable système disponible pour fournir les informations d'audit.  
  
|Value|Description|  
|-----------|-----------------|  
|**GUID d'instance d'exécution**|Insérez le GUID qui identifie de manière unique l'instance d'exécution du package.|  
|**ID du package**|Insérez le GUID qui identifie de manière unique le package.|  
|**Nom du package**|Insérez le nom du package.|  
|**ID de version**|Insérez le GUID qui identifie de manière unique la version du package.|  
|**Heure de début de l'exécution**|Insérez l'heure à laquelle l'exécution du package a commencé.|  
|**Nom de l'ordinateur**|Insérez le nom de l'ordinateur sur lequel le package a été lancé.|  
|**Nom d'utilisateur**|Insérez le nom de connexion de l'utilisateur qui a lancé le package.|  
|**Nom de la tâche**|Insérez le nom de la tâche de flux de données à laquelle la transformation d'audit est associée.|  
|**ID de la tâche**|Insérez le GUID qui identifie de manière unique le flux de données à laquelle la transformation d'audit est associée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../../integration-services/integration-services-error-and-message-reference.md)  
  
  
