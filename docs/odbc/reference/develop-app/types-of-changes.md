---
title: Types de modifications | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], types of changes
- backward compatibility [ODBC], types of changes
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5f43dbf75754a16b3163bbb8e268400f34d372b4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68087809"
---
# <a name="types-of-changes"></a>Types de changements
Trois types de modifications sont apportées dans ODBC *3.x* (et n’importe quelle version d’ODBC). Chacune de ces affecte la compatibilité descendante différemment et est gérée de manière différente. Ces modifications sont décrites dans le tableau suivant.  
  
|Type de modification|Description|  
|--------------------|-----------------|  
|Nouvelles fonctionnalités|Il s’agit des fonctionnalités qui sont nouvelles dans ODBC *3.x*, telles que la liaison hors ligne ou les descripteurs. Celles-ci sont implémentées uniquement lorsque l’application et de pilote, ainsi que le Gestionnaire de pilotes, sont de version *3.x*, donc il n’existe aucune tentative pour établir ces une compatibilité descendante.|  
|Fonctionnalités en doublon|Il s’agit des fonctionnalités qui existent dans ODBC *2.x* et ODBC *3.x* mais sont implémentées de différentes façons dans chacun. Les fonctions **SQLAllocHandle** et **SQLAllocStmt** sont un exemple. Problèmes de compatibilité descendante pour ces et autres fonctionnalités en double sont principalement gérées par les mappages dans le Gestionnaire de pilotes.|  
|Changements de comportement|Il s’agit des fonctionnalités qui sont gérées différemment dans ODBC *2.x* et ODBC *3.x*. Une valeur datetime **#define** est un exemple. Ces fonctionnalités sont gérées par ODBC *3.x* pilote basé sur un paramètre d’attribut environnement. (Consultez [des changements de comportement](../../../odbc/reference/develop-app/behavioral-changes.md) pour plus d’informations.)|
