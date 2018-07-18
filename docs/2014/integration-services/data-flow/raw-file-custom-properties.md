---
title: Propriétés personnalisées des fichiers bruts | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7e81f7e1-fac0-4b57-b145-8f1b9e4720bf
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a991f1e7362be2e9516857ec2f6d98b4e487b536
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277445"
---
# <a name="raw-file-custom-properties"></a>Propriétés personnalisées des fichiers bruts
  **Propriétés personnalisées des sources**  
  
 La source de fichier brut comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source de fichier brut. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (énumération)|Mode utilisé pour accéder aux données brutes. Les valeurs possibles sont `File name` (0) et `File name from variable` (1). La valeur par défaut est `File name` (0).|  
|FileName|String|Chemin d'accès et nom de fichier du fichier source.|  
  
 La sortie et les colonnes de sortie de la source de fichier brut ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Source de fichier brut](raw-file-source.md).  
  
 **Propriétés personnalisées des destinations**  
  
 La destination de fichier brut comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination de fichier brut. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (énumération)|Valeur qui indique si la propriété FileName contient un nom de fichier ou le nom d’une variable qui contient un nom de fichier. Les options disponibles sont `File name` (0) et `File name from variable` (1).|  
|FileName|String|Nom du fichier dans lequel la destination de fichier brut écrit.|  
|WriteOption|Integer (énumération)|Valeur qui spécifie si la destination de fichier brut supprime un fichier existant qui porte le même nom. Les options sont `Create Always` (0), `Create Once` (1), `Truncate and Append` (3), et `Append` (2). La valeur par défaut de cette propriété est `Create Always` (0).|  
  
> [!NOTE]  
>  Une opération d'ajout exige que les métadonnées des données ajoutées correspondent à celles des données déjà présentes dans le fichier.  
  
 L'entrée et les colonnes d'entrée de la destination de fichier brut ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination de fichier brut](raw-file-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](../common-properties.md)  
  
  
