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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 940bcc3e2ee6a042394797d6038028cce64862f1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305950"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Suppression de lignes dans l’ensemble de lignes avec SQLSetPos
L’opération de suppression de **SQLSetPos** permet à la source de données de supprimer une ou plusieurs lignes sélectionnées d’une table. Pour supprimer des lignes avec **SQLSetPos**, l’application appelle **SQLSetPos** avec l' *opération* définie à SQL_DELETE et *RowNumber* définie sur le numéro de la ligne à supprimer. Si *RowNumber* a la valeur 0, toutes les lignes de l’ensemble de lignes sont supprimées.  
  
 Une fois **SQLSetPos** retourné, la ligne supprimée est la ligne actuelle et son état est SQL_ROW_DELETED. La ligne ne peut pas être utilisée dans d’autres opérations positionnées, telles que les appels à **SQLGetData** ou **SQLSetPos**.  
  
 Lors de la suppression de toutes les lignes de l’ensemble de lignes (*NombLigne* est égal à 0), l’application peut empêcher le pilote de supprimer certaines lignes à l’aide du tableau d’opérations de ligne, de la même façon que pour l’opération de mise à jour de **SQLSetPos**. (Voir [mise à jour de lignes dans l’ensemble de lignes avec SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Chaque ligne supprimée doit être une ligne qui existe dans le jeu de résultats. Si les mémoires tampons de l’application ont été remplies par l’extraction et si un tableau d’état de ligne a été conservé, ses valeurs à chacune de ces positions de ligne ne doivent pas être SQL_ROW_DELETED, SQL_ROW_ERROR ou SQL_ROW_NOROW.
