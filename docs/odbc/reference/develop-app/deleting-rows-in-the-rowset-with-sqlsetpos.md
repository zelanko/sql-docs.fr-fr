---
title: Suppression de lignes dans l’ensemble de lignes avec SQLSetPos | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e39b70f92f7b239b011cdd4fdd6abd36c27561c2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076805"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Suppression de lignes dans l’ensemble de lignes avec SQLSetPos
L’opération de suppression de **SQLSetPos** rend la source de données à supprimer une ou plusieurs lignes sélectionnées d’une table. Pour supprimer des lignes avec **SQLSetPos**, l’application appelle **SQLSetPos** avec *opération* défini sur SQL_DELETE et *RowNumber* définie sur le numéro de la ligne à supprimer. Si *RowNumber* est 0, toutes les lignes dans l’ensemble de lignes sont supprimées.  
  
 Après avoir **SQLSetPos** est retournée, la ligne supprimée est la ligne actuelle et son statut est SQL_ROW_DELETED. La ligne ne peut pas être utilisée dans toutes les opérations positionnées supplémentaires, comme les appels à **SQLGetData** ou **SQLSetPos**.  
  
 Lors de la suppression de toutes les lignes de l’ensemble de lignes (*RowNumber* est égal à 0), l’application peut empêcher le pilote de supprimer certaines lignes à l’aide du tableau d’opération de ligne, de la même façon que l’opération de mise à jour de **SQLSetPos** . (Consultez [mise à jour des lignes dans l’ensemble de lignes avec SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Chaque ligne supprimée doit être une ligne qui existe dans le jeu de résultats. Si les mémoires tampons d’application ont été remplies par extraction et si un tableau d’état de ligne a été maintenu, ses valeurs à chacune de ces positions de ligne ne doivent pas être SQL_ROW_DELETED, SQL_ROW_ERROR ou SQL_ROW_NOROW.
