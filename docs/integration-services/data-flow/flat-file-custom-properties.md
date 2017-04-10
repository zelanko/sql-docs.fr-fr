---
title: "Propri&#233;t&#233;s personnalis&#233;es des fichiers plats | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Propri&#233;t&#233;s personnalis&#233;es des fichiers plats
  **Propriétés personnalisées des sources**  
  
 La source de fichier plat comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source de fichier plat. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|FileNameColumnName|Chaîne|Nom d'une colonne de sortie qui contient le nom de fichier. Si le nom n'est pas spécifié, aucune colonne de sortie contenant le nom de fichier ne sera générée.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de source de fichier plat**, mais elle peut être définie à l’aide de **l’éditeur avancé**.|  
|RetainNulls|Booléen|Valeur qui spécifie si les valeurs NULL du fichier source doivent être conservées comme valeurs NULL lorsque les données sont traitées par le moteur du pipeline de transformation des données. La valeur par défaut de cette propriété est **False**.|  
  
 La sortie de la source de fichier plat n'est pas dotée de propriétés personnalisées.  
  
 Le tableau suivant décrit les propriétés personnalisées des colonnes de sortie de la source de fichier plat. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|FastParse|Booléen|Valeur qui indique si la colonne utilise les routines d'analyse fournies par DTS (routines plus rapides mais qui ne tiennent pas compte des paramètres régionaux) ou les routines d'analyse standard qui tiennent compte des paramètres régionaux. Pour plus d'informations, consultez [Fast Parse](../Topic/Fast%20Parse.md) et [Standard Parse](../Topic/Standard%20Parse.md). La valeur par défaut de cette propriété est **False**.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de source de fichier plat**, mais elle peut être définie à l’aide de **l’éditeur avancé**.|  
  
 Pour plus d'informations, consultez [Flat File Source](../../integration-services/data-flow/flat-file-source.md).  
  
 **Propriétés personnalisées des destinations**  
  
 La destination de fichier plat comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination de fichier plat. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|En-tête|Chaîne|Bloc de texte inséré dans le fichier avant l'écriture des données.<br /><br /> Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.|  
|Remplacer|Booléen|Valeur qui spécifie s'il faut remplacer un fichier de destination existant qui porte le même nom ou lui ajouter des données. La valeur par défaut de cette propriété est **True**.|  
  
 L'entrée et les colonnes d'entrée de la destination de fichier plat ne disposent pas de propriétés personnalisées.  
  
 Pour plus d'informations, consultez [Flat File Destination](../../integration-services/data-flow/flat-file-destination.md).  
  
## Voir aussi  
 [Propriétés communes](../Topic/Common%20Properties.md)  
  
  