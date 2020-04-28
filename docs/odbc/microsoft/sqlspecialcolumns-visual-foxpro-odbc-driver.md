---
title: SQLSpecialColumns (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96b439674c8bda3494b4cefd0c1118602b537cd0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299379"
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 1  
  
 Récupère l’ensemble optimal de colonnes qui identifie de façon unique une ligne dans la table.  
  
 Le pilote ODBC Visual FoxPro retourne les colonnes qui composent la clé primaire de la table FoxPro. (Voir [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) Si elle est appelée avec *fColType* défini sur SQL_ROWVER, aucune colonne n’est retournée. **SQLSpecialColumns** fonctionne uniquement pour les sources de données qui sont des [bases de](../../odbc/microsoft/visual-foxpro-terminology.md)données.  
  
 Pour plus d’informations, consultez [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) dans le *Guide de référence du programmeur ODBC*.
