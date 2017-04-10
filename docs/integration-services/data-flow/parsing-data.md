---
title: "Analyse de donn&#233;es | Microsoft Docs"
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
  - "analyse [Integration Services]"
  - "analyse de données [Integration Services]"
ms.assetid: 8893ea9d-634c-4309-b52c-6337222dcb39
caps.latest.revision: 39
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# Analyse de donn&#233;es
  Les flux de données des packages extraient et chargent des données à partir de banques de données hétérogènes qui peuvent utiliser différents types de données standard et personnalisés. Dans un flux de données, les sources [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sont chargées d’extraire les données, d’analyser les données de type string et de les convertir en données de type [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les transformations effectuées par la suite peuvent analyser les données afin de les convertir en un type distinct ou créer des copies de colonnes avec d'autres types de données. Les expressions utilisées dans les composants peuvent également convertir les arguments et opérandes en d'autres types de données. Enfin, lorsque les données sont chargées dans une banque de données, la destination peut analyser les données afin de les convertir en un type de données utilisé par la destination. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Types d'analyses  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] propose deux types d’analyses en vue de convertir les données : l’analyse rapide et l’analyse standard.  
  
-   L'analyse rapide est un ensemble de routines simple et rapide d'analyse des données. Elle ne prend pas en charge la conversion des données présentant des spécificités régionales et accepte uniquement les formats de date et d'heure les plus courants. Pour plus d’informations, consultez [Analyse rapide](../Topic/Fast%20Parse.md).  
  
-   L'analyse standard est un ensemble complet de routines d'analyse qui prend en charge la conversion de tous les types de données fournis par les API de conversion de type de données Automation disponibles dans Oleaut32.dll et Ole2dsip.dll. Pour plus d’informations, consultez [Analyse standard](../Topic/Standard%20Parse.md).  
  
  