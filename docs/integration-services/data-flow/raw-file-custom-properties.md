---
title: "Propri&#233;t&#233;s personnalis&#233;es des fichiers bruts | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e81f7e1-fac0-4b57-b145-8f1b9e4720bf
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# Propri&#233;t&#233;s personnalis&#233;es des fichiers bruts
  **Propriétés personnalisées des sources**  
  
 La source de fichier brut comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source de fichier brut. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (énumération)|Mode utilisé pour accéder aux données brutes. Les valeurs possibles sont **Nom de fichier** (0) et **Nom de fichier à partir d’une variable** (1). La valeur par défaut est **Nom de fichier** (0).|  
|FileName|Chaîne|Chemin d'accès et nom de fichier du fichier source.|  
  
 La sortie et les colonnes de sortie de la source de fichier brut ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Source de fichier brut](../../integration-services/data-flow/raw-file-source.md).  
  
 **Propriétés personnalisées des destinations**  
  
 La destination de fichier brut comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination de fichier brut. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (énumération)|Valeur qui indique si la propriété FileName contient un nom de fichier ou le nom d’une variable qui contient un nom de fichier. Les options proposées sont **Nom de fichier** (0) et **Nom de fichier à partir d’une variable** (1).|  
|FileName|Chaîne|Nom du fichier dans lequel la destination de fichier brut écrit.|  
|WriteOption|Integer (énumération)|Valeur qui spécifie si la destination de fichier brut supprime un fichier existant qui porte le même nom. Les options proposées sont **Toujours créer** (0), **Créer une fois** (1), **Tronquer et ajouter** (3) et **Ajouter** (2). La valeur par défaut de cette propriété est **Toujours créer** (0).|  
  
> [!NOTE]  
>  Une opération d'ajout exige que les métadonnées des données ajoutées correspondent à celles des données déjà présentes dans le fichier.  
  
 L'entrée et les colonnes d'entrée de la destination de fichier brut ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination de fichier brut](../../integration-services/data-flow/raw-file-destination.md).  
  
## Voir aussi  
 [Propriétés communes](../Topic/Common%20Properties.md)  
  
  