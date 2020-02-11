---
title: Définition de ExtendedAnsiSQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 330b55ef2d4fee090c453990d3fe75e6e2dacb6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063601"
---
# <a name="setting-extendedansisql"></a>Définition de ExtendedAnsiSQL
L’attribut peut être contrôlé dans la chaîne de connexion en ajoutant l’attribut ExtendedAnsiSQL :  
  
|Valeur|Description|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (valeur par défaut)|Ce paramètre n’active pas les nouvelles fonctionnalités.|  
|ExtendedAnsiSQL = 1|Ce paramètre active les nouvelles fonctionnalités.|  
  
 L’attribut peut également être défini dans un nom de source de nom via la boîte de dialogue **Options avancées** lors de la configuration d’un DSN via le panneau de configuration.  
  
 L’affectation de la valeur 0 à l’attribut désactive les nouvelles fonctionnalités. la valeur 1 active les nouvelles fonctionnalités.  
  
 L’attribut peut également être défini à l’aide de SQLSetConnectAttr (). La valeur de l’attribut est 65501 et est définie sur une valeur SQLINTEGER destinée de 1 ou 0, comme indiqué dans le tableau précédent. Il peut être appelé avant ou après la connexion, mais il est préférable de l’appeler après la connexion en raison de l’ordre dans lequel le pilote traite les attributs de connexion et les chaînes de connexion mis en cache.
