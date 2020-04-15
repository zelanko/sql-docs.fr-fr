---
title: Fast Forward-Only Cursors (ODBC) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 50d79875e0f3f661c0a959f50ce68c4f2761d186
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298415"
---
# <a name="fast-forward-only-cursors-odbc"></a>Curseurs avant uniquement rapides (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lorsqu’il est [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]relié [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à une instance de , le conducteur native Client ODBC prend en charge les optimisations de performance pour les curseurs avant seulement et lus. Les curseurs avant uniquement rapides sont implémentés en interne par le pilote et le serveur d'une manière très semblable aux jeux de résultats par défaut. Les curseurs avant uniquement rapides présentent d'autres caractéristiques, au-delà de leurs performances élevées :  
  
-   [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) n’est pas pris en charge. Les colonnes de jeu de résultats doivent être liées à des variables de programme.  
  
-   Le serveur ferme automatiquement le curseur lorsque la fin de celui-ci est détectée. L’application doit toujours appeler [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) ou [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), mais le conducteur n’a pas à envoyer la demande proche au serveur. Cela permet d'économiser un aller-retour au serveur par le biais du réseau.  
  
 L'application demande des curseurs avant uniquement rapides à l'aide de l'attribut d'instruction SQL_SOPT_SS_CURSOR_OPTIONS spécifique au pilote. Lorsqu'ils sont définis avec la valeur SQL_CO_FFO, les curseurs avant uniquement rapides sont activés sans auto-extraction. Lorsqu'ils sont définis sur SQL_CO_FFO_AF, l'option d'auto-extraction est également activée. Pour plus d’informations sur l’autofetch, voir [Using Autofetch with ODBC Cursors](../../../relational-databases/native-client-odbc-cursors/programming/using-autofetch-with-odbc-cursors.md).  
  
 Les curseurs avant uniquement rapides avec auto-extraction peuvent être utilisés pour extraire un petit jeu de résultats avec un seul aller-retour au serveur. Dans ces étapes, *n* est le nombre de lignes à retourner:  
  
1.  Affectez la valeur SQL_CO_FFO_AF à SQL_SOPT_SS_CURSOR_OPTIONS.  
  
2.  Réglez SQL_ATTR_ROW_ARRAY_SIZE à *n* 1.  
  
3.  Lier les colonnes de résultat à des tableaux d’éléments *n* et 1 (pour être sûr si *n* - 1 rangées sont effectivement récupérés).  
  
4.  Ouvrez le curseur avec **SQLExecDirect** ou **SQLExecute**.  
  
5.  Si le statut de retour est SQL_SUCCESS, appelez **SQLFreeStmt** ou **SQLCloseCursor** pour fermer le curseur. Toutes les données des lignes seront dans les variables de programme liées.  
  
 Avec ces étapes, le **SQLExecDirect** ou **SQLExecute** envoie une demande ouverte de curseur avec l’option autofetch activée. Lors de cette demande unique de la part du client, le serveur :  
  
-   ouvre le curseur ;  
  
-   génère le jeu de résultats et envoie les lignes au client ;  
  
-   détecte la fin du curseur et le ferme, la taille de l'ensemble de lignes ayant été définie avec une unité de plus que le nombre de lignes dans le jeu de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de la programmation de Cursesor &#40;&#41;oDBC](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
