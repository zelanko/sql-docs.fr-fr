---
title: Suppression des lignes dans le Rowset avec SQLSetPos (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 940bcc3e2ee6a042394797d6038028cce64862f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305950"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Suppression de lignes dans l’ensemble de lignes avec SQLSetPos
L’opération de suppression de **SQLSetPos** permet à la source de données de supprimer une ou plusieurs rangées sélectionnées d’une table. Pour supprimer les lignes avec **SQLSetPos**, l’application appelle **SQLSetPos** avec *Opération* réglée à SQL_DELETE et *RowNumber* réglé au nombre de la ligne à supprimer. Si *RowNumber* est 0, toutes les lignes dans le ram ensemble sont supprimées.  
  
 Après le retour **de SQLSetPos,** la ligne supprimée est la ligne actuelle et son statut est SQL_ROW_DELETED. La ligne ne peut pas être utilisée dans d’autres opérations positionnées, comme les appels à **SQLGetData** ou **SQLSetPos**.  
  
 Lors de la suppression de toutes les lignes de l’achambre *(RowNumber* est égal à 0), l’application peut empêcher le conducteur de supprimer certaines lignes en utilisant le tableau d’opération de la ligne, de la même manière que pour l’opération de mise à jour de **SQLSetPos**. (Voir [Mise à jour des lignes dans le Rowset avec SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Chaque ligne supprimée doit être une ligne qui existe dans le jeu de résultats. Si les tampons d’application ont été remplis par aller chercher et si un tableau d’état de ligne a été maintenu, ses valeurs à chacune de ces positions de rangée ne devraient pas être SQL_ROW_DELETED, SQL_ROW_ERROR, ou SQL_ROW_NOROW.
