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
manager: craigg
ms.openlocfilehash: c9b8999e229e8a6ed4804b2f06a4072d139ae93a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818151"
---
# <a name="setting-extendedansisql"></a>Définition de ExtendedAnsiSQL
L’attribut peut être contrôlé dans la chaîne de connexion en ajoutant l’attribut ExtendedAnsiSQL :  
  
|Valeur|Description|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (valeur par défaut)|Ce paramètre ne permet pas de nouvelles fonctionnalités.|  
|ExtendedAnsiSQL = 1|Ce paramètre active les nouvelles fonctionnalités.|  
  
 L’attribut peut également être défini dans une source de données via le **Options avancées** boîte de dialogue lors de la configuration d’une source de données via le panneau de configuration.  
  
 Définissant l’attribut sur 0 désactive les nouvelles fonctionnalités ; la valeur 1 active les nouvelles fonctionnalités.  
  
 L’attribut peut également être défini à l’aide de SQLSetConnectAttr(). La valeur d’attribut est 65501 et est définie sur la valeur SQLINTEGER 1 ou 0, comme indiqué dans le tableau précédent. Elle peut être appelée avant ou après la connexion, mais il est préférable d’appeler après la connexion en raison de l’ordre dans lequel les processus de pilote mis en cache les chaînes de connexion et les attributs de connexion.
