---
title: Limitations de Type de données | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e42d037592d444b21d4eb8a24879667dd12f5409
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-limitations"></a>Limitations de Type de données
Les pilotes de base de données Microsoft ODBC Desktop impose des limitations sur les types de données :  
  
|Type de données| Description|  
|---------------|-----------------|  
|Tous les types de données|La colonne affectée est la valeur NULL peuvent entraîner des échecs de conversion de type.|  
|BINARY|Création d’une colonne binaire de longueur zéro retourne en fait une colonne binaire de 255 octets.|  
|DATE|Le type de données DATE ne peut pas être converti vers un autre type de données (ou lui-même) par la fonction CONVERT.|  
|DECIMAL (valeur numérique exacte)|Non pris en charge.|  
|Types de données à virgule flottante|Le nombre de décimales dans un nombre à virgule flottante peut être limité par le format de nombre défini dans la section International du Panneau de configuration Windows.|  
|NUMERIC|Prend en charge la précision maximale et une échelle de 28.|  
|TIMESTAMP|Impossible de convertir le type de données TIMESTAMP à elle-même par la fonction CONVERT.|  
|TINYINT|Les valeurs TINYINT sont toujours non signés.|  
|Chaînes de longueur nulle|Lorsqu’un fichier dBASE, Microsoft Excel, Paradox ou Textdriver est utilisé, l’insertion d’une chaîne de longueur zéro dans une colonne insère en fait une valeur NULL à la place.|
