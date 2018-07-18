---
title: Formats de date et heure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- time data types [Integration Services]
- fast parse [Integration Services]
- date data types
- date and time formats for fast parse
ms.assetid: bed6e2c1-791a-4fa1-b29f-cbfdd1fa8d39
caps.latest.revision: 52
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d7c54b3ee399043d752efb9e55ce9c2f8fed488d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289385"
---
# <a name="date-and-time-formats"></a>Formats de date et d'heure
  L'analyse rapide propose un ensemble de routines simples et rapides d'analyse des données. L'analyse rapide prend en charge les formats suivants de types de données de date et d'heure.  
  
## <a name="date-data-types"></a>Types de données de date  
 L'analyse rapide prend en charge les formats de chaîne suivants pour les données de date :  
  
-   Formats de date qui incluent des espaces de début. Par exemple, la valeur «  2004- 02-03 » est valide.  
  
-   Formats ISO 8601 répertoriés dans le tableau suivant :  
  
    |Format|Description|  
    |------------|-----------------|  
    |AAAAMMJJ<br /><br /> AAAA-MM-JJ|Formats de base et étendus pour une année à quatre chiffres, un mois à deux chiffres et un jour à deux chiffres. Dans le format étendu, les parties de la date sont séparées par un tiret (-).|  
    |AAAA-MM|Formats à précision réduite de base et étendus pour une année à quatre chiffres et un mois à deux chiffres. Dans le format étendu, les parties de la date sont séparées par un tiret (-).|  
    |AAAA|Le format à précision réduite est une année à quatre chiffres.|  
  
 L'analyse rapide ne prend pas en charge les formats suivants pour les données de date :  
  
-   Valeurs de mois alphabétiques. Par exemple, le format de date Oct-31-2003 n'est pas valide.  
  
-   Les formats ambigus tels que JJ-MM-AAAA et MM-JJ-AAAA. Par exemple, les dates 03-04-1995 et 04-03-1995 ne sont pas valides.  
  
-   Formats tronqués de base et étendus pour une année civile à quatre chiffres et un jour à trois chiffres dans une année, AAAAJJJ et AAAA-JJJ.  
  
-   Formats de base et étendus pour une année à quatre chiffres, un nombre à deux chiffres pour la semaine de l'année et un nombre à un chiffre pour le jour de la semaine, AAAASssJ et AAAA-Sss-J.  
  
-   Les formats tronqués de base et étendus pour une date comportant l'année et la semaine sont une année à quatre chiffres et un nombre à deux chiffres pour la semaine, AAASss et AAA-Sss.  
  
 L'analyse rapide génère en sortie des données sous la forme DT_DBDATE. Les valeurs de date aux formats tronqués sont complétées. Par exemple, AAA devient AAAA0101.  
  
 Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).  
  
## <a name="time-data-type"></a>Type de données d'heure  
 L'analyse rapide prend en charge les formats de chaîne suivants pour les données d'heure :  
  
-   Formats d'heure qui incluent des espaces de début. Par exemple, la valeur « 10:24» est valide.  
  
-   Format 24 heures. L'analyse rapide ne prend pas en charge la notation AM et PM.  
  
-   Formats d'heure ISO 8601 répertoriés dans le tableau suivant :  
  
    |Format|Description|  
    |------------|-----------------|  
    |HHMISS<br /><br /> HH:MI:SS|Formats de base et étendus pour une heure à deux chiffres, une minute à deux chiffres et une seconde à deux chiffres. Dans le format étendu, les parties de l'heure sont séparées par deux points (:).|  
    |HHMI<br /><br /> HH:MI|Format tronqué de base et étendu pour une heure à deux chiffres et une minute à deux chiffres. Dans le format étendu, les parties de l'heure sont séparées par deux points (:).|  
    |HH|Format tronqué pour une heure à deux chiffres.|  
    |00:00:00<br /><br /> 000000<br /><br /> 0000<br /><br /> 00<br /><br /> 240000<br /><br /> 24:00:00<br /><br /> 2400<br /><br /> 24|Format pour minuit.|  
  
-   Formats d'heure qui spécifient un fuseau horaire, répertoriés dans le tableau suivant :  
  
    |Format|Description|  
    |------------|-----------------|  
    |+HH:MI<br /><br /> +HHMI|Formats de base et étendus qui indiquent le nombre d'heures et de minutes ajoutées au temps universel coordonné (UTC) pour obtenir l'heure locale.|  
    |-HH:MI<br /><br /> -HHMI|Formats de base et étendus qui indiquent le nombre d'heures et de minutes soustraites du temps universel coordonné (UTC) pour obtenir l'heure locale.|  
    |+HH|Format tronqué qui indique le nombre d'heures ajoutées au temps universel coordonné (UTC) pour obtenir l'heure locale.|  
    |-HH|Format tronqué qui indique le nombre d'heures soustraites du temps universel coordonné (UTC) pour obtenir l'heure locale.|  
    |Z|Valeur 0 qui indique que l'heure est représentée au format UTC.|  
  
     Les formats de toutes les données d'heure et de date/heure peuvent inclure un élément de fuseau horaire. Toutefois, le système ignore la valeur de fuseau horaire, sauf lorsque les données sont de type DT_DBTIMESTAMPOFFSET. Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).  
  
     Dans les formats qui incluent un élément de fuseau horaire, aucun espace ne figure entre l'élément d'heure et l'élément de fuseau horaire, comme le montre l'exemple suivant :  
  
     HH:MI:SS[+HH:MI]  
  
     Dans l'exemple précédent, les crochets indiquent que la valeur de fuseau horaire est facultative.  
  
-   Formats d'heure qui incluent une fraction décimale, répertoriés dans le tableau suivant :  
  
    |Format|Description|  
    |------------|-----------------|  
    |HH[.nnnnnnn]|n est une valeur comprise entre 0 et 9 999 999 qui représente une fraction d'heures. Les crochets indiquent que cette valeur est facultative.<br /><br /> Par exemple, la valeur 12.750 signifie 12:45.|  
    |HHMI[.nnnnnnn]<br /><br /> HH:MI[.nnnnnnn]|n est une valeur comprise entre 0 et 9 999 999 qui représente une fraction de minutes. Les crochets indiquent que cette valeur est facultative.<br /><br /> Par exemple, la valeur 1220.500 signifie 12:20:30.|  
    |HHMISS[.nnnnnnn]<br /><br /> HH:MI:SS[.nnnnnnn]|n est une valeur comprise entre 0 et 9 999 999 qui représente une fraction de secondes. Les crochets indiquent que cette valeur est facultative.<br /><br /> Par exemple, la valeur 122040.250 signifie 12:20:40.15.|  
  
    > [!NOTE]  
    >  Dans le tableau précédent, le séparateur de fraction pour les formats d'heure peut être une décimale ou une virgule.  
  
-   Valeurs d'heure qui incluent un saut de seconde, comme le montrent les exemples suivants :  
  
     23:59:60[.0000000]  
  
     235960[.0000000]  
  
 L'analyse rapide génère en sortie des chaînes sous la forme DT_DBTIME et DT_DBTIME2. Les valeurs d'heure aux formats tronqués sont complétées. Par exemple, HH:MI devient HH:MM:00.000.  
  
 Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).  
  
## <a name="datetime-data-type"></a>Type de données de date/heure  
 L'analyse rapide prend en charge les formats de chaîne suivants pour les données de date/heure :  
  
-   Formats qui incluent des espaces de début. Par exemple, la valeur « 2003-01-10T203910» est valide.  
  
-   Combinaisons de formats de date valides et de formats d'heure valides séparés par un T majuscule, ainsi que de formats de fuseau horaire valides, par exemple YYYYMMDDT[HHMISS][+HH:MI]. Les valeurs d'heure et de fuseau horaire ne sont pas requises. Par exemple, « 2003-10-14 » est valide.  
  
 L'analyse rapide ne prend pas en charge les intervalles de temps. Par exemple, un intervalle de temps identifié par une date et une heure de début et de fin au format AAAAMMJJThhmmss/AAAAMMJJThhmmss ne peut pas être analysé.  
  
 L'analyse rapide génère en sortie des chaînes sous la forme DT_DATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2 et DT_DBTIMESTAMPOFFSET. Les valeurs de date/heure aux formats tronqués sont complétées. Le tableau suivant répertorie les valeurs ajoutées pour les parties des date et heure manquantes.  
  
|Partie de date/heure|Remplissage|  
|---------------------|-------------|  
|Secondes|Ajout de 00.|  
|Minutes|Ajouter 00:00.|  
|Heure|Ajout de 00:00:00.|  
|Jour|Ajout de 01 pour le jour du mois.|  
|Mois|Ajout de 01 pour le mois de l'année.|  
  
 Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).  
  
  
