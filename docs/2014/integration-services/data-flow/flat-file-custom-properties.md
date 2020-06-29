---
title: Propriétés personnalisées des fichiers plats | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 685abe5eec37eba41a8e3c1e1ee5ce6df49947a3
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432146"
---
# <a name="flat-file-custom-properties"></a>Propriétés personnalisées des fichiers plats
  **Propriétés personnalisées des sources**  
  
 La source de fichier plat comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source de fichier plat. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|FileNameColumnName|String|Nom d'une colonne de sortie qui contient le nom de fichier. Si le nom n'est pas spécifié, aucune colonne de sortie contenant le nom de fichier ne sera générée.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de source de fichier plat**, mais elle peut être définie à l’aide de **l’éditeur avancé**.|  
|RetainNulls|Boolean|Valeur qui spécifie si les valeurs NULL du fichier source doivent être conservées comme valeurs NULL lorsque les données sont traitées par le moteur du pipeline de transformation des données. La valeur par défaut de cette propriété est `False`.|  
  
 La sortie de la source de fichier plat n'est pas dotée de propriétés personnalisées.  
  
 Le tableau suivant décrit les propriétés personnalisées des colonnes de sortie de la source de fichier plat. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|FastParse|Boolean|Valeur qui indique si la colonne utilise les routines d'analyse fournies par DTS (routines plus rapides mais qui ne tiennent pas compte des paramètres régionaux) ou les routines d'analyse standard qui tiennent compte des paramètres régionaux. Pour plus d'informations, consultez [Fast Parse](../fast-parse.md) et [Standard Parse](../standard-parse.md). La valeur par défaut de cette propriété est `False`.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de source de fichier plat**, mais elle peut être définie à l’aide de **l’éditeur avancé**.|  
  
 Pour plus d'informations, consultez [Flat File Source](flat-file-source.md).  
  
 **Propriétés personnalisées des destinations**  
  
 La destination de fichier plat comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination de fichier plat. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|En-tête|String|Bloc de texte inséré dans le fichier avant l'écriture des données.<br /><br /> Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.|  
|Remplacer|Boolean|Valeur qui spécifie s'il faut remplacer un fichier de destination existant qui porte le même nom ou lui ajouter des données. La valeur par défaut de cette propriété est `True`.|  
  
 L'entrée et les colonnes d'entrée de la destination de fichier plat ne disposent pas de propriétés personnalisées.  
  
 Pour plus d'informations, consultez [Flat File Destination](flat-file-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](../common-properties.md)  
  
  
