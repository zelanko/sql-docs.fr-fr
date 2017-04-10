---
title: "Transformation d&#39;audit | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.audittrans.f1"
helpviewer_keywords: 
  - "données d'environnement dans les packages [Integration Services]"
  - "transformation d'audit"
ms.assetid: 8c143682-9c81-4150-83d6-1d9678151d37
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# Transformation d&#39;audit
  La transformation d'audit permet au flux de données d'un package de contenir des données relatives à l'environnement d'exécution du package. Par exemple, le nom du package, de l'ordinateur et de l'opérateur peuvent être ajoutés au flux de données. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] comprend des variables système qui fournissent ces informations.  
  
## Variables système  
 Le tableau suivant décrit les variables système utilisables par la transformation d'audit.  
  
|Variable système|Index|Description|  
|---------------------|-----------|-----------------|  
|**ExecutionInstanceGUID**|0|GUID identifiant l'instance d'exécution du package.|  
|**PackageID**|1|Identificateur unique du package.|  
|**PackageName**|2|Nom du package.|  
|**VersionID**|3|Version du package.|  
|**ExecutionStartTime**|4|Heure à laquelle l'exécution du package a commencé.|  
|**MachineName**|5|Nom de l'ordinateur.|  
|**UserName**|6|Nom de connexion de la personne qui a démarré le package.|  
|**TaskName**|7|Nom de la tâche de flux de données à laquelle la transformation d'audit est associée.|  
|**TaskId**|8|Identificateur unique de la tâche de flux de données.|  
  
## Configuration de la transformation d'audit  
 Pour configurer la transformation d'audit, vous devez indiquer le nom d'une nouvelle colonne de sortie à ajouter à la sortie de la transformation, puis mapper la variable système avec la colonne de sortie. Vous pouvez mapper une même variable système avec plusieurs colonnes.  
  
 Cette transformation a une entrée et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation d'audit** , consultez [Audit Transformation Editor](../../../integration-services/data-flow/transformations/audit-transformation-editor.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../Topic/Common%20Properties.md)  
  
-   [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  