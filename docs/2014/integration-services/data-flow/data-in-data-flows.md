---
title: Données dans des flux de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- comparing data
- data types [Integration Services], data flow
- parsing [Integration Services]
- string comparisons
- data flow [Integration Services], data options
ms.assetid: 8a9d6186-eb52-48e3-997e-021f24d458a3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 225b6010e5d5a6c45a84d7e22272c4e5242906fd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62827901"
---
# <a name="data-in-data-flows"></a>Données dans des flux de données
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] propose un ensemble de types de données qui sont utilisés dans les flux de données.  
  
## <a name="data-type-conversion"></a>Conversion de type de données  
 La source que vous ajoutez à un flux de données convertit les données sources en types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Les transformations effectuées par la suite peuvent convertir les données en types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] différents et selon le type de banque de données dans lequel les données sont chargées, les destinations peuvent convertir le type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] final dans le type requis par la banque de données de destination. Pour plus d’informations, consultez [Types de données Integration Services](integration-services-data-types.md).  
  
 Pour convertir les données en un type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , un composant de flux de données analyse les données. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] propose deux types d’analyses des données : l’analyse rapide et l’analyse standard. La plupart des composants de flux de données ne peuvent utiliser que l'analyse standard. Cependant la source de fichier plat et la transformation de conversion de données peuvent utiliser l'analyse rapide ou l'analyse standard. Pour plus d’informations, consultez [Analyse des données](parsing-data.md).  
  
## <a name="data-type-comparison"></a>Comparaison des types de données  
 De nombreuses transformations comparent les valeurs de données. Par exemple, la transformation d'agrégation compare les valeurs dans le but d'agréger les valeurs dans un ensemble de lignes de données ; la transformation de tri compare les valeurs afin de les trier et la transformation de recherche compare les valeurs à celles d'une table de référence distincte. Pour spécifier la manière dont les chaînes doivent être comparées, la transformation inclut un ensemble d'options de comparaison qui déterminent par exemple si la casse doit être ignorée, si les espaces doivent être ignorés dans les chaînes et comment gérer les caractères Kana dans les textes japonais. Pour plus d'informations, voir [Comparing String Data](comparing-string-data.md).  
  
 L'évaluateur d'expression compare également les valeurs de données lorsqu'il évalue les expressions utilisées par les variables, les contraintes de précédence et les transformations.  
  
## <a name="data-flow-troubleshooting"></a>Dépannage du flux de données  
 Une fois que vous avez déployé un package sur le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous pouvez analyser le flux de données dans le package au moment de l’exécution pour vérifier les performances ou pour détecter d’autres problèmes. Des rapports standard sont disponibles et vous permettent de consulter l'état et l'historique du package. Vous pouvez interroger les vues de base de données qui fournissent des informations détaillées sur l'exécution du package. De plus, vous pouvez ajouter et supprimer dynamiquement des drainages de données au moment de l'exécution pour cibler des éléments spécifiques de votre package. Pour plus d’informations, consultez [Analyse des flux de données](data-flow.md).  
  
  
