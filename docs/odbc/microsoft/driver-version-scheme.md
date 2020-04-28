---
title: Schéma de version du pilote | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], versions
ms.assetid: e4a8d9d7-8aba-48ab-8be6-1a6129adfb8f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 864a8bd892315b060fc6fcf42dbe69dfea61ae59
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303450"
---
# <a name="driver-version-scheme"></a>Schéma des versions du pilote
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le tableau suivant répertorie toutes les versions publiées du pilote Microsoft ODBC pour Oracle.  
  
|Version du pilote|Numéro de build|Historique des disponibilités|  
|--------------------|------------------|--------------------------|  
|1.0|2.00.6235|Visual C++ 4,2 et Visual Basic 5,0, édition entreprise|  
|2.0|2.73.7269|Visual Studio 97 et MDAC 1.5 a|  
|2,0 mis à jour|2.73.7283.01|IIS 4,0|  
|2,0 mis à jour|2.73.7283.03|MDAC 1.5 b et 1.5 c|  
|2,0 mis à jour|2.73.7356|SDK ODBC 3,5|  
|2.5|2.573.2927|Visual Studio 6,0 et MDAC 2,0|  
|2,5 mis à jour|2.573.3513|SQL Server 7,0<br /><br /> SQL Server 6,5 SP5|  
  
 Build 2.00.6235 (version 1) était la première version du pilote Microsoft ODBC pour Oracle. Après la publication de la première version, une convention d’affectation de noms a été adoptée.  
  
 Par exemple, 2.73.7283.03 peut être divisé en composants distincts suivants :  
  
-   2 = le numéro de version.  
  
-   73 = la version du serveur Oracle pour lequel le pilote a été conçu.  
  
-   7283,03 = Numéro de build du pilote.  
  
> [!NOTE]  
>  Avec la version 2.573.2973, la Convention d’affectation de noms a entraîné une certaine confusion : 2,573 est une version antérieure à 2,73, mais chaque section du numéro de build doit être considérée comme individuelle. Le nombre 573 est supérieur à 73, donc il s’agit d’une version plus récente. En outre, « 2,5 » indique le numéro de version du pilote.
