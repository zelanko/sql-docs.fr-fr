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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b5c2e4ed4d8bd64d02fb6a62861db832f6b0898
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300799"
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
