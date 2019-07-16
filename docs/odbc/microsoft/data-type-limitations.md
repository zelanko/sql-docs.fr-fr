---
title: Limitations du Type de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 64d16a9181c475427677371d1e6e180570225b7a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096462"
---
# <a name="data-type-limitations"></a>Limitations des types de données
Les pilotes de base de données Microsoft ODBC Desktop impose les restrictions suivantes sur les types de données :  
  
|Type de données|Description|  
|---------------|-----------------|  
|Tous les types de données|Échecs de conversion de type peuvent entraîner la colonne affectée est définie sur NULL.|  
|BINARY|Création d’une colonne binaire de longueur zéro retourne en fait une colonne binaire de 255 octets.|  
|DATE|Le type de données DATE ne peut pas être converti vers un autre type de données (ou lui-même) par la fonction CONVERT.|  
|DECIMAL (valeur numérique exacte)|Non pris en charge.|  
|Types de données à virgule flottante|Le nombre de décimales dans un nombre à virgule flottante peut être limité par le format de nombre défini dans la section International du Panneau de configuration Windows.|  
|NUMERIC|Prend en charge la précision maximale et une échelle de 28.|  
|TIMESTAMP|Impossible de convertir le type de données TIMESTAMP à elle-même par la fonction CONVERT.|  
|TINYINT|TINYINT valeurs sont toujours non signés.|  
|Chaînes de longueur nulle|Quand un fichier dBASE, Microsoft Excel, Paradox ou Textdriver est utilisé, l’insertion d’une chaîne de longueur nulle dans une colonne insère en fait une valeur NULL à la place.|
