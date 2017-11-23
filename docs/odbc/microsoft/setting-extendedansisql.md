---
title: "Paramètre ExtendedAnsiSQL | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 59955db9520b409e46d179dd50fc33cedd8e15db
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="setting-extendedansisql"></a>Paramètre ExtendedAnsiSQL
L’attribut peut être contrôlé dans la chaîne de connexion en ajoutant l’attribut ExtendedAnsiSQL :  
  
|Valeur| Description|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (valeur par défaut)|Ce paramètre ne permet pas de nouvelles fonctionnalités.|  
|ExtendedAnsiSQL = 1|Ce paramètre active les nouvelles fonctionnalités.|  
  
 L’attribut peut également être défini dans une source de données via le **Options avancées** boîte de dialogue lors de la configuration d’une source de données via le panneau de configuration.  
  
 Définition de l’attribut à 0 désactive les nouvelles fonctionnalités ; la valeur 1 active les nouvelles fonctionnalités.  
  
 L’attribut peut également être défini à l’aide de SQLSetConnectAttr(). La valeur d’attribut est 65501 et est définie sur une valeur SQLINTEGER de 1 ou 0, comme indiqué dans le tableau précédent. Elle peut être appelée avant ou après la connexion, mais il est préférable d’appeler après la connexion en raison de l’ordre dans lequel les processus de pilote mis en cache les chaînes de connexion et les attributs de connexion.
