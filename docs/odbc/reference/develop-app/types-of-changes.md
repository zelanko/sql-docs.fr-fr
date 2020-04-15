---
title: Types de changements Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301604"
---
# <a name="types-of-changes"></a>Types de changements
Trois types de modifications sont apportés dans ODBC *3.x* (et toute version d’ODBC). Chacune d’entre elles affecte différemment la compatibilité vers l’arrière et est traitée d’une manière différente. Ces changements sont décrits dans le tableau suivant.  
  
|Type de changement|Description|  
|--------------------|-----------------|  
|Nouvelles fonctionnalités|Ce sont des fonctionnalités qui sont nouvelles à ODBC *3.x*, tels que la liaison hors ligne ou descripteurs. Ceux-ci ne sont mis en œuvre que lorsque l’application et le pilote, ainsi que le driver Manager, sont de la version *3.x*, il n’y a donc aucune tentative de les rendre compatibles vers l’arrière.|  
|Caractéristiques dupliquées|Ce sont des fonctionnalités qui existent dans ODBC *2.x* et ODBC *3.x* mais sont implémentées de différentes manières dans chacune. Les fonctions **SQLAllocHandle** et **SQLAllocStmt** en sont un exemple. Les problèmes de compatibilité rétrograde pour ces fonctionnalités et d’autres fonctionnalités dupliquées sont principalement gérés par des cartographies dans le Driver Manager.|  
|Changements de comportement|Ce sont des fonctionnalités qui sont traitées différemment dans ODBC *2.x* et ODBC *3.x*. Une date **#define** en est un exemple. Ces fonctionnalités sont traitées par le pilote ODBC *3.x* en fonction d’un paramètre d’attribut de l’environnement. (Voir [changements comportementaux](../../../odbc/reference/develop-app/behavioral-changes.md) pour plus d’informations.)|
