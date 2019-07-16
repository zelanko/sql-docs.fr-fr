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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063601"
---
# <a name="setting-extendedansisql"></a>Définition de ExtendedAnsiSQL
L’attribut peut être contrôlé dans la chaîne de connexion en ajoutant l’attribut ExtendedAnsiSQL :  
  
|Value|Description|  
|-----------|-----------------|  
|ExtendedAnsiSQL=0 (default)|Ce paramètre ne permet pas de nouvelles fonctionnalités.|  
|ExtendedAnsiSQL=1|Ce paramètre active les nouvelles fonctionnalités.|  
  
 L’attribut peut également être défini dans une source de données via le **Options avancées** boîte de dialogue lors de la configuration d’une source de données via le panneau de configuration.  
  
 Définissant l’attribut sur 0 désactive les nouvelles fonctionnalités ; la valeur 1 active les nouvelles fonctionnalités.  
  
 L’attribut peut également être défini à l’aide de SQLSetConnectAttr(). La valeur d’attribut est 65501 et est définie sur la valeur SQLINTEGER 1 ou 0, comme indiqué dans le tableau précédent. Elle peut être appelée avant ou après la connexion, mais il est préférable d’appeler après la connexion en raison de l’ordre dans lequel les processus de pilote mis en cache les chaînes de connexion et les attributs de connexion.
