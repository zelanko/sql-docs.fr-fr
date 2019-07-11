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
manager: craigg
ms.openlocfilehash: ca1b0fc2f7a1a74e1b9ab9a85baba945e4edf491
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792949"
---
# <a name="types-of-changes"></a>Types de changements
Trois types de modifications sont apportées dans ODBC *3.x* (et n’importe quelle version d’ODBC). Chacune de ces affecte la compatibilité descendante différemment et est gérée de manière différente. Ces modifications sont décrites dans le tableau suivant.  
  
|Type de modification|Description|  
|--------------------|-----------------|  
|Nouvelles fonctionnalités|Il s’agit des fonctionnalités qui sont nouvelles dans ODBC *3.x*, telles que la liaison hors ligne ou les descripteurs. Celles-ci sont implémentées uniquement lorsque l’application et de pilote, ainsi que le Gestionnaire de pilotes, sont de version *3.x*, donc il n’existe aucune tentative pour établir ces une compatibilité descendante.|  
|Fonctionnalités en doublon|Il s’agit des fonctionnalités qui existent dans ODBC *2.x* et ODBC *3.x* mais sont implémentées de différentes façons dans chacun. Les fonctions **SQLAllocHandle** et **SQLAllocStmt** sont un exemple. Problèmes de compatibilité descendante pour ces et autres fonctionnalités en double sont principalement gérées par les mappages dans le Gestionnaire de pilotes.|  
|Changements de comportement|Il s’agit des fonctionnalités qui sont gérées différemment dans ODBC *2.x* et ODBC *3.x*. Une valeur datetime **#define** est un exemple. Ces fonctionnalités sont gérées par ODBC *3.x* pilote basé sur un paramètre d’attribut environnement. (Consultez [des changements de comportement](../../../odbc/reference/develop-app/behavioral-changes.md) pour plus d’informations.)|
