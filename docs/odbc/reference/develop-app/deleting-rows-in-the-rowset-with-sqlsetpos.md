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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076805"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Suppression de lignes dans l’ensemble de lignes avec SQLSetPos
L’opération de suppression de **SQLSetPos** permet à la source de données de supprimer une ou plusieurs lignes sélectionnées d’une table. Pour supprimer des lignes avec **SQLSetPos**, l’application appelle **SQLSetPos** avec l' *opération* définie à SQL_DELETE et *RowNumber* définie sur le numéro de la ligne à supprimer. Si *RowNumber* a la valeur 0, toutes les lignes de l’ensemble de lignes sont supprimées.  
  
 Une fois **SQLSetPos** retourné, la ligne supprimée est la ligne actuelle et son état est SQL_ROW_DELETED. La ligne ne peut pas être utilisée dans d’autres opérations positionnées, telles que les appels à **SQLGetData** ou **SQLSetPos**.  
  
 Lors de la suppression de toutes les lignes de l’ensemble de lignes (*NombLigne* est égal à 0), l’application peut empêcher le pilote de supprimer certaines lignes à l’aide du tableau d’opérations de ligne, de la même façon que pour l’opération de mise à jour de **SQLSetPos**. (Voir [mise à jour de lignes dans l’ensemble de lignes avec SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Chaque ligne supprimée doit être une ligne qui existe dans le jeu de résultats. Si les mémoires tampons de l’application ont été remplies par l’extraction et si un tableau d’état de ligne a été conservé, ses valeurs à chacune de ces positions de ligne ne doivent pas être SQL_ROW_DELETED, SQL_ROW_ERROR ou SQL_ROW_NOROW.
