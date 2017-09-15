---
title: Types de modifications | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], types of changes
- backward compatibility [ODBC], types of changes
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9a494595625d264159fbb39db03818d50ed97876
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="types-of-changes"></a>Types de modifications
Trois types de modifications sont apportées dans ODBC 3. *x* (et n’importe quelle version d’ODBC). Chacun de ces affecte différemment de la compatibilité descendante et est géré d’une manière différente. Ces modifications sont décrites dans le tableau suivant.  
  
|Type de modification| Description|  
|--------------------|-----------------|  
|Nouvelles fonctionnalités|Il s’agit des fonctionnalités qui sont nouvelles dans ODBC 3. *x*, tels que la liaison hors ligne ou de descripteurs. Celles-ci sont implémentées uniquement lorsque l’application et de pilote, ainsi que le Gestionnaire de pilotes, sont de la version 3*.x*, donc il n’existe aucune tentative pour rendre ces une compatibilité descendante.|  
|Fonctionnalités en double|Il s’agit des fonctionnalités qui existent dans ODBC 2*.x* alors que ODBC 3.* x* mais sont implémentées de différentes façons dans chacun. Les fonctions **SQLAllocHandle** et **SQLAllocStmt** sont un exemple. Problèmes de compatibilité descendante pour ces et autres fonctionnalités en double sont principalement traitées par les mappages dans le Gestionnaire de pilotes.|  
|Changements de comportement|Il s’agit des fonctionnalités qui sont gérées différemment dans ODBC 2*.x* alors que ODBC 3.* x*. Une valeur datetime **#define** est un exemple. Ces fonctionnalités sont gérées par la version ODBC 3. *x* pilote basé sur un paramètre d’attribut environnement. (Consultez [modifications comportementales](../../../odbc/reference/develop-app/behavioral-changes.md) pour plus d’informations.)|
