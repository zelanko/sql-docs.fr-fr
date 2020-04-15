---
title: Caractéristiques du curseur et type de curseur (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8354fdabf6830780ec2d128492c86cc1edd582ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301626"
---
# <a name="cursor-characteristics-and-cursor-type"></a>Caractéristiques et types de curseurs
Une application peut spécifier les caractéristiques d’un curseur au lieu de spécifier le type de curseur (avant seulement, statique, keyset-driven, ou dynamique). Pour ce faire, l’application sélectionne la défilement du curseur (en définissant l’attribut de l’SQL_ATTR_CURSOR_SCROLLABLE) et la sensibilité (en définissant l’attribut de l’SQL_ATTR_CURSOR_SENSITIVITY déclaration) avant d’ouvrir le curseur sur la poignée de déclaration. Le conducteur choisit alors le type de curseur qui fournit le plus efficacement les caractéristiques que l’application a demandées.  
  
 Chaque fois qu’une application définit l’un des attributs de l’énoncé SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY ou SQL_ATTR_CURSOR_TYPE, le conducteur apporte toute modification requise aux attributs d’autres énoncés dans cet ensemble de quatre attributs afin que ses valeurs restent cohérentes. Par conséquent, lorsque l’application spécifie une caractéristique du curseur, le conducteur peut modifier l’attribut qui indique le type de curseur en fonction de cette sélection implicite; lorsque l’application spécifie un type, le conducteur peut modifier l’un des autres attributs pour être compatible avec les caractéristiques du type sélectionné. Pour plus d’informations sur ces attributs de déclaration, consultez la description de la fonction [SQLSetStmtAttr.](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)  
  
 Une application qui définit les attributs de l’instruction pour spécifier à la fois un type de curseur et des caractéristiques de curseur court le risque d’obtenir un curseur qui n’est pas la méthode la plus efficace disponible sur ce pilote pour répondre aux exigences de l’application.  
  
 Le paramètre implicite des attributs de déclaration est défini par le conducteur, sauf qu’il doit suivre ces règles :  
  
-   Les curseurs avant-seulement ne sont jamais défilementables; voir la définition de SQL_ATTR_CURSOR_SCROLLABLE dans [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   Les curseurs insensibles ne sont jamais updatables (et donc leur concordance est lue seulement); ceci est basé sur leur définition des curseurs insensibles dans la norme ISO SQL.  
  
 Par conséquent, le paramètre implicite des attributs de déclaration se produit dans les cas décrits dans le tableau suivant.  
  
|Ensembles d’applications attribuent à|Autres attributs définis implicitement|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY à SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY à SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY à SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES|SQL_ATTR_CURSOR_SENSITIVITY à SQL_UNSPECIFIED ou SQL_SENSITIVE, tel que défini par le conducteur. Il ne peut jamais être mis à SQL_INSENSITIVE, parce que les curseurs insensibles sont toujours lus seulement.|  
|SQL_ATTR_CURSOR_SCROLLABLE à SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE à SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN ou SQL_CURSOR_DYNAMIC, comme l’a précisé le conducteur. Il n’est jamais mis à SQL_CURSOR_FORWARD_ONLY.|  
|SQL_ATTR_CURSOR_SENSITIVITY à SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY à SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY à SQL_SENSITIVE|SQL_ATTR_CONCURRENCY à SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES, comme l’a précisé le conducteur. Il n’est jamais mis à SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN ou SQL_CURSOR_DYNAMIC, comme l’a précisé le conducteur.|  
|SQL_ATTR_CURSOR_SENSITIVITY à SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY à SQL_CONCUR_READ_ONLY, SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES, comme l’a précisé le conducteur.<br /><br /> SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN ou SQL_CURSOR_DYNAMIC, comme l’a précisé le conducteur.|  
|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE à SQL_SCROLLABLE.<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY à SQL_SENSITIVE. (Mais seulement si SQL_ATTR_CONCURRENCY n’est pas égale à SQL_CONCUR_READ_ONLY. Les curseurs dynamiques updatables sont toujours sensibles aux changements qui ont été apportés dans leur propre transaction.)|  
|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_FORWARD_ONLY|SQL_ATTR_CURSOR_SCROLLABLE à SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE à SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY à SQL_UNSPECIFIED ou SQL_SENSITIVE (selon des critères définis par le conducteur, si SQL_ATTR_CONCURRENCY n’est pas SQL_CONCUR_READ_ONLY).|  
|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE à SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY à SQL_INSENSITIVE (si SQL_ATTR_CONCURRENCY est SQL_CONCUR_READ_ONLY).<br /><br /> SQL_ATTR_SENSITIVITY à SQL_UNSPECIFIED ou à SQL_SENSITIVE (si SQL_ATTR_CONCURRENCY n’est pas SQL_CONCUR_READ_ONLY).|
