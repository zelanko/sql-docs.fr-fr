---
title: Réglage ÉtenduAnsiSQL Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300799"
---
# <a name="setting-extendedansisql"></a>Définition de ExtendedAnsiSQL
L’attribut peut être contrôlé dans la chaîne de connexion en ajoutant l’attribut ExtendedAnsiSQL :  
  
|Valeur|Description|  
|-----------|-----------------|  
|ExtendedAnsiSQL-0 (par défaut)|Ce paramètre n’active pas les nouvelles fonctionnalités.|  
|ÉtenduAnsiSQL-1|Ce paramètre permet aux nouvelles fonctionnalités.|  
  
 L’attribut peut également être défini dans un DSN via la boîte de dialogue **Options avancées** lors de la configuration d’un DSN par panneau de contrôle.  
  
 Définir l’attribut à 0 désactive les nouvelles fonctionnalités; le réglage à 1 permet les nouvelles fonctionnalités.  
  
 L’attribut peut également être défini à l’aide de SQLSetConnectAttr(). La valeur d’attribut est de 65501 et est réglée à une valeur SQLINTEGER de 1 ou 0, comme indiqué dans le tableau précédent. Il peut être appelé avant ou après la connexion, mais il est préférable de l’appeler après la connexion en raison de l’ordre dans lequel le pilote traite les attributs de connexion mis en cache et les chaînes de connexion.
