---
description: Types de données C dans ODBC
title: Types de données C dans ODBC | Microsoft Docs
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
ms.openlocfilehash: 395f60860dd3179326687a6c2fb10bbaf027ca3a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494759"
---
# <a name="c-data-types-in-odbc"></a>Types de données C dans ODBC
ODBC définit les types de données C utilisés par les variables d’application et leurs identificateurs de type correspondants. Celles-ci sont utilisées par les mémoires tampons liées aux colonnes de jeu de résultats et aux paramètres d’instruction. Supposons, par exemple, qu’une application souhaite récupérer des données à partir d’une colonne de jeu de résultats au format caractère. Elle déclare une variable avec le type de données SQLCHAR * et lie cette variable à la colonne du jeu de résultats avec un identificateur de type SQL_C_CHAR. Pour obtenir la liste complète des types de données et des identificateurs de type C, consultez l' [annexe D : types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 ODBC définit également un mappage par défaut de chaque type de données SQL à un type de données C. Par exemple, un entier de 2 octets dans la source de données est mappé à un entier de 2 octets dans l’application. Pour utiliser le mappage par défaut, une application spécifie l’identificateur de type SQL_C_DEFAULT. Toutefois, l’utilisation de cet identificateur est déconseillée pour des raisons d’interopérabilité.  
  
 Tous les types de données Integer C définis dans ODBC *1. x* ont été signés. Les types de données C non signés et leurs identificateurs de type correspondants ont été ajoutés dans ODBC 2,0. Pour cette raison, les applications et les pilotes doivent être particulièrement vigilants lors de la gestion des versions *1. x* .  
  
## <a name="c-data-type-extensibility"></a>Extensibilité du type de données C  
 Dans ODBC 3,8, vous pouvez spécifier des types de données C spécifiques au pilote. Cela vous permet de lier un type SQL en tant que type C spécifique au pilote dans les applications ODBC quand vous appelez [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)ou [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md). Cela peut être utile pour la prise en charge de nouveaux types de serveurs, car les types de données C existants peuvent ne pas représenter correctement les nouveaux types de données serveur. L’utilisation de types C spécifiques au pilote peut augmenter le nombre de conversions que les pilotes peuvent effectuer.  
  
 Supposons, par exemple, qu’un système de gestion de base de données (SGBD) a introduit un nouveau type SQL, **DateTimeOffset**, pour représenter la date et l’heure avec les informations de fuseau horaire. Il n’y aurait pas de type C spécifique dans ODBC qui correspondait à **DateTimeOffset**. Une application doit lier **DateTimeOffset** en tant que SQL_C_BINARY et la convertir en un type de données défini par l’utilisateur. À compter de ODBC 3,8 avec l’extensibilité du type de données C, un pilote peut définir un nouveau type C correspondant. Par exemple, pour le nouveau type SQL DATETIMEOFFSET, le pilote peut définir un nouveau type C correspondant, tel que SQL_C_DATETIMEOFFSET. Ensuite, une application peut lier le nouveau type SQL en tant que type C spécifique au pilote.  
  
 Un type de données C est défini dans le pilote comme suit :  
  
-   Le niveau de compatibilité ODBC pour une application, le pilote ODBC et le gestionnaire de pilotes est 3,8 (ou version ultérieure).  
  
-   La plage de données d’un type C spécifique au pilote est comprise entre 0x4000 et 0x7FFF.  
  
-   Le pilote définit la structure des données correspondant au type C.  Cela peut être fait dans le kit de développement logiciel (SDK) spécifique au pilote.  
  
 Le gestionnaire de pilotes ne validera pas un type C défini dans la plage de 0x4000 et 0x7FFF ; le pilote effectue la validation et toute conversion de type de données. Toutefois, si la plage de données d’un type C passé au gestionnaire de pilotes est comprise entre 0x0000 et 0x3FFF ou entre 0x8000 et 0xFFFF, le gestionnaire de pilotes valide le type de données C.  
  
> [!NOTE]  
>  Les types de données C spécifiques au pilote doivent être décrits dans la documentation du pilote.  
  
 Pour spécifier un niveau de compatibilité ODBC de 3,8, une application appelle [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md) avec l’attribut SQL_ATTR_ODBC_VERSION défini sur **SQL_OV_ODBC3_80**. Pour déterminer la version du pilote, une application appelle **SQLGetInfo** avec SQL_DRIVER_ODBC_VER.  
  
 Pour plus d’informations sur ODBC 3,8, voir [What’s New in odbc 3,8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données C](../../../odbc/reference/appendixes/c-data-types.md)
