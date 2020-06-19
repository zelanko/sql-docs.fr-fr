---
title: Éditeur de transformation d’audit | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittransformation.f1
helpviewer_keywords:
- Audit Transformation Editor
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 6a58d216b33f5fb8fd582050374d06463fd2c99e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84925522"
---
# <a name="audit-transformation-editor"></a>Éditeur de transformation d'audit
  La transformation d'audit permet au flux de données d'un package de contenir des données relatives à l'environnement d'exécution du package. Par exemple, le nom du package, de l'ordinateur et de l'opérateur peuvent être ajoutés au flux de données. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] comprend des variables système qui fournissent ces informations.  
  
 Pour en savoir plus sur la transformation d'audit, consultez [Audit Transformation](data-flow/transformations/audit-transformation.md).  
  
## <a name="options"></a>Options  
 **Nom de la colonne de sortie**  
 Indique le nom de la nouvelle colonne de sortie qui va contenir les informations d'audit.  
  
 **Type d’audit**  
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
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
