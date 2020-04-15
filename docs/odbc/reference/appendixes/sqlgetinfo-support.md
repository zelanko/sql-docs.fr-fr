---
title: Soutien SQLGetInfo (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a21c035a14814f51d4344894ef253b2cc844f4c2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307800"
---
# <a name="sqlgetinfo-support"></a>SQLGetInfo, prise en charge
Quand un ODBC 2. *x* application appelle **SQLGetInfo** à un pilote ODBC 3 *.x,* les arguments *InfoType* dans le tableau suivant doivent être pris en charge.  
  
|*InfoType InfoType*|Retours|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2.0) **Note :** Ce type d’information n’est pas déprécié; les bitmasks dans la colonne à droite sont dépréciés.|Un bitmask SQLINTEGER énumérant les clauses de la déclaration **ALTER TABLE** appuyée par la source de données.<br /><br /> Les bitmasks suivants sont utilisés pour déterminer quelles clauses sont prises en charge :<br /><br /> SQL_AT_DROP_COLUMN - La capacité de laisser tomber des colonnes est prise en charge. Que cela se traduit par une cascade ou restreindre le comportement est défini par le conducteur. (ODBC 2.0)<br /><br /> SQL_AT_ADD_COLUMN - La possibilité d’ajouter plusieurs colonnes dans une seule instruction ALTER TABLE est prise en charge. Ce bit ne se combine pas avec d’autres bits SQL_AT_ADD_COLUMN_XXX ou SQL_AT_CONSTRAINT_XXX bits. (ODBC 2.0)|  
|SQL_FETCH_DIRECTION (ODBC 1.0)<br /><br /> Le type d’information a été introduit dans ODBC 1.0; chaque bitmask est étiqueté avec la version dans laquelle il a été introduit.|Un bitmask SQLINTEGER énumérant les options de direction d’aller chercher.<br /><br /> Les bitmasks suivants sont utilisés en conjonction avec le drapeau pour déterminer quelles options sont prises en charge :<br /><br /> SQL_FD_FETCH_NEXT (ODBC 1.0) SQL_FD_FETCH_FIRST (ODBC 1.0) SQL_FD_FETCH_LAST (ODBC 1.0) SQL_FD_FETCH_PRIOR (ODBC 1.0) SQL_FD_FETCH_ABSOLUTE (ODBC 1.0) SQL_FD_FETCH_RELATIVE (ODBC 1.0) SQL_FD_FETCH_BOOKMARK (ODBC 2.0)|  
|SQL_LOCK_TYPES (ODBC 2.0)|Un bitmask SQLINTEGER énumérant les types de serrures pris en charge pour *l’argument fLock* dans **SQLSetPos**.<br /><br /> Les bitmasks suivants sont utilisés en conjonction avec le drapeau pour déterminer quels types de serrures sont pris en charge :<br /><br /> SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1.0)|Une valeur SQLSMALLINT indiquant le niveau de conformité ODBC.<br /><br /> SQL_OAC_NONE - Aucun<br /><br /> SQL_OAC_LEVEL1 - Niveau 1 pris en charge<br /><br /> SQL_OAC_LEVEL2 - Niveau 2 pris en charge|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)|Une valeur SQLSMALLINT indiquant la grammaire SQL soutenue par le conducteur. Voir [Annexe C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md) pour une définition des niveaux de conformité SQL.<br /><br /> SQL_OSC_MINIMUM - Grammaire minimale soutenue<br /><br /> SQL_OSC_CORE - Grammaire de base soutenue<br /><br /> SQL_OSC_EXTENDED - Grammaire étendue soutenue|  
|SQL_POS_OPERATIONS (ODBC 2.0)|Un bitmask SQLINTEGER énumérant les opérations soutenues dans **SQLSetPos**.<br /><br /> Les bitmasks suivants sont utilisés en conjonction avec le drapeau pour déterminer quelles options sont prises en charge :<br /><br /> SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2.0)|Un bitmask SQLINTEGER énumérant les déclarations de SQL positionnées en soutien.<br /><br /> Les bitmasks suivants sont utilisés pour déterminer quelles déclarations sont prises en charge :<br /><br /> SQL_PS_POSITIONED_DELETE SQL_PS_POSITIONED_UPDATE SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1.0)|Un bitmask SQLINTEGER énumérant les options de contrôle de concurrence supportées pour le curseur.<br /><br /> Les bitmasks suivants sont utilisés pour déterminer quelles options sont prises en charge :<br /><br /> SQL_SCCO_READ_ONLY cursor est lu uniquement. Aucune mise à jour n’est autorisée.<br /><br /> SQL_SCCO_LOCK - Cursor utilise le niveau de verrouillage le plus bas suffisant pour s’assurer que la ligne peut être mise à jour.<br /><br /> SQL_SCCO_OPT_ROWVER - Cursor utilise un contrôle de concurrence optimiste, comparant les versions de ligne, telles que SQLBase ROWID ou Sybase TIMESTAMP.<br /><br /> SQL_SCCO_OPT_VALUES - Cursor utilise un contrôle de concurrence optimiste, comparant les valeurs.|  
|SQL_STATIC_SENSITIVITY (ODBC 2.0)|Un bitmask SQLINTEGER énumérant si les modifications apportées par une application à un curseur statique ou à clé par **SQLSetPos** ou des instructions de mise à jour ou de suppression positionnées peuvent être détectées par cette application.<br /><br /> SQL_SS_ADDITIONS - Les lignes ajoutées sont visibles au curseur; le curseur peut faire défiler à ces lignes. Lorsque ces lignes sont ajoutées au curseur est dépendante du conducteur.<br /><br /> SQL_SS_DELETIONS - Les lignes supprimées ne sont plus disponibles pour le curseur et ne laissent pas de « trou » dans l’ensemble de résultats ; après que le curseur défile d’une ligne supprimée, il ne peut pas revenir à cette ligne.<br /><br /> SQL_SS_UPDATES - Mises à jour des rangées sont visibles par le curseur; si le curseur fait défiler et retourne à une ligne mise à jour, les données retournées par le curseur sont les données mises à jour, et non les données d’origine. Cette option ne s’applique qu’aux curseurs statiques ou aux mises à jour sur les curseurs pilotés par les clés qui ne mettent pas à jour la clé. Cette option ne s’applique pas pour un curseur dynamique ou dans le cas où une clé est modifiée dans un curseur mixte.<br /><br /> La question de savoir si une application peut détecter les modifications apportées au résultat défini par d’autres utilisateurs, y compris d’autres curseurs dans la même application, dépend du type de curseur.|  
  
 Une application ODBC 3 *.x* travaillant avec un conducteur ODBC 3 *.x* ne devrait pas appeler **SQLGetInfo** avec les arguments *InfoType* décrits dans le tableau précédent, mais devrait utiliser les arguments ODBC 3 *.x* *InfoType* énumérés dans le paragraphe suivant. Il n’y a pas de correspondance individuelle entre les arguments *d’InfoType* utilisés dans ODBC 2. *x* et ceux utilisés dans ODBC 3 *.x*. Une application ODBC 3 *.x* fonctionnant avec un ODBC 2. *x* pilote, d’autre part, devrait utiliser les arguments *InfoType* décrit précédemment.  
  
 Certains des types d’information dans le tableau précédent sont dépréciés en faveur des types d’information d’attributs de curseur. Ces types d’information dépréciés sont SQL_FETCH_DIRECTION, SQL_LOCK_TYPES, SQL_POS_OPERATIONS, SQL_POSITIONED_STATEMENTS, SQL_SCROLL_CONCURRENCY et SQL_STATIC_SENSITIVITY. Les nouveaux types d’attributs curseurs sont SQL_XXX_CURSOR_ATTRIBUTES1and SQL_XXX_CURSOR_ATTRIBUTES2, où XXX est égal à DYNAMIC, FORWARD_ONLY, KEYSET_DRIVEN ou STATIC. Chacun des nouveaux types indique les capacités du conducteur pour un seul type de curseur. Pour plus d’informations sur ces options, consultez la description de la fonction [SQLGetInfo.](../../../odbc/reference/syntax/sqlgetinfo-function.md)
