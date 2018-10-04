---
title: Format de Package SSIS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: cfe0e5dc-5be3-4222-b721-fe83665edd94
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 43c0662c9084c654b4138a8443f1e2e98eaec376
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200019"
---
# <a name="ssis-package-format"></a>Format de package SSIS
  Dans la version actuelle de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], des modifications significatives ont été apportées au format de package (fichier .dtsx) pour faciliter la lecture du format et la comparaison des packages. Vous pouvez également fusionner de manière plus fiable les packages qui ne contiennent pas de modifications en conflit ou de modifications stockées selon le format binaire.  
  
 Pour voir le format de fichier de package DTSX actuel, consultez [\[:\]Data Transformation Services Package XML File Format Specification](http://go.microsoft.com/fwlink/?LinkId=233251).  
  
 La liste suivante présente les modifications apportées au format de fichier. Pour afficher des exemples de code liés à ces modifications, consultez [Modifications de format de package dans SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=233255)  
  
-   Les conventions de mise en forme ont été appliquées pour faciliter la lecture et la compréhension du fichier .dtsx.  
  
-   Le format est plus concis. Les éléments distincts de chaque propriété ont été conservés en tant qu'attributs, à l'exception de PackageFormatVersion. Les attributs sont répertoriés par ordre alphabétique, et les propriétés qui ont des valeurs par défaut ne sont plus conservées. Enfin, les éléments pouvant apparaître plusieurs fois, sont maintenant contenus dans un élément parent.  
  
-   La plupart des objets d'un package qui peuvent être référencés par d'autres objets possèdent maintenant un attribut `refId` défini dans la définition XML du package. Au lieu des ID de lignage, c'est l'attribut `refID` qui est maintenant conservé. Les ID de lignage sont toujours utilisés au moment de l'exécution et régénérés lors du chargement du package.  
  
     Le `refId` valeur est une chaîne unique qui est lisible et compréhensible, par rapport aux GUID ou aux valeurs entières. La chaîne est similaire aux valeurs de chemin d'accès utilisées pour les configurations de packages dans les versions précédentes de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
     Si vous fusionnez des modifications entre deux versions d’un package, le `refId` peut être utilisé dans les opérations de recherche/remplacement pour vous assurer que toutes les références à cet objet ont été correctement mis à jour.  
  
-   Les informations de mise en page sont contenues dans une section CDATA.  
  
-   Les annotations sont conservées en texte clair. Cela simplifie l'extraction des informations pour la génération automatisée de la documentation.  
  
  
