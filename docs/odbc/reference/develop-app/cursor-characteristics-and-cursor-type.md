---
title: Caractéristiques du curseur et type de curseur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: 6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e8803e7827102f564be63454b0387df938064d84
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002057"
---
# <a name="cursor-characteristics-and-cursor-type"></a>Caractéristiques et types de curseurs
Une application peut spécifier les caractéristiques d’un curseur au lieu de spécifier le type de curseur (avant uniquement, statique, piloté par jeu de clés ou dynamique). Pour ce faire, l’application sélectionne la fonction de défilement du curseur (en définissant l’attribut d’instruction SQL_ATTR_CURSOR_SCROLLABLE) et la sensibilité (en définissant l’attribut d’instruction SQL_ATTR_CURSOR_SENSITIVITY) avant d’ouvrir le curseur sur l’instruction. traitée. Le pilote choisit ensuite le type de curseur qui fournit le plus efficacement les caractéristiques demandées par l’application.  
  
 Chaque fois qu’une application définit l’un des attributs d’instruction SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY ou SQL_ATTR_CURSOR_TYPE, le pilote apporte toute modification requise aux autres attributs d’instruction dans cet ensemble de quatre attributs pour que leurs valeurs restent cohérentes. Par conséquent, lorsque l’application spécifie une caractéristique de curseur, le pilote peut modifier l’attribut qui indique le type de curseur en fonction de cette sélection implicite ; Lorsque l’application spécifie un type, le pilote peut modifier tous les autres attributs pour qu’ils soient cohérents avec les caractéristiques du type sélectionné. Pour plus d’informations sur ces attributs d’instruction, consultez la description de la fonction [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) .  
  
 Une application qui définit des attributs d’instruction pour spécifier à la fois un type de curseur et des caractéristiques de curseur exécute le risque d’obtenir un curseur qui n’est pas la méthode la plus efficace disponible sur ce pilote pour respecter les exigences de l’application.  
  
 Le paramètre implicite des attributs d’instruction est défini par le pilote, sauf qu’il doit respecter les règles suivantes :  
  
-   Les curseurs avant uniquement ne peuvent jamais faire l’aller défiler. consultez la définition de SQL_ATTR_CURSOR_SCROLLABLE dans [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   Les curseurs non sensibles ne peuvent jamais être mis à jour (et leur concurrence est donc en lecture seule); elle est basée sur la définition de curseurs non sensibles dans la norme ISO SQL.  
  
 Par conséquent, le paramètre implicite des attributs d’instruction se produit dans les cas décrits dans le tableau suivant.  
  
|Application affecte à l’attribut la valeur|Autres attributs définis implicitement|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY à SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY à SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES|SQL_ATTR_CURSOR_SENSITIVITY à SQL_UNSPECIFIED ou SQL_SENSITIVE, comme défini par le pilote. Il ne peut jamais être défini sur SQL_INSENSITIVE, car les curseurs non sensibles sont toujours en lecture seule.|  
|SQL_ATTR_CURSOR_SCROLLABLE à SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE à SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN ou SQL_CURSOR_DYNAMIC, comme spécifié par le pilote. Il n’a jamais la valeur SQL_CURSOR_FORWARD_ONLY.|  
|SQL_ATTR_CURSOR_SENSITIVITY à SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY à SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY à SQL_SENSITIVE|SQL_ATTR_CONCURRENCY à SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES, comme spécifié par le pilote. Il n’a jamais la valeur SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN ou SQL_CURSOR_DYNAMIC, comme spécifié par le pilote.|  
|SQL_ATTR_CURSOR_SENSITIVITY à SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY à SQL_CONCUR_READ_ONLY, SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES, comme spécifié par le pilote.<br /><br /> SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN ou SQL_CURSOR_DYNAMIC, comme spécifié par le pilote.|  
|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE à SQL_SCROLLABLE.<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY à SQL_SENSITIVE. (Mais uniquement si SQL_ATTR_CONCURRENCY n’est pas égal à SQL_CONCUR_READ_ONLY. Les curseurs dynamiques pouvant être mis à jour sont toujours sensibles aux modifications apportées dans leur propre transaction.)|  
|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_FORWARD_ONLY|SQL_ATTR_CURSOR_SCROLLABLE à SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE à SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY à SQL_UNSPECIFIED ou SQL_SENSITIVE (selon les critères définis par le pilote, si SQL_ATTR_CONCURRENCY n’est pas SQL_CONCUR_READ_ONLY).|  
|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE à SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY à SQL_INSENSITIVE (si SQL_ATTR_CONCURRENCY est SQL_CONCUR_READ_ONLY).<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED ou SQL_SENSITIVE (si SQL_ATTR_CONCURRENCY n’est pas SQL_CONCUR_READ_ONLY).|
