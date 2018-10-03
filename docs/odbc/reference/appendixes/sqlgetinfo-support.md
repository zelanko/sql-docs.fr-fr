---
title: Prise en charge de SQLGetInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLGetInfo
- backward compatibility [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], support
ms.assetid: 57326f57-daba-46b6-b0be-6c97213b9ef1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6eb6bedb20e1f61c48776d03df59aa6865cfb2a3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680777"
---
# <a name="sqlgetinfo-support"></a>SQLGetInfo, prise en charge
Lorsqu’une application ODBC 2. *x* application appelle **SQLGetInfo** à un ODBC 3 *.x* pilote, le *InfoType* arguments dans le tableau suivant doivent être pris en charge.  
  
|*infoType*|Valeur renvoyée|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2.0) **Remarque :** ce type d’information n’est pas déconseillé ; les masques de bits dans la colonne à droite sont déconseillés.|Un masque de bits SQLINTEGER énumérant les clauses dans le **ALTER TABLE** instruction pris en charge par la source de données.<br /><br /> Les masques de bits suivants sont utilisés pour déterminer les clauses sont prises en charge :<br /><br /> SQL_AT_DROP_COLUMN = permet de supprimer des colonnes est pris en charge. Si cela entraîne en cascade ou limiter le comportement est définie par le pilote. ODBC (2.0)<br /><br /> SQL_AT_ADD_COLUMN = la possibilité d’ajouter la prise en charge de plusieurs colonnes dans une instruction ALTER TABLE unique. Ce bit n’associe pas avec les autres SQL_AT_ADD_COLUMN_XXX ou SQL_AT_CONSTRAINT_XXX bits. ODBC (2.0)|  
|SQL_FETCH_DIRECTION (ODBC 1.0)<br /><br /> Le type d’informations a été introduit dans ODBC 1.0 ; chaque masque de bits est étiquetée avec la version dans laquelle il a été introduite.|Un masque de bits SQLINTEGER énumérant les options de direction d’extraction prises en charge.<br /><br /> Les masques de bits suivants sont utilisés conjointement avec l’indicateur pour déterminer quelles options sont prises en charge :<br /><br /> SQL_FD_FETCH_NEXT (ODBC 1.0) SQL_FD_FETCH_BOOKMARK (ODBC 1.0) SQL_FD_FETCH_ABSOLUTE (ODBC 1.0) SQL_FD_FETCH_PRIOR (ODBC 1.0) SQL_FD_FETCH_LAST (ODBC 1.0) SQL_FD_FETCH_RELATIVE (ODBC 1.0) SQL_FD_FETCH_BOOKMARK (ODBC 2.0)|  
|SQL_LOCK_TYPES (ODBC 2.0)|Un masque de bits SQLINTEGER le verrou pris en charge de l’énumération des types pour le *troupeau* argument dans **SQLSetPos**.<br /><br /> Les masques de bits suivants sont utilisés conjointement avec l’indicateur pour déterminer quels types de verrou sont prises en charge :<br /><br /> SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1.0)|Une valeur SQLSMALLINT indiquant le niveau de conformité de ODBC.<br /><br /> SQL_OAC_NONE = None<br /><br /> SQL_OAC_LEVEL1 = 1 niveau pris en charge<br /><br /> SQL_OAC_LEVEL2 = 2 niveau pris en charge|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)|Une valeur SQLSMALLINT indiquant la grammaire SQL pris en charge par le pilote. Consultez [annexe c : SQL grammaire](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md) pour une définition de niveaux de conformité de SQL.<br /><br /> SQL_OSC_MINIMUM = grammaire minimale prise en charge<br /><br /> SQL_OSC_CORE = grammaire Core prise en charge<br /><br /> SQL_OSC_EXTENDED = grammaire étendu pris en charge|  
|SQL_POS_OPERATIONS (ODBC 2.0)|Un masque de bits SQLINTEGER énumérant les opérations prises en charge dans **SQLSetPos**.<br /><br /> Les masques de bits suivants sont utilisés conjointement avec l’indicateur pour déterminer quelles options sont prises en charge :<br /><br /> SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2.0)|Un masque de bits SQLINTEGER l’énumération prises en charge positionné des instructions SQL.<br /><br /> Les masques de bits suivants sont utilisés pour déterminer quelles instructions sont prises en charge :<br /><br /> SQL_PS_POSITIONED_DELETE SQL_PS_POSITIONED_UPDATE SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1.0)|Un masque de bits SQLINTEGER énumérant les options de contrôle d’accès concurrentiel pris en charge pour le curseur.<br /><br /> Les masques de bits suivants sont utilisés pour déterminer quelles options sont prises en charge :<br /><br /> SQL_SCCO_READ_ONLY = curseur est en lecture seule. Aucune mise à jour n’est autorisées.<br /><br /> SQL_SCCO_LOCK = curseur utilise le niveau de verrouillage pour vous assurer que la ligne peut être mis à jour le plus bas.<br /><br /> SQL_SCCO_OPT_ROWVER = le contrôle d’accès concurrentiel optimiste curseur utilise en comparant des versions de ligne, tels que SQLBase ROWID ou Sybase TIMESTAMP.<br /><br /> SQL_SCCO_OPT_VALUES = le contrôle d’accès concurrentiel optimiste curseur utilise en comparant les valeurs.|  
|SQL_STATIC_SENSITIVITY (ODBC 2.0)|Un masque de bits SQLINTEGER énumérant si les modifications apportées par une application pour un curseur statique ou commandé par keyset via **SQLSetPos** ou mise à jour positionnée ou les instructions delete peuvent être détectées par l’application.<br /><br /> SQL_SS_ADDITIONS = Added lignes sont visibles par le curseur ; le curseur peut défiler à ces lignes. Où ces lignes sont ajoutées au curseur dépend du pilote.<br /><br /> SQL_SS_DELETIONS = Deleted lignes ne sont plus disponibles jusqu’au curseur et ne laissez pas un « trou » dans le jeu de résultats ; une fois que le curseur se place à partir d’une ligne supprimée, elle ne peut pas retourner à cette ligne.<br /><br /> SQL_SS_UPDATES = mises à jour des lignes sont visibles par le curseur ; Si le curseur défile à partir d’et renvoie à une ligne mise à jour, les données retournées par le curseur sont les données mises à jour, pas les données d’origine. Cette option s’applique uniquement comme étant statiques curseurs ou les mises à jour sur les curseurs qui ne mettent pas à jour la clé. Cette option ne s’applique pas pour un curseur dynamique ou dans le cas dans lequel une clé est modifiée dans un curseur mixte.<br /><br /> Si une application peut détecter les modifications apportées au jeu par d’autres utilisateurs, y compris d’autres curseurs dans la même application, de résultats varie selon le type de curseur.|  
  
 Un ODBC 3 *.x* application fonctionne avec un ODBC 3 *.x* pilote ne doit pas appeler **SQLGetInfo** avec la *InfoType* les arguments décrits dans l’exemple précédent de table mais vous devez utiliser le ODBC 3 *.x* *InfoType* arguments répertoriés dans le paragraphe suivant. Il n’est pas une correspondance exacte entre *InfoType* arguments utilisés dans ODBC 2. *x* et ceux utilisés dans ODBC 3 *.x*. Un ODBC 3 *.x* application fonctionne avec une API ODBC 2. *x* pilote, quant à eux, doit utiliser le *InfoType* arguments décrits précédemment.  
  
 Certains types d’informations dans le tableau précédent sont déconseillées au profit des types d’informations de curseur attributs. Ces déconseillée informations types SQL_FETCH_DIRECTION SQL_LOCK_TYPES, SQL_POS_OPERATIONS, SQL_POSITIONED_STATEMENTS, SQL_SCROLL_CONCURRENCY et SQL_STATIC_SENSITIVITY. Les nouveaux types d’attributs de curseur sont SQL_XXX_CURSOR_ATTRIBUTES2 SQL_XXX_CURSOR_ATTRIBUTES1and, où XXX est égal à DYNAMIC, FORWARD_ONLY, KEYSET_DRIVEN ou statique. Chacun des nouveaux types indique les fonctionnalités du pilote pour un type de curseur unique. Pour plus d’informations sur ces options, consultez le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description de fonction.
