---
title: Format de package SSIS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cfe0e5dc-5be3-4222-b721-fe83665edd94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 813339fea4db41433ca73e47245cb9c87f393421
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85420936"
---
# <a name="ssis-package-format"></a>Format de package SSIS
  Dans la version actuelle de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], des modifications significatives ont été apportées au format de package (fichier .dtsx) pour faciliter la lecture du format et la comparaison des packages. Vous pouvez également fusionner de manière plus fiable les packages qui ne contiennent pas de modifications en conflit ou de modifications stockées au format binaire.  
  
 Pour afficher le format de fichier de package DTSX actuel, consultez [ \[ MS-dtsx \] : spécification de format de fichier XML du package DTS (Data Transformation Services](https://go.microsoft.com/fwlink/?LinkId=233251)).  
  
 La liste suivante présente les modifications apportées au format de fichier. Pour afficher des exemples de code liés à ces modifications, consultez [Modifications de format de package dans SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=233255)  
  
-   Les conventions de mise en forme ont été appliquées pour faciliter la lecture et la compréhension du fichier .dtsx.  
  
-   Le format est plus concis. Les éléments distincts de chaque propriété ont été conservés en tant qu'attributs, à l'exception de PackageFormatVersion. Les attributs sont répertoriés par ordre alphabétique, et les propriétés qui ont des valeurs par défaut ne sont plus conservées. Enfin, les éléments pouvant apparaître plusieurs fois, sont maintenant contenus dans un élément parent.  
  
-   La plupart des objets d'un package qui peuvent être référencés par d'autres objets possèdent maintenant un attribut `refId` défini dans la définition XML du package. Au lieu des ID de lignage, c'est l'attribut `refID` qui est maintenant conservé. Les ID de lignage sont toujours utilisés au moment de l'exécution et régénérés lors du chargement du package.  
  
     La valeur `refId` est une chaîne unique lisible et compréhensible, par comparaison aux GUID ou aux valeurs entières. La chaîne est similaire aux valeurs de chemin d'accès utilisées pour les configurations de packages dans les versions précédentes de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
     Si vous fusionnez des modifications entre deux versions d'un package, `refId` peut être utilisé dans des opérations de recherche/remplacement pour garantir que toutes les références à cet objet sont correctement mises à jour.  
  
-   Les informations de mise en page sont contenues dans une section CDATA.  
  
-   Les annotations sont conservées en texte clair. Cela simplifie l'extraction des informations pour la génération automatisée de la documentation.  
  
  
