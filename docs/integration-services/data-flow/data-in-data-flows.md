---
title: "Donn&#233;es dans des flux de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conversion des types de données [Integration Services]"
  - "comparaison de données"
  - "types de données [Integration Services], flux de données"
  - "analyse [Integration Services]"
  - "comparaisons de chaînes"
  - "flux de données [Integration Services], options de données"
ms.assetid: 8a9d6186-eb52-48e3-997e-021f24d458a3
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# Donn&#233;es dans des flux de donn&#233;es
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] propose un ensemble de types de données qui sont utilisés dans les flux de données.  
  
## Conversion de type de données  
 La source que vous ajoutez à un flux de données convertit les données sources en types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les transformations effectuées par la suite peuvent convertir les données en types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] différents et selon le type de banque de données dans lequel les données sont chargées, les destinations peuvent convertir le type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] final dans le type requis par la banque de données de destination. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Pour convertir les données en un type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], un composant de flux de données analyse les données. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] propose deux types d’analyses des données : l’analyse rapide et l’analyse standard. La plupart des composants de flux de données ne peuvent utiliser que l'analyse standard. Cependant la source de fichier plat et la transformation de conversion de données peuvent utiliser l'analyse rapide ou l'analyse standard. Pour plus d’informations, consultez [Analyse des données](../../integration-services/data-flow/parsing-data.md).  
  
## Comparaison des types de données  
 De nombreuses transformations comparent les valeurs de données. Par exemple, la transformation d'agrégation compare les valeurs dans le but d'agréger les valeurs dans un ensemble de lignes de données ; la transformation de tri compare les valeurs afin de les trier et la transformation de recherche compare les valeurs à celles d'une table de référence distincte. Pour spécifier la manière dont les chaînes doivent être comparées, la transformation inclut un ensemble d'options de comparaison qui déterminent par exemple si la casse doit être ignorée, si les espaces doivent être ignorés dans les chaînes et comment gérer les caractères Kana dans les textes japonais. Pour plus d'informations, voir [Comparing String Data](../../integration-services/data-flow/comparing-string-data.md).  
  
 L'évaluateur d'expression compare également les valeurs de données lorsqu'il évalue les expressions utilisées par les variables, les contraintes de précédence et les transformations.  
  
## Dépannage du flux de données  
 Une fois que vous avez déployé un package sur le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez analyser le flux de données dans le package au moment de l’exécution pour vérifier les performances ou pour détecter d’autres problèmes. Des rapports standard sont disponibles et vous permettent de consulter l'état et l'historique du package. Vous pouvez interroger les vues de base de données qui fournissent des informations détaillées sur l'exécution du package. De plus, vous pouvez ajouter et supprimer dynamiquement des drainages de données au moment de l'exécution pour cibler des éléments spécifiques de votre package. Pour plus d’informations, consultez [Analyse des flux de données](../../integration-services/performance/analysis-of-data-flow.md).  
  
  