---
title: Types de données C à ODBC ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
ms.assetid: c91bef31-3794-4736-966a-d50997b2233c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e1efba2187e2c1f2d813d43640fc9259ad4f2b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306294"
---
# <a name="c-data-types-in-odbc"></a>Types de données C dans ODBC
ODBC définit les types de données C qui sont utilisés par les variables d’application et leurs identifiants de type correspondants. Ceux-ci sont utilisés par les tampons qui sont tenus de donner des résultats définis colonnes et paramètres de déclaration. Supposons, par exemple, qu’une application veuille récupérer des données à partir d’une colonne de résultat définie dans le format de caractère. Il déclare une variable avec le type de données SQLCHAR et lie cette variable à la colonne de l’ensemble de résultat avec un type d’identificateur de SQL_C_CHAR. Pour une liste complète des types de données C et des identificateurs de type, voir [l’annexe D : Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 ODBC définit également une cartographie par défaut de chaque type de données SQL à un type de données C. Par exemple, un intégrant de 2-byte dans la source de données est cartographié à un intégrant de 2-byte dans l’application. Pour utiliser la cartographie par défaut, une application spécifie l’identifiant de type SQL_C_DEFAULT. Cependant, l’utilisation de cet identifiant est déconseillée pour des raisons d’interopérabilité.  
  
 Tous les types de données integer C définis dans ODBC *1.x* ont été signés. Des types de données C non signés et leurs identifiants de type correspondant ont été ajoutés dans ODBC 2.0. Pour cette raison, les applications et les pilotes doivent être particulièrement prudents lorsqu’il s’agit de versions *1.x.*  
  
## <a name="c-data-type-extensibility"></a>C Data Type Extensibility  
 Dans ODBC 3.8, vous pouvez spécifier les types de données C spécifiques au conducteur. Cela vous permet de lier un type SQL comme type C spécifique au conducteur dans les applications ODBC lorsque vous appelez [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md), ou [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md). Cela peut être utile pour prendre en charge de nouveaux types de serveurs, car les types de données C existants peuvent ne pas représenter correctement les nouveaux types de données serveur. L’utilisation de types C spécifiques au conducteur peut augmenter le nombre de conversions que les conducteurs peuvent effectuer.  
  
 Supposons, par exemple, qu’un système de gestion de base de données (DBMS) ait introduit un nouveau type SQL, **DATETIMEOFFSET**, pour représenter la date et l’heure avec des informations sur les fuseaux horaires. Il n’y aurait pas de type C spécifique dans ODBC qui correspondait à **DATETIMEOFFSET**. Une application devrait lier **DATETIMEOFFSET** comme SQL_C_BINARY et la jeter à un type de données défini par l’utilisateur. Commençant dans ODBC 3.8 avec l’extéabilité de type de données C, un conducteur peut définir un nouveau type C correspondant. Par exemple, pour le nouveau type SQL DATETIMEOFFSET, le conducteur peut définir un nouveau type C correspondant tel que SQL_C_DATETIMEOFFSET. Ensuite, une application peut lier le nouveau type SQL comme un type C spécifique au conducteur.  
  
 Un type de données C est défini dans le conducteur comme suit :  
  
-   Le niveau de conformité ODBC pour une demande, le pilote ODBC et driver Manager est de 3,8 (ou plus).  
  
-   La plage de données d’un type C spécifique au conducteur se situe entre 0x4000 et 0x7FFF.  
  
-   Le conducteur définit la structure des données correspondant au type C.  Cela peut être fait dans le SDK spécifique au conducteur.  
  
 Le gestionnaire de pilote ne validera pas un type C défini dans la gamme de 0x4000 et 0x7FFF; le pilote effectuera la validation et toute conversion de type de données. Mais si la plage de données d’un type C transmise au gestionnaire de pilote se situe entre 0x00000 et 0x3FFF ou entre 0x8000 et 0xFFFF, le gestionnaire de pilote validera le type de données C.  
  
> [!NOTE]  
>  Les types de données C spécifiques au conducteur doivent être décrits dans la documentation du conducteur.  
  
 Pour spécifier un niveau de conformité ODBC de 3,8, une application appelle [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md) avec l’attribut SQL_ATTR_ODBC_VERSION défini à **SQL_OV_ODBC3_80**. Pour déterminer la version du conducteur, une application appelle **SQLGetInfo** avec SQL_DRIVER_ODBC_VER.  
  
 Pour plus d’informations sur ODBC 3.8, voir [What’s New in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données C](../../../odbc/reference/appendixes/c-data-types.md)
