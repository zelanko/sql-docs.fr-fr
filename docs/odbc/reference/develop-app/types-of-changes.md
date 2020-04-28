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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f44adb59aa9b0f25475a76a97fe3670de0228c08
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301604"
---
# <a name="types-of-changes"></a>Types de changements
Trois types de modifications sont effectués dans ODBC *3. x* (et n’importe quelle version de ODBC). Chacun d’eux affecte la compatibilité descendante différemment et est géré d’une manière différente. Ces modifications sont décrites dans le tableau suivant.  
  
|Type de modification|Description|  
|--------------------|-----------------|  
|Nouvelles fonctionnalités|Il s’agit de fonctionnalités nouvelles dans ODBC *3. x*, telles que les liaisons hors ligne ou les descripteurs. Celles-ci sont implémentées uniquement lorsque l’application et le pilote, ainsi que le gestionnaire de pilotes, sont de la version *3. x*, donc aucune tentative de mise à compatibilité descendante n’est effectuée.|  
|Fonctionnalités dupliquées|Il s’agit de fonctionnalités qui existent dans ODBC *2. x* et ODBC *3. x* , mais qui sont implémentées de manière différente dans chaque. Les fonctions **SQLAllocHandle** et **SQLAllocStmt,** en sont un exemple. Les problèmes de compatibilité descendante pour ces fonctionnalités et d’autres fonctionnalités dupliquées sont principalement gérés par les mappages dans le gestionnaire de pilotes.|  
|Changements de comportement|Il s’agit de fonctionnalités gérées différemment dans ODBC *2. x* et ODBC *3. x*. Un **#define** DateTime en est un exemple. Ces fonctionnalités sont gérées par le pilote ODBC *3. x* en fonction d’un paramètre d’attribut d’environnement. (Pour plus d’informations, consultez [changements de comportement](../../../odbc/reference/develop-app/behavioral-changes.md) .)|
